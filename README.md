# Перебор точек в 3D-пространстве на примере Ниагары

Этот проект выполняет фильтрацию точек в 3D-пространстве на основе геометрической фигуры "песочные часы". Исходные точки считываются из файла, а затем проверяется, какие из них попадают в песочные часы, вращающиеся вокруг определённой оси.

## Описание функций

### `read_points(file_name)`
Читает точки из файла в формате `.xyz`. Файл должен содержать 4 столбца: метка класса точки и её координаты (x, y, z).

**Параметры:**
- `file_name`: имя файла, содержащего данные точек.

**Возвращает:**
- Массив меток классов точек.
- Массив координат точек в виде 2D массива (N, 3).

### `points_in_hourglass(coords, apex, direction, cos_alpha, h)`
Проверяет, попадает ли точка в "песочные часы". Песочные часы представляют собой фигуру с апексом в заданной точке и с вращающейся осью.

**Параметры:**
- `coords`: координаты точек.
- `apex`: вершина песочных часов (точка апекса).
- `direction`: направление оси, вокруг которой вращаются песочные часы.
- `cos_alpha`: косинус угла с осью вращения.
- `h`: максимальная дальность от апекса.

**Возвращает:**
- Массив, показывающий, какие точки попадают в песочные часы.

### `rotate_directions(initial_direction, angles_deg)`
Генерирует вращения направлений вокруг оси, задавая угол поворота от 0 до 360 градусов.

**Параметры:**
- `initial_direction`: начальное направление оси.
- `angles_deg`: массив углов поворота в градусах.

**Возвращает:**
- Массив вращённых направлений.

### `filter_points_in_hourglass(file_name, apex, initial_direction, alpha=90, h=1.0, target_count=10)`
Основная функция, которая выполняет фильтрацию точек из файла. Она выбирает только те точки, которые попадают в песочные часы для различных направлений оси.

**Параметры:**
- `file_name`: имя файла с точками.
- `apex`: вершина песочных часов.
- `initial_direction`: начальное направление оси вращения.
- `alpha`: угол, определяющий область песочных часов (по умолчанию 90°).
- `h`: дальность от апекса, на которой точки должны находиться.
- `target_count`: максимальное количество точек, которые должны быть возвращены.

**Возвращает:**
- Список выбранных точек и их меток классов.

## Зависимости

Для работы программы необходимы следующие библиотеки:

- `numpy`: для работы с массивами и линейной алгебры.
- `time`: для измерения времени выполнения.

## Файл входных данных

Файл входных данных (`Niagara.xyz`) должен иметь следующий формат:

```
class_label x y z
```

где:
- `class_label` — метка класса точки.
- `x`, `y`, `z` — координаты точки в 3D пространстве.
