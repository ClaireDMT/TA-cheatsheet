export default class extends Controller {
  static targets = [ "startTime", "endTime" ]

  connect() {
    flatpickr(this.startTimeTarget, {
      format: "d.m.y",
      altFormat: "d.m.y",
      altInput: true,
      defaultDate: Date.today,
      minDate: "today"
    })
    flatpickr(this.endTimeTarget, {
      format: "d.m.y",
      altFormat: "d.m.y",
      altInput: true,
      defaultDate: Date.tomorrow,
      minDate: "today"
    })
  }

  updateEnd() {
    const fpStart = this.startTimeTarget;
    const fpEnd = flatpickr(this.endTimeTarget, {});
    fpEnd.set('minDate', this.#dayAfter(fpStart.value));
  }

  #dayAfter(date) {
    const result = new Date(date);
    result.setDate(result.getDate() + 1);
    return result;
  }
}
