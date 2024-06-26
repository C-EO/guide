# Action rows

With the components API, you can create interactive message components to enhance the functionality of your slash commands. To get started with this, the first component type you'll need to understand is the action row. To send any type of component, it **must** be placed in an action row.

Action rows are a fairly simple form of layout component. A message may contain up to five rows, each of which has a "width" of five units. This can be thought of as a flexible 5x5 grid. A button will consume one unit of width in a row, while a select menu will consume the whole five units of width. At this time, these are the only types of components that can be sent in a message.

:::warning
The "width units" referred to are not fixed - the actual width of each individual button will be dynamic based on its label contents.
:::

## Building action rows

To create an action row, use the <DocsLink section="builders" path="ActionRowBuilder:Class" /> class and the <DocsLink section="builders" path="ActionRowBuilder:Class#addComponents" type="method" /> method to add buttons or a select menu. 

```js
const row = new ActionRowBuilder()
	.addComponents(component);
```

::: warning
If you're using TypeScript, you'll need to specify the type of components your action row holds. This can be done by specifying the component builder you will add to it using a generic parameter in <DocsLink section="builders" path="ActionRowBuilder:Class" />.

```diff
- new ActionRowBuilder()
+ new ActionRowBuilder<ButtonBuilder>()
```
:::

## Sending action rows

Once one or many components are inside your row(s), send them in the `components` property of your <DocsLink path="InteractionReplyOptions:Interface" /> (extends <DocsLink path="BaseMessageOptions:Interface" />).

```js {4}
const row = new ActionRowBuilder()
	.addComponents(component);

await interaction.reply({ components: [row] });
```

To learn how to create the buttons and select menus that will go inside your row, including more detailed examples on how you might use them, continue on to the other pages in this section.
