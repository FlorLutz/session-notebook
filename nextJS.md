# NextJS

## Basics

- framework for react (which is a library for js)
- more rigid, controls a lot of the work flow
- takes care of routing through folder structure
- bundler, transpiler and development server built in
- differences to react (as with vite):
  - document.js instead of main index.html
  - css modules instead of css
- server side rendering enabled
- image optimization through `import Image from next`
- height and width must be given:

```
<Image
    src="/images/a_small_dog.jpg"
    height={144}
    width={144}
    alt="A picture of a small dog"
  />
```

- images from external sources must also be included in the next.config.js:

```
const nextConfig = {
  reactStrictMode: true,
  images: {
    domains: ["images.unsplash.com"],
  },
};
```

## (Dynamic) Routing

- folders and files in pre-built pages-folder create routes
- any index.js is default for folder (www.app.com/faq will render pages/faq/index.js)
- useRouter hook is used to create dynamic routes
- `[slug].js` names refer to dynamic naming
- dynamic routes can also include page numbers, see the example below:

```
// pages/movies/categories/[categorySlug]/page/[pageNumber].js
import { useRouter } from "next/router";

export default function CategoryPage() {
  const router = useRouter();
  const { categorySlug, pageNumber } = router.query;

  return (
    <div>
      <p>Category Slug: {categorySlug}</p>
      <p>Page Number: {pageNumber}</p>
    </div>
  );
}
```

- use the Link component to refer to dynamic routes:

```
import Link from "next/link";

export default function Movies({ movies }) {
  return (
    <ul>
      {movies.map(({ id, slug, title }) => (
        <li key={id}>
          <Link href={`/movies/${slug}`}>{title}</Link>
        </li>
      ))}
    </ul>
  );
}
```

- routing changes can also be triggered in events through the router.push("/path") method:

```
import { useRouter } from "next/router";

export default function Form() {
  const router = useRouter();

  function handleSubmit(event) {
    // some data handling … ✨

    router.push("/home");
  }

  return <form onSubmit={handleSubmit}>…</form>;
}
```

- Head component with hook allows for individual page titles and favicons:

```
import Head from "next/head";

export default function Movies() {
  return (
    <>
      <Head>
        <title>Movies</title>
        <meta name="viewport" content="initial-scale=1.0, width=device-width" />
      </Head>
      <ul>…</ul>
    </>
  );
}
```
