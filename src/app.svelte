<script>
  import InputField from './components/InputField.svelte';
  import Checkbox from './components/Checkbox.svelte';
  import SubmitButton from './components/SubmitButton.svelte';
  import Notification from './components/Notification.svelte';

  let name = "";
  let company = "";
  let email = "";
  let phone = "";
  let subject = "";
  let message = "";
  let consent = false;
  let errors = {};
  let notificationMessage = "";

  const validateForm = () => {
    errors = {};

    if (email && !/\S+@\S+\.\S+/.test(email)) errors.email = "Некорректный email";
    if (phone && !/^\d+$/.test(phone)) errors.phone = "Телефон должен содержать только цифры";
    return Object.keys(errors).length === 0; // Вернуть true, если ошибок нет
  };

  const handleSubmit = () => {
    let res = validateForm();
    if (res) {
      notificationMessage = "Данные успешно отправлены.";
      name = "";
      company = "";
      email = "";
      phone = "";
      subject = "";
      message = "";
      consent = false;
      errors = {};
    } 
  };

    const closeNotification = () => {
    notificationMessage = "";
  };
  
</script>
<div class="form-wrapper">
    <form on:submit|preventDefault={handleSubmit}>
    <div class="form-title">
        <h2>For business enquiries please use the form below</h2>
        <p>*Required</p>
    </div>
    <InputField label="Name" bind:value={name} required={true} errorMessage={errors.name} />
    <InputField label="Company" bind:value={company} required={true} errorMessage={errors.company} />
    <InputField label="E-mail" type="email" bind:value={email} required={true} errorMessage={errors.email} />
    <InputField label="Phone" type="tel" bind:value={phone} errorMessage={errors.phone} />
    <InputField label="Subject" bind:value={subject} />
    <InputField label="Message" bind:value={message} required={true} errorMessage={errors.message} />
    <div class="checkbox-wrapper">
        <Checkbox label="I accept Terms and Privacy Policy" bind:checked={consent} />
    </div>
    <div class="btn-wrapper">
        <SubmitButton color="red" />
    </div>
    </form>

     {#if notificationMessage}
    <Notification message={notificationMessage} onClose={closeNotification} />
  {/if}
</div>


<style>
  .form-wrapper {
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    filter: drop-shadow(0 0 50px rgba(0, 0, 0, 0.7));
  }

  .form-title {
    text-align: center;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .form-title h2 {
    font-weight: 400;
    font-size: 18px;
    line-height: 21.6px;
  }

  .form-title p {
    font-weight: 300;
    font-size: 15px;
    line-height: 18px;
    color: rgba(121, 126, 163, 1);
  }

  .checkbox-wrapper {
    display: flex;
    justify-content: center;
  }

  form {
    display: flex;
    flex-direction: column;
    gap: 20px;
    width: 390px;
    border-radius: 27px;
    padding: 45px 40px;
    background-color: rgba(23, 25, 41, 1);
    color: #fff;
  }

  .btn-wrapper {
    margin: 0 auto;
  }
</style>