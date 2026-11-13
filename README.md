# SaveYourAir

**SaveYourAir is a web service for selecting a filtering respirator and tracking continuous wear time.** Enter the conditions for a walk, run, bike ride, or physically demanding outdoor work. The service recommends a specific respirator and shows its manufacturer, protection class, and part numbers for the mask and any required filters.

<img width="1447" height="1045" alt="1_WEB_Eng" src="https://github.com/user-attachments/assets/497e34cc-ed05-41ce-8b66-87011f9d43d6" />


### How to use

1. **Set your activity and temperature.** Select walking, running, cycling, or heavy outdoor work. Choose winter (−30 to +5 °C) or summer (+5 to +50 °C), then enter the air temperature.
2. **Select the pollutants and pollution level.** You can combine urban smog (PM2.5), road dust (PM10), paints and varnishes, plant pollen, microorganisms and viruses, wood dust, and cement dust. Choose one of five levels from green through yellow, red, purple, and maroon.
3. **Check the recommendation and start the countdown.** Select **Put on** (**Надеть** in the web interface) to start the timer. The same button changes to **Take off** (**Снять**). Select it to end the session and reset the countdown. The dial changes color as time runs low.

### How the respirator is selected

The service checks these rules in order and uses the first match. Paints and varnishes take precedence when several pollutants are selected.

| Conditions | Recommended configuration |
| --- | --- |
| Paints and varnishes with aerosols and organic vapors covered by type A | **3M 7502**, A2P3 · 2 × 6055, 2 × 5935, 2 × 501 |
| Purple or maroon level, or heavy outdoor work | **3M 7502**, P3 R · 2 × 6035 |
| Red level, wood dust, or cement dust | **3M Aura 9332+**, disposable FFP3 with an exhalation valve |
| Other supported combinations | **3M Aura 9322+**, disposable FFP2 with an exhalation valve |

The browser applies these rules to the conditions you enter manually. The microorganisms and viruses category follows the same selection rules as urban smog.

### How the timer is calculated

