

<div class="card">
    <slot>

    </slot>
</div>

<style>
.card {
    background: #fff;
    padding: 20px;
    border-radius: 6px;
    box-shadow: 0px  2px 4px rgba(0,0,0,0.1);
}
@media screen and (max-width: 900px) {
     
    .card {
        margin: 5px;
    background: #fff;
    padding: 20px;
    border-radius: 6px;
    box-shadow: 0px  2px 4px rgba(0,0,0,0.1);
}
}
</style>