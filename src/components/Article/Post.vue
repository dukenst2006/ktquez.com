<template>
  <div class="fullX post" v-html="post | marked"></div>    
</template>

<script>
  import marked from 'marked'
  import hljs from 'highlight.js'

  export default {
    props: {
      post: {
        required: true,
        type: String
      }
    },
    compiled () {
      marked.setOptions({
        highlight: (code, lang) => {
          return hljs.highlightAuto(code, [lang]).value
        }
      })
    },
    filters: {
      marked
    }
  }
</script>

<style lang="postcss">

  :root {
    --font: Raleway, Calibri, 'trebuchet MS';
  }

  .post {
    
    & h1, 
    & h2, 
    & h3, 
    & h4, 
    & h5, 
    & h6 {
      color: #000;
      float: left;
      font-weight: bold;
      font-family: var(--font);
      margin-top: 20px;
    }

    & strong {
      font-family: var(--font);
    }

    & img {
      width: 100%;
    }

    & a {
      color: #4ac6b7;
    }

    & hr {
      border: 1px solid #dedede;
    }

    & p {
      margin: 20px 0 10px;
      line-height: 1.5em;
      font-size: 17px;
      letter-spacing: .5px;    
      width: 100%;
      float: left;
      
      /* code inline */
      & code {
        font-size: 14px;
        padding: 6px;        
      }
    }  

    & pre {
      width: 100%;
      margin: 30px 0;

      & code {
        padding: 20px;
        margin: 10px 0;
        width: calc(100% - 40px);
        float:left;
        font-size: 14px;
        overflow-y: auto;
        line-height: 22px;
      }
    }      

    & table {
      
      & tr, 
      & td,
      & th {
        border: 1px solid #ddd;
        padding: 10px;
      }

      & th {
        background: #fff;
      }

      & tr:nth-child(even) {        
        background: #fff;
      }

      & td {
      }
    }

    & ol, 
    & ul, 
    & li {
      float: left;
      margin-left: 10px;
      width: calc(100% - 10px);
    }

    & ul {
      margin-top: 20px;
    }

    & li {
      margin-bottom: 10px;
    }

    & blockquote p{
      padding-left: 20px;
      border-left: 4px solid #ccc;
      width: calc(100% - 20px);
    }
  }
</style>
