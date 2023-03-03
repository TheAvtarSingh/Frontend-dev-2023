# Frontend-dev-2023

## Creation of Login Page of Admin 

### Create React Function Return using `rfc` and make a form

#### Note the Method="post" and onSubmit in form tag

```
<section className="vh-80">
      <div className="d-flex flex-row justify-content-around">
        {/* cont 1 */}
        <div className="m-0 p-0">
          <img
            src="https://mdbcdn.b-cdn.net/img/Photos/new-templates/bootstrap-login-form/draw2.webp"
            className="image-fluid"
            alt="sample"
          />
        </div>

        {/* Cont 2 */}
        {console.log("admin", admin)}
        <form className="mt-5 m-5" method="post" onSubmit={loginAdmin}>
          <h1 className="mb-5">Enter Your Details </h1>
          <div>
            <label htmlFor="adminEmail" className="form-label">
              Email address
            </label>
            <input
              value={admin.adminEmail}
              type="email"
              name="adminEmail"
              className="form-control"
              placeholder="Enter Your Email Address"
              onChange={handleChange}
            />
          </div>

          <div>
            <label className="form-label mt-3">Password</label>
            <input
              value={admin.adminPassword}
              type="password"
              pattern="(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{8,}"
              className="form-control mb-5"
              name="adminPassword"
              onChange={handleChange}
              placeholder="Enter Your Password"
            />
          </div>

          <div className="row mb-4">
            <div className="col d-flex justify-content-center">
              
            </div>

            <div className="col">
              <a href="#!">Forgot password?</a>
            </div>
          </div>
          <button
            type="submit"
            className="btn btn-primary btn-block mb-4"
            value="submit"
          >
            Sign in
          </button>
        </form>
      </div>
    </section>

```

![image](https://user-images.githubusercontent.com/88712571/222626881-08b48138-1525-4f1e-a879-51a59858ca32.png)

## Crete a State 

```
  const [admin, setAdmin] = useState({
    adminEmail: "",
    adminPassword: "",
  });
  
```

## create a handler method - specified in onChange
```
  const handleChange = (e) => {
    setAdmin({ ...admin, [e.target.name]: e.target.value });
  };

```

## Make a LoginAdmin() which get the request from form

```
  const loginAdmin = async (e) =>{
    e.preventDefault();
    fetch("http://localhost:5000/api/loginAdmin",{
      method:"POST",
      headers:{
        "Content-Type": "application/json",
      },
      body: JSON.stringify({
        adminEmail: admin.adminEmail,
        adminPassword: admin.adminPassword,
      }),
    }).then((res)=>{
      return res.json();
    }).then((resData)=>{
      if(resData.errors === undefined){
        console.log(resData.errors);
        setTimeout(()=>{ navigate("/") }, 5000);
      }else{
        return resData;
      }
    })
  }
  
```

### Note the Url in fetch method [Check in Backend]

