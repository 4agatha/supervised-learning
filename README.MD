Перед нами стояла задача создать и проверить модель машинного обучения, которая проанаизирует активность и поведение старых клиентов банка и научится на основе найденных закономерностей предсказывать поведение других клиентов, тем самым, давая возможность банку сократить потери и увеличить прибыль.

Для выполнения этой задачи мы обучили три разные модели машинного обучения: Дерево решений, Случайный лес и Логистическую регрессию. Сравнили результаты работы моделей по опорной метрике (F1) и дополнительной метрике (AUC-ROC)

Для борьбы с дисбаланосом классов в целевом признаке обучающей выборки мы использовали три разным методики:

1. При помощи аргумента class_weight='balanced', встроенного в алгоритмы машинного обучения, мы сбалансировали классификацию и проверили работу всех трех моделей
2. Использовали технику upsampling и, увеличив выборку за счет добавления объектов малого класса целевого признака, проверили работу всех трех моделей
3. Использовали технику downsampling и, уменьшив выборку за счет уменьшения количества объектов большего класса целевого признака, проверили работу всех трех моделей.

Мы построили модель с предельно большим значением F1-меры. Чтобы задать планку качества работы модели, довели метрику до 0.59.

По завершении работы можно сделать вывод, что дисбаланс классов действительно влияет на результаты работы моделей машинного обучения - качество моделей стабильно выше при обучении на выборке со сбалнсированным соотношением классов.

В целом модель случайного леса справлялась с задачей лучше при всех механизмах борьбы с дисбалансом, а наименьшие результаты показала логистическая регрессия. При этом можно наблюдать разницу в работе этой модели на несбалансированной классификации и после применения методов борьбы с дисбалансом. То есть эта модель в данном случае оказалась наиболее чувствительной к дисбалансу.

Наше исследование показало, что зависимость метрики AUC-ROC от баланса классов незначительна - для некоторых методов борьбы с дисбалансом модели машинного обучения показали меньший результат, по сравнению с обучением на выборке с несбалансированной классификацией.

Наилучший показатель этой метрики дало обучение моделей случайного леса и логистической регресси на уменьшенной выборке со сбалансированной классификацией целевого признака.