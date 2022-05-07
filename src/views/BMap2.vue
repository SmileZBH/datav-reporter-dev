<template>
    <div>
        <ve-map :data="chartData"></ve-map>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                chartData:{
                    columns: ['税收'],
                    rows: [{
                        '位置':'上海',
                        '税收':123
                    },{
                        '位置':'北京',
                        '税收':456
                    }]
                }
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>