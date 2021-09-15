<template>
  <div class="main">
    <div class="title">
      Simulador de Prestamos
    </div>
    <div class="form">
      <div class="input_field">
        <label for="">Monto</label>
        <input type="number" class="input" v-model="amount">
      </div>
      <div class="input_field">
        <label for="">Numero de cuotas</label>
        <input type="number" class="input" v-model="loan_term">
      </div>
      <div class="input_field">
        <label for="">Cuota doble</label>
        <div class="custom_select">
          <select v-model="is_double_fee">
            <option value="false">No</option>
            <option value="true">Si</option>
          </select>
        </div>
      </div>
      <div class="input_field">
        <label for="">Tasa de Interés Anual()</label>
        <input type="number" class="input" v-model="interest_rate">
      </div>
      <div class="input_field">
        <input type="submit" value="Simular" class="btn" v-on:click="simulate">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    msg: String
  },
  data: function(){
    return {
      amount: 0,
      loan_term: 0,
      is_double_fee: 'false',
      interest_rate: 0
    }
  },
  methods: {
    simulate: function() {
      const data = {
        'amount': this.amount,
        'loan_term': this.loan_term,
        'interest_rate': this.interest_rate
      }

      fetch('http://localhost:3000/calculator', {
        method: 'POST',
        body: JSON.stringify(data),
        headers: {
          'Content-Type': 'application/json'
        }
      })
      .then(res => res.json())
      .catch(err => console.error("Error", err))
      .then(response => console.log("Success", response))
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .main {
    max-width: 500px;
    width: 100%;
    background: #fff;
    margin: 20px auto;
    padding: 30px;
    box-shadow: 1px 1px 2px rgba(0,0,0,0.125);
  }
  .main .title {
    font-size: 24px;
    font-weight: 700;
    margin-bottom: 25px;
    color: #fec107;
    text-transform: uppercase;
    text-align: center;
  }
  .main .form {
    width: 100%;
  }

  .main .form .input_field {
    margin-bottom: 15px;
    display: flex;
    align-items: center;
  }

  .main .form .input_field label {
    width: 200px;
    /*color: #757575;*/
    margin-right: 10px;
    font-size: 14px;
  }

  .main .form .input_field .input {
    width: 100%;
    outline: none;
    border: 1px solid #d5dbd9;
    font-size: 15px;
    padding: 8px 10px;
    border-radius: 3px;
    transition: all 0.3s ease;
  }

  .main .form .input_field .custom_select {
    position: relative;
    width: 100%;
    height: 37px;
  }

  .main .form .input_field .custom_select select{
    -webkit-appearance: none;
    appearance: none;
    border: 1px solid #d5dbd9;
    width: 100%;
    height: 100%;
    border-radius: 3px;
    outline: none;
  }

  .main .form .input_field .custom_select:before {
    content: "";
    position: absolute;
    top: 12px;
    right: 10px;
    border: 8px solid;
    border-color: #d5dbd9 transparent transparent transparent;
    pointer-events: none;
  }

  .main .form .input_field .input:focus{
    border: 1px solid #fec107;
  }

  .main .form .input_field .btn {
    width: 100%;
    padding: 8px 10px;
    font-size: 15px;
    border: 0;
    background: #fec107;
    color: #fff;
    cursor: pointer;
    border-radius: 3px;
    outline: none;
  }

  .main .form .input_field .btn:hover {
    background: #ffd658;
  }

  @media (max-width: 420px) {
    .main .form .input_field {
      flex-direction: column;
      align-items: flex-start;
    }

    .main .form .input_field label{
      margin-bottom: 5px;
    }
    
  }
</style>
