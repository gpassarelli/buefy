<template>
    <section class="api-view">
        <h2 class="title is-4">API</h2>

        <template v-for="component in data">
            <div :key="component.title">
                <h3
                    v-if="component.title"
                    class="subtitle">
                    {{ component.title }}
                </h3>
                <b-tabs>
                    <b-tab-item v-if="component.props" label="Properties">
                        <b-table :data="component.props" :columns="propsColumns"/>
                    </b-tab-item>

                    <b-tab-item v-if="component.slots" label="Slots">
                        <b-table :data="component.slots" :columns="slotsColumns"/>
                    </b-tab-item>

                    <b-tab-item v-if="component.events" label="Events">
                        <b-table :data="component.events" :columns="eventsColumns"/>
                    </b-tab-item>

                    <b-tab-item v-if="component.methods" label="Methods">
                        <b-table :data="component.methods" :columns="methodsColumns"/>
                    </b-tab-item>
                </b-tabs>
            </div>
        </template>
    </section>
</template>

<script>
    export default {
        props: {
            data: Array
        },
        data() {
            return {
                propsColumns: [
                    { label: 'Name', field: 'name', renderHtml: true },
                    { label: 'Description', field: 'description', renderHtml: true },
                    { label: 'Type', field: 'type' },
                    { label: 'Values', field: 'values', renderHtml: true },
                    { label: 'Default', field: 'default', renderHtml: true }
                ],
                slotsColumns: [
                    { label: 'Slot name', field: 'name', renderHtml: true },
                    { label: 'Description', field: 'description', renderHtml: true },
                    { label: 'Props (if scoped)', field: 'props', renderHtml: true }
                ],
                eventsColumns: [
                    { label: 'Name', field: 'name', renderHtml: true },
                    { label: 'Description', field: 'description', renderHtml: true },
                    { label: 'Parameters', field: 'parameters', renderHtml: true }
                ],
                methodsColumns: [
                    { label: 'Name', field: 'name', renderHtml: true },
                    { label: 'Description', field: 'description', renderHtml: true },
                    { label: 'Return', field: 'return', renderHtml: true }
                ]
            }
        }
    }
</script>
