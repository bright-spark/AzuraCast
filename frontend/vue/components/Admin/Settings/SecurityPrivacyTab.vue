<template>
    <b-form-fieldset>
        <template #label>
            {{ $gettext('Privacy') }}
        </template>

        <div class="form-row">
            <b-wrapped-form-group
                id="edit_form_analytics"
                class="col-md-12"
                :field="form.analytics"
            >
                <template #label>
                    {{ $gettext('Listener Analytics Collection') }}
                </template>
                <template #description>
                    {{
                        $gettext('Aggregate listener statistics are used to show station reports across the system. IP-based listener statistics are used to view live listener tracking and may be required for royalty reports.')
                    }}
                </template>
                <template #default="slotProps">
                    <b-form-radio-group
                        :id="slotProps.id"
                        v-model="slotProps.field.$model"
                        stacked
                    >
                        <b-form-radio value="all">
                            <b>
                                {{ $gettext('Full:') }}
                            </b>
                            {{ $gettext('Collect aggregate listener statistics and IP-based listener statistics') }}
                        </b-form-radio>
                        <b-form-radio value="no_ip">
                            <b>
                                {{ $gettext('Limited:') }}
                            </b>
                            {{ $gettext('Only collect aggregate listener statistics') }}
                        </b-form-radio>
                        <b-form-radio value="none">
                            <b>
                                {{ $gettext('None:') }}
                            </b>
                            {{ $gettext('Do not collect any listener analytics') }}
                        </b-form-radio>
                    </b-form-radio-group>
                </template>
            </b-wrapped-form-group>
        </div>
    </b-form-fieldset>

    <b-form-fieldset>
        <template #label>
            {{ $gettext('Security') }}
        </template>

        <div class="form-row">
            <b-wrapped-form-checkbox
                id="edit_form_always_use_ssl"
                class="col-md-12"
                :field="form.always_use_ssl"
            >
                <template #label>
                    {{ $gettext('Always Use HTTPS') }}
                </template>
                <template #description>
                    {{
                        $gettext('Set to "Yes" to always use "https://" secure URLs, and to automatically redirect to the secure URL when an insecure URL is visited.')
                    }}
                </template>
            </b-wrapped-form-checkbox>

            <b-wrapped-form-group
                id="edit_form_api_access_control"
                class="col-md-12"
                :field="form.api_access_control"
            >
                <template #label>
                    {{ $gettext('API "Access-Control-Allow-Origin" Header') }}
                </template>
                <template #description>
                    {{
                        $gettext('Set to * to allow all sources, or specify a list of origins separated by a comma (,).')
                    }}
                    <br>
                    <a
                        href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Origin"
                        target="_blank"
                    >
                        {{ $gettext('Learn more about this header.') }}
                    </a>
                </template>
            </b-wrapped-form-group>
        </div>
    </b-form-fieldset>
</template>

<script setup>
import BWrappedFormGroup from "~/components/Form/BWrappedFormGroup.vue";
import BFormFieldset from "~/components/Form/BFormFieldset.vue";
import BWrappedFormCheckbox from "~/components/Form/BWrappedFormCheckbox.vue";

const props = defineProps({
    form: {
        type: Object,
        required: true
    }
});
</script>
