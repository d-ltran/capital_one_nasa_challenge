
<form id="search-form">

  <div class="field">
   <label class="label">Search</label>
   <input type="text" class="input" name="query">
  </div>
  <!-- start date box -->
  <div class="field">
   <label class="label">Start Date</label>
   <input type="text" class="input" name="start_date">
  </div>
  <!-- end date box -->
  <div class="field">
   <label class="label">End Date</label>
   <input type="text" class="input" name="end_Date">
  </div>
  <!-- submit button -->
  <div class="field has-text-right">
   <button type="submit" class="button is-danger"> Submit</button>
  </div>

</form>
<script>
const searchForm = document.getElementById('search-form');
const queryInput = signupForm.querySelector('input[name=query]');
const startInput  = signupForm.querySelector('input[name=start_date]');
const endInput  = signupForm.querySelector('input[name=end_date]');

searchForm.addEventListener('submit', processSearchForm);
function processSearchForm(e){
     e.preventDefault();
}
const query = queryInput.value;
const start_date = startInput.value;
const end_date = endInput.value;
</script>
