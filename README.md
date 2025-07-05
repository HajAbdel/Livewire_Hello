# Hello Livewire
Hello Livewire Commands

# Install livewire

```cmd
composer require livewire/livewire
```

# Make component 

```cmd
php artisan make:livewire NomComponent
```

or make it in sub folder

```cmd
php artisan make:livewire FolderName/NomComponent
```

- Generated Class: app/Livewire/NomComposant.php

```php
<?php
namespace App\Http\Livewire;
use Livewire\Component;
class NomComposant extends Component
{
    public $name = '';
    public $message = '';
    public function sayHello()
    {
        $this->message = "Bonjour, " . $this->name;
    }
    public function render()
    {
        return view('livewire.nom-composant');
    }
}
```

- Generated Vue : resources/views/livewire/nom-composant.blade.php
```html
<div>
    <input type="text" wire:model="name" placeholder="Entrez votre nom" class="border p-2 rounded">
    <button wire:click="sayHello" class="bg-blue-500 text-white px-4 py-2 rounded ml-2">
        Say Hello
    </button>
    @if ($message)
        <p class="mt-3 text-green-600">{{ $message }}</p>
    @endif
</div>
```
  
# Code of layout/app (resources/views/layouts/app.blade.php) :

```html
<head>
    @livewireStyles
</head>
<body>
    {{ $slot ?? '' }}
    @livewireScripts
</body>
```
# To call livewire component

```html
<livewire:nom-composant />
```
if component is in sub folder

```html
<livewire:admin.dashboard />
```

or using parameter

```html
<livewire:nom-composant :post="$post" />
```

# Bonus : Recompile if Livewire used with Vite

```cmd
npm run dev
```

