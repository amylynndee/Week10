<template>
    <tr  v-bind:class=" { present: student.present, absent: !student.present }">
        <td>{{ student.name }}</td>
        <td>{{ student.starID }}</td>
        <td><input type="checkbox" v-bind:checked="student.present" v-on:change="arrivedOrLeft(student, $event.target.checked)"></td>
        <td v-show="edit"><img v-on:click="deleteStudent" src="@/assets/delete_2.png"></td>
    </tr>
</template>

<script>
export default {
    name: 'StudentRow',
    props: {
        student: Object,
        edit: Boolean
    },
    methods: {
        arrivedOrLeft(student, present) {
            this.$emit('student-arrived-or-left', student, present)
        },
        deleteStudent() {
            this.$emit('delete-student', this.student)
        }
    }

}
</script>

<style scoped>

.present {
    color: gray;
    font-style: italic;
    background-color: aqua;
}

.absent {
    color: white;
    font-weight: bold;
    background-color: rebeccapurple;
}

</style>