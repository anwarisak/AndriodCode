> button variable
```
        EditText edusername = findViewById(R.id.edusername);
        EditText edpass = findViewById(R.id.edpass);

        Button btnlogin = findViewById(R.id.btnlogin);

        btnlogin.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {


                String user = edusername.getText().toString();
                String pass = edpass.getText().toString();

                saveStudents(stdname, stdphone);


            }
        });
```
> depadence
```
implementation 'com.android.volley:volley:1.2.1'
```