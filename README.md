Продовжуйте створювати додаток для роботи з колекцією продуктів, розширте проєкт з попереднього уроку новими роутами, валідацією даних та фільтрацією.

# TASK 1 (якщо не встигли зробити на минулому занятті)

Створіть роут POST `/products` для створення нового продукту. Тіло запиту має в себе включати наступні властивості:

- name - обов’язково;
- price - обов’язково;
- category - обов’язково;
- description - не обов’язково;

Обробка цього роута має включати:

- Реєстрацію роута в файлі `src/routers/products.js`
- Опис контролера для цього роута в файлі `src/controllers/products.js`
- Створення сервісу в файлі `src/services/products.js`
- При вдалому запиті відповідь сервера має містити об’єкт з наступними властивостями:

```code
   {
       status: 201,
       message: "Successfully created a product!",
       data: <об'єкт створеного продукту>
   }
```

# TASK 2 (якщо не встигли зробити на минулому занятті)

Створіть роут PATCH `/products/:productId` для оновлення даних одного продукту по його ідентифікатору. Тіло запиту має в себе включати наступні властивості:

- name - не обов’язково;
- price - не обов’язково;
- category - не обов’язково;
- description - не обов’язково;

Обробка цього роута має включати:

- Реєстрацію роута в файлі `src/routers/products.js`
- Опис контролера для цього роута в файлі `src/controllers/products.js`
- Створення сервісу в файлі `src/services/products.js`
- Якщо за переданим ідентифікатором продукт було знайдено, то відповідь сервера має містити об’єкт з наступними властивостями:

```code
   {
       status: 200,
       message: "Successfully patched a product!",
       data: <оновлений об'єкт продукту>
   }
```

- Додайте перевірку чи продукт за переданим ідентифікатором було знайдено. Якщо продукт не було знайдено, то за допомогою `http-errors` створіть помилку зі статусом 404 і повідомленням "Product not found".

```code
   http-errors(404, "Product not found")
```

# TASK 3 (якщо не встигли зробити на минулому занятті)

Створіть роут DELETE `/products/:productId` для видалення одного продукту по його ідентифікатору.

Обробка цього роута має включати:

- Реєстрацію роута в файлі `src/routers/products.js`
- Опис контролера для цього роута в файлі `src/controllers/products.js`
- Створення сервісу в файлі `src/services/products.js`
- Відповідь сервера, в разі успішного видалення продукту, має бути зі статусом 204 без тіла відповіді

- Додайте перевірку чи продукт за переданим ідентифікатором було знайдено. Якщо продукт не було знайдено, то за допомогою `http-errors` створіть помилку зі статусом 404 і повідомленням "Product not found".

```code
   http-errors(404, "Product not found")
```

# TASK 4

## Валідація вхідних даних

Додайте валідацію вхідних даних (body) для маршрутів `POST` і `PATCH`, згідно властивостей, описаних в моделі MongoDB. Створіть для цього middleware `validateBody`.

## Валідація id

Додайте валідацію ідентифікатора, створивши middleware для перевірки валідності ID, згідно зі схемою Mongoose.

# TASK 5

Додайте можливість задати порядок сортування елементів в відповіді для маршруту GET /products. Для цього використовуйте такі query параметри запиту:

- `sortBy` - визначає, за якою властивістю потрібно робити сортування
- `sortOrder` - визначає порядок сортування (**`asc`** - висхідний порядок сортування (значення за замовчуванням) або **`desc`** - низхідний порядок сортування)

# TASK 6

Додайте можливість фільтрації продуктів за категорією (властивість `category`) та за ціною (властивість `price`) у відповіді для маршруту GET `/products`. Для цього використовуйте такі query параметри запиту:

- `category` - назва категорії
- `minPrice` - мінімільна ціна продукту
- `maxPrice` - максимальна ціна продукту
