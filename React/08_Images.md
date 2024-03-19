## Interview que on Images

1. **Difference between lazy and eager loading:**
   - **Lazy Loading** delays the initialization of resources until they are needed. It loads resources like images or data only when accessed or a condition is met, reducing initial load times and enhancing the speed and responsiveness of applications. This approach is more efficient for mobile users or limited bandwidth, as it loads only required resources. However, it may introduce a delay when accessing resources for the first time [3].
   - **Eager Loading** initializes or loads resources as soon as the code is executed or the page is loaded, regardless of immediate need. This ensures immediate availability of resources, providing a smoother post-load experience but can lead to longer initial load times. It consumes more bandwidth and memory upfront by loading all resources, which is less efficient for limited resources [3].

2. **if the  app has broken link on page, how to handle it:**
   - To handle broken links on a page, you can implement a feature that checks for the existence of the linked resource before rendering the link. If the resource is not available, you can display a message indicating that the link is broken or provide an alternative link. This can be achieved through server-side checks or client-side JavaScript that attempts to fetch the resource and handles the error if the fetch fails.

3. **Handling fast scrolling where images are not immediately available, If user scrolls the screen faster,the images will not be available immediately how will you handle it:**
   - When a user scrolls the screen faster, and images are not available immediately, you can implement a combination of lazy loading and placeholder images. Lazy loading ensures that images are loaded only when they are about to appear in the viewport, reducing the initial page load time. Placeholder images can be used to reserve space for the images, preventing layout shifts as the images load. This approach provides a smoother user experience by ensuring that the page layout remains stable even as images are being loaded [6][7].

4. **Adding lazy loading to banner and promo images, Will you add lazy loading on banner , promo image?:**
   - For banner and promo images, it is recommended to use `loading='eager'` to ensure these critical elements are loaded immediately. This is particularly important for the home page and above-the-fold content, as it helps preserve resources until the images are needed, keeping load times down. However, this approach may sometimes cause a delay for metrics like Google's 'First Contentful Paint' (FCP), so it's crucial to balance the need for immediate availability with the overall performance of the website [1].

