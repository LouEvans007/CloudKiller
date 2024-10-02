Это программа, которая поможет вводить запросы на УЯЗВИМЫЕ страницы на сайты, которые используют cloudflare в качестве защиты. Вам нужно только ввести сквол запрос, который блокирует ваф 
и программа предоставит вам закодированную версию этого запроса.

Программа находится в стадии разработки, поэтому кодирует не все запросы верно. Если вы с таким столкнулись, то можете скопровать основной код и спросить у чата гпт как
закодировать запрос в соответствии с моей кодировкой.

Общее тестирование на проникновение со сквол на сайт с cloudflare включает в себя такие этапы:
1. Вы находите уязвимую ссылку на нужном сайте, для упрощения можете попробовать с помощью программы lostools, которая проведет тест полезной нагрузки
2. Вставляете закодированные сквол запросы к базе данных на сайт и смотрите на реакцию сервера
3. Для автоматизации тестирования используется sqlmap. вы нашли уязвимый параметр с закодированным запросом, например https://www.example.com--c126.aspx?id=%256F%72%253D%251%252D%252D
команда sqlmap -u "https://www.example.com--c126.aspx" --data="id=%256F%72%253D%251%252D%252D" --batch --level=5 --risk=3
следовательно с помощью data вы передаете параметры как если бы они были отправлены в POST-запросе
