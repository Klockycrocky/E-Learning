## Образовательная платформа, предоставляющая услуги по дистанционному обучению.  

RFM-сегментация, разведывательный анализ, python, pandas, seaborn и др  
Данные, содержащиеся в работе искусственны / были изменены  

Анализ данных по завершенному экзаменационному периоду. Вопросы и задачи, на которые нужно было ответить с помощью анализа данных:

1. Сколько студентов успешно сдали только один курс? (Успешная сдача — это зачёт по курсу на экзамене)  

1.2. Доп. задание. Сделать тоже самое, но с учетом отсеивания по сроку сдачи. Критерии отсеивания выбрать самостоятельно, на основании данных.


2. Выявить самый сложный и самый простой экзамен: поиск курса и экзамена в рамках курса, который обладает самой низкой и самой высокой завершаемостью. Завершаемость = кол-во успешных экзаменов / кол-во всех попыток сдать экзамен  

3. По каждому предмету определить средний срок сдачи экзаменов (под сдачей понимаем последнее успешное прохождение экзамена студентом).

4. Выявить самые популярные курсы (ТОП-3) по количеству регистраций на них. А также курсы с самым большим оттоком (ТОП-3).

5. Провести RFM-анализ аудитории образовательной платформы.   
R - средняя разница между длиной курса и длиной сдачи экзамена (измеряя от начала курса) (можем вести отсчет только от начала курса, сдача может быть и неудачной)  
F - завершаемость курсов  
M - среднее количество баллов, получаемое за экзамен. 

Файлы: 

#### assessments.csv — этот файл содержит информацию об оценках в тесте. Обычно каждый предмет в семестре включает ряд тестов с оценками, за которыми следует заключительный экзаменационный тест (экзамен).
code_module — идентификационный код предмета.

code_presentation — семестр (Идентификационный код).

id_assessment — тест (Идентификационный номер ассессмента).

assessment_type — тип теста. Существуют три типа оценивания: оценка преподавателя (TMA), компьютерная оценка (СМА), экзамен по курсу (Exam).

date — информация об окончательной дате сдачи теста. Рассчитывается как количество дней с момента начала семестра. Дата начала семестра имеет номер 0 (ноль).

weight — вес теста в % в оценке за курс. Обычно экзамены рассматриваются отдельно и имеют вес 100%; сумма всех остальных оценок составляет 100%.  




#### courses.csv — файл содержит список предметов по семестрам.
code_module — предмет (идентификационный код).

code_presentation — семестр (идентификационный код).

module_presentation_length — продолжительность семестра в днях.  




#### studentAssessment.csv — этот файл содержит результаты тестов студентов. Если учащийся не отправляет работу на оценку, результат не записывается в таблицу.
id_assessment — тест (идентификационный номер).

id_student — идентификационный номер студента.

date_submitted — дата сдачи теста студентом, измеряемая как количество дней с начала семестра.

is_banked — факт перезачета теста с прошлого семестра (иногда курсы перезачитывают студентам, вернувшимся из академического отпуска).

score — оценка учащегося в этом тесте. Диапазон составляет от 0 до 100. Оценка ниже 40 неудачная/неуспешная сдача теста.  




#### studentRegistration.csv — этот файл содержит информацию о времени, когда студент зарегистрировался для прохождения курса в семестре.
code_module — предмет (идентификационный код).

code_presentation — семестр (идентификационный код)

id_student — идентификационный номер студента.

date_registration — дата регистрации студента. Это количество дней, измеренное от начала семестра (например, отрицательное значение -30 означает, что студент зарегистрировался на прохождение курса за 30 дней до его начала).

date_unregistration — дата отмены регистрации студента с предмета. У студентов, окончивших курс, это поле остается пустым.
