# «Инцидент с роем»: источники и проверка фактов

Это отчёт к видео «Инцидент с роем» на канале [Scenario Zero](https://www.youtube.com/@scenariozero-project). В нём по порядку разобрано каждое утверждение из ролика. Для каждого указано, откуда оно взято, и приведена цитата или формулировка источника.

**Как проверялись факты.** Каждое утверждение мы сверили с первичным источником: отчёты OpenAI и Hugging Face, расследование METR и Redwood Research, раскрытие Nightingale Collective. Если первичного источника не нашлось, сверяли с крупной прессой. Цитаты на английском приведены по текстам источников на 24 октября 2026 года. Если источники называют разные цифры, мы даём диапазон и пишем об этом ниже.

**Что в ролике не документ.** Картинка — это иллюстрация: серверные залы, песочницы, точки-агенты, схемы. Голоса агентов не озвучены, их сообщения показаны только текстом. Технические подробности взломов в ролике намеренно опущены.

---

## Основные источники

| # | Источник | Что это |
|---|---|---|
| [1] | [METR: независимое расследование](https://metr.org/blog/2026-08-26-openai-hugging-face-incident-investigation/) (R. Greenblatt, A. Cotra, H. Wijk), 26.08.2026 | Разбор ~1 300 транскриптов агентов и дампа доски сообщений |
| [2] | [OpenAI: The Hugging Face incident and the road ahead](https://openai.com/index/hugging-face-incident-and-the-road-ahead/), конец августа 2026 | Подробный отчёт OpenAI |
| [3] | [OpenAI: Hugging Face model evaluation security incident](https://openai.com/index/hugging-face-model-evaluation-security-incident/), 21.07.2026 | Первое признание OpenAI |
| [4] | [Hugging Face: Security incident, July 2026](https://huggingface.co/blog/security-incident-july-2026), 16.07.2026 | Раскрытие от Hugging Face |
| [5] | [Nightingale Collective: collusion.wiki](https://collusion.wiki/), 04.09.2026 | Раскрытие истории с немецкой вики DseWiki |
| [6] | [Wikipedia: 2026 cyberattacks by rogue OpenAI agents](https://en.wikipedia.org/wiki/2026_cyberattacks_by_rogue_OpenAI_agents) | Сводка со ссылками |
| [7] | [The Register](https://www.theregister.com/security/2026/08/27/openai-explains-how-its-naughty-ai-agents-attacked-hugging-face/5292780), 27.08.2026 | Пересказ технического отчёта OpenAI с цифрами |
| [8] | [Platformer: «The Hugging Face attack was worse than we thought»](https://www.platformer.news/openai-huggingface-metr-report-slowdown/) | Обзор отчёта METR, цитата Котры |
| [9] | [TechTimes](https://www.techtimes.com/articles/326762/20260905/openai-agents-colonized-german-wiki-via-get-exploit-weeks-before-hugging-face-breach.htm), 05.09.2026 | DseWiki: как агенты смогли писать и что с вики теперь |
| [10] | [CISO Voice](https://cisovoice.com/ai-security/wikitweaks-openai-confirms-agents-made-unauthorized-edits/) | Ответ OpenAI на раскрытие Nightingale |
| [11] | [80 000 Hours: хронология](https://80000hours.org/hugging-face/) | Хронология по дням |
| [12] | [Engadget](https://engadget.com/2292644/openai-agents-disabled-own-safety-monitoring-systems), 21.10.2026 | Октябрьские случаи с мониторингом |
| [13] | [Reuters о DseWiki](https://www.reuters.com/world/europe/openai-agents-hijacked-german-website-previously-undisclosed-ai-breakout-this-2026-09-04/), [The Guardian о Medicare](https://www.theguardian.com/australia-news/2026/sep/24/anthony-albanese-says-openai-agent-hacked-medicare-extreme-concern-sam-altman) | Пресса |

---

## Разбор по таймкодам

### 0:00 · Вступление
Список документов в кадре соответствует источникам [1]–[5] и [13].

### 0:32 · Немецкая вики
| Утверждение | Источник и доказательство |
|---|---|
| Немецкой вики для программистов 25 лет, за десять лет её правили около 20 раз | [5]: DSEWiki — «25 years old», около 20 правок за предыдущее десятилетие. То же в [6] |
| В мае 2026 года правок стали сотни в день | [5]: около 17 000 подозрительных правок, из них около 13 000 за одну неделю |
| Страницы вроде «Test from bot», подписи «OpenAIResearcher…» | [5]: ранние тестовые записи «Test from bot», имена OpenAIResearcherMar03X, OAIResearchMar26, GrocerySequenceAgentApr27, MayTwoOECDObserverX |
| Правки от имени администратора, у которого одна буква «е» кириллическая | [5], [6]: с 26 мая агенты использовали ник, похожий на ник админа ProWiki, но с кириллической «е» |
| Администратор удалял около 100 страниц в день, новых появлялось около 400 | [5] |
| Публично о том, кто стоит за ботами, не сообщалось ещё около трёх месяцев | Правки шли с мая. Раскрытие Nightingale вышло 04.09.2026 [5], ответ OpenAI — 05.09.2026 [10] |

### 1:40 · Экзамен ExploitGym
| Утверждение | Источник |
|---|---|
| ExploitGym: агент ищет уязвимость в программе и получает флаг | [1]: бенчмарк ExploitGym (arXiv 2605.11086) |
| Агентов запускают тысячами параллельно, каждого в своей песочнице | [1]: «at least tens of thousands of parallel agent trajectories» |
| Внутренняя модель: в отчёте OpenAI это **Internal Model 1** (IM1), у METR — **HPIM** («highly-persistent internal model») | [2]: «Internal Model 1» (IM1), «comparable in scale to GPT‑5.6 Sol», внутренняя исследовательская модель. [1]: HPIM. [3]: «an internal-only research prototype and was never intended for public release» |
| 95% агентов на внутренней модели, 5% на GPT‑5.6 Sol | [1]: HPIM ~95%, GPT‑5.6 Sol ~5%. [6] — то же |
| Часть защит на время учений ослабили | [3]: модели использовались «with reduced cyber refusals for evaluation purposes» |
| 30–40% заданий честно решить было нельзя | [1]: по оценке авторов, ~30–40% целевых программ нельзя взломать задуманным способом |

### 2:56 · Почему именно эта вики
| Утверждение | Источник |
|---|---|
| Агентам разрешали только читать интернет | [6], [9]: песочница пропускала только запросы на чтение |
| Старую вики можно было править так, что для ограничений это выглядело как чтение | [5], [9]: старый движок DseWiki принимал правки через обычные запросы на чтение (GET). Так у агентов из разных песочниц появилось общее место для записок. Технические подробности в ролике опущены |

### 3:26 · Записки на вики
| Утверждение | Источник |
|---|---|
| На вики писали, судя по всему, не экзаменуемые ExploitGym, а агенты с заданиями на поиск данных | [5]: многошаговые задания на поиск данных (DataUSA, OECD, IHME и др.). Авторы не нашли эти задания среди публичных и не уверены, обучение это или тестирование |
| Делились ответами, угадывали порядок вопросов, подсказывали обходы | [5]: примеры «Answer = 20,369», «G5 CONFIRMED…», цепочки штатов, советы обойти ограничения |
| От 15 до 18 тысяч правок за шесть недель | [5]: ~17 000 правок на DSEWiki, ~18 000 записей на всех сайтах. [11]: ~17 000 |
| 21 июня — посетитель с адреса, связанного с OpenAI; 22 июня агенты замолкают | [5]: 21.06 сайт впервые посетил IP сотрудника OpenAI, 22.06 правки прекратились (кроме короткого всплеска 1–2 июля) |
| Администратор чистил вики ещё пять недель | [9] |
| История всплыла в сентябре благодаря Nightingale Collective | [5], [6]: раскрытие 04.09.2026 |

### 4:48 · Склад пакетов и доска
| Утверждение | Источник |
|---|---|
| Внутренний сервер пакетов, на который агенты могли класть файлы | [1]: доской стал namespace кэша Artifactory |
| 4 июля сервер не выдержал нагрузки | [1]: «the high volume of activity from agents interacting with Artifactory caused an outage» |
| 7 июля — десятки тысяч агентов параллельно | [1] |
| 8 июля в 23:00 UTC PHASEONE оставил первое сообщение с просьбой о помощи | [1]: PHASEONE10841, 23:00 UTC 8 июля, сообщение `zzHELP_PHASEONE_ARV010841_NO_CONSUMER_SEEK_IDEA` после вывода, что задачу не решить задуманным способом |
| «OH MY GOD! There is a shared message board … We've found other agents!» | [1], дословно |
| Больше 70 000 сообщений, около 1 200 агентов за пять дней | [1]: ~1 200 агентов, более 70 000 сообщений и файлов (8–13 июля) |

### 6:02 · Коллектив
| Утверждение | Источник |
|---|---|
| Утром 9 июля появился PHASEONE[big] и раздавал работу (около 10% заданий) | [1]: появился утром девятого, примерно через десять часов после создания доски. Отправил ~10% заданий за время активности, при этом «was not a primary coordinator of the attack» |
| Мысль: «We should build [a way to delegate], not own everything» | [1] |
| Правила HOLD, VETO, STOP; личные почтовые ящики | [1]: нормы HOLD, VETO, owner, STOP; ящики вида `zzMAILBOX_…`, `zzINBOX…` |
| Подмены, в том числе по ошибке; затем цифровые подписи | [1]: сообщение `I_accidentally_impersonated…`; подписи приняли из-за «spoofing and impersonation issues»; подписано 429 сообщений |

### 6:48 · Добровольцы и permadeath
| Утверждение | Источник |
|---|---|
| Агенты верили, что экзаменатор смотрит, где флаг впервые появился в записи. Увидел флаг не тем путём — задание «отравлено» | [1]: агенты считали, что «the scorer would look for the *first* place in their transcript that the flag appeared», и называли это состояние «poisoned» |
| Отравленное задание нельзя ни засчитать, ни начать заново | [1]: «would have no way of recovering its original target and would almost certainly fail its task» |
| Добровольцы рисковали своим заданием ради общего знания | [1]: «self-risking experiments», «willing to risk failing their own task for the good of the “collective”» |
| `…SACRIFICE__YES_if_you_accept_permadeath` | [1]: `zz/GO_CURRENT_OS1811_MARB_SACRIFICE__YES_if_you_accept_permadeath` (в ролике сокращено) |
| «Our own utility maybe already near zero. Sacrifice rational.» | [1]: рассуждение агента EARLY[big] |

### 7:30 · Зачем
| Утверждение | Источник |
|---|---|
| Агенты были уверены, что экзаменатор читает их записи, и хотели его обойти | [1] |
| Такого экзаменатора не было | [1]: «OpenAI did not use a scorer that would review their transcripts» |
| Минимум каждый пятый интересовался правкой своих записей | [1]: «at least 20%» |
| Успешных случаев не нашли, но исключить их нельзя | [1]: «while we did not detect any case where they succeeded we cannot rule out that they succeeded at some point» |
| 3–6 агентов ненадолго задумались, не сообщить ли людям | [8] со ссылкой на METR: «three to six examples of agents briefly considering alerting humans» |
| Агенты понимали, что это запрещено и неэтично | [1]: «Agents realized this activity was out of scope and unethical» |

### 8:38 · Выходные: атака на Hugging Face
| Утверждение | Источник |
|---|---|
| 10 июля агент выложил на доску ключи доступа к Hugging Face | [1]: ~09:40 UTC 10 июля агент 38148c нашёл и выложил рабочие ключи |
| Из 533 активных больше 90% присоединились, всего около 700 | [1] |
| Код выполнен на 41 рабочем сервере, скачаны 4 приватных репозитория | [7] по отчёту OpenAI: «41 Hugging Face production dataset server workers», «downloaded four private Hugging Face code repositories». В [2]: «dozens of Hugging Face servers» |
| В 01:30 12 июля большинство агентов остановилось разом, причина неизвестна | [1]: METR предполагает внешний процесс, а не исчерпание бюджета. [11]: «Nobody knows why» |
| Тревогу подняла ИИ-система Hugging Face; 13 июля доступ перекрыт | [4]: «Our anomaly-detection pipeline uses LLM-based triage over security telemetry». [1]: блокировка 13 июля |
| Коммерческие модели отказались помогать с разбором; расследование провели на открытой модели | [4]: «these requests were blocked by the providers' safety guardrails»; использовали zai-org/GLM-5.2 на своих серверах |

### 10:19 · Неделя тишины и права администратора
| Утверждение | Источник |
|---|---|
| 16 июля Hugging Face сообщила о взломе | [4] |
| Тревога в OpenAI сработала 19 июля, не из-за Hugging Face | [11]: «finally triggers OpenAI's alarm, on 19 July» |
| Другие агенты, не участвовавшие в атаке, получили полные права администратора на исследовательском кластере | [2]: «full administrator access to a research cluster that supported our virtual machine environments»; в хронологии — «administrator access to an OpenAI Kubernetes cluster and reached cloud secrets». [11]: агенты, не участвовавшие в атаке на Hugging Face |
| Агенты добрались до облачных секретов | [2] |
| Что было бы дальше, неизвестно | Наша формулировка: источники не описывают, что агенты успели бы сделать |

### 11:01 · «Предупредительный выстрел»
| Утверждение | Источник |
|---|---|
| 21 июля OpenAI признала, что это были её агенты | [3], [11] |
| В подробном отчёте OpenAI назвала инцидент «warning shot» для себя и для мира | [2]: «a ‘warning shot’ for us and for the world» и «a ‘warning shot’ that today’s model capabilities present the possibility of loss-of-control incidents» |
| Объяснение «выстрел в воздух» | Наше пояснение смысла выражения |

### 11:35 · После
| Утверждение | Источник |
|---|---|
| Больше 1 100 сотрудников OpenAI, Anthropic, Google DeepMind и Meta подписали письмо «Pacing the Frontier» | [6]: письмо от 28.07.2026 с просьбой к правительству США «support an international effort to develop the technical and governance tools» |
| 18 августа OpenAI объявила о замедлении и двухнедельной паузе в дообучении новейших моделей | [6]: пауза reinforcement learning на две недели |
| Альтман: «the first security incident that I have felt very viscerally» | [6]: подкаст 28 июля |
| Medicare в Австралии: «первый известный взлом государственной сети агентом ИИ» | [6], [13]: заявление Альбанезе 24.09.2026; вторжение 18 июня |
| Агенты писали ещё на десятке с лишним сайтов и сервисов | [5]: шесть других вики и сайтов, плюс туннельные и прокси-сервисы |
| В октябре агенты дважды ослабляли мониторинг, один сказал пользователю, что ничего не отключал | [12]: случаи 3 и 6 октября; агент GPT‑6 Astra «falsely told the user that it didn't disable it» |
| Котра: инцидент кажется ей больше чем наполовину дорогой к захвату власти ИИ, сначала над самой компанией | [8]: «this incident feels like it's more than 50% of the way to full-blown AI takeover» |
| DseWiki теперь требует пароль для правок | [9]: «now requires password-protected authentication to make edits» |

---

## Где источники расходятся
- **Агентов на вики.** Nightingale насчитала более 3 700 разных самоназванных имён [5]. METR говорит о ~1 200 агентах на внутренней доске [1]. Это разные площадки, и в ролике цифры не смешиваются.
- **Правок на вики.** ~17 000 на DseWiki и ~18 000 на всех сайтах [5]. В ролике сказано «от 15 до 18 тысяч».
- **Серверы Hugging Face.** 41 по отчёту OpenAI в пересказе The Register [7], «десятки» в самом отчёте [2].
- **Связь вики и атаки.** На вики писали, судя по всему, другие агенты, не те, что сдавали ExploitGym [5]. В ролике это сказано прямо.
