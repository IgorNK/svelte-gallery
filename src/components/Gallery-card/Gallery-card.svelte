<script lang="ts">
  export let image: string;
  export let title: string;
  export let info: string;
  import "../../routes/index.css";
</script>

<div class="GalleryCard">
  <img class="GalleryCard-image" alt={image} src={image} />
  <div class="GalleryCard-overlay" />
  <div class="GalleryCard-container">
    <a class="GalleryCard-title">{title}</a>
    <p class="GalleryCard-info">{info}</p>
  </div>
</div>

<style>
  .GalleryCard {
    width: 100%;
    height: 100%;
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    overflow: hidden;
  }

  .GalleryCard-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    aspect-ratio: 1/0.75;
    cursor: pointer;
  }

  .GalleryCard-container {
    width: 100%;
    height: 100%;
    box-sizing: border-box;
    padding: 10%;
    padding-top: 50%;
    position: absolute;
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    justify-content: center;
    opacity: 0%;
    transform: translate(50em, 0);
  }

  .GalleryCard:hover .GalleryCard-container {
    opacity: 100%;
    transform: translate(0, 0);
    transition: 0.6s ease-out;
  }

  .GalleryCard-title {
    font-family: 'Alegreya', Arial, Helvetica, sans-serif;
    font-weight: 700;
    text-decoration: underline;
    cursor: pointer;
    color: #000;
    text-shadow: 6px 6px 20px #fff,
    -4px 2px 30px #fff;
    font-size: 24px;
    width: 100%;
    text-align: end;
  }

  .GalleryCard-title:hover {
    color: var(--blue);
    transition: 0.4s ease-in-out;
    text-shadow: 6px 6px 20px #ecee6a,
    -4px 2px 30px #fff;
  }

  .GalleryCard-info {
    font-family: 'Alegreya', Arial, Helvetica, sans-serif;
    font-weight: 400;
    font-size: 18px;
    text-shadow: 3px 3px 20px #fff,
    -2px 1px 30px #fff;
    width: 100%;
    text-align: end;
  }

  .GalleryCard-overlay {
    width: 100%;
    height: 100%;
    position: absolute;
    transform: translate(0, 0);
    background-color: rgba(0.0, 0.0, 0.0, 0.5);
  }

  .GalleryCard:hover .GalleryCard-overlay {
    background-color: rgba(0.0, 0.0, 0.0, 0.0);
    transform: translate(-100%, 0);
    transition: 0.6s ease-out;
  }

</style>