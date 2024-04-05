<template>
    <header>
        <figure>
            <img src="https://th.bing.com/th/id/OIG2.ozgVD8yt9rSu5T8CjgIe?pid=ImgGn" alt="Logo">
        </figure>
        <nav>
            <ul>
                <li>Home</li>
                <li>Projects</li>
                <li>Profile</li>
                <li>Contacts</li>
            </ul>
        </nav>
    </header>
</template>

<script>
export default {
    name: 'HeaderApp',
    data() {


        return {}
    }
}
</script>

<style lang="scss" scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #000836;
    padding: 20px;
    margin-bottom: 80px;

    figure {
        width: 120px;

        img {
            border-radius: 50%;
            object-fit: contain;
        }
    }

    nav {
        ul {
            display: flex;
            gap: 50px;

            li {
                color: #e8f0f1;
                list-style-type: none;
                font-size: 24px;
                font-weight: 700;
                cursor: pointer;

                &:hover {
                    color: #f9a300;
                }
            }
        }
    }
}
</style>