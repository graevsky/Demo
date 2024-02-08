Лабу сдать без этого можно, но не на максималку
- utils.component.ts превратить в сервис
- много бизнес-логики в контроллерах (UserResource)
- у класса Utils слишком много работы, она из разных доменов
- транзакции не везде закрываются
- не везде логически правильные статус коды ответов (e.g. 400 когда 409 больше подходит)
- @Transactinal на методе когда внутри метода программная транзакция используется
- "неожиданная" логика обработки ошибок: e.g. UserBean::findUserByLogin вернет null если БД вообще не доступна (сетевая ошибка например)
- статический генератор токенов с захардкоженом секретом
- токены парсятся по несколько раз за один запрос, дублированный код обработки токенов в контроллерам (там больше одной строчки работы с ним)
- по фронту из очевидных минусов: каждый компонент, которому нужны данные от сервера (точки в данном случае), получает их самостоятельно, т.е. сейчас это по одному одинаковому запросу для таблицы и графика, потенциально их могло бы быть больше. Т.е. минус в том, что отсутвет общий источник данных для различных компонентов
