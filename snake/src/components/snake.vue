
<script>
export default {
  data() {
      return {
          body: null,
          direction: null,
          lastStepDirection: null,
          }
  },
  methods:{
    init(startBody, direction, rows, cols) {
        this.body = startBody;
        this.direction = direction;
        this.lastStepDirection = direction;
    },

    getNextStepHeadPoint() {
        // Получаем в отдельную переменную голову змейки.
        const firstPoint = this.body[0];
        // Возвращаем точку, где окажется голова змейки в зависимости от направления.
        switch (this.direction) {
        case 'up':
            return {x: firstPoint.x, y: firstPoint.y == 0 ? this.rowsCount-1 : firstPoint.y - 1};
        case 'right':
            return {x: firstPoint.x == this.colsCount-1 ? 0: firstPoint.x + 1, y: firstPoint.y};
        case 'down':
            return {x: firstPoint.x, y: firstPoint.y == this.rowsCount-1 ? 0: firstPoint.y + 1};
        case 'left':
            return {x: firstPoint.x == 0 ? this.colsCount-1 : firstPoint.x - 1, y: firstPoint.y};
        }
    },

    getBody() {
        return this.body;
    },

    getLastStepDirection() {
        return this.lastStepDirection;
    },

    isOnPoint(point) {
        return this.body.some(snakePoint => snakePoint.x === point.x && snakePoint.y === point.y);
    },

    makeStep() {
        // Записываем направление движения, которое сейчас произойдет как направление прошлого шага.
        this.lastStepDirection = this.direction;
        // Вставляем следующую точку в начало массива.
        this.body.unshift(this.getNextStepHeadPoint());
        // Удаляем последний лишний элемент.
        this.body.pop();
    },

    growUp() {
        // Получаем индекс последней точки в массиве точек змейки (последний элемент this.body).
        const lastBodyIdx = this.body.length - 1;
        // Получаем последнюю точку змейки.
        const lastBodyPoint = this.body[lastBodyIdx];
        // Клонируем последнюю точку змейки (делаем копию).
        const lastBodyPointClone = Object.assign({}, lastBodyPoint);
        // Добавляем копию в наш массив this.body.
        this.body.push(lastBodyPointClone);
    },

    setDirection(direction) {
        this.direction = direction;
    },    
  },
}
</script>