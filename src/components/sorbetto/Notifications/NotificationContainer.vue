<template>
  <div class="notification-container">
    <transition-group name="fade">
      <NotificationItem
        v-for="notification in notifications"
        :notification="notification"
        :key="notification.id"
      />
    </transition-group>
  </div>
</template>

<script>
const NotificationItem = () =>
  import("@/components/sorbetto/Notifications/Notification");

export default {
  computed: {
    notifications() {
      return this.$store.getters.getNotifications;
    },
  },
  components: {
    NotificationItem,
  },
};
</script>

<style lang="scss" scoped>
.notification-container {
  position: fixed;
  z-index: 1000;
  top: 110px;
  right: 30px;
  width: 400px;
}

@media screen and(max-width: 600px) {
  .notification-container {
    width: 90%;
    max-width: 350px;
  }
}
</style>
