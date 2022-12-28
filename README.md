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

        }

        }
```
> Check user
```


    void checkVoter(String user , String pass ){
        String url ="http://10.0.2.2/voting/voters.php?username="+user+"&pass="+pass;

        JsonArrayRequest ja = new JsonArrayRequest(Request.Method.GET,
                url,
                null,
                new Response.Listener<JSONArray>() {
                    @Override
                    public void onResponse(JSONArray response) {
                        try {
                            JSONObject ob = response.getJSONObject(0);
                            if (ob.getString("code").equals("yes")){
                            if (ob.getInt("vs_status")==1){
                                // save id to sharepreferenc
                                // go to the next activity
                            PreManager pr = new PreManager(MainActivity.this);
                            pr.setElc_id(ob.getString("elc_id"));
                            pr.setvs_id(ob.getString("vs_id"));

                                startActivity(new Intent(MainActivity.this,
                                        Candidates.class
                                ));


                            }else{
                                Toast.makeText(MainActivity.this, "election window is closed",Toast.LENGTH_LONG).show();

                            }
                            }else   {
                                Toast.makeText(MainActivity.this, "username or password is incorect",Toast.LENGTH_LONG).show();


                            }

                        } catch (JSONException e) {
                            e.printStackTrace();
                        }

                    }
                },
                new Response.ErrorListener() {
                    @Override
                    public void onErrorResponse(VolleyError error) {
                        Toast.makeText(MainActivity.this, "error"+error.getMessage(), Toast.LENGTH_LONG).show();

                    }
                }

        );

        RequestQueue queue = Volley.newRequestQueue(MainActivity.this);
        queue.add(ja);

    }
}// end of class
```
> depadence
```
implementation 'com.android.volley:volley:1.2.1'
```