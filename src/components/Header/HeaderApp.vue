<template>
    <header>
        <figure>
            <img src="https://th.bing.com/th/id/OIG2.ozgVD8yt9rSu5T8CjgIe?pid=ImgGn" alt="Logo">
        </figure>
        <nav>
            <ul>
                <li>
                    <router-link :to="{ name: 'home' }" class="nav-item">
                        Home
                    </router-link>
                </li>

                <li>
                    <router-link :to="{ name: 'projects' }" class="nav-item">
                        Projects
                    </router-link>
                </li>
                <li>Profile</li>
                <li>
                    <router-link :to="{ name: 'contact-us' }" class="nav-item">
                        Contact Us
                    </router-link>
                </li>
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
                font-size: 24px;
                font-weight: 700;
                text-decoration: none;
                list-style-type: none;
                cursor: pointer;

                &:hover {
                    color: #f9a300;
                }
                .nav-item{
                    color: #e8f0f1;
                    font-size: 24px;
                    font-weight: 700;
                    text-decoration: none;
                    &:hover {
                    color: #f9a300;
                    }
                }
            }
        }
    }
}
</style>