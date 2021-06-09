<template>
  <div class="card" :class="user.gender">
    <img
      class="card__img"
      :src="user.picture"
      :alt="`${user.firstName} ${user.lastName}`"
    />
    <div class="card__cta" :class="`border-${user.gender}`">
      <h2>
        <span>{{ user.title }}.</span>
        {{ user.firstName }}
        {{ user.lastName }}
      </h2>
      <span>
        <i class="fas fa-map-marker-alt"></i> {{ user.streetNumber }}
        {{ user.streetName }}, {{ user.city }}, {{ user.country }}
      </span>
      <span> <i class="fas fa-phone-alt"></i> Phone: {{ user.phone }} </span>
      <span> <i class="fas fa-envelope"></i> {{ user.email }} </span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    user: Object
  }
};
</script>

<style lang="scss">
.card {
  padding: 2rem;
  border-radius: 1rem;
  display: flex;
  align-items: center;

  &__img {
    border-radius: 50%;
    margin-right: 3rem;
  }

  &__cta {
    display: flex;
    flex-direction: column;
    font-size: 1.4rem;
    line-height: 1.8;
    padding: 2rem 0;

    & i {
      margin-right: 0.5rem;
    }

    h2 {
      font-size: 2rem;
      margin-bottom: 1rem;
      letter-spacing: 0.2rem;

      span {
        font-size: 1.4rem;
        font-weight: normal;
      }
    }
  }
}

.male {
  background-color: #181818;
  color: white;
}

.female {
  background-color: #d4bcd6;
  color: #181818;
}

.border-male {
  border-top: 1px solid white;
  border-bottom: 1px solid white;
}

.border-female {
  border-top: 1px solid #181818;
  border-bottom: 1px solid #181818;
}
</style>
