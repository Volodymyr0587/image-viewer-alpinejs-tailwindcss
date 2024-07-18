# image-viewer-alpinejs-tailwindcss
swapping the big image with a smaller image when clicked

```html
{{-- Images viewer --}}
<div x-data="{ bigImage: '{{ isset($media->images) && $media->images->count() > 0 ? asset('storage/' . $media->images->first()->path) : '' }}' }"
    class="grid gap-4">
    @if ($media->images && $media->images->count() > 0)
    <div>
        <img :src="bigImage"
            class="h-auto w-full max-w-full rounded-lg object-cover object-center md:h-[480px]"
            alt="Big Image" />
    </div>

    <div class="grid grid-cols-6 gap-4">
        @foreach ($media->images as $image)
        <div>
            <img @click="bigImage = '{{ asset('storage/' . $image->path) }}'"
                src="{{ asset('storage/' . $image->path) }}"
                class="object-cover object-center h-20 max-w-full rounded-lg cursor-pointer"
                alt="gallery-image" />
        </div>
        @endforeach
    </div>
    @else
    <div class="text-center">
        <p>No images available for this media.</p>
    </div>
    @endif
</div>
{{-- END Images viewer --}}

```
