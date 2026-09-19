# Знакомство с Expo через MD

## _Создание проекта_ 
### Что такое EXPO
Expo - это <u>фреймворк</u>, который 
упрощает разработку приложений для Android и IOS.
 >Фреймворк - это готовая программная платформа, которая задает правила, архитектуру и стандарты для создания приложений

Ещё EXPO - это проект с открытым исходным кодом и активным комьюнити в GitHub и Discord.

### Системные требование:
- Node.js (LTS )
- Поддерживаются macOS, Windows (Powershell и WSL 2 ) и Linux.

>Node.js - это свободная среда выполнения JavaScript, которая позволяет запускать код JS вне браузера, в том числе на сервере.   
А Node.js LTS - это стабильная версия программной платформы Node.js

### Начните с проекта по умолчанию.

 Рекомендуем начать с проекта по умолчанию, созданного с помощью ```create-expo-app```. Проект по умолчанию включает примеры кода, которые помогут вам начать работу.
    
```
- npx create-expo-app@latest
```
## _Начнём с примера._
Вместо проекта по умолчанию вы можете начать с одного из [примеров Expo](https://github.com/expo/examples "Примеры") . Это небольшие приложения, каждое из которых демонстрирует определенную функцию или интеграцию, например, Expo Router, Expo Widgets или экран камеры.

Чтобы просмотреть весь список и выбрать нужный пункт в интерактивном режиме, запустите программу ```create-expo-appс``` соответствующей ```--exampl``` опцией, но без указания имени:
```
- npx create-expo-app@latest --example
```
```
- npx create-expo-app@latest --example with-widgets
```
## Настройте агента ИИ.
Новый проект включает файлы контекста проекта, которые считывают агенты ИИ: __AGENTS.md__ , __CLAUDE.md__ и __.claude/settings.json__ . Claude Code и Codex также имеют официальный плагин Expo. С помощью одной команды вы можете установить [Expo Skills](https://docs.expo.dev/skills/) и зарегистрировать сервер [Expo Model Context Protocol (MCP)](https://docs.expo.dev/mcp/) :
>### Кодекс Клода
```- claude plugin install expo@claude-plugins-official```

    Затем войдите ```/mcp``` в свою учетную запись Expo в рамках сессии Claude Code.
>### Кодекс 
```- codex plugin add expo@openai-curated```

    Затем войдите в свою учетную запись Expo:

```- codex mcp login expo```

 Для агентов Cursor и других агентов установите Expo Skills и Expo MCP Server отдельно. В разделе, посвященном агентам ИИ и обзору Expo, описана настройка каждого агента.

 
##  Настройка окружения
Чтобы начать разработку, необходимо подготовить локальное окружение для запуска проекта на Android и iOS.
- Где разрабатывать: Рекомендуется использовать реальное устройство, чтобы видеть приложение так же, как его увидят пользователи. Альтернативы: эмулятор Android или симулятор iOS.
- Как разрабатывать:
  - Expo Go: «Песочница» для студентов и новичков, позволяющая быстро попробовать Expo. Имеет ограничения и не подходит для production-проектов.
  - Development build: Собственная сборка вашего приложения с включенными инструментами разработчика Expo. Поддерживает кастомные нативные модули и предназначена для реальных проектов.

-  Настройка Android: Скачайте Expo Go из Google Play Store или отсканируйте QR-код со страницы документации.

## Начало разработки
- Запуск сервера разработки: Выполните в терминале команду ```npx expo start``` (или ```yarn expo start```, ```pnpm expo start```, ```bun expo start```).
- Открытие приложения:
  - На физическом устройстве: отсканируйте QR-код из терминала камерой или через приложение Expo Go.
  - На эмуляторе/симуляторе: нажмите клавишу ```A``` (Android) или ```I``` (iOS) в терминале.
  - Решение проблем: Если устройства не видят друг друга (часто в публичных сетях), запустите сервер с флагом ```--tunnel``` (```npx expo start --tunnel```). Однако это может замедлить обновление экрана, поэтому по возможности используйте локальную сеть (LAN).

- Первые изменения: Откройте файл ```src/app/index.tsx``` и внесите правки. По умолчанию включен Fast Refresh, который автоматически обновляет экран при сохранении файла. Если этого не происходит, встряхните устройство, откройте меню разработчика (```Cmd + D```на iOS или через меню на Android) и убедитесь, что Fast Refresh активен.

- Структура файлов: По умолчанию используется файловая маршрутизация. Директория ```app``` (или ```src/app```) определяет навигацию: каждый файл становится экраном, а файл ```_layout.tsx``` задает общую оболочку (например, табы или заголовки).


## Создание вашего первого приложения.

  + Предварительные требования: Установите Node.js (LTS-версию), редактор кода (например, VS Code) и приложение Expo Go на свой смартфон (iOS/Android).
    
  + Инициализация: 

  ```- npx create-expo-app@latest StickerSmash```
  
    При запросе выберите шаблон с TypeScript и актуальную версию SDK (например, SDK 57)
  ```- cd StickerSmash```
  
  + Очистка шаблона: По умолчанию Expo создает шаблон с примерами. Чтобы начать с чистого листа, выполните:

  ```- npm run reset-project```
  
  Этот скрипт удаляет лишние файлы из ```src/app```, оставляя только ```index.tsx``` (главный экран) и ```_layout.tsx``` (корневой макет), а старые файлы перемещает в папку ```example/``` на случай, если они вам понадобятся.

  + Запуск: Команда ```npx expo start``` запускает Metro Bundler. В терминале появится QR-код. На iOS откройте камеру, на Android – приложение Expo Go ? "Scan QR code". Для веб-версии нажмите клавишу ```w``` в терминале.

 ## Добавление навигации.

  + __Файловая маршрутизация (Expo Router)__: В Expo Router каждый файл в папке ```src/app``` автоматически становится экраном. Имя файла определяет путь (например, ```about.tsx``` ? маршрут ```/about```).
  + __Корневой макет__ (_layout.tsx): Этот файл оборачивает все экраны. Для создания стековой навигации используется компонент ```<Stack>```:

   ```python
   import { Stack } from 'expo-router';
  export default function RootLayout() {
    return <Stack>
      <Stack.Screen name="(tabs)" options={{ headerShown: false }} />
    </Stack>;
  }
  ```
  + __Нижняя панель вкладок (Bottom Tabs)__: Создайте папку ```(tabs)``` внутри ```src/app```. Скобки в названии означают, что это группа маршрутов, а не часть URL-пути. Внутри создайте ```_layout.tsx```:
 ```python
    import { Tabs } from 'expo-router';
  import { Ionicons } from '@expo/vector-icons'; // Требуется установка: npx expo install @expo/vector-icons

  export default function TabLayout() {
    return (
      <Tabs screenOptions={{ tabBarActiveTintColor: '#ffd33d' }}>
        <Tabs.Screen name="index" options={{ 
          title: 'Home', 
          tabBarIcon: ({ color }) => <Ionicons name="home" size={24} color={color} /> 
        }} />
      </Tabs>
    );
  }
  ```
+ __Переходы__: Используйте компонент ```<Link href="/about">Текст</Link>``` вместо стандартных обработчиков нажатий для навигации.
## Создание экрана.
+ __Компонент Image__: Используйте ```<Image>``` из библиотеки ```expo-image``` (встроена в шаблон). Она лучше стандартной ```Image``` из React Native, так как обеспечивает кэширование, плавные переходы и одинаковое поведение на всех платформах.
+ __Структура проекта__: 

  + ```src/app/``` – только для файлов маршрутизации (экранов и макетов).
  + ```src/components/``` – для переиспользуемых UI-компонентов (кнопки, просмотрщики изображений).

+ __Обработка нажатий__: Используйте ```<Pressable>``` вместо ```<Button>```. Pressable предоставляет доступ к состоянию нажатия (```pressed```), поддерживает долгие нажатия (```onLongPress```) и легко стилизуется через CSS-in-JS (```StyleSheet```).
## Использование инструмента выбора изображений.
+ __Установка__: ```npx expo install expo-image-picker```
+ __Логика выбора__: Создайте асинхронную функцию, которая вызывает системный интерфейс выбора файлов:
```python
  import * as ImagePicker from 'expo-image-picker';
  import { useState } from 'react';

  const [selectedImage, setSelectedImage] = useState<string | undefined>(undefined);

  const pickImageAsync = async () => {
    let result = await ImagePicker.launchImageLibraryAsync({
      mediaTypes: ['images'], // Разрешаем только изображения
      allowsEditing: true,    // Включает инструмент обрезки на iOS/Android
      quality: 1,             // Максимальное качество
    });

    if (!result.canceled) {
      setSelectedImage(result.assets[0].uri); // Сохраняем URI выбранного файла
    } else {
      alert('Вы не выбрали изображение.');
    }
  };
  ```
+ __Отображение__: Передайте ```selectedImage``` в ваш компонент ```ImageViewer```. Если он равен ```undefined```, показывайте изображение-заглушку (placeholder).
## Создание модального окна.
+ __Компонент Modal__: Используйте встроенный ```<Modal>``` из ```react-native```.
+ __Ключевые пропсы__:

    + ```visible={isVisible}```: управляет показом/скрытием (контролируется через useState).
    + ```transparent={true}```: делает фон за модальным окном прозрачным.
    + ```animationType="slide"```: задает анимацию появления (снизу вверх).

+ __Список элементов__: Для отображения списка стикеров используйте ```<FlatList>``` с пропом ```horizontal```. 

    + Нюанс: На веб-платформе горизонтальный скроллбар может выглядеть некрасиво. Используйте ```showsHorizontalScrollIndicator={Platform.OS === 'web'}```, чтобы показывать его только в браузере.
## Добавление жестов.

+ __Установка__: ```npx expo install react-native-gesture-handler react-native-reanimated```
+ __Инициализация__: Оберните самый верхний компонент вашего экрана в ```<GestureHandlerRootView>```. Без этого жесты не будут работать.
+ __Анимация двойного нажатия__:
      
    1. Используйте ```useSharedValue``` для хранения текущего масштаба (например, ```scaleImage```).
    2. Создайте жест: ```const doubleTap = Gesture.Tap().numberOfTaps(2).onStart(() => { ... })```. Внутри ```onStart``` меняйте значение ```scaleImage.value``` (умножайте на 2 или делите).
    3. Примените анимацию через ```useAnimatedStyle```, используя функцию ```withSpring(scaleImage.value)``` для свойств ```width``` и ```height```. Это создаст реалистичный "пружинистый" эффект.
+ __Анимация перетаскивания (Pan)__:
  
  1. Создайте две shared-переменные: ```translateX``` и ```translateY``` (изначально равны 0).
  2. Создайте жест: 
  `const drag = Gesture.Pan().onChange((event) => { translateX.value += event.changeX; translateY.value += event.changeY; })`.
  3. В ``useAnimatedStyle`` верните объект `transform: [{ translateX: translateX.value }, { translateY: translateY.value }]` и примените его к `<Animated.View>`, оборачивающему стикер.
## Создание скриншота.
+ __Установка__: ```npx expo install react-native-view-shot expo-media-library```
+ __Запрос разрешений__: При первом запуске приложение должно запросить доступ к медиатеке. Используйте хук:
```python
  const [permissionResponse, requestPermission] = ImagePicker.useMediaLibraryPermissions();
  useEffect(() => {
    if (!permissionResponse?.granted) requestPermission();
  }, []);
  ```
+ __Захват и сохранение__:

1. Создайте реф: `const imageRef = useRef<View>(null)`;
2. Привяжите его к `<View>`, который содержит и фоновое изображение, и стикер: `<View ref={imageRef} collapsable={false}>...</View>`. (Важно: проп `collapsable={false}` предотвращает оптимизацию React Native, которая могла бы удалить этот View из нативного дерева, сделав захват невозможным).
 3. Функция сохранения:
 ```python
 const onSaveImageAsync = async () => {
  const localUri = await captureRef(imageRef, { height: 440, quality: 1 });
  await MediaLibrary.saveToLibraryAsync(localUri);
  alert('Сохранено!');
};
```
## Обработка межплатформенных различий
+ __Проблема__: `react-native-view-shot` работает только на нативных платформах (iOS/Android). В браузере (Web) он выдаст ошибку.
+ __Решение__: Используйте модуль `Platform` из `react-native` для разделения логики.
 ```python
  import { Platform } from 'react-native';
  import domtoimage from 'dom-to-image'; // Установить: npm install dom-to-image

  const onSaveImageAsync = async () => {
    if (Platform.OS !== 'web') {
      // Логика для iOS/Android (captureRef + MediaLibrary)
    } else {
      // Логика для Web
      const dataUrl = await domtoimage.toJpeg(imageRef.current, { quality: 0.95 });
      const link = document.createElement('a');
      link.download = 'sticker-smash.jpeg';
      link.href = dataUrl;
      link.click(); // Инициирует скачивание файла в браузере
    }
  };
  ```
+ __Исправление TypeScript__: Поскольку у `dom-to-image` нет встроенных типов, создайте в корне проекта файл `types.d.ts` с содержимым: `declare module 'dom-to-image';`.
## Настройка строки состояния, заставки и иконки приложения

+ __Строка состояния__ (Status Bar): Библиотека `expo-status-bar` уже установлена. Добавьте `<StatusBar style="light" />` (белый текст) или "dark" (черный текст) в ваш _layout.tsx.

+ __Иконка приложения__: Замените файл assets/images/icon.png на свой (рекомендуемый размер 1024?1024 px). Путь к нему уже прописан в app.json в поле "icon". При сборке через EAS (Expo Application Services) система автоматически создаст иконки всех нужных размеров для разных устройств.

+ __Заставка (Splash Screen)__: Настраивается в app.json через плагин expo-splash-screen. По умолчанию он использует ту же иконку по центру цветного фона. 
  + Важное ограничение: Заставку невозможно увидеть в Expo Go или при обычной разработке (npx expo start). Чтобы протестировать её, необходимо создать сборку для распространения (Preview или Production build) через EAS.
  0. Ресурсы для обучения (Learning resources)
Для дальнейшего роста как разработчика Expo/React Native рекомендуется изучить:

    React: Углубите знания о хуках (useState, useEffect, useRef, useCallback), так как они являются основой управления состоянием в Expo.
    Flexbox: Изучите руководство по макетам в React Native (justifyContent, alignItems, flexDirection), так как это основной способ верстки.
    Expo Router: Официальная документация по вложенным маршрутам, динамическим параметрам ([id].tsx) и модальным окнам как маршрутам.
    EAS (Expo Application Services): Изучите процесс создания Development builds (собственных сборок для тестирования нативного кода) и процесс отправки приложений в App Store и Google Play.
    Отладка (Debugging): Освойте использование React Native Debugger, Flipper или встроенных инструментов Chrome DevTools для веб-версии для поиска ошибок и анализа производительности.