<template>
    <table v-if="meetings.length > 0">
        <thead>
        <tr>
            <th>Nazwa spotkania</th>
            <th>Opis</th>
            <th>Uczestnicy</th>
            <th></th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="meeting in meetings" :key="meeting.name">
            <td>{{ meeting.name }}</td>
            <td>{{ meeting.description }}</td>
            <td>
                <ol>
                    <li v-for="participant in meeting.participants">{{participant}}</li>
                </ol>
            </td>
            <td>
                <button></button>
            </td>

        </tr>
        </tbody>
    </table>
</template>

<script>
    export default {
        props: ['meetings']
    }
</script>