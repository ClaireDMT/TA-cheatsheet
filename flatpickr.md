`export default class extends Controller {
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
`

`<%= f.input :start_date,
												as: :string,
												placeholder: 'from',
												input_html: { data: { flatpickr_target: 'startTime',
                                              validate_form_target: "start",
                                              action: 'change->validate-form#enableButton',
                                              action: 'change->flatpickr#updateEnd' } },
												label: false %>
					</div>
					<div class="date-input">
						<%= f.input :end_date,
												as: :string,
												placeholder: 'to',
												input_html: { data: { flatpickr_target: 'endTime', validate_form_target: "end", action: 'change->validate-form#enableButton' } },
												label: false %>
					</div>
				</div>
        `
