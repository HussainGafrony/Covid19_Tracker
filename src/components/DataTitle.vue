<template>
    <div class="text-center">
        <h2 class="text-md-h5 font-weight-bold mt-4">{{ text }}</h2>

        <div class="text-md-h5 mt-4 mb-10">
            {{ timstamp }}
        </div>
    </div>
</template>
<script>
import Moment from 'moment';
export default {

    name: ' DataTitle_',
    props:['text','dataDate'],
    computed:{
        timstamp: function(){
            return Moment(this.dataDate).format('MMMM Do YYYY, h:mm:ss a');
        // return Moment(this.dataDate).format('MMMM Do YYYY');
        }
    }
}
</script>