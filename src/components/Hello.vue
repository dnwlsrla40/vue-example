<template>
    <div>
        <v-text-field :rules="nameRules" required v-model="member.name"
            label="name" type="text" prepend-icon="mdi-account"> </v-text-field>
        <v-text-field :rules="passwordRules" required v-model="member.password"
            label="Password" type="password" prepend-icon="mdi-lock"> </v-text-field>
    </div>
</template>

<script>
export default {

}
</script>
