# snip
<details><summary>frontend</summary>
  
```js
{
	// Place your global snippets here. Each snippet is defined under a snippet name and has a scope, prefix, body and 
	// description. Add comma separated ids of the languages where the snippet is applicable in the scope field. If scope 
	// is left empty or omitted, the snippet gets applied to all languages. The prefix is what is 
	// used to trigger the snippet and the body will be expanded and inserted. Possible variables are: 
	// $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. 
	// Placeholders with the same ids are connected.
	// Example:
	"React Functional Component": {
		"prefix": "$rfc",
		"body": [
		  "import React from \"react\"",
		  "",
		  "const ${1:name} = (props) => {",
		  "  return (",
		  "    <div>",
		  "      $2",
		  "    </div>",
		  "  )",
		  "};",
		  "",
		  "export default ${1:name};",
		  ""
		],
		"description": "React Functional Component"
	  },

	"action": {
		"prefix": "$act",
		"body": [
		  "import { REGISTER_REQUEST, REGISTER_SUCCESS, REGISTER_FAIL } from \"./types\";",
		  "",
		  "import axios from \"../../axios/axios\";",
		  "",
		  "const ${1:register} = (${2|data, axiosPrivate|}) => async (dispatch) => {",
		  "   $3 ",
		  "};",
		  "",
		  "export default ${1:register};"
		],
		"description": "action"
	  },

	  "dispatch type": {
		"prefix": " $actType",
		"body": [
		  "dispatch({ type: $2_${1|REQUEST,SUCCESS|} });"
		],
		"description": "dispatch type"
	  },

	  "dispatch type + payload": {
		"prefix": "$actTypePayload",
		"body": [
		  "dispatch({",
		  "  type: $2_${1|REQUEST,SUCCESS|},",
		  "  payload: {",
		  "    accessToken: res?.data?.accessToken,",
		  "    userInfo: res?.data?.userInfo,",
		  "  },",
		  "});"
		],
		"description": "dispatch type + payload"
	  },

	  "FAIL dispatch type + payload": {
		"prefix": "$actTypeFail",
		"body": [
		  "dispatch({ type: $1_FAIL, payload: { errorMsg } });"
		],
		"description": "FAIL dispatch type + payload"
	  },

	  "error message": {
		"prefix": "$act-err-msg",
		"body": [
		  "// if (signal.aborted) dispatch({ type: CLEAR_COVER }); //if (signal.aborted) return;",	
		  "let errorMsg = \"\";",
		  "if (!error?.response) {",
		  "  errorMsg = \"Server not respond\";",
		  "} else if (error.response?.status === 400) {",
		  "  errorMsg = ${1|'Invalid email or password',error?.response?.data?.errors[0]?.msg|};",
		  "$2} else if (error.response?.status === 401) { errorMsg = \"Email or password is incorrect\"; //Unauthorized Error => use in LOGIN",
		  "} else {",
		  "  errorMsg = \"Error in login! Please try again\"",
		  "}"
		],
		"description": "error message"
	  },

	  "public + private": {
		"prefix": "$src-axios",
		"body": [
		  "import axios from \"axios\";",
		  "",
		  "const BASE_URL = \"http://localhost:3500\";",
		  "export default axios.create({",
		  "  baseURL: BASE_URL,",
		  "});",
		  "",
		  "// axios private instance",
		  "export const axiosPrivate = axios.create({",
		  "  baseURL: BASE_URL,",
		  "  headers: {",
		  "    \"Content-Type\": \"application/json\",",
		  "  },",
		  "  withCredentials: true,",
		  "});",
		  ""
		],
		"description": "public + private"
	  },

	  "POST without res": {
		"prefix": "$axios-post",
		"body": [
		  "await axios.post(",
		  "  \"/user/register\", ",
		  "  JSON.stringify({ ${1|...data,x|} }), ",
		  "  {",
		  "    headers: { \"Content-Type\": \"application/json\" },",
		  "    withCredentials: true,",
		  "  }",
		  ");"
		],
		"description": "POST without res"
	  },

	  "POST with res": {
		"prefix": "$axios-post-res",
		"body": [
		  "const res = await axios.post(",
		  "  \"/user/auth\",",
		  "  JSON.stringify({ ${1|...data,x|} }),",
		  "  {",
		  "    headers: { \"Content-Type\": \"application/json\" },",
		  "    withCredentials: true,",
		  "  }",
		  ");"
		],
		"description": "POST with res"
	  },

	  "GET with res": {
		"prefix": "$axios-get-res",
		"body": [
		  "const response = await axios.get(\"/user/refresh\", { withCredentials: true, });"
		],
		"description": "GET with res"
	  },

	  "reducer setup": {
		"prefix": "$reducer",
		"body": [
		  "import {",
		  "  X_REQUEST,",
		  "  X_SUCCESS,",
		  "  X_FAIL,",
		  "} from \"../actions/types\";",
		  "",
		  "const initialState = {",
		  "  $1",
		  "};",
		  "",
		  "function XReducer(state = initialState, action) {",
		  "  const { type, payload } = action;",
		  "",
		  "  switch (type) {",
		  "",
		  "",
		  "    default:",
		  "      return state;",
		  "  }",
		  "}",
		  "",
		  "",
		  "export default XReducer;",
		  ""
		],
		"description": "reducer setup"
	  },

	  "initialState": {
		"prefix": "$initialState",
		"body": [
		  "${1|isLoading: false,errorMessage: null,x:y|}",
		],
		"description": "initialState"
	  },

	  "case": {
		"prefix": "$reducer-case",
		"body": [
		  "case X_Y:",
		  "  return {",
		  "    ...state,",
		  "    isLoading: true,",
		  "    errorMessage: null,",
		  "    posts: [...state.posts, ...payload.posts],",
		  "    userInfo: payload.userInfo,",
		  "    userInfo: {",
		  "      ...state.userInfo,",
		  "      verified: payload.verified,",
		  "    },",
		  "  };"
		],
		"description": "case"
	  },

	  "action types": {
		"prefix": "$type",
		"body": [
		  "export const ${1:X_Y} = \"${1:X_Y}\";$2"
		],
		"description": "action types"
	  },

	  "index if reducer": {
		"prefix": "$reducer-index",
		"body": [
		  "import { combineReducers } from \"redux\";",
		  "import ${1:x}Reducer from \"./login\";",
		  "",
		  "export default combineReducers({",
		  "  ${2:user}: ${1:x}Reducer,",
		  "});"
		],
		"description": "index if reducer"
	  },

	  "redux store": {
		"prefix": "$redux-store",
		"body": [
			"import { createStore, applyMiddleware } from \"redux\";",
			"// import { composeWithDevTools } from \"redux-devtools-extension\";",
			"import { composeWithDevTools } from '@redux-devtools/extension';",
			"// import thunk from 'redux-thunk'",
			"import {thunk} from \"redux-thunk\";",
			"",
			"import rootReducer from \"./reducers\";",
			"",
			"const initialState = {};",
			"",
			"const middlewares = [thunk];",
			"",
			"const store = createStore(",
			"  rootReducer,",
			"  initialState,",
			"  composeWithDevTools(applyMiddleware(...middlewares))",
			");",
			"",
			"export default store;",
			""
		  ],
		"description": "redux store"
	  },

	  "RRD + REDUX": {
		"prefix": "$src-index",
		"body": [
		  "import React from \"react\";",
		  "import ReactDOM from \"react-dom/client\";",
		  "import \"./index.css\";",
		  "import App from \"./App\";",
		  "import { BrowserRouter, Routes, Route } from \"react-router-dom\";",
		  "import { Provider } from \"react-redux\";",
		  "import store from \"./redux/store\";",
		  "",
		  "const root = ReactDOM.createRoot(document.getElementById(\"root\"));",
		  "root.render(",
		  "  <Provider store={store}>",
		  "    <BrowserRouter>",
		  "      <Routes>",
		  "        <Route path=\"*\" element={<App />} />",
		  "      </Routes>",
		  "    </BrowserRouter>",
		  "  </Provider>",
		  ");",
		  ""
		],
		"description": "RRD + REDUX"
	  },

	  "tailwind + fonts + background + custome classes": {
		"prefix": "$src-indexcss",
		"body": [
		  "@tailwind base;",
		  "@tailwind components;",
		  "@tailwind utilities;",
		  "",
		  "* {",
		  "  margin: 0;",
		  "  padding: 0;",
		  "  box-sizing: border-box;",
		  "}",
		  "",
		  ".lazyImage span {",
		  "  width: 100%;",
		  "  height: 100%;",
		  "}",
		  ".lazyImage span img {",
		  "  object-fit: cover;",
		  "  height: 100%;",
		  "  width: 100%;",
		  "}",
		  "",
		  "",
		  "/* persian font */",
		  "@layer utilities {    ",
		  "  @font-face {",
		  "    font-family: 'Vazir';",
		  "    src: url('../public/font/Vazir.eot');",
		  "    src: url('../public/font/Vazir.woff') format('woff');",
		  "    src: url('../public/font/Vazir.ttf') format('truetype');",
		  "    font-weight: normal;",
		  "    font-style: normal;",
		  "  }",
		  "",
		  "  body {",
		  "    font-family: \"Vazir\";",
		  "  }",
		  "}",
		  "",
		  "",
		  "/* background */",
		  "@layer base {",
		  "  body {",
		  "    @apply bg-gray-200;",
		  "  }",
		  "",
		  "  /* right-to-left */",
		  "  .rtl{",
		  "    direction: rtl;",
		  "  }",
		  "  ",
		  "  /* remove eye icon from input */",
		  "  input::-ms-reveal,",
		  "  input::-ms-clear {",
		  "    display: none;",
		  "  }",
		  "",
		  "}",
		  "",
		  "/* custom classes */",
		  "@layer components {",
		  "  .textInput {",
		  "    @apply ring-1 rounded-lg text-gray-600 font-normal text-lg px-4 py-3 w-full border-none bg-gray-100;",
		  "  }",
		  "  .blue-btn {",
		  "    @apply block p-3 bg-blue-600 w-full rounded-lg font-bold text-xl text-gray-200 hover:bg-blue-700 transition-colors;",
		  "  }",
		  "  .divider {",
		  "    @apply h-[0.1rem] bg-gray-200 w-full;",
		  "  }",
		  "  .green-btn {",
		  "    @apply px-12 py-3 m-auto inline-block text-lg font-bold bg-green-600 rounded-lg text-gray-100 hover:bg-green-700 transition-colors  shadow-green-600 shadow-2xl hover:shadow-none;",
		  "  }",
		  "  .errorInfo {",
		  "    @apply text-red-600 w-7 drop-shadow-[0_5px_6px_rgba(220,38,38,0.65)];",
		  "  }",
		  "}",
		  ""
		],
		"description": "tailwind + fonts + background + custome classes"
	  },

	  "tailwind-config": {
		"prefix": "$src-tailwind-config",
		"body": [
			"/** @type {import('tailwindcss').Config} */",
			"module.exports = {",
			"  content: [\"./src/**/*.{js,jsx,ts,tsx}\"],",
			"  darkMode: 'class', // darkmode",
			"  theme: {",
			"    extend: {},",
			"  },",
			"  plugins: [",
			"    require(\"@tailwindcss/forms\"),",
			"    require(\"tailwind-scrollbar\")({ nocompatible: true }),",
			"  ],",
			"};"
		  ],
		"description": "tailwind-config"
	  },

	  "app.js": {
		"prefix": "$src-app",
		"body": [
			"import { Routes, Route } from \"react-router-dom\";",
			"import Login from \"./pages/login\";",
			"import Home from \"./pages/home\";",
			"import Reset from \"./pages/reset\";",
			"import PersistLogin from \"./auth/PersistLogin\";",
			"import Unauthorized from \"./pages/unauthorized/Unauthorized\";",
			"import Admin from \"./pages/unauthorized/Admin\";",
			"import RequireAuth from \"./auth/RequireAuth\";",
			"import NotFound from \"./pages/notFound/NotFound\";",
			"import Layout from \"./auth/Layout\";",
			"",
			"const ROLES = {",
			"  User: 1000,",
			"  Editor: 1002,",
			"  Admin: 1001,",
			"};",
			"",
			"function App() {",
			"  return (",
			"    <Routes>",
			"      {/* PUBLIC ROUTES */}",
			"      <Route path=\"/login\" element={<Login />} />",
			"      <Route path=\"/reset\" element={<Reset />} />",
			"",
			"      {/* PROTECTED ROUTES */}",
			"      <Route element={<PersistLogin />}>",
			"        <Route element={<RequireAuth allowedRoles={[ROLES.Admin, ROLES.Editor, ROLES.User]}/>}>",
			"          {/* PAGES WITHOUT NAVBAR */}",
			"          <Route path=\"/\" element={<Home />} />",
			"",
			"          {/* PAGES CONTAIN NAVBAR - using Layout */}",
			"          <Route element={<Layout />}>",
			"            <Route path=\"/\" element={<About/>} />",
			"          </Route>",
			"",
			"          {/* ADMIN */}",
			"          <Route element={<RequireAuth allowedRoles={[ROLES.Admin]} />}>",
			"            <Route path=\"/admin\" element={<Admin />} />",
			"          </Route>",
			"",
			"          {/* UNAUTHORIZED */}",
			"          <Route path=\"/unauthorized\" element={<Unauthorized />} />",
			"        </Route>",
			"",
			"        {/* NOT FOUND 404 */}",
			"        <Route path=\"/*\" element={<NotFound />} />",
			"      </Route>",
			"    </Routes>",
			"  );",
			"}",
			"",
			"export default App;"
		  ],
		"description": "app.js"
	  },

	  "data using in app": {
		"prefix": "$offline-data",
		"body": [
		  "export const menu = [",
		  "  {",
		  "    name: \"Campus\",",
		  "    icon: \"campus\",",
		  "    description: \"A unique, exclusive space for college students on Facebook.\",",
		  "  },",
		  "];",
		  "",
		  "",
		  "export const create = [",
		  "  {",
		  "    name: \"Post\",",
		  "    icon: \"edit\",",
		  "  },",
		  "];",
		  ""
		],
		"description": "data using in app"
	  },

	  "map-offline-data": {
		"prefix": "$map-offline-data",
		"body": [
		  "<!-- import { menu, create } from \"../../data/allMenu\"; -->",
		  "{menu.slice(0, visible ? menu.length : 8).map((item, index) => (",
		  "  <AllMenuItem",
		  "    index={index}",
		  "    name={item.name}",
		  "    icon={item.icon}",
		  "    description={item.description}",
		  "  />",
		  "))}"
		],
		"description": "map-offline-data"
	  },

	  "": {
		"prefix": "$use-screen-size",
		"body": [
		  "import { useMediaQuery } from \"react-responsive\";",
		  "",
		  "",
		  "const useScreenSize = () => {",
		  "  const isSM = useMediaQuery({ minWidth: 640 })",
		  "  const isMD = useMediaQuery({ minWidth: 768 })",
		  "  const isLG = useMediaQuery({ minWidth: 1024 })",
		  "  const isXL = useMediaQuery({ minWidth: 1280 })",
		  "  const is2XL = useMediaQuery({ minWidth: 1536 })",
		  "  return { isSM, isMD, isLG, isXL, is2XL };",
		  "}",
		  "",
		  "",
		  "export default useScreenSize;",
		  ""
		],
		"description": ""
	  },

	  "use-click-outside": {
		"prefix": "$use-click-outside",
		"body": [
		  "import { useEffect } from \"react\";",
		  "",
		  "const useClickOutside = (ref, cb) => {",
		  "  useEffect(() => {",
		  "    const listener = (e) => {",
		  "      if (!ref.current || ref.current.contains(e.target)) {",
		  "        return;",
		  "      }",
		  "      cb();",
		  "    };",
		  "",
		  "    document.addEventListener(\"mousedown\", listener);",
		  "    document.addEventListener(\"touchstart\", listener);",
		  "",
		  "    return () => {",
		  "      document.removeEventListener(\"mousedown\", listener);",
		  "      document.removeEventListener(\"touchstart\", listener);",
		  "    };",
		  "  }, [ref]);",
		  "};",
		  "",
		  "export default useClickOutside;",
		  ""
		],
		"description": "use-click-outside"
	  },

	  "useClickOutsideProp": {
		"prefix": "$useClickOutsideProp",
		"body": [
		  "useClickOutside(searchBox, () => {setShow(false)});",
		  "",
		  "<div ref={searchBox}></div>"
		],
		"description": "useClickOutsideProp"
	  },

	  "useClickOutside": {
		"prefix": "$useClickOutside",
		"body": [
		  "useClickOutside(searchBox, setShow(false));",
		  "",
		  "<div ref={searchBox}></div>"
		],
		"description": "useClickOutside"
	  },

	  "": {
		"prefix": "$useScreenSize",
		"body": [
		  "const { ${1|isSM,isMD,isLG,isXL,is2XL|} } = useScreenSize();",
		  "//className={`${isLG ? \"\" : \"bg-red-200\"}",
		  "//OR",
		  "//{isLG && <X/>}"
		],
		"description": ""
	  },

	  "refresh": {
		"prefix": "$persistLogin",
		"body": [
		  "import { Outlet, Navigate } from \"react-router-dom\";",
		  "import { useDispatch, useSelector } from \"react-redux\";",
		  "import newAccessTokenAction from \"../../redux/actions/newAccessToken\";",
		  "import { useEffect } from \"react\";",
		  "import BLoader from \"../ui/BarLoader\";",
		  "",
		  "const PersisLogin = () => {",
		  "  const user = useSelector((state) => state.user);",
		  "  const newAccessToken = useSelector((state) => state.newAccessToken);",
		  "  const dispatch = useDispatch();",
		  "",
		  "  useEffect(() => {",
		  "    console.log(user);",
		  "    if (!user?.accessToken) dispatch(newAccessTokenAction());",
		  "  }, []);",
		  "",
		  "  return (",
		  "    <>",
		  "      {!user?.accessToken && <Navigate to=\"/login\" />}",
		  "      <BLoader isLoading={newAccessToken?.isLoading} />",
		  "      {user?.accessToken && <Outlet />}",
		  "    </>",
		  "  );",
		  "};",
		  "export default PersisLogin;",
		  ""
		],
		"description": "refresh"
	  },

	  "": {
		"prefix": "$noAuth",
		"body": [
		  "import { Navigate, Outlet } from \"react-router-dom\";",
		  "import { useSelector, useDispatch } from \"react-redux\";",
		  "import { useEffect } from \"react\";",
		  "import newAccessTokenAction from \"../../redux/actions/newAccessToken\";",
		  "",
		  "const NotAuth = () => {",
		  "  const user = useSelector((state) => state.user);",
		  "  const dispatch = useDispatch();",
		  "",
		  "  useEffect(() => {",
		  "    if (!user?.accessToken) dispatch(newAccessTokenAction());",
		  "  }, []);",
		  "",
		  "  return user?.accessToken ? <Navigate to=\"/\" /> : <Outlet />;",
		  "};",
		  "",
		  "export default NotAuth;",
		  ""
		],
		"description": ""
	  },

	  "state": {
		"prefix": "$useSelector",
		"body": [
		  "// import { useDispatch, useSelector } from 'react-redux';",
		  "const ${1:user} = useSelector((state) => state.${1:user});"
		],
		"description": "state"
	  },

	  "useDispatch": {
		"prefix": "$useDispatch",
		"body": [
		  "// import { useDispatch, useSelector } from 'react-redux';",
		  "const dispatch = useDispatch();"
		],
		"description": "useDispatch"
	  },

	  "dispatch an action": {
		"prefix": "$dispatch",
		"body": [
		  "dispatch(xAction(${1|values,values.password,user.email|}));"
		],
		"description": "dispatch an action"
	  },

	  "input with formik & yup": {
		"prefix": "$input-formik",
		"body": [
		  "<div className={`${isLG ? \"\" : \"space-y-4\"}  relative`}>",
		  "  <div className=\"relative\">",
		  "    <input",
		  "      className={`textInput ${formik.touched.${1:first_name} && formik.errors.${1:first_name} ? \"ring-red-400\" : \"\"}`}",
		  "      id=\"${1:first_name}\"",
		  "      name=\"${1:first_name}\"",
		  "      onBlur={formik.handleBlur}",
		  "      onChange={formik.handleChange}",
		  "      value={formik.values.${1:first_name}}",
		  "      type=\"${2|text,email,password|}\"",
		  "      placeholder=\"${3:First name}\"",
		  "    />",
		  "    {formik.touched.${1:first_name} && formik.errors.${1:first_name} ? <ExclamationCircleIcon className=\"errorInfo\" /> : null}",
		  "  </div>",
		  "  {formik.touched.${1:first_name} && formik.errors.${1:first_name} ? <ErrorMessage message={formik.errors.${1:first_name}} /> : null}",
		  "</div>"
		],
		"description": "input with formik & yup"
	  },

	  "form with formik & yup": {
		"prefix": "$form",
		"body": [
		  "<form className=\"p-2 mt-2 space-y-3\" onSubmit={formik.handleSubmit}>",
		  "",
		  "  $1",
		  "  <p className=\"text-sm p-2 text-gray-500 \">text</p>",
		  "  {register?.errorMessage && (<p>{register?.errorMessage}</p>)}",
		  "  <div className=\"text-center\">",
		  "    <button",
		  "      disabled={!(formik.isValid && formik.dirty)}",
		  "      className=\"disabled:cursor-not-allowed disabled:bg-green-300\"",
		  "      type=\"submit\"",
		  "    >",
		  "      Sign Up",
		  "    </button>",
		  "  </div>",
		  "</form>"
		],
		"description": "form with formik & yup"
	  },

	  "input select": {
		"prefix": "$input-select-formik",
		"body": [
		  "<!-- const ${2:options} = [1, 2, 3] -->",
		  "",
		  "<div>",
		  "  <div className=\"flex space-x-1 items-center \">",
		  "    <span className=\"text-gray-500 text-lg\"> title </span>",
		  "    <QuestionMarkCircleIcon className=\"w-5 text-gray-500 \" />",
		  "  </div>",
		  "",
		  "  <div className=\"flex justify-around mt-2\">",
		  "    <select",
		  "      name=\"${1:FROM_INITIALVALUE}\"",
		  "      id=\"${1:FROM_INITIALVALUE}\"",
		  "      onChange={formik.handleChange}",
		  "      onBlur={formik.handleBlur}",
		  "      value={formik.values.${1:FROM_INITIALVALUE}}",
		  "      className=\"w-24 rounded-lg text-lg border-gray-500 text-gray-500 font-semibold ring-0 border-2\"",
		  "    >",
		  "      {${2:options}.map((${3:opt}, index) => (",
		  "        <option value={${3:opt}} key={index}>",
		  "          {${3:opt}}",
		  "        </option>",
		  "      ))}",
		  "      </select>",
		  "  </div>",
		  "</div>"
		],
		"description": "input select"
	  },

	  "input radio": {
		"prefix": "$input-radio-formik",
		"body": [
		  "<div>",
		  "  <div className=\"text-lg text-gray-500 flex items-center space-x-1\">",
		  "    <span> ${1:FROM_INITIALVALUE} </span>",
		  "    <QuestionMarkCircleIcon className=\"w-5\" />",
		  "  </div>",
		  "  <div className=\"flex justify-around\">",
		  "    <label",
		  "      className=\"border-gray-500 w-24 px-2 py-2 rounded-lg border-2 text-gray-500 text-lg flex items-center justify-between \"",
		  "      htmlFor=\"${2:female}\"",
		  "    >",
		  "      ${2:Female}",
		  "      <input",
		  "        className=\"bg-gray-200 border-2 focus:ring-0\"",
		  "        type=\"radio\"",
		  "        name=\"${1:FROM_INITIALVALUE}\"",
		  "        id=\"${2:female}\"",
		  "        value=\"${2:female}\"",
		  "        onChange={formik.handleChange}",
		  "        onBlur={formik.handleBlur}",
		  "      />",
		  "    </label>",
		  "  </div>",
		  "</div>"
		],
		"description": "input radio"
	  },

	  "use formik": {
		"prefix": "$useFormik",
		"body": [
		  "// import { useFormik } from \"formik\";",	
		  "  const formik = useFormik({",
		  "    initialValues: {",
		  "      first_name: \"\",",
		  "      last_name: \"\",",
		  "      email: \"\",",
		  "      password: \"\",",
		  "      bYear: new Date().getFullYear() - 18;,",
		  "      bMonth: new Date().getMonth() + 1,",
		  "      bDay: new Date().getDate(),",
		  "      gender: \"male\",",
		  "    },",
		  "    validationSchema: ${1:YUP_NAME}Validation,",
		  "    onSubmit: (values) => {",
		  "      dispatch(${2:x}Action(${3|values,values.email|}));",
		  "    },",
		  "  });"
		],
		"description": "use formik"
	  },

	  "use yup": {
		"prefix": "$yup",
		"body": [
		  "//import * as Yup from \"yup\";",	
		  "const ${1:register}Validation = Yup.object({",
		  "  ${2:FROM_INITIALVALUES}: Yup.string()",
		  "    .required(\"What's your first name?\")",
		  "    .min(4, \" Must be at least 4 characters\")",
		  "    .email(\"Invalid email address\")",
		  "    .oneOf([Yup.ref(\"password\")], \"Password must match\")",
		  "    .matches(",
		  "      /^(?=.*[a-z])(?=.*[A-Z])(?=.*\\d)(?=.*[@$!%*?&])[A-Za-z\\d@$!%*?&]{8,}$/,",
		  "      \"password must contain uppercase, lowercase, number and  special character\"",
		  "    ),",
		  "});"
		],
		"description": "use yup"
	  },

	  "ref + autofocus": {
		"prefix": "$input-ref",
		"body": [
		  "// const searchIcon = useRef(null);",
		  "",
		  "<div className=\"relative flex items-center \">",
		  "  <span className=\"absolute ml-3 text-gray-600\" ref={searchIcon}>",
		  "    <MagnifyingGlassIcon className=\"w-5\" />",
		  "  </span>",
		  "  <input",
		  "    onFocus={() => (searchIcon.current.style.display = \"none\")}",
		  "    onBlur={() => (searchIcon.current.style.display = \"block\")}",
		  "    autoFocus={true}",
		  "    type=\"text\"",
		  "    className=\"w-full border-none rounded-full text-gray-600 text-md bg-gray-200 pl-9\"",
		  "    placeholder=\"Search Facebook\"",
		  "  />",
		  "</div>"
		],
		"description": "ref + autofocus"
	  },

	  "profile img": {
		"prefix": "$img-profile",
		"body": [
		  "<img src={${1:user?.userInfo?.picture}} alt=\"\" className=\"w-8 h-8 rounded-full mr-2 bg-gray-300 object-cover\" />"
		],
		"description": "profile"
	  },

	  "without crop": {
		"prefix": "$img-complete",
		"body": [
		  "<img",
		  "  src={`/assets/left/${ OFFLINE_ICON }.png`}",
		  "  alt=\"\"",
		  "  className=\"object-contain w-9\"",
		  "/>"
		],
		"description": "without crop"
	  },

	  "profile": {
		"prefix": "$navlink-active",
		"body": [
		  "<NavLink",
		  "  to=\"/\"",
		  "  className={({ isActive }) =>",
		  "    \"hover:bg-gray-200 rounded-lg py-3 px-6 hidden sm:block transition-colors \" +",
		  "    (isActive",
		  "      ? \"border-b-4 border-b-blue-500 rounded-none hover:bg-transparent\"",
		  "      : \"\")",
		  "  }",
		  ">",
		  "  HOME",
		  "</NavLink>"
		],
		"description": "navlink active"
	  },

	  "navlink": {
		"prefix": "$navlink",
		"body": [
		  "<NavLink",
		  "   to={`/profile/${user?.userInfo?.username}`}",
		  "   className=\"flex justify-center items-center space-x-1 rounded-full transition-colors hover:bg-gray-200 p-1\"",
		  ">"
		],
		"description": "navlink"
	  },

	  "badge": {
		"prefix": "$badge",
		"body": [
		  "<span className=\"absolute top-1 left-4 p-2 w-5 h-5 text-sm rounded-full flex items-center justify-center text-gray-200 font-bold bg-red-600\">",
		  "   19",
		  "</span>"
		],
		"description": "badge"
	  },

	  "display/hide with ref": {
		"prefix": "$open-close-ref",
		"body": [
		  "const [${2:showAllMenu}, ${3:setShowAllMenu}] = useState(false);",
		  "const ${1:AllMenuRef} = useRef(null);",
		  "",
		  "useClickOutside(${1:AllMenuRef}, () => {${3:setShowAllMenu}(false)});",
		  "",
		  "<div ref={${1:AllMenuRef}}>",
		  "  <div",
		  "    onClick={() => ${3:setShowAllMenu}((prev) => !prev)}",
		  "    className={`flex items-center justify-center w-10 h-10 cursor-pointer transition-colors rounded-full ${${2:showAllMenu} && \"bg-blue-100\"}`}",
		  "  >",
		  "    <MenuIcon />",
		  "  </div>",
		  "  {${2:showAllMenu} && <AllMenu />}",
		  "</div>"
		],
		"description": "display/hide with ref"
	  },

	  "scrollbar": {
		"prefix": "$scrollbar",
		"body": [
		  "<div className=\"overflow-y-scroll scrollbar-thin h-[94%] pr-6 scrollbar-thumb-rounded-md scrollbar-thumb-gray-300\">",
		  "  <!-- child content -->",
		  "</div>"
		],
		"description": "scrollbar"
	  },

	  "forward back": {
		"prefix": "$forward-back",
		"body": [
			"// const [visible, setVisible] = useState(0);",
			"",
			"{visible === 0 && (<button onClick={() => setVisible(1)}>Setting</button>)} ",
			"{visible === 1 && <Setting setVisible={setVisible} />} /* <button onClick={() => setVisible(0)}>back</button> */"
		],
		"description": "forward back"
	  },

	  "img public": {
		"prefix": "$img-public",
		"body": [
		  "// icon from props",
		  "<img src={`/assets/icons/${ icon }.png`} alt='' className='w-7' />"
		],
		"description": "img public"
	  },
	
	  "tab icon & text": {
		"prefix": "$tab-icon",
		"body": [
		  "<title>Facebook</title>",
		  "<link rel=\"icon\" href=\"/facebook.png\" type=\"image/x-icon\" />"
		],
		"description": "tab icon & text"
	  },

	  "refresh token hook ": {
		"prefix": "$use-refresh-token",
		"body": [
		  "import axios from \"../axios/axios\";",
		  "import { REFRESH_ACCESSTOEKN } from \"../redux/actions/types\";",
		  "import { useDispatch } from \"react-redux\";",
		  "",
		  "const useRefreshToken = () => {",
		  "  const dispatch = useDispatch();",
		  "",
		  "  const refresh = async () => {",
		  "    try {",
		  "      const { data } = await axios.get(\"/user/refresh\", {",
		  "        withCredentials: true,",
		  "      });",
		  "      dispatch({",
		  "        type: REFRESH_ACCESSTOEKN,",
		  "        payload: {",
		  "          accessToken: data.accessToken,",
		  "          userInfo: data.userInfo,",
		  "        },",
		  "      });",
		  "      return data?.accessToken;",
		  "    } catch (error) {",
		  "      return Promise.reject(error);",
		  "    }",
		  "  };",
		  "  return refresh;",
		  "};",
		  "",
		  "export default useRefreshToken;",
		  ""
		],
		"description": "refresh token hook "
	  },

	  "Brear token attachment hook ": {
		"prefix": "$use-axios-private",
		"body": [
		  "import { axiosPrivate } from \"../axios/axios\";",
		  "import { useEffect } from \"react\";",
		  "import { useSelector, useDispatch } from \"react-redux\";",
		  "import useRefreshToken from \"./useRefreshToken\";",
		  "",
		  "const useAxiosPrivate = () => {",
		  "  const user = useSelector((state) => state.user);",
		  "  const dispatch = useDispatch();",
		  "  const refresh = useRefreshToken();",
		  "",
		  "  useEffect(() => {",
		  "    const requestIntercept = axiosPrivate.interceptors.request.use(",
		  "      (config) => {",
		  "        if (!config.headers[\"Authorization\"]) {",
		  "          config.headers[\"Authorization\"] = `Bearer ${user?.accessToken}`;",
		  "",
		  "          console.log(config.headers[\"Authorization\"]);",
		  "        }",
		  "",
		  "        return config;",
		  "      },",
		  "      (error) => Promise.reject(error)",
		  "    );",
		  "",
		  "    const responseIntercept = axiosPrivate.interceptors.response.use(",
		  "      (response) => response,",
		  "      async (error) => {",
		  "        const prevRequest = error?.config;",
		  "        if (error?.response?.status === 403 && !prevRequest?.sent) {",
		  "          prevRequest.sent = true;",
		  "          const newAccessToken = await refresh();",
		  "          console.log(newAccessToken);",
		  "          prevRequest.headers[\"Authorization\"] = `Bearer ${ newAccessToken }`;",
		  "          return axiosPrivate(prevRequest);",
		  "        }",
		  "        return Promise.reject(error);",
		  "      }",
		  "    );",
		  "",
		  "    return () => {",
		  "      axiosPrivate.interceptors.request.eject(requestIntercept);",
		  "      axiosPrivate.interceptors.response.eject(responseIntercept);",
		  "    };",
		  "  }, [user, dispatch]);",
		  "  return axiosPrivate;",
		  "};",
		  "",
		  "export default useAxiosPrivate;",
		  ""
		],
		"description": "Brear token attachment hook "
	  },

	  "backdrop + modal": {
		"prefix": "$backdrop-modal",
		"body": [
		  "<!-- const [showModal, setShowModal] = useState(!!token);",
		  "const modalRef = useRef(null);",
		  "",
		  "useClickOutside(modalRef, () => {",
		  "  setShowModal(false);",
		  "}); -->",
		  "",
		  "{showModal && (",
		  "  <div className=\"absolute inset-0 flex items-center justify-center bg-gray-200 bg-opacity-90 z-10\">",
		  "    <div",
		  "      ref=\"{modalRef}\"",
		  "      className=\"w-80 h-52 flex flex-col items-center rounded-lg shadow-md bg-white \"",
		  "    >",
		  "      <!-- content -->",
		  "    </div>",
		  "  </div>",
		  "  )}",
		  ""
		],
		"description": "backdrop + modal"
	  },

	  "timer": {
		"prefix": "$timer",
		"body": [
		  "const timerId = setTimeout(() => {",
		  "  ${1:navigate(\"/\");}",
		  "}, 3000);",
		  "return () => clearTimeout(timerId);"
		],
		"description": "timer"
	  },

	  "useNavigate": {
		"prefix": "$useNavigate",
		"body": [
		  "//import { useNavigate } from \"react-router-dom\";",
		  "//const navigate = useNavigate();",
		  "navigate(\"/\");"
		],
		"description": "useNavigate"
	  },

	  "DONT USE IN ACTION": {
		"prefix": "$dispatch-AP-here",
		"body": [
		  "//const axiosPrivate = useAxiosPrivate();",
		  "const response = await axiosPrivate.post(\"/user/sendVerification\")"
		],
		"description": "DONT USE IN ACTION"
	  }, 

	  "axios private in comp": {
		"prefix": "$dispatch-AP-for-act",
		"body": [
		  "//const axiosPrivate = useAxiosPrivate();",
		  "dispatch(myAction(axiosPrivate, { text, path:myPath }, formData,  signal, setX));"
		],
		"description": "axios private in comp"
	  },

	  "axios private in act": {
		"prefix": "$dispatch-AP-in-act",
		"body": [
		  "//const xAction = (formData, axiosPrivate, signal, setCoverPicture, token) => async (dispatch) => {",
		  "const res = await axiosPrivate.post(\"/post/uploadImages\", formData, {signal}); // res",
		  "await axiosPrivate.post(\"/user/activate\", JSON.stringify({ token }), {signal: controller.signal}); // signal + controller",
		  "const res = await axiosPrivate.post('/post/uploadImages', formData, {headers: {'Content-Type': 'multipart/form-data'}}); //UPLOAD FILE",
		  "await axiosPrivate.post(\"/user/updateCover\", { url: res?.data?.images[0]?.url }, { signal }); //after upload => update DB with uploaded image",
		  "const res = await axiosPrivate.post('/post/createPost', {images: res?.data?.images || [], ...values}); //after upload => send images and data to backend "
		],
		"description": "axios private in act"
	  },

	  "context as global state": {
		"prefix": "$context",
		"body": [
		  "//index.js => after <BrowserRouter> => wrap with <AuthProvider> ",
		  "//const { auth, setAuth } = useAuth(); => setAuth({ username, roles, accessToken });",
		  "",
		  "import { createContext, useState } from \"react\";",
		  "",
		  "const AuthContext = createContext({});",
		  "",
		  "export const AuthProvider = ({ children }) => {",
		  "  const [auth, setAuth] = useState({});",
		  "",
		  "  return (",
		  "    <AuthContext.Provider value={{ auth, setAuth }}>",
		  "      {children}",
		  "    </AuthContext.Provider>",
		  "  );",
		  "};",
		  "",
		  "export default AuthContext;",
		  ""
		],
		"description": "context as global state"
	  },

	  "prev + change new": {
		"prefix": "$setX-prev",
		"body": [
		  "setX((prev) => { return [{ id: X, url: img }, ...prev]}); //list of objects",
		  "setX((prev) => { return { ...prev, roles: response.data.roles }}); //object",
		],
		"description": "prev + change new"
	  },

	  "start and end component": {
		"prefix": "$useLocation-start-end",
		"body": [
		  "const navigate = useNavigate();",
		  "const location = useLocation();",
		  "const handleClick = (e) => {",
		  "  e.preventDefault();",
		  "  navigate(\"/login\", { state: { from: location.pathname } });",
		  "};",
		  "// {user.roles ? <button onClick={handleClick}>log in</button> : <p>download here!</p>}"
		],
		"description": "start and end component"
	  },

	  "middle like login": {
		"prefix": "$useLocation-middle",
		"body": [
		  "const navigate = useNavigate();",
		  "const location = useLocation();",
		  "const from = location.state?.from || \"/\"; // submit => navigate(from, { replace: true })"
		],
		"description": "middle like login"
	  },

	  "RequireAuth": {
		"prefix": "$requireAuth",
		"body": [
		  "import { useSelector } from \"react-redux\";",
		  "import { Navigate, Outlet, useLocation } from \"react-router-dom\";",
		  "const RequireAuth = ({ allowedRoles, children }) => {",
		  "",
		  "  const user = useSelector((state) => state.user);",
		  "  const role = user?.roles?.find((role) => allowedRoles.includes(role));",
		  "",
		  "  return (",
		  "    <>",
		  "      {role && <Outlet />}",
		  "      {!role && <Navigate to=\"/unauthorized\" />}",
		  "    </>",
		  "  );",
		  "};",
		  "",
		  "export default RequireAuth;",
		  ""
		],
		"description": "RequireAuth"
	  },

	  "PersisLogin": {
		"prefix": "$PersisLogin",
		"body": [
		  "import { Outlet, Navigate } from \"react-router-dom\";",
		  "import { useDispatch, useSelector } from \"react-redux\";",
		  "import newAccessTokenAction from \"../redux/actions/newAccessToken\";",
		  "import { useEffect } from \"react\";",
		  "",
		  "const PersisLogin = () => {",
		  "  const user = useSelector((state) => state.user);",
		  "  const newAccessToken = useSelector((state) => state.newAccessToken);",
		  "  const dispatch = useDispatch();",
		  "",
		  "  useEffect(() => {",
		  "    console.log(user);",
		  "    if(!user?.accessToken && !newAccessToken.errorMessage) dispatch(newAccessTokenAction())",
		  "  }, []);",
		  "  ",
		  "  return(",
		  "",
		  "    user?.isLoading || newAccessToken?.isLoading ? <div>Loading...</div> : ",
		  "    !user?.accessToken && newAccessToken.errorMessage ? <Navigate to=\"/login\" /> :",
		  "    user?.accessToken && <Outlet />",
		  "  )",
		  "};",
		  "export default PersisLogin;",
		  "",
		  ""
		],
		"description": "PersisLogin"
	  },

	  "navbar can be here": {
		"prefix": "$layout",
		"body": [
		  "import { Outlet } from \"react-router-dom\"",
		  "",
		  "const Layout =()=>{",
		  "    return <Outlet/>",
		  "}",
		  "",
		  "export default Layout"
		],
		"description": "navbar can be here"
	  },

	  "give to parent": {
		"prefix": "$mouse-hover",
		"body": [
		  "onMouseLeave={() => setShow(false)} onMouseMove={() => setShow(true)} //give to parent"
		],
		"description": "give to parent"
	  },

	  "scroll-x": {
		"prefix": "$scrollbar-x",
		"body": [
		  "<div className=\"flex gap-2 overflow-x-scroll scrollbar-thin w-[94%] pb-6 scrollbar-thumb-rounded-md scrollbar-thumb-gray-300\">",
		  "  {images.map((img, index) => {",
		  "    return (",
		  "      <div key={index} className=\"relative w-64 h-64 flex-shrink-0\">  ",
		  "        <img className=\"w-full h-full object-cover relative\" src={img.url} alt=\"\" />",
		  "        <button className=\"absolute top-1 right-1\">",
		  "          حذف",
		  "        </button>",
		  "      </div>",
		  "    );",
		  "  })}",
		  "</div>"
		],
		"description": "scroll-x"
	  },

	  "text on the image": {
		"prefix": "$img+text",
		"body": [
		  "<div className=\"relative w-[300px] h-[300px]\">",
		  "  <img src={bg} className=\"w-full h-full object-cover\" alt=\"\" />",
		  "  <div className=\"absolute top-0 left-0 w-full h-full flex items-center justify-center overflow-hidden p-5\">",
		  "    <p className=\"text-center overflow-y-scroll scrollbar-thin scrollbar-thumb-rounded-md scrollbar-thumb-gray-300 break-words w-full h-full\">",
		  "      {text}",
		  "    </p>",
		  "  </div>",
		  "</div>"
		],
		"description": "text on the image"
	  },

	  "get": {
		"prefix": "$use-get",
		"body": [
		  "import { useEffect } from \"react\";",
		  "import { useDispatch } from \"react-redux\";",
		  "import { GET_POSTS_FAIL, GET_POSTS_SUCCESS, GET_POSTS_REQUEST} from \"../redux/actions/types\";",
		  "import useAxiosPrivate from \"./useAxiosPrivate\";",
		  "",
		  "const useGet${1|AllPosts,MyPosts|} = (pageNum = 1, pageLimit = 3, ${2:username_FOR_MY}$4) => {",
		  "  const dispatch = useDispatch();",
		  "  const axiosPrivate = useAxiosPrivate();",
		  "",
		  "  useEffect(() => {",
		  "    dispatch({ type: GET_POSTS_REQUEST });",
		  "    const controller = new AbortController(); // handle the cancellation of the API request",
		  "    const { signal } = controller;",
		  "    axiosPrivate",
		  "      .get(`/post/posts?pageNum=${ pageNum }&pageLimit=${ pageLimit }`, { signal }, {${2:username_FOR_MY}}$3)",
		  "      .then(({ data }) => {",
		  "        dispatch({",
		  "          type: GET_POSTS_SUCCESS,",
		  "          payload: {",
		  "            posts: data?.docs, //docs from PG-AG",
		  "            hasNextPage: data?.hasNextPage, //from PG-AG",
		  "            totalPages: data?.totalPages, //from PG-AG",
		  "            nextPage: data?.nextPage, //from PG-AG",
		  "          },",
		  "        });",
		  "      })",
		  "      .catch((error) => {",
		  "        if (signal.aborted) return;",
		  "        dispatch({",
		  "          type: GET_POSTS_FAIL,",
		  "          payload: { errorMessage: error.response?.data?.message },",
		  "        });",
		  "      });",
		  "",
		  "    // clean up func => cancelling ongoing requests => 1.when the component unmounts OR 2.when the dependencies change",
		  "    return () => {",
		  "      controller.abort();",
		  "    };",
		  "  }, [pageNum, pageLimit]);",
		  "};",
		  "",
		  "export default useGet${1|AllPosts,MyPosts|};",
		  ""
		],
		"description": "get all"
	  },

	  "lazy load parent + useGet": {
		"prefix": "$lazy-load-parent",
		"body": [
		  "// useGet() + state management",
		  "const [pageNum, setPageNum] = useState(1);",
		  "useGet(pageNum);",
		  "const ${1:posts} = useSelector((state) => state?.${1:posts});",
		  "const dispatch = useDispatch();",
		  "",
		  "// Lazy loading => IntersectionObserver for monitoring last element to re-load new ${1:posts}",
		  "const intObserver = useRef(null);",
		  "const lastElementRef = useCallback(",
		  "  (lastPost) => {",
		  "    if (${1:posts}?.isLoading) return;",
		  "    if (intObserver.current) intObserver.current.disconnect(); // disconnect prev IntersectionObserver",
		  "    // add new IntersectionObserver",
		  "    intObserver.current = new IntersectionObserver((entries) => { ",
		  "      // element enter to the viewport && hasNextPage",
		  "      if (entries[0].isIntersecting && ${1:posts}?.hasNextPage) {",
		  "        setPageNum(${1:posts}?.nextPage);",
		  "      }",
		  "    });",
		  "",
		  "    if (lastPost) intObserver.current.observe(lastPost); // if last element exist => connect IntersectionObserver for monitor it",
		  "  },",
		  "  [${1:posts}?.isLoading, ${1:posts}?.hasNextPage, ${1:posts}?.nextPage]",
		  ");",
		  "",
		  "",
		  "// ****jsx****",
		  "{${1:posts}?.${1:posts}.map((${2:post}, i) => {",
		  "  // last element's => give them ref",
		  "  if (${1:posts}?.${1:posts}?.length === i + 1) {",
		  "    return <${3:CHILD_COMP} key={${2:post}?._id} ref={lastElementRef} ${2:post}={${2:post}} />;",
		  "  } else {",
		  "    return <${3:CHILD_COMP} key={${2:post}?._id} ${2:post}={${2:post}} />;",
		  "  }",
		  "})}",
		  ""
		],
		"description": "lazy load parent"
	  },

	  "lazy load child": {
		"prefix": "$lazy-load-child",
		"body": [
		  "import { LazyLoadImage } from \"react-lazy-load-image-component\";",
		  "import \"react-lazy-load-image-component/src/effects/blur.css\";",
		  "",
		  "const ${1:Post} = React.forwardRef(({ ${2:post} }, ref) => {",
		  "  return (",
		  "    <>",
		  "      <div ref={ref} className=\"\">",
		  "        <img",
		  "          src={${2:post}?.user[0]?.picture || ${2:post}?.user?.picture}",
		  "          alt=\"\"",
		  "          className=\"\"",
		  "        />",
		  "",
		  "        {${2:post}?.images.map((img, index) => (",
		  "          <div",
		  "            key={index}",
		  "            className=\"\"",
		  "          >",
		  "            {/* react-lazy-load perhaps need style in index.css */}",
		  "            <div className=\"w-full h-full lazyImage\">",
		  "              <LazyLoadImage src={img?.url} effect=\"blur\" alt=\"\" />",
		  "            </div>",
		  "          </div>",
		  "        ))}",
		  "      </div>",
		  "    </>",
		  "  );",
		  "});",
		  "",
		  "export default ${1:Post};"
		],
		"description": "lazy load child"
	  },

	  "useGet()": {
		"prefix": "$useGet",
		"body": [
		  "useGet(pageNum);"
		],
		"description": "useGet()"
	  },

	  "moment": {
		"prefix": "$moment",
		"body": [
		  "// import Moment from \"react-moment\";",
		  "<Moment className=\"text-sm\" fromNow interval={30}>",
		  "    {post?.createdAt}",
		  "</Moment>"
		],
		"description": "moment"
	  },

	  "clean-up-unmount": {
		"prefix": "$clean-up-unmount",
		"body": [
		  " // clean up when comp unmount",
		  "  useEffect(() => {",
		  "    return () => dispatch({ type: GET_POSTS_CLEAN });",
		  "  }, [dispatch]);"
		],
		"description": "clean-up-unmount"
	  },

	  "abortController": {
		"prefix": "$abortController",
		"body": [
		  "useEffect(() => {",
		  " const controller = new AbortController(); // handle the cancellation of the API request",
		  " const { signal } = controller;",
		  " axiosPrivate.get(..., { signal }) OOORRR dispatch(...)$1",
		  "   ",
		  " // in catch (try-catch or .then().catch()) => before error handling",
		  " if (signal.aborted) return;",
		  "     ",
		  "",
		  " // clean up func",
		  " return () => {",
		  "   controller.abort();",
		  "};",
		  "}, []);"
		],
		"description": "abortController"
	  },

	  "crop helper": {
		"prefix": "$crop-helper",
		"body": [
		  "export const createImage = (url) => {",
		  "  return new Promise((resolve, reject) => {",
		  "    const image = new Image();",
		  "    image.addEventListener(\"load\", () => resolve(image));",
		  "    image.addEventListener(\"error\", (error) => reject(error));",
		  "    image.src = url;",
		  "  });",
		  "};",
		  "",
		  "// use this in components",
		  "export default async function getCroppedImg(imageSrc, pixelCrop) {",
		  "  try {",
		  "    const image = await createImage(imageSrc);",
		  "    const canvas = document.createElement(\"canvas\");",
		  "    const ctx = canvas.getContext(\"2d\");",
		  "",
		  "    if (!ctx) return null;",
		  "",
		  "    canvas.width = image.width;",
		  "    canvas.height = image.height;",
		  "",
		  "    ctx.drawImage(image, 0, 0);",
		  "",
		  "    const data = ctx.getImageData(",
		  "      pixelCrop.x,",
		  "      pixelCrop.y,",
		  "      pixelCrop.width,",
		  "      pixelCrop.height",
		  "    );",
		  "",
		  "    canvas.width = pixelCrop.width;",
		  "    canvas.height = pixelCrop.height;",
		  "",
		  "    ctx.putImageData(data, 0, 0);",
		  "",
		  "    return new Promise((resolve, _) => {",
		  "      canvas.toBlob((file) => {",
		  "        resolve(URL.createObjectURL(file));",
		  "      }, \"image/jpeg\");",
		  "    });",
		  "  } catch (error) {}",
		  "}"
		],
		"description": "crop helper"
	  },


	  "input files": {
		"prefix": "$input-files",
		"body": [
		  "    // const handleSelectedFiles = (e) => {",
		  "    //   const file = e.target.files[0]; //single",
		  "    //   let files = Array.from(e.target.files); //multi",
		  "    //   files.forEach((img) => { //multi",
		  "    //     const type = file.type.split(\"/\")[1]; //single",
		  "    //     let type = img.type.split(\"/\")[1]; //multi",
		  "    //     if (![\"jpeg\", \"png\", \"webp\", \"gif\"].includes(type)) {",
		  "    //       files = files.filter((item) => item.name !== img.name); //multi",
		  "    //       setErrorMsg(`${img?.name || file?.name} فرمت صحیح وارد کنید`);",
		  "    //       setCoverPicture(\"\"); //single",
		  "    //       return;",
		  "    //     } else if (img.size > 1024 * 1024 * 5) {",
		  "    //       files = files.filter((item) => item.name !== img.name); //multi",
		  "    //       setErrorMsg(`${img.name} حجم عکس‌ها باید کمتر از 5 مگابایت باشد`);",
		  "    //       setCoverPicture(\"\"); //single",
		  "    //       return;",
		  "    //     } else {",
		  "    //       const reader = new FileReader();",
		  "    //       reader.readAsDataURL(file || img);",
		  "    //       reader.onload = (e) => {",
		  "    //         setImages((images) => [...images, e.target.result]); //multi",
		  "    //         setCoverPicture(e.target.result); //single",
		  "    //       };",
		  "    //     }",
		  "    //   });",
		  "    // };",
		  "  ",
		  "  <div onClick={() => inputImgRef.current?.click()} className=\"bg-gray-300 text-gray-600 p-5 rounded-md mt-10 w-md sm:max-w-sm cursor-pointer\">",
		  "     upload your files",
		  "  </div>",
		  "  <input",
		  "      type=\"file\"",
		  "      accept=\"image/jpeg,image/png,image/webp,image/gif\"",
		  "      ref={inputImgRef}",
		  "      multiple",
		  "      hidden // hide the input but ref to UPPER div",
		  "      onChange={handleSelectedFiles} //*multi*",
		  "      //onInput={handleSelectedFiles} //*single* - fix same file select",
		  "      //onClick={(e) => (e.target.value = null)} //*single* - fix same file select",
		  "  />"
		],
		"description": "input files"
	  },

	  "crop funcs": {
		"prefix": "$crop-funcs",
		"body": [
		  "//const inputImgRef = useRef(null);",
		  "//const coverRef = useRef(null);",
		  "//const [coverPicture, setCoverPicture] = useState(\"\"); //just use for crop proccess =then=> reset",
		  "//const [zoom, setZoom] = useState(1);",
		  "//const [crop, setCrop] = useState({ x: 0, y: 0 });",
		  "//const [croppedAreaPixels, setCroppedAreaPixels] = useState(null);",
		  "//const isMyProfile = profileInfo?.username === user?.username;",
		  "",
		  "const onCropComplete = useCallback((_, croppedAreaPixels) => {",
		  "  setCroppedAreaPixels(croppedAreaPixels);",
		  "}, []);",
		  "",
		  "const cancelCoverChangeHandler = () => {",
		  "  setCoverPicture(\"\");",
		  "};",
		  "",
		  "const updateCoverPictureHandler = async () => {",
		  "  try {",
		  "    const controller = new AbortController();",
		  "    const { signal } = controller;",
		  "    const img = await getCroppedImg(coverPicture, croppedAreaPixels);",
		  "    const blob = await fetch(img).then((b) => b.blob());",
		  "    const path = `${user?.userInfo?.username}/cover_pictures`;",
		  "    let formData = new FormData();",
		  "    formData.append(\"file\", blob);",
		  "    formData.append(\"path\", path);",
		  "    dispatch( changeCoverAction(formData, axiosPrivate, signal, setCoverPicture) );",
		  "  } catch (error) {",
		  "    setErrorMsg(\"Error In crop and update cover\");",
		  "  }",
		  "};",
		  ""
		],
		"description": "crop funcs"
	  },

	  "ref in parent element": {
		"prefix": "$cropper-ui",
		"body": [
		  "{/*parent element*/}",
		  "<div ref={coverRef} className=\"h-96 w-full relative m-auto\">",
		  "  <!-- ... -->",
		  "  {(coverPicture || cover?.isLoading) && (",
		  "     <Cropper",
		  "        image={coverPicture}",
		  "        zoom={zoom}",
		  "        crop={crop}",
		  "        aspect={coverRef.current?.getBoundingClientRect().width ? coverRef.current?.getBoundingClientRect().width / 384 : 1}",
		  "        onZoomChange={setZoom}",
		  "        onCropChange={setCrop}",
		  "        onCropComplete={onCropComplete}",
		  "        objectFit=\"horizontal-cover\"",
		  "      />",
		  "      <!-- ... -->",
		  "  )}",
		  "  <!-- ... -->",
		  "</div>",
		  ""
		],
		"description": "ref in parent element"
	  },

	  "then catch": {
		"prefix": "$then-catch",
		"body": [
		  ".then(({ data }) => {",
		  "  $1",
		  "})",
		  ".catch((error) => {",
		  "  //if (signal.aborted) return;",
		  "  ",
		  "});"
		],
		"description": "then catch"
	  },

	  "input range": {
		"prefix": "$input-range",
		"body": [
		  "//state + ref",
		  "const sliderRef = useRef(null);",
		  "const [zoom, setZoom] = useState(1);",
		  "",
		  "const zoomIn = () => {",
		  "  sliderRef.current.stepUp();",
		  "  setZoom(sliderRef.current.value);",
		  "};",
		  "const zoomOut = () => {",
		  "  sliderRef.current.stepDown();",
		  "  setZoom(sliderRef.current.value);",
		  "};",
		  "",
		  "//ui",
		  "<input",
		  "  type=\"range\"",
		  "  min={1}",
		  "  max={10}",
		  "  step={0.1}",
		  "  value={zoom}",
		  "  ref={sliderRef}",
		  "  onChange={(e) => setZoom(e.target.value)}",
		  "  className=\"w-full h-2 bg-gray-200 rounded-lg cursor-pointer appearance-none\"",
		  "/>;",
		  "<button onClick={zoomOut}></button>",
		  "<button onClick={zoomIn}></button>"
		],
		"description": "input range"
	  },

	  "ui state context": {
		"prefix": "$useStateContext",
		"body": [
		  "import React, { createContext, useContext, useState } from \"react\";",
		  "",
		  "const StateContext = createContext();",
		  "",
		  "const initialState = {",
		  "  chat: false,",
		  "  cart: false,",
		  "  userProfile: false,",
		  "  notification: false,",
		  "};",
		  "",
		  "export const ContextProvider = ({ children }) => {",
		  "  const [activeMenu, setActiveMenu] = useState(true);",
		  "  const [isClicked, setIsCliked] = useState(initialState);",
		  "  const [currentColor, setCurrentColor] = useState(\"#03C9D7\");",
		  "  const [currentMode, setCurrentMode] = useState(\"Dark\");",
		  "  const [themeSettings, setThemeSettings] = useState(false);",
		  "",
		  "  const handleClick = (clicked) => {",
		  "    setIsCliked({ ...initialState, [clicked]: !isClicked[clicked] });",
		  "  };",
		  "",
		  "  const setMode = (e) => {",
		  "    setCurrentMode(e.target.value);",
		  "    localStorage.setItem(\"themeMode\", e.target.value);",
		  "    setThemeSettings(false);",
		  "  };",
		  "",
		  "  const setColor = (color) => {",
		  "    setCurrentColor(color);",
		  "    localStorage.setItem(\"colorMode\", color);",
		  "    setThemeSettings(false);",
		  "  };",
		  "",
		  "  const [screenSize, setScreenSize] = useState(undefined);",
		  "",
		  "  return (",
		  "    <StateContext.Provider",
		  "      value={{",
		  "        activeMenu,",
		  "        setActiveMenu,",
		  "        isClicked,",
		  "        setIsCliked,",
		  "        handleClick,",
		  "        screenSize,",
		  "        setScreenSize,",
		  "        currentColor,",
		  "        currentMode,",
		  "        setColor,",
		  "        setMode,",
		  "        themeSettings,",
		  "        setThemeSettings,",
		  "      }}",
		  "    >",
		  "      {children}",
		  "    </StateContext.Provider>",
		  "  );",
		  "};",
		  "",
		  "export const useStateContext = () => useContext(StateContext);"
		],
		"description": "ui state context"
	  },

	  "use context": {
		"prefix": "$use-context",
		"body": [
		  "const {",
		  "    activeMenu,",
		  "    themeSettings,",
		  "    setThemeSettings,",
		  "    currentColor,",
		  "    currentMode,",
		  "    isClicked,",
		  "} = use${1:State}Context();"
		],
		"description": "use context"
	  },

	  "check is dark mode": {
		"prefix": "$is-dark-mode",
		"body": [
		  "<div className={currentMode === \"Dark\" ? \"dark\" : \"\"}>",
		  "",
		  "</div>"
		],
		"description": "check is dark mode"
	  }

	  

	  


	}
```

</details>
