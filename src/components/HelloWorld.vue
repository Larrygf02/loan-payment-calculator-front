<template>
  <div class="main">
    <div class="title">
      Simulador de Prestamos
    </div>
    <div class="form">
      <div class="input_field">
        <label for="">Monto</label>
        <input type="number" class="input">
      </div>
      <div class="input_field">
        <label for="">Numero de cuotas</label>
        <input type="number" class="input">
      </div>
      <div class="input_field">
        <label for="">Cuota doble</label>
        <div class="custom_select">
          <select>
            <option value="false">No</option>
            <option value="true">Si</option>
          </select>
        </div>
      </div>
      <div class="input_field">
        <label for="">Tasa de Interés Anual()</label>
        <input type="number" class="input">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
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
    color: #757575;
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
</style>
