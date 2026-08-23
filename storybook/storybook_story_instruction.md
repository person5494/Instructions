# Как добавить Storybook story для компонента

Рядом с компонентом создайте файл:

```text
ComponentName.stories.tsx
```

Например:

```text
Button/
├── Button.tsx
├── Button.module.css
├── Button.stories.tsx
└── index.ts
```

## Базовый шаблон

```tsx
import type { Meta, StoryObj } from '@storybook/react-vite'

import { ComponentName } from './ComponentName'

const meta: Meta<typeof ComponentName> = {
  title: 'Shared/ComponentName',
  component: ComponentName,
}

export default meta

type Story = StoryObj<typeof ComponentName>
```

После этого для каждого основного варианта или состояния добавьте отдельную story.

Например:

```tsx
export const Default: Story = {
  args: {
    children: 'Default',
  },
}

export const Disabled: Story = {
  args: {
    children: 'Disabled',
    disabled: true,
  },
}
```

Если у компонента есть варианты через пропсы:

```tsx
export const Primary: Story = {
  args: {
    variant: 'primary',
    children: 'Primary',
  },
}

export const Secondary: Story = {
  args: {
    variant: 'secondary',
    children: 'Secondary',
  },
}
```

## Что желательно проверить

Добавьте stories для основных состояний и вариантов, которые есть у компонента:

- обычное состояние;
- `disabled`;
- разные `variant`;
- разные `size`;
- `checked`, `selected`, `error` и другие состояния, если они есть у компонента.

`hover`, `active` и `focus` отдельно описывать обычно не нужно — их можно проверить прямо в Storybook мышкой и клавишей `Tab`.

## Запуск

```bash
npm run storybook
```

После этого компонент появится в меню Storybook.
