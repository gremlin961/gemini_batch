# gemini_batch
Batch predictions with Gemini

Run the following SQL scripts to setup your source BQ environment.

## Make sure to change YOUR_PROJECT_NAME to the name of your GCP project in steps 2 and 3!


1 - Create a new dataset in BQ named gemini_batch_test

CREATE SCHEMA `gemini_batch_test`
OPTIONS (
  location='us-central1'
);


2 - Create a new input table and add a single entry for a batch prediction job.

CREATE TABLE `YOUR_PROJECT_NAME.gemini_batch_test.batch_input_table` (
    request STRING
    );


3 - Create a new table in an exisitng dataset named gemini_batch_test

INSERT INTO `YOUR_PROJECT_NAME.gemini_batch_test.batch_input_table` (request)
VALUES ('{"contents":[{"role":"user","parts":{"text":"Give me a recipe for banana bread."}}],"system_instruction":{"parts":[{"text":"You are a chef."}]},"generation_config":{"top_k":5}}');



