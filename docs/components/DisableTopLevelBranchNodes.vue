<template>
  <treeselect
    :options="options"
    :disable-top-level-branch-nodes="true"
    placeholder="Where are you from?"
    />
</template>

<script>
  export default {
    data: () => ({
      options: [
        {
          id: '1',
          label: 'A',
          children: [
            {
              id: '1-1',
              label: 'AA',
              children: [
                {
                  id: '1-1-1',
                  label: 'AAA',
                },
                {
                  id: '1-1-2',
                  label: 'AAB',
                },
              ],
            },
          ],
        },
        {
          id: '2',
          label: 'B',
          children: [
            {
              id: '2-1',
              label: 'BA',
            },
          ],
        },
        {
          id: '3',
          label: 'C',
        },
      ],
    }),
  }
</script>
