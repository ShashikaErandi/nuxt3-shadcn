
import { Sidebar } from 'lucide-vue-next';

import { SidebarMenu } from '#build/components';
<template>
    <div class="grid lg:flex items-start">
        <div>
            <Sidebar />
        </div>
        <div class="p-8 w-full">
            <slot />
        </div>
    </div>
</template>
  