The service starts with reference wear intervals from [DGUV Rule 112-190, Section 8](https://vorschriften.bgn-branchenwissen.de/daten/dguv/112_190/8.htm). The base interval is **150 min** for the valved disposable respirators listed above, **135 min** for the reusable half mask with P3 filters, and **120 min** for the reusable half mask with combination filters.

| Factor | Timer adjustment |
| --- | --- |
| Activity | ×1.00 for walking. ×0.70 for running, cycling, or heavy outdoor work |
| Winter, −30 to −15 °C | ×0.90 |
| Summer, +30 to +50 °C | ×0.85 |
| Maroon pollution level | ×0.90. Respirator selection follows the purple-level rules |

The service multiplies the applicable factors. For example, cycling at +35 °C with road dust at the maroon level gives **01:12:18** using the P3 configuration. The activity mapping, temperature ranges, and maroon adjustment are service rules.

> The countdown is a reminder to take a break. Filter replacement follows the manufacturer’s instructions and actual exposure conditions. For work involving hazardous substances or infectious aerosols, verify the respirator selection and fit against the applicable requirements and the material’s safety data sheet, where relevant.

[NIOSH guidance on respirator selection](https://www.cdc.gov/niosh/ppe/respirators/selection.html) · [3M A2P3 filter kit documentation](https://www.3mkazakhstan.com/3M/ru_KZ/p/d/v101711024/)



**SaveYourAir — веб-сервис для подбора фильтрующего респиратора и отслеживания времени непрерывного ношения.** Укажите условия прогулки, пробежки, поездки на велосипеде или тяжёлой работы на улице. Сервис покажет конкретную модель, производителя, класс защиты и артикулы маски и сменных фильтров.

<img width="1447" height="1045" alt="1_WEB_Eng" src="https://github.com/user-attachments/assets/497e34cc-ed05-41ce-8b66-87011f9d43d6" />

### Как пользоваться

1. **Укажите нагрузку и температуру.** Выберите ходьбу, бег, велосипед или тяжёлую работу на открытом воздухе. Укажите сезон и температуру. Зимой доступен диапазон от −30 до +5 °C, летом — от +5 до +50 °C.
2. **Выберите загрязнения и уровень.** Можно сочетать городской смог (PM2.5), дорожную пыль (PM10), лаки и краски, пыльцу растений, микроорганизмы и вирусы, древесную и цементную пыль. Выберите зелёный, жёлтый, красный, фиолетовый или бордовый уровень.
3. **Проверьте рекомендацию и запустите таймер.** Нажмите **«Надеть»**, чтобы начать обратный отсчёт. Кнопка сменит надпись на **«Снять»**. Повторное нажатие завершает сеанс и обнуляет таймер. По мере истечения времени циферблат меняет цвет.

### Как подбирается респиратор

Сервис проверяет правила по порядку и применяет первое подходящее. При выборе нескольких загрязнений приоритет у лаков и красок.

| Условия | Рекомендуемый комплект |
| --- | --- |
| Аэрозоль лаков и красок и органические пары, для которых подходит фильтр типа A | **3M 7502**, A2P3 · 2 × 6055, 2 × 5935, 2 × 501 |
| Фиолетовый или бордовый уровень либо тяжёлая работа на улице | **3M 7502**, P3 R · 2 × 6035 |
| Красный уровень, древесная или цементная пыль | **3M Aura 9332+**, одноразовый FFP3 с клапаном выдоха |
| Остальные поддерживаемые сочетания | **3M Aura 9322+**, одноразовый FFP2 с клапаном выдоха |

Браузер применяет правила к условиям, которые вы вводите вручную. Для категории «Микроорганизмы и вирусы» действуют те же правила подбора, что и для городского смога.

### Как рассчитывается таймер

Сервис использует исходные интервалы из [DGUV 112-190, раздел 8](https://vorschriften.bgn-branchenwissen.de/daten/dguv/112_190/8.htm). Базовый интервал для указанных одноразовых респираторов с клапаном составляет **150 мин**, для полумаски с фильтрами P3 — **135 мин**, с комбинированными фильтрами — **120 мин**.

| Фактор | Поправка к таймеру |
| --- | --- |
| Нагрузка | ×1,00 для ходьбы. ×0,70 для бега, велосипеда и тяжёлой работы на улице |
| Зима, от −30 до −15 °C | ×0,90 |
| Лето, от +30 до +50 °C | ×0,85 |
| Бордовый уровень | ×0,90. Респиратор подбирается по правилам фиолетового уровня |

Поправки перемножаются. Например, для поездки на велосипеде при +35 °C с дорожной пылью на бордовом уровне таймер для комплекта P3 покажет **01:12:18**. Соответствие видов деятельности категориям нагрузки, температурные диапазоны и поправка для бордового уровня заданы правилами сервиса.

> Таймер напоминает о перерыве. Срок замены фильтров определяют по инструкции производителя и фактическим условиям воздействия. При работе с опасными веществами или инфекционными аэрозолями проверьте выбор респиратора и его прилегание по применимым требованиям. Для химических материалов также учитывайте паспорт безопасности.

[Рекомендации NIOSH по подбору респиратора](https://www.cdc.gov/niosh/ppe/respirators/selection.html) · [Документация 3M на комплект A2P3](https://www.3mkazakhstan.com/3M/ru_KZ/p/d/v101711024/)



**SaveYourAir — сүзгіш респираторды таңдап, оны үздіксіз тағу уақытын бақылауға арналған веб-сервис.** Жаяу серуендеу, жүгіру, велосипед тебу немесе ашық ауада ауыр жұмыс істеу жағдайларын көрсетіңіз. Сервис респиратордың нақты моделін, өндірушісін, қорғаныс класын, сондай-ақ маска мен ауыстырмалы сүзгілердің артикулдарын көрсетеді.

<img width="1447" height="1045" alt="1_WEB_Eng" src="https://github.com/user-attachments/assets/497e34cc-ed05-41ce-8b66-87011f9d43d6" />

### Қалай қолдануға болады

1. **Әрекет түрі мен температураны көрсетіңіз.** Жаяу жүруді, жүгіруді, велосипед тебуді немесе ашық ауада ауыр жұмыс істеуді таңдаңыз. Маусым мен ауа температурасын көрсетіңіз. Қысқы аралық −30-дан +5 °C-қа дейін, жазғы аралық +5-тен +50 °C-қа дейін.
2. **Ластағыштар мен ластану деңгейін таңдаңыз.** Қалалық смогты (PM2.5), жол шаңын (PM10), лактар мен бояуларды, өсімдік тозаңын, микроағзалар мен вирустарды, ағаш пен цемент шаңын қатар таңдауға болады. Жасыл, сары, қызыл, күлгін немесе қою қызыл деңгейді таңдаңыз.
3. **Ұсынысты қарап, таймерді іске қосыңыз.** Кері санақты бастау үшін **«Тағу»** түймесін басыңыз (сервис интерфейсінде **«Надеть»**). Түйменің жазуы **«Шешу»** болып өзгереді (интерфейсте **«Снять»**). Оны қайта басқанда сеанс аяқталып, таймер нөлге түседі. Уақыт азайған сайын таймер шкаласының түсі өзгереді.

### Респиратор қалай таңдалады

Сервис ережелерді ретімен тексеріп, бірінші сәйкес келгенін қолданады. Бірнеше ластағыш таңдалса, лактар мен бояуларға басымдық беріледі.

| Жағдай | Ұсынылатын жиынтық |
| --- | --- |
| Лактар мен бояулардың аэрозолі және A типті сүзгіге сәйкес келетін органикалық булар | **3M 7502**, A2P3 · 2 × 6055, 2 × 5935, 2 × 501 |
| Күлгін немесе қою қызыл деңгей, не ашық ауадағы ауыр жұмыс | **3M 7502**, P3 R · 2 × 6035 |
| Қызыл деңгей, ағаш немесе цемент шаңы | **3M Aura 9332+**, дем шығару клапаны бар бір реттік FFP3 |
| Қолдау көрсетілетін өзге жағдайлар | **3M Aura 9322+**, дем шығару клапаны бар бір реттік FFP2 |

Браузер ережелерді қолмен енгізілген деректерге қолданады. «Микроағзалар мен вирустар» санатына қалалық смогқа арналған респиратор таңдау ережелері қолданылады.

### Таймер қалай есептеледі

Сервис [DGUV 112-190 ережесінің 8-бөліміндегі](https://vorschriften.bgn-branchenwissen.de/daten/dguv/112_190/8.htm) бастапқы уақыт мәндерін қолданады. Жоғарыда көрсетілген клапанды бір реттік респираторлар үшін бастапқы уақыт **150 мин**, P3 сүзгілері бар жартылай маска үшін **135 мин**, ал біріктірілген сүзгілері бар жартылай маска үшін **120 мин**.

| Фактор | Таймер коэффициенті |
| --- | --- |
| Дене жүктемесі | Жаяу жүру үшін ×1,00. Жүгіру, велосипед тебу немесе ашық ауадағы ауыр жұмыс үшін ×0,70 |
| Қыста −30-дан −15 °C-қа дейін | ×0,90 |
| Жазда +30-дан +50 °C-қа дейін | ×0,85 |
| Қою қызыл деңгей | ×0,90. Респиратор күлгін деңгейдің ережелері бойынша таңдалады |

Қолданылатын коэффициенттер өзара көбейтіледі. Мысалы, ауа температурасы +35 °C болып, жол шаңының деңгейі қою қызыл болса, велосипед тебу кезінде P3 жиынтығына арналған таймер **01:12:18** көрсетеді. Әрекет түрлерінің жүктеме санаттарына сәйкестігі, температура аралықтары және қою қызыл деңгейдің коэффициенті сервис ережелерімен белгіленген.

> Таймер үзіліс жасау керегін еске салады. Сүзгілерді ауыстыру мерзімі өндіруші нұсқаулығына және ластағыштардың нақты әсер ету жағдайларына байланысты. Қауіпті заттармен немесе жұқпалы аэрозольдермен жұмыс істегенде, респиратордың дұрыс таңдалғанын және бетке тығыз жанасуын қолданылатын талаптарға сай тексеріңіз. Химиялық материалдар үшін қауіпсіздік паспортын да ескеріңіз.

[Респиратор таңдау жөніндегі NIOSH ұсынымдары](https://www.cdc.gov/niosh/ppe/respirators/selection.html) · [3M A2P3 сүзгілер жиынтығының құжаттамасы](https://www.3mkazakhstan.com/3M/ru_KZ/p/d/v101711024/)

