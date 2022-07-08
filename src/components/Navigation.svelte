<script>
    import {navigation} from "../store/data";
</script>

<nav>
    <ul>
        {#each navigation as item}
            <li>
                <a href={item.url}>{item.name}</a>
            </li>
        {/each}
    </ul>
</nav>

<style
type="scss"
>
@import "../scss/mixins.scss";
@import "../scss/variables.scss";

ul{
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    li{
        list-style: none;
        a{
            text-decoration: none;
            color: $black;
            font-size: 1.2em;
            padding: toRem(10) toRem(5);
            margin: toRem(10);
            transition: $transition;
            position: relative;
            &::after{
                content: "";
                position: absolute;
                bottom: 0;
                left: 0;
                width: 0;
                height: toRem(3);
                background: $black;
                transition: $transition;
                }
            &:hover{
               &::after{
                   width: 100%;
               }
            }
        }
    }
}

</style>