<template>
  <li>
    <h3>{{ fullName }}</h3>
    <h4>${{ rate }}/hour</h4>
    <div>
      <base-badge
        v-for="area in areas"
        :key="area"
        :type="area"
        :title="area"
      />
    </div>
    <div class="actions">
      <base-button mode="outline" link :to="coachContactLink"
        >Contact</base-button
      >
      <base-button link :to="coachDetailsLink">View details</base-button>
    </div>
  </li>
</template>

<script>
import BaseButton from '@/components/ui/BaseButton';
import BaseBadge from '@/components/ui/BaseBadge';
export default {
  components: { BaseBadge, BaseButton },
  props: {
    id: {
      type: String,
      required: true,
    },
    firstName: {
      type: String,
      required: true,
    },
    lastName: {
      type: String,
      required: true,
    },
    rate: {
      type: Number,
      required: true,
    },
    areas: {
      type: Array,
      required: true,
    },
  },
  computed: {
    fullName() {
      return this.firstName + ' ' + this.lastName;
    },
    coachContactLink() {
      return this.$route.path + '/' + this.id + '/contact';
    },
    coachDetailsLink() {
      return this.$route.path + '/' + this.id;
    },
  },
};
</script>

<style scoped>
li {
  margin: 1rem 0;
  border: 1px solid #424242;
  border-radius: 12px;
  padding: 1rem;
}

h3 {
  font-size: 1.5rem;
}

h3,
h4 {
  margin: 0.5rem 0;
}

div {
  margin: 0.5rem 0;
}

.actions {
  display: flex;
  justify-content: flex-end;
}
</style>
