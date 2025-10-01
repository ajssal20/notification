<script>
  import '../app.css';
  import favicon from '$lib/assets/favicon.svg';

  let description = "";
  let title = "";

  async function notify() {
    let permission = Notification.permission;

    if (permission !== "granted") {
      permission = await Notification.requestPermission();
    }

    if (permission === "granted") {
      new Notification(title || "Neue Nachricht", {
        body: description || "Du hast eine Nachricht erhalten",
        icon: favicon
      });
    }
  }
</script>

  <h1 class="text-xl font-semibold text-pink-900 text-center">
    Create a new Notification
  </h1>

  <div class="flex flex-col space-y-2">
    <label for="description" class="font-medium text-pink-900">
      Description
    </label>
    <textarea
      bind:value={description}
      name="description"
      rows="3"
      class="p-2 rounded-xl border border-pink-300 focus:ring-2 focus:ring-pink-400 outline-none"
    ></textarea>
  </div>

  <div class="flex flex-col space-y-2">
    <label for="title" class="font-medium text-pink-900">
      Title
    </label>
    <input
      bind:value={title}
      type="text"
      placeholder="Title"
      name="title"
      class="p-2 rounded-xl border border-pink-300 focus:ring-2 focus:ring-pink-400 outline-none"
    />
  </div>

  <button
    on:click={notify}
    class="w-full px-4 py-2 rounded-2xl bg-pink-200 text-pink-900 font-medium shadow-md hover:bg-pink-300 transition"
  >
    Create Notification
  </button>
