<template>

  <div class="note" >
</br></br><h1>แบบสอบถามSaturdayJS</h1>
<input type="text" name="name" value=""  v-model="name" placeholder="ชื่อ"></br>
<input type="date" name="" value="" v-model="date" placeholder="วันที่"></br>
<textarea name="note" cols="50%" rows="15%" v-model="note"> ..NOTE.. </textarea></br>
<input type="button" name="save" value="save" @click="insert()">
<input type="reset" name="cancel" value="cancel" @click="clear()"></br></br></br>
 </div>
</template>

<script>
// Initialize Firebaseง
import firebase from 'firebase'
var config = {
  apiKey: 'AIzaSyAKTflFSPUw-0BHPiN3jwEfj2vmWtPBj5o',
  authDomain: 'query-1726.firebaseapp.com',
  databaseURL: 'https://query-1726.firebaseio.com',
  projectId: 'query-1726',
  storageBucket: 'query-1726.appspot.com',
  messagingSenderId: '1056071193148'
}
var firebaseApp = firebase.initializeApp(config)
var db = firebaseApp.database()
var getData = db.ref(this.name)
export default {
  name: 'app',
  firebase: {
    datas: []
  },
  data () {
    return {
      note: '',
      name: '',
      date: '',
      datas: getData
    }
  },
  methods: {
    insert: function () {
      if (this.note !== '' && this.name !== '' && this.date !== '') {
        db.ref(this.name).push(this.name)
        db.ref(this.name).push(this.date)
        db.ref(this.name).push(this.note)
        this.note = ''
        this.date = ''
        this.name = ''
      }
    }
}
}
</script>
<style>
.note {
  display: inline-block;
  margin: 10 10px;
  margin-left: 5%;
}
</style>
