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


<details><summary>backend</summary>
  
```js
{
	// Place your global snippets here. Each snippet is defined under a snippet name and has a scope, prefix, body and 
	// description. Add comma separated ids of the languages where the snippet is applicable in the scope field. If scope 
	// is left empty or omitted, the snippet gets applied to all languages. The prefix is what is 
	// used to trigger the snippet and the body will be expanded and inserted. Possible variables are: 
	// $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. 
	// Placeholders with the same ids are connected.
	// Example:
	"server": {
		"prefix": "$server",
		"body": [
		  "import express from 'express';",
		  "import mongoose from 'mongoose';",
		  "import \"dotenv/config\";",
		  "",
		  "import connectDB from \"./config/db.js\";",
		  "import credentials from \"./middlewares/credentials.js\";",
		  "import corsOptions from \"./config/corsOptions.js\";",
		  "",
		  "import cookieParser from \"cookie-parser\";",
		  "",
		  "import userRoutes from \"./routes/api/userRoutes.js\";",
		  "import postRoutes from \"./routes/api/postRoutes.js\";",
		  "import verifyJWT from \"./middlewares/verifyJWT.js\";",
		  "",
		  "import cors from \"cors\";",
		  "import fileUpload from \"express-fileupload\";",
		  "",
		  "const PORT = process.env.PORT || 8000",
		  "",
		  "const app = express();",
		  "",
		  "connectDB()",
		  "app.use(credentials) //enable HTTP cookies over CORS",
		  "app.use(cors(corsOptions)); //allow request: 1.no origins 2.allowedOrigins",
		  "",
		  "// parse req to JSON",
		  "app.use(express.json())",
		  "app.use(cookieParser())",
		  "",
		  "//file upload",
		  "app.use(fileUpload({ useTempFiles: true }));",
		  "",
		  "//routes",
		  "app.use(\"/user\", userRoutes); // public",
		  "app.use(\"/post\", verifyJWT, postRoutes); //private",
		  "",
		  "// not found routes ",
		  "app.all(\"*\", (req, res) => {",
		  "    res.status(404);",
		  "    if (req.accepts(\"json\")) {",
		  "      res.json({ error: \"404 Not Found\" });",
		  "    } else {",
		  "      res.type(\"text\").send(\"404 Not Found\");",
		  "    }",
		  "  });",
		  "",
		  "//error ",
		  "app.use((err, _, res) => {",
		  "    res.status(500).send(err.message);",
		  "});",
		  "",
		  "// when connect to DB run this!",
		  "mongoose.connection.once(\"open\", () => {",
		  "    console.log(\"Connected to mongoDB\");",
		  "    app.listen(PORT, console.log(`Server running on port ${ PORT }`));",
		  "});",
		  "",
		  "",
		  ""
		],
		"description": "server"
	  },

	  "express as app": {
		"prefix": "$appex",
		"body": [
		  "const app = express();"
		],
		"description": "express as app"
	  },

	  "cors + credentials + corsOptions": {
		"prefix": "$cors",
		"body": [
		  "app.use(credentials) //enable HTTP cookies over CORS",
		  "app.use(cors(corsOptions)); //allow request: 1.no origins 2.allowedOrigins"
		],
		"description": "cors + credentials + corsOptions"
	  },

	  "config connectDB": {
		"prefix": "$connectDB",
		"body": [
		  "connectDB();"
		],
		"description": "config connectDB"
	  },

	  "// parse req to JSON": {
		"prefix": "$jcookie",
		"body": [
		  "// parse req to JSON",
		  "app.use(express.json())",
		  "app.use(cookieParser())"
		],
		"description": "parse req to JSON"
	  },

	  "file upload": {
		"prefix": "$upload",
		"body": [
		  "//file upload",
		  "//import fileUpload from 'express-fileupload';",
		  "app.use(fileUpload({ useTempFiles: true }));"
		],
		"description": "file upload"
	  },

	  "public route": {
		"prefix": "$route",
		"body": [
		  "app.use(\"/user\", userRoutes); // public route"
		],
		"description": "public route"
	  },

	  "private route using verifyJWT": {
		"prefix": "$proute",
		"body": [
		  "app.use(\"/post\", verifyJWT, postRoutes); //private route"
		],
		"description": "private route using verifyJWT"
	  },

	  "not found routes ": {
		"prefix": "$notFoundRoutes",
		"body": [
		  "// not found routes ",
		  "app.all(\"*\", (req, res) => {",
		  "    res.status(404);",
		  "    if (req.accepts(\"json\")) {",
		  "      res.json({ error: \"404 Not Found\" });",
		  "    } else {",
		  "      res.type(\"text\").send(\"404 Not Found\");",
		  "    }",
		  "  });"
		],
		"description": "not found routes"
	  },

	  "error": {
		"prefix": "$err",
		"body": [
		  "//error ",
		  "app.use((err, _, res) => {",
		  "    res.status(500).send(err.message);",
		  "});"
		],
		"description": "error"
	  },

	  "mongoose setup": {
		"prefix": "$mongoose",
		"body": [
		  "// when connect to DB run this!",
		  "mongoose.connection.once(\"open\", () => {",
		  "    console.log(\"Connected to mongoDB\");",
		  "    app.listen(PORT, console.log(`Server running on port ${PORT}`));",
		  "});"
		],
		"description": "mongoose setup"
	  },

	  "db.js": {
		"prefix": "$db",
		"body": [
		  "import mongoose from \"mongoose\";",
		  "",
		  "const connectDB = async () => {",
		  "  try {",
		  "    await mongoose.connect(process.env.DATABASE_URI, { useNewUrlParser: true }); //useNewUrlParser mongoose new feature available!",
		  "  } catch (error) {",
		  "    console.log(error);",
		  "  }",
		  "};",
		  "",
		  "export default connectDB;",
		  ""
		],
		"description": "db.js"
	  },

	  "authValidator.js -> email + pass": {
		"prefix": "$authValidator",
		"body": [
		  "import { body } from \"express-validator\";",
		  "",
		  "const authValidator = () => {",
		  "  return [",
		  "    body(\"email\")",
		  "      .not()",
		  "      .isEmpty()",
		  "      .isEmail()",
		  "      .withMessage(\"Invalid email address\"),",
		  "    body(\"password\").not().isEmpty().withMessage(\"Invalid credentials\"),",
		  "  ];",
		  "};",
		  "",
		  "export default authValidator;",
		  ""
		],
		"description": "authValidator.js -> email + pass"
	  },

	  "registerValidator.js -> data's + custom('email already in use')": {
		"prefix": "$registerValidator",
		"body": [
		  "import { body } from \"express-validator\";",
		  "import User from \"../models/userModel.js\";",
		  "",
		  "const registerValidator = () => {",
		  "  return [",
		  "    body(\"first_name\")",
		  "      .isLength({ min: 4 })",
		  "      .withMessage(\"First name must be at least 4 chars long\"),",
		  "    body(\"last_name\")",
		  "      .isLength({ min: 4 })",
		  "      .withMessage(\"Last name must be at least 4 chars long\"),",
		  "    body(\"email\")",
		  "      .isEmail()",
		  "      .withMessage(\"Invalid email address\")",
		  "      .custom(async (value) => {",
		  "        return User.findOne({ email: value }).then((user) => {",
		  "          if (user) {",
		  "            return Promise.reject(\"Email already in use\");",
		  "          }",
		  "        });",
		  "      }),",
		  "    body(\"password\")",
		  "      .isLength({ min: 8 })",
		  "      .withMessage(\"Password must be at least 8 chars length\")",
		  "      .matches(/(?=.*[0-9])(?=.*[!@#$%^&*])(?=.*[a-zA-Z])/)",
		  "      .withMessage(",
		  "        \"Password must contain string, at least one special and one numeric character\"",
		  "      ),",
		  "    body(\"bYear\")",
		  "      .not()",
		  "      .isEmpty()",
		  "      .withMessage(\"Bearth year can not be empty\")",
		  "      .isInt({ min: 1950 })",
		  "      .withMessage(\"Bearth year must be at least 1950\"),",
		  "    body(\"bMonth\")",
		  "      .not()",
		  "      .isEmpty()",
		  "      .withMessage(\"Bearth month can not be empty\")",
		  "      .isInt({ min: 1, max: 12 })",
		  "      .withMessage(\"Bearth month must be between 1 and 12\"),",
		  "    body(\"bDay\")",
		  "      .not()",
		  "      .isEmpty()",
		  "      .withMessage(\"Bearth day can not be empty\")",
		  "      .isInt({ min: 1, max: 31 })",
		  "      .withMessage(\"Bearth day muse be between 1 and 31\"),",
		  "    body(\"gender\")",
		  "      .isIn([\"male\", \"female\", \"custom\"])",
		  "      .withMessage(\"gender can be male, female or custom\"),",
		  "  ];",
		  "};",
		  "",
		  "export default registerValidator;",
		  ""
		],
		"description": "registerValidator.js -> data's + custom('email already in use')"
	  },

	  "allowedOrigins.js": {
		"prefix": "$allowedOrigins",
		"body": [
		  "const allowedOrigins = [",
		  "  \"http://localhost:3000\",",
		  "  \"http://localhost:3001\",",
		  "  \"http://localhost:3500\",",
		  "  \"https://www.mysite.com\",",
		  "];",
		  "",
		  "export default allowedOrigins;",
		  ""
		],
		"description": "allowedOrigins.js"
	  },

	  "corsOptions.js": {
		"prefix": "$corsOptions",
		"body": [
		  "// allow request with:",
		  "// 1. no origins (like mobile apps or curl requests)",
		  "// 2. allowedOrigins ",
		  "",
		  "import allowedOrigins from \"./allowedOrigins.js\";",
		  "",
		  "const corsOptions = {",
		  "  origin: (origin, callback) => {",
		  "    if (allowedOrigins.indexOf(origin) !== -1 || !origin) {",
		  "      callback(null, true);",
		  "    } else {",
		  "      callback(new Error(\"Not allowed by CORS\"));",
		  "    }",
		  "  },",
		  "  optionsSuccessStatus: 200,",
		  "};",
		  "",
		  "export default corsOptions;",
		  ""
		],
		"description": "corsOptions.js"
	  },

	  "user Data + search + ref + refreshToken": {
		"prefix": "$userModel",
		"body": [
		  "import mongoose from \"mongoose\";",
		  "// import UserModel from \"../models/userModel.js\";",
		  "// import bcrypt from \"bcrypt\";",
		  "// import randomstring from \"randomstring\";",
		  "",
		  "const { ObjectId } = mongoose.Schema;",
		  "",
		  "const userSchema = mongoose.Schema(",
		  "  {",
		  "    first_name: {",
		  "      type: String,",
		  "      required: [true, \"first name is required\"],",
		  "      trim: true, // remove left & right space from string",
		  "      text: true,",
		  "    },",
		  "",
		  "    username: {",
		  "      type: String,",
		  "      required: [true, \"username is required\"],",
		  "      trim: true,",
		  "      text: true,",
		  "      unique: true,",
		  "    },",
		  "",
		  "    email: {",
		  "      type: String,",
		  "      required: [true, \"Email is required\"],",
		  "      trim: true,",
		  "    },",
		  "",
		  "    password: {",
		  "      type: String,",
		  "      required: [true, \"Password is required\"],",
		  "    },",
		  "",
		  "  roles: {",
    	  "    User: { type: Number, default: 1000 },",
     	  "    Editor: Number,",
    	  "    Admin: Number,",
    	  "  },"
		  "",
		  "    picture: {",
		  "      type: String,",
		  "      trim: true,",
		  "      default:",
		  "        \"https://library.kissclipart.com/20181001/wbw/kissclipart-gsmnet-ro-clipart-computer-icons-user-avatar-4898c5072537d6e2.png\",",
		  "    },",
		  "",
		  "    bYear: {",
		  "      type: Number,",
		  "      required: true,",
		  "      trim: true,",
		  "    },",
		  "",
		  "    verified: {",
		  "      type: Boolean,",
		  "      default: false,",
		  "    },",
		  "",
		  "    followers: {",
		  "      type: Array,",
		  "      default: [],",
		  "    },",
		  "",
		  "    requests: {",
		  "      type: Array,",
		  "      default: [],",
		  "    },",
		  "",
		  "    search: [",
		  "      {",
		  "        user: {",
		  "          type: ObjectId,",
		  "          ref: \"User\",",
		  "        },",
		  "      },",
		  "    ],",
		  "",
		  "    details: {",
		  "      bio: {",
		  "        type: String,",
		  "      },",
		  "      relationship: {",
		  "        type: String,",
		  "        enum: [\"Single\", \"In a relationship\", \"Married\", \"Divorced\"],",
		  "        default: \"Single\"",
		  "      },",
		  "    },",
		  "",
		  "    savedPosts: [",
		  "      {",
		  "        post: {",
		  "          type: ObjectId,",
		  "          ref: \"post\",",
		  "        },",
		  "        savedAt: {",
		  "          type: Date,",
		  "          default: new Date(),",
		  "        },",
		  "      },",
		  "    ],",
		  "",
		  "    refreshToken: [String],",
		  "  },",
		  "  { timestamps: true }",
		  ");",
		  "",
		  "// EXTRA HERE !!!",
		  "",
		  "export default mongoose.model(\"User\", userSchema);",
		  ""
		],
		"description": "user Data + search + ref + refreshToken"
	  },

	  "pre.save hashing password": {
		"prefix": "$userModelHashPass",
		"body": [
		  "userSchema.pre(\"save\", async function (next) {",
		  "  let user = this;",
		  "  if (!user.isModified(\"password\")) return next(); // if password is not changed ---> don't hash",
		  "",
		  "  try {",
		  "    const salt = await bcrypt.genSalt(12);",
		  "    user.password = await bcrypt.hash(user.password, salt);",
		  "",
		  "    return next();",
		  "  } catch (err) {",
		  "    return next(err);",
		  "  }",
		  "});"
		],
		"description": "pre.save -> hashing password"
	  },

	  "methode(password) -> compare Password": {
		"prefix": "$userModelComparePassword",
		"body": [
		  "userSchema.methods.comparePassword = async function (password) {",
		  "  return bcrypt.compare(password, this.password);",
		  "};"
		],
		"description": "*** don't use *** methode(password) -> compare Password"
	  },

	  "methode() -> generate Username -> this.username  ": {
		"prefix": "$userModelGenerateUsername ",
		"body": [
		  "userSchema.methods.generateUsername = async function () {",
		  "  let user = null;",
		  "  let username = this.username;",
		  "  do {",
		  "    user = await UserModel.findOne({ username }); // import UserModel in UserModel for use it !!! ",
		  "    if (user) username += randomstring.generate(4);",
		  "  } while (user);",
		  "",
		  "  return username;",
		  "};"
		],
		"description": "methode() -> generate Username -> this.username  "
	  },

	  "credentials.js -> enable HTTP cookies over CORS": {
		"prefix": "$credentials",
		"body": [
		  "// enable HTTP cookies over CORS",
		  "import allowedOrigins from \"../config/allowedOrigins.js\";",
		  "",
		  "const credentials = (req, res, next) => {",
		  "  const origin = req.headers.origin;",
		  "  if (allowedOrigins.includes(origin)) {",
		  "    res.header(\"Access-Control-Allow-Credentials\", true);",
		  "  }",
		  "  next();",
		  "};",
		  "",
		  "export default credentials;",
		  ""
		],
		"description": "credentials.js -> enable HTTP cookies over CORS"
	  },

	  "verifyJWT.js -> 1.if Bearer token -> next() 2.create req.userId": {
		"prefix": "$verifyJWT",
		"body": [
		  "import jwt from \"jsonwebtoken\";",
		  "",
		  "const verifyJWT = (req, res, next) => {",
		  "  const authHeader = req.headers.authorization || req.headers.Authorization;",
		  "  if (!authHeader?.startsWith(\"Bearer \")) return res.sendStatus(401);",
		  "",
		  "  const token = authHeader.split(\" \")[1];",
		  "",
		  "  jwt.verify(token, process.env.ACCESS_TOKEN_SECRET, (err, decoded) => {",
		  "    if (err) return res.sendStatus(403);",
		  "",
		  "    req.userId = decoded.id;",
		  "    //req.user = decoded.userInfo.username;",
		  "    //req.roles = decoded.userInfo.roles;",

		  "    next();",
		  "  });",
		  "};",
		  "",
		  "export default verifyJWT;",
		  ""
		],
		"description": "verifyJWT.js -> 1.if Bearer token -> next() 2.create req.userId"
	  },

	  "userRoutes.js": {
		"prefix": "$userRoutes",
		"body": [
		  "import express from \"express\";",
		  "import userController from \"../../controllers/userController.js\";",
		  "import registerValidator from \"../../validators/registerValidator.js\";",
		  "import authValidator from \"../../validators/authValidator.js\";",
		  "import verifyJWT from \"../../middlewares/verifyJWT.js\";",
		  "import uploadController from \"../../controllers/uploadController.js\";",
		  "",
		  "const router = express.Router();",
		  "",
		  "// public routes",
		  "router.post(\"/register\", registerValidator(), userController.register);",
		  "router.post(\"/auth\", authValidator(), userController.auth);",
		  "router.get(\"/refresh\", userController.refreshTokn);",
		  "router.post(\"/findUser\", userController.findUser);",
		  "router.post(\"/sendResetPasswordCode\", userController.sendResetPasswordCode);",
		  "router.post(\"/validateResetCode\", userController.validateResetCode);",
		  "router.post(\"/changePassword\", userController.changePassword);",
		  "",
		  "// protected routes",
		  "router.use(verifyJWT);",
		  "router.post(\"/activate\", userController.activateAccount);",
		  "router.post(\"/sendVerification\", userController.sendVerificationEmail);",
		  "router.get(\"/logout\", userController.logout);",
		  "router.post(\"/coverImages\", uploadController.getListImages);",
		  "router.post(\"/profileImages\", uploadController.getListImages);",
		  "router.get(\"/getProfile/:username\", userController.getProfile);",
		  "router.post(\"/updateCover\", userController.updateCover);",
		  "router.post(\"/updatePicture\", userController.updatePicture);",
		  "router.post(\"/updateDetails\", userController.updateDetails);",
		  "export default router;",
		  ""
		],
		"description": "userRoutes.js"
	  },

	  "postRoutes.js -> protected in server.js": {
		"prefix": "$postRoutes",
		"body": [
		  "import express from \"express\";",
		  "import postController from \"../../controllers/postController.js\";",
		  "import uploadController from \"../../controllers/uploadController.js\";",
		  "import imageUpload from \"../../middlewares/imageUpload.js\";",
		  "",
		  "const router = express.Router();",
		  "",
		  "router.post(\"/createPost\", postController.createPost);",
		  "router.post(\"/uploadImages\", imageUpload, uploadController.uploadImages);",
		  "router.get(\"/posts\", postController.getPosts);",
		  "router.post(\"/myPosts\", postController.getMyPosts);",
		  "",
		  "export default router;",
		  ""
		],
		"description": "postRoutes.js -> protected in server.js"
	  },

	  "emailing verification link using OAuth2": {
		"prefix": "$mailerSendVerificationEmail",
		"body": [
		  "import nodemailer from \"nodemailer\";",
		  "import { google } from \"googleapis\";",
		  "",
		  "const { OAuth2 } = google.auth; // google.auth return an object that we need OAuth2",
		  "",
		  "const {",
		  "  EMAIL,",
		  "  GOOGLE_CLIENT_ID,",
		  "  GOOGLE_CLIENT_SECRET,",
		  "  GOOGLE_REFRESH_TOKEN,",
		  "  OAUTH_LINK,",
		  "} = process.env;",
		  "",
		  "// ***passenger***",
		  "const auth = new OAuth2(",
		  "  GOOGLE_CLIENT_ID,",
		  "  GOOGLE_CLIENT_SECRET,",
		  "  GOOGLE_REFRESH_TOKEN,",
		  "  OAUTH_LINK",
		  ");",
		  "",
		  "// VERIFICATION EMAIL",
		  "const sendVerificationEmail = (email, name, url) => {",
		  "  // ***give ticket***",
		  "  auth.setCredentials({",
		  "    refresh_token: GOOGLE_REFRESH_TOKEN,",
		  "  });",
		  "",
		  "  const accessToken = auth.getAccessToken(); // receive flight-cart ",
		  "  // ***give flight-cart to flight attendant***",
		  "  const smtp = nodemailer.createTransport({",
		  "    service: \"gmail\",",
		  "    auth: {",
		  "      type: \"OAUTH2\",",
		  "      user: EMAIL,",
		  "      clientId: GOOGLE_CLIENT_ID,",
		  "      clientSecret: GOOGLE_CLIENT_SECRET,",
		  "      accessToken,",
		  "      refreshToken: GOOGLE_REFRESH_TOKEN,",
		  "    },",
		  "  });",
		  "  // placement & destination",
		  "  const mailOptions = {",
		  "    from: EMAIL,",
		  "    to: email,",
		  "    subject: \"Facebook email verification\",",
		  "    html: `<div style=\"max-width:700px;margin-bottom:1rem;display:flex;align-items:center;gap:10px;font-family:Roboto;font-weight:600;color:#3b5998\"><img src=\"https://res.cloudinary.com/dmhcnhtng/image/upload/v1645134414/logo_cs1si5.png\" alt=\"\" style=\"width:30px\"><span>Action requise : Activate your facebook account</span></div><div style=\"padding:1rem 0;border-top:1px solid #e5e5e5;border-bottom:1px solid #e5e5e5;color:#141823;font-size:17px;font-family:Roboto\"><span>Hello ${ name }</span><div style=\"padding:20px 0\"><span style=\"padding:1.5rem 0\">You recently created an account on Facebook. To complete your registration, please confirm your account.</span></div><a href=${ url } style=\"width:200px;padding:10px 15px;background:#4c649b;color:#fff;text-decoration:none;font-weight:600\">Confirm your account</a><br><div style=\"padding-top:20px\"><span style=\"margin:1.5rem 0;color:#898f9c\">Facebook allows you to stay in touch with all your friends, once refistered on facebook,you can share photos,organize events and much more.</span></div></div>`,",
		  "  };",
		  "  // ***flight attendant seat you***",
		  "  smtp.sendMail(mailOptions, (err, res) => {",
		  "    if (err) return err",
		  "    return res;",
		  "  });",
		  "};",
		  "",
		  "// RESET PASSWORD HERE !!!",
		  "",
		  "export default sendVerificationEmail;",
		  ""
		],
		"description": "emailing verification link using OAuth2"
	  },

	  "send reset password": {
		"prefix": "$mailerSendResetPasswordCode",
		"body": [
		  "// RESET PASSWORD",
		  "export const sendResetPasswordCode = async (email, name, code) => {",
		  "  auth.setCredentials({",
		  "    refresh_token: GOOGLE_REFRESH_TOKEN,",
		  "  });",
		  "  const accessToken = auth.getAccessToken();",
		  "  const smtp = nodemailer.createTransport({",
		  "    service: \"gmail\",",
		  "    auth: {",
		  "      type: \"OAuth2\",",
		  "      user: EMAIL,",
		  "      clientId: GOOGLE_CLIENT_ID,",
		  "      clientSecret: GOOGLE_CLIENT_SECRET,",
		  "      refreshToken: GOOGLE_REFRESH_TOKEN,",
		  "      accessToken,",
		  "    },",
		  "  });",
		  "  const mailOptions = {",
		  "    from: EMAIL,",
		  "    to: email,",
		  "    subject: \"Reset Facebook Password\",",
		  "    html: `<div style=\"max-width:700px;margin-bottom:1rem;display:flex;align-items:center;gap:10px;font-family:Roboto;font-weight:600;color:#3b5998\"><img src=\"https://res.cloudinary.com/dmhcnhtng/image/upload/v1645134414/logo_cs1si5.png\" alt=\"\" style=\"width:30px\"><span>Action requise : Activate your facebook account</span></div><div style=\"padding:1rem 0;border-top:1px solid #e5e5e5;border-bottom:1px solid #e5e5e5;color:#141823;font-size:17px;font-family:Roboto\"><span>Hello ${ name }</span><div style=\"padding:20px 0\"><span style=\"padding:1.5rem 0\">You recently created an account on Facebook. To complete your registration, please confirm your account.</span></div><a  style=\"width:200px;padding:10px 15px;background:#4c649b;color:#fff;text-decoration:none;font-weight:600\">${ code }</a><br><div style=\"padding-top:20px\"><span style=\"margin:1.5rem 0;color:#898f9c\">Facebook allows you to stay in touch with all your friends, once refistered on facebook,you can share photos,organize events and much more.</span></div></div>`,",
		  "  };",
		  "  smtp.sendMail(mailOptions, (err, res) => {",
		  "    if (err) return err;",
		  "    return res;",
		  "  });",
		  "};"
		],
		"description": "send reset password"
	  },

	  "output: Nothing": {
		"prefix": "$conRegister",
		"body": [
		  "//register new user",
		  "  async register(req, res) {",
		  "    try {",
		  "      const errors = validationResult(req);",
		  "      if (!errors.isEmpty()) {",
		  "        return res.status(400).json({ errors: errors.array() });",
		  "      }",
		  "",
		  "      const newUser = await new UserModel({",
		  "        ...req.body,",
		  "        username: req.body.first_name + req.body.last_name,",
		  "      });",
		  "",
		  "      newUser.username = await newUser.generateUsername();",
		  "",
		  "      // create a mailVerificationToken based on id, secret, exp",
		  "      const mailVerificationToken = jwt.sign(",
		  "        { id: newUser._id.toString() },",
		  "        process.env.MAIL_JWT_TOKEN,",
		  "        { expiresIn: \"30m\" }",
		  "      ); //",
		  "      const url = `${process.env.BASE_URL}/activate/${ mailVerificationToken }`;",
		  "",
		  "      sendVerificationEmail(newUser.email, newUser.first_name, url);",
		  "",
		  "      await newUser.save();",
		  "",
		  "      res.json({ message: \"New user successfully created\" });",
		  "    } catch (error) {",
		  "      res.status(500).json({ message: error.message }); // server error",
		  "    }",
		  "  }"
		],
		"description": "output: Nothing"
	  },

	  "update -> verified: true *output: Nothing*": {
		"prefix": "$conActivateAccount",
		"body": [
		  "//verify account with token",
		  "  async activateAccount(req, res) {",
		  "    const { token } = req.body;",
		  "    if (!token) return res.status(400).json({ message: \"token not valid\" });",
		  "",
		  "    const user = jwt.verify( // if verify success -> return an obj(user) based on jwt payload(id)",
		  "      token,",
		  "      process.env.MAIL_JWT_TOKEN,",
		  "",
		  "      async (err, user) => {",
		  "        if (err) {",
		  "          return res.status(400).json({ message: \"Invalid token\" });",
		  "        }",
		  "        const foundUser = await UserModel.findById(user.id);",
		  "        if (!foundUser)",
		  "          return res.status(400).json({ message: \"Invalid token\" });",
		  "",
		  "        if (foundUser.id !== req.userId)",
		  "          return res.status(403).json({ message: \"invalid token\" });",
		  "",
		  "        if (foundUser.verified == true) {",
		  "          return res",
		  "            .status(400)",
		  "            .json({ message: \"this email is already activated\" });",
		  "        } else {",
		  "          await UserModel.findByIdAndUpdate(user.id, { verified: true });",
		  "          return res",
		  "            .status(200)",
		  "            .json({ message: \"Account has been activated successfully\" });",
		  "        }",
		  "      }",
		  "    );",
		  "  }"
		],
		"description": "update -> verified: true *output: Nothing*"
	  },

	  "login -> *output: accessToken, userInfo*": {
		"prefix": "$conAuth",
		"body": [
		  "//authenticate and login user",
		  "  async auth(req, res) {",
		  "    const cookies = req.cookies;",
		  "",
		  "    const errors = validationResult(req);",
		  "    if (!errors.isEmpty()) {",
		  "      return res.status(400).json({ errors: errors.array() });",
		  "    }",
		  "",
		  "    const { email, password } = req.body;",
		  "",
		  "    const foundUser = await UserModel.findOne({ email });",
		  "",
		  "    if (!foundUser) {",
		  "      return res.sendStatus(401);",
		  "    }",
		  "",
		  "    const matchPass = await bcrypt.compare(password, foundUser.password);",
		  "",
		  "    if (!matchPass) return res.sendStatus(401);",
		  "",
		  "    const accessToken = jwt.sign(",
		  "      { id: foundUser.id },",
		  "      process.env.ACCESS_TOKEN_SECRET,",
		  "      { expiresIn: \"5m\" }",
		  "    );",
		  "",
		  "    const newRefreshToken = jwt.sign(",
		  "      { id: foundUser.id },",
		  "      process.env.REFRESH_TOKEN_SECRET,",
		  "      { expiresIn: \"15d\" }",
		  "    );",
		  "",
		  "    let newRefreshTokenArray = !cookies?.jwt",
		  "      ? foundUser.refreshToken",
		  "      : foundUser.refreshToken.filter((rt) => rt !== cookies.jwt);",
		  "",
		  "    if (cookies?.jwt) {",
		  "      const refreshToken = cookies.jwt;",
		  "      const foundToken = await UserModel.findOne({ refreshToken });",
		  "      if (!foundToken) {",
		  "        newRefreshTokenArray = [];",
		  "      }",
		  "      res.clearCookie(\"jwt\", { // clear cookie",
		  "        httpOnly: true,",
		  "        sameSite: \"None\",",
		  "        secure: true,",
		  "      });",
		  "    }",
		  "",
		  "    foundUser.refreshToken = [...newRefreshTokenArray, newRefreshToken];",
		  "",
		  "    await foundUser.save();",
		  "",
		  "    res.cookie(\"jwt\", newRefreshToken, { // set cookie",
		  "      httpOnly: true,   // can not access with js *security*",
		  "      sameSite: \"None\", ",
		  "      secure: true,",
		  "      maxAge: 1000 * 60 * 60 * 24 * 15, // 15 day's",
		  "    });",
		  "",
		  "    const userInfo = {",
		  "      first_name: foundUser.first_name,",
		  "      last_name: foundUser.last_name,",
		  "      picture: foundUser.picture,",
		  "      username: foundUser.username,",
		  "      verified: foundUser.verified,",
		  "    };",
		  "    res.json({ accessToken, userInfo });",
		  "  }"
		],
		"description": "login -> *output: accessToken, userInfo*"
	  },

	  "*output: accessToken, userInfo*": {
		"prefix": "$conRefreshTokn",
		"body": [
		  "  //refresh token",
		  "  async refreshTokn(req, res) {",
		  "    const cookies = req.cookies;",
		  "",
		  "    if (!cookies?.jwt) return res.sendStatus(401);",
		  "",
		  "    const refreshToken = cookies.jwt;",
		  "    res.clearCookie(\"jwt\", { httpOnly: true, sameSite: \"None\", secure: true });",
		  "",
		  "    const foundUser = await UserModel.findOne({ refreshToken });",
		  "",
		  "    if (!foundUser) {",
		  "      jwt.verify(",
		  "        refreshToken,",
		  "        process.env.REFRESH_TOKEN_SECRET,",
		  "        async (err, decoded) => {",
		  "          if (err) return;",
		  "",
		  "          const hackedUser = await UserModel.findOne({ id: decoded.id });",
		  "",
		  "          if (hackedUser) {",
		  "            hackedUser.refreshToken = [];",
		  "            await hackedUser.save();",
		  "          }",
		  "        }",
		  "      );",
		  "",
		  "      return res.sendStatus(403);",
		  "    }",
		  "",
		  "    const newRefreshTokenArray = foundUser.refreshToken.filter(",
		  "      (rt) => rt !== refreshToken",
		  "    );",
		  "",
		  "    jwt.verify(",
		  "      refreshToken,",
		  "      process.env.REFRESH_TOKEN_SECRET,",
		  "      async (err, decoded) => {",
		  "        if (err) {",
		  "          foundUser.refreshToken = [...newRefreshTokenArray];",
		  "          await foundUser.save();",
		  "        }",
		  "",
		  "        if (err || foundUser.id !== decoded.id) return res.sendStatus(403);",
		  "",
		  "        const accessToken = jwt.sign(",
		  "          { id: decoded.id },",
		  "          process.env.ACCESS_TOKEN_SECRET,",
		  "          { expiresIn: \"5m\" }",
		  "        );",
		  "",
		  "        const newRefreshToken = jwt.sign(",
		  "          { id: foundUser.id },",
		  "          process.env.REFRESH_TOKEN_SECRET,",
		  "          { expiresIn: \"15d\" }",
		  "        );",
		  "",
		  "        foundUser.refreshToken = [...newRefreshTokenArray, newRefreshToken];",
		  "",
		  "        await foundUser.save();",
		  "",
		  "        res.cookie(\"jwt\", newRefreshToken, {",
		  "          httpOnly: true,",
		  "          secure: true,",
		  "          sameSite: \"None\",",
		  "          maxAge: 1000 * 60 * 60 * 24 * 15,",
		  "        });",
		  "",
		  "        const userInfo = {",
		  "          first_name: foundUser.first_name,",
		  "          last_name: foundUser.last_name,",
		  "          picture: foundUser.picture,",
		  "          username: foundUser.username,",
		  "          verified: foundUser.verified,",
		  "        };",
		  "        res.json({ accessToken, userInfo });",
		  "      }",
		  "    );",
		  "  }"
		],
		"description": "*output: accessToken, userInfo*"
	  },

	  "resend verification email": {
		"prefix": "$conSendVerificationEmail",
		"body": [
		  "// resend verification email",
		  "  async sendVerificationEmail(req, res) {",
		  "    try {",
		  "      const id = req.userId;",
		  "      const user = await UserModel.findById(id);",
		  "      if (user.verified === true) {",
		  "        return res",
		  "          .status(400)",
		  "          .json({ message: \"This accounst is already activated\" });",
		  "      }",
		  "      const mailVerificationToken = jwt.sign(",
		  "        { id: id.toString() },",
		  "        process.env.MAIL_JWT_TOKEN,",
		  "        { expiresIn: \"30m\" }",
		  "      );",
		  "      const url = `${process.env.BASE_URL}/activate/${ mailVerificationToken }`;",
		  "      sendVerificationEmail(user.email, user.first_name, url);",
		  "      return res.status(200).json({",
		  "        message: \"Email verification link has been sent to your mail\",",
		  "      });",
		  "    } catch (error) {",
		  "      res.status(500).json({ message: error.message });",
		  "    }",
		  "  }"
		],
		"description": "send verification email"
	  },

	  "login -": {
		"prefix": "$Con",
		"body": [
		  "import { validationResult } from \"express-validator\";",
		  "import bcrypt from \"bcrypt\";",
		  "import UserModel from \"../models/userModel.js\";",
		  "import jwt from \"jsonwebtoken\";",
		  "import sendVerificationEmail from \"../utilities/mailer.js\";",
		  "// import CodeModel from \"../models/codeModel.js\";",
		  "import randomstring from \"randomstring\";",
		  "import { sendResetPasswordCode } from \"../utilities/mailer.js\";",
		  "",
		  "",
		  "class XController {",
		  "  constructor() {}",
		  "",
		  "  // CONTROLLERS",
		  "",
		  "}",
		  "",
		  "export default new XController();",
		  ""
		],
		"description": "login -"
	  },

	  ".env": {
		"prefix": "$env",
		"body": [
		  "PORT=3500",
		  "DATABASE_URI=mongodb://127.0.0.1:27017/facebook",
		  "",
		  "# FOR LOGIN WITH GMAIL & VERIFICATION LINK",
		  "GOOGLE_CLIENT_ID=934475808916-ubr2ohht4tat4tk38eg4qalcsb7sf5d5.apps.googleusercontent.com",
		  "GOOGLE_CLIENT_SECRET=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",
		  "GOOGLE_REFRESH_TOKEN=1//04q1u_OcdnbRTCgYIARAAGAQSNwF-L9IrBezysY9Sm5MCWf1YscXg3VA40rLqwa4xZIQVSJbkk5lBldJ55SXfN1WkADKoQuXrAj8",
		  "GOOGLE_ACCESS_TOKEN=ya29.a0AfB_byB4MElsKtyEDy8PrXXOgR8Rl32E9Khu1xLgdGyaw4TVWxwpOGkegQN6FZrTPRZ1BxphI1UT8IpEKeWpDrPEtgSPojsibPCAc0Nr6hjwQ09e0DF2z1Y6Dcgax-LE1BGNKOs045Nh4A2KuomzoUVba5COr7QHyRnVaCgYKATcSARASFQGOcNnC7iVsHk8d4iW_Ep0WfmmRFw0171",
		  "OAUTH_LINK=https://developers.google.com/oauthplayground",
		  "EMAIL=thisismeee25@gmail.com",
		  "BASE_URL=http://localhost:3000",
		  "MAIL_JWT_TOKEN=2fe8428a0afe38c26232a70f2c13d657eccd9549a846d48d895a5ded71e01cb23550192db5f8a3b381b2fb44adfc8eb6330d956d096fbb705bec2bee76c6de56",
		  "",
		  "# FOR STAY LOGIN",
		  "ACCESS_TOKEN_SECRET=bcf9b3aed5c70008ca1e26b5aa909a3c751b451b18c85a763e4ceb6559f2a56cf67cb45593fd714f27719978db6125dae6ca1fd79c4b9b7819df7d6d13fda572",
		  "REFRESH_TOKEN_SECRET=7eabb5a52a23dd1713cc5158e09aecacff9e50449ef5f3aa10632e2458bff56f406fb9ed982149f6224db75b6c26176ecdff71b1af9959aab1b4a95bb342adb9"
		],
		"description": ".env"
	  },

	  "req.body": {
		"prefix": "$req-body",
		"body": [
		  "const { token, email } = req.body;"
		],
		"description": "req.body"
	  },

	  "req.cookies -> active cookieParser": {
		"prefix": "$req-cookies",
		"body": [
		  "const cookies = req.cookies;"
		],
		"description": "req.cookies -> active cookieParser"
	  },

	  "created in JWTverify": {
		"prefix": "$req-userId",
		"body": [
		  "const id = req.userId;"
		],
		"description": "created in JWTverify"
	  },

	  "validator": {
		"prefix": "$validationResult",
		"body": [
		  "const errors = validationResult(req);",
		  "if (!errors.isEmpty()) {",
		  "  return res.status(400).json({ errors: errors.array() });",
		  "}"
		],
		"description": "validator"
	  },

	  "match password with bcrypt": {
		"prefix": "$matchPass",
		"body": [
		  "const matchPass = await bcrypt.compare(password, foundUser.password);",
		],
		"description": "match password with bcrypt"
	  },

	  "create new user, product, ... based on model": {
		"prefix": "$newModel",
		"body": [
		  "const newUser = await new UserModel({",
		  "  ...req.body,",
		  "  username: req.body.first_name + req.body.last_name,",
		  "});"
		],
		"description": "create new user, product, ... based on model"
	  },

	  "findById": {
		"prefix": "$findById",
		"body": [
		  "const foundUser = await UserModel.findById(user.id);"
		],
		"description": "findById"
	  },

	  "findByIdAndUpdate": {
		"prefix": "$findByIdAndUpdate",
		"body": [
		  "await UserModel.findByIdAndUpdate(user.id, { verified: true });"
		],
		"description": "findByIdAndUpdate"
	  },

	  "find by one property": {
		"prefix": "$findOne",
		"body": [
		  "const hackedUser = await UserModel.findOne({ id: decoded.id });",
		  "// OR",
		  "const id = decoded.id",
		  "const hackedUser = await UserModel.findOne({ id });",
		  "",
		  "// ------------------------------------------------",
		  "",
		  "const foundUser = await UserModel.findOne({ refreshToken: cookies.jwt});",
		  "// OR",
		  "const refreshToken = cookies.jwt;",
		  "const foundUser = await UserModel.findOne({ refreshToken });"
		],
		"description": "find by one property"
	  },

	  "empty arg => .this": {
		"prefix": "$xMethod()",
		"body": [
		  "const newUser = await new UserModel({",
		  "  ...req.body,",
		  "  username: req.body.first_name + req.body.last_name,",
		  "});",
		  "// method = generateUsername()",
		  "newUser.username = await newUser.generateUsername();"
		],
		"description": "empty arg "
	  },

	  "has arg but ????????": {
		"prefix": "$xMethode(y)",
		"body": [
		  "?????"
		],
		"description": "has arg ????????"
	  },

	  "(payload, SECRET, exp)": {
		"prefix": "$jwt-sign ",
		"body": [
		  "const accessToken = jwt.sign(",
		  "  { id: foundUser.id }, //{userInfo: { username: foundUser.username, roles }}, => verifyJWT.js",
		  "  process.env.ACCESS_TOKEN_SECRET,",
		  "  { expiresIn: \"5m\" }",
		  ");",
		  "",
		  "// ----if req.userId----",
		  "const id = req.userId;",
		  "const mailVerificationToken = jwt.sign(",
		  "  { id: id.toString() },",
		  "  process.env.MAIL_JWT_TOKEN,",
		  "  { expiresIn: \"30m\" }",
		  ");"
		],
		"description": "(payload, SECRET, exp)"
	  },

	  "allowedRoles or not": {
		"prefix": "$verifyRoles",
		"body": [
		  "//ues like this in routes: ",
		  "//router.get(\"/\", verifyRoles(ROLES_LIST.Admin), userController.getAllUsers);",
		  "const verifyRoles = (...allowedRoles) => {",
		  "  return (req, res, next) => {",
		  "    if (!req?.roles) return res.sendStatus(401);",
		  "    const rolesArray = [...allowedRoles];",
		  "    const result = req.roles",
		  "      .map((role) => rolesArray.includes(role))",
		  "      .find((val) => val == true);",
		  "    if (!result) return res.sendStatus(401);",
		  "    next();",
		  "  };",
		  "};",
		  "",
		  "export default verifyRoles;",
		  ""
		],
		"description": "allowedRoles or not"
	  },

	  "x is verify? , SECRET, cd(err, user_of_X) ": {
		"prefix": "$jwt-verify",
		"body": [
		  "jwt.verify(",
		  "  ${1|x,refreshToken|},",
		  "  process.env.REFRESH_TOKEN_SECRET,",
		  "  async (err, ${2|decoded, user|}) => {",
		  "     $3           ",
		  "  }",
		  ");"
		],
		"description": "x is verify? , SECRET, cd(err, user_of_X) "
	  },

	  "set cookie": {
		"prefix": "$setCookie",
		"body": [
		  "res.cookie(\"jwt\", newRefreshToken, { // set cookie",
		  "  httpOnly: true,   // can not access with js *security*",
		  "  sameSite: \"None\", ",
		  "  secure: true,",
		  "  maxAge: 1000 * 60 * 60 * 24 * 15, // 15 day's",
		  "});",
		  ""
		],
		"description": "set cookie with <<newRefreshToken>> as <<jwt>>"
	  },

	  "clear cookie with name jwt": {
		"prefix": "$clearCookie",
		"body": [
		  "res.clearCookie(\"jwt\", { httpOnly: true, sameSite: \"None\", secure: true });"
		],
		"description": "clear cookie with name jwt"
	  },

	  "seve query changes in db": {
		"prefix": "$-save",
		"body": [
		  "await foundedUser.save();",
		  "// OR",
		  "await newUser.save();"
		],
		"description": "seve query changes in db"
	  },

	  "res => message": {
		"prefix": "$res-msg",
		"body": [
		  "res.status(200).json({ message: \"text\" });"
		],
		"description": "res => message (in func or if => return)"
	  },

	  "res => output (if in func return)": {
		"prefix": "$res-output",
		"body": [
		  "res.json({ accessToken, userInfo });"
		],
		"description": "res => output (in func or if => return)"
	  },

	  "res => err (if in func return)": {
		"prefix": "$res-err-msg",
		"body": [
		  "",
		  "// catch(error)",
		  "res.status(500).json({ message: error.message });",
		  "",
		  "// if",
		  "return res.status(400).json({ message: \"Invalid token\" });"
		],
		"description": "res => err (if in func return)"
	  },

	  "controller template": {
		"prefix": "$ConTemp",
		"body": [
		  "async register(req, res) {",
		  "    ",
		  "}"
		],
		"description": "controller template"
	  },

	  "newRefreshTokenArray from db + remove expired RT from cookie": {
		"prefix": "$getNewRTArrFromDB",
		"body": [
		  "let newRefreshTokenArray = !cookies?.jwt",
		  "  ? foundUser.refreshToken",
		  "  : foundUser.refreshToken.filter((rt) => rt !== cookies.jwt);"
		],
		"description": "newRefreshTokenArray from db + remove expired RT from cookie"
	  },

	  "": {
		"prefix": "$clearRTsFromCookie",
		"body": [
		  "const refreshToken = cookies.jwt;",
		  "const foundToken = await UserModel.findOne({ refreshToken });",
		  "if (!foundToken) {",
		  "  newRefreshTokenArray = [];",
		  "}",
		  "res.clearCookie(\"jwt\", { // clear cookie",
		  "  httpOnly: true,",
		  "  sameSite: \"None\",",
		  "  secure: true,",
		  "});"
		],
		"description": ""
	  },

	  "add newRefreshTokenArray + NewRT to DB": {
		"prefix": "$saveNewRTtoDB",
		"body": [
		  "foundUser.refreshToken = [...newRefreshTokenArray, newRefreshToken];",
		  "await foundUser.save();"
		],
		"description": "add newRefreshTokenArray + NewRT to DB"
	  },

	  "userInfo": {
		"prefix": "$userInfo",
		"body": [
		  "const userInfo = {",
		  "  first_name: foundUser.first_name,",
		  "  last_name: foundUser.last_name,",
		  "  picture: foundUser.picture,",
		  "  username: foundUser.username,",
		  "  verified: foundUser.verified,",
		  "};"
		],
		"description": "userInfo"
	  },

	  "delete RT from RTArray => NewRTArray": {
		"prefix": "$filterRTFromRTArray",
		"body": [
		  "const newRefreshTokenArray = foundUser.refreshToken.filter(",
		  "  (rt) => rt !== refreshToken",
		  ");"
		],
		"description": "delete RT from RTArray => NewRTArray"
	  },


	  "rate limit": {
		"prefix": "$rateLimit",
		"body": [
		  "import rateLimit from \"express-rate-limit\";",
		  "",
		  "const phoneLimiter = rateLimit({",
		  "  windowMs: 3 * 60 * 1000,",
		  "  max: 4,",
		  "  message: async (req, res) => {",
		  "    return {",
		  "      message: \"بیش از حد مجاز تلاش کردید بعد از 3 دقیقه دوباره تلاش کنید\",",
		  "    };",
		  "  },",
		  "  standardHeaders: true,",
		  "  legacyHeaders: false,",
		  "});",
		  "",
		  "const codeLimiter = rateLimit({",
		  "  windowMs: 2 * 60 * 1000,",
		  "  max: 3,",
		  "  message: async (req, res) => {",
		  "    return {",
		  "      message: \"بیش از حد مجاز تلاش کردید بعد از 3 دقیقه دوباره تلاش کنید\",",
		  "    };",
		  "  },",
		  "  standardHeaders: true,",
		  "  legacyHeaders: false,",
		  "});",
		  "",
		  "export { codeLimiter, phoneLimiter };",
		  ""
		],
		"description": "rate limit"
	  },

	  "error handler": {
		"prefix": "$AppError",
		"body": [
		  "class AppError extends Error {",
		  "  constructor(message, statusCode) {",
		  "    super(message);",
		  "    this.statusCode = statusCode;",
		  "    this.status = `${ statusCode }`.startsWith(\"4\") ? \"fail\" : \"error\"; // errors start with 4 is fail",
		  "    this.isOperational = true; // indicate WE create this error not app",
		  "    Error.captureStackTrace(this, this.constructor); // display stack trace of error",
		  "  }",
		  "}",
		  "",
		  "export default AppError;",
		  ""
		],
		"description": "error handler"
	  },

	  "catch function": {
		"prefix": "$catchFn",
		"body": [
		  "//catch handler for async func's",
		  "",
		  "const catchFn = (fn) => {",
		  "  return (req, res, next) => {",
		  "    fn(req, res, next).catch(next);",
		  "  };",
		  "};",
		  "",
		  "export default catchFn;",
		  ""
		],
		"description": "catch function"
	  },

	  "dev + prod + json errors": {
		"prefix": "$errorController",
		"body": [
		  "//handle errors : ",
		  "//     1.backend=development ",
		  "//     2.frontend=production ",
		  "//     3.input json errors=production",
		  "",
		  "import AppError from \"../utils/AppError.js\";",
		  "",
		  "const handleEntityParseFailed = () => {",
		  "  const message = \"رشته JSON ارسالی معتبر نیست\";",
		  "  return new AppError(message, 400);",
		  "};",
		  "",
		  "const sendErrorDev = (err, res) => {",
		  "  res.status(err.statusCode).json({",
		  "    status: err.status,",
		  "    error: err,",
		  "    message: err.message,",
		  "    stack: err.stack,",
		  "  });",
		  "};",
		  "",
		  "const sendErrorProd = (err, res) => {",
		  "  console.log({ message: err.message, status: err.status });",
		  "  if (err.isOperational) {",
		  "    res.status(err.statusCode).json({",
		  "      status: err.status,",
		  "      message: err.message,",
		  "    });",
		  "  } else {",
		  "    console.log(\"ERROR 💥\", err);",
		  "    res.status(500).json({",
		  "      status: \"error\",",
		  "      message: \"خطایی در سرور رخ داد\",",
		  "    });",
		  "  }",
		  "};",
		  "",
		  "const globalErrorHandler = (err, _req, res, _next) => {",
		  "  err.statusCode = err.statusCode || 500;",
		  "  err.status = err.status || \"error\";",
		  "  if (process.env.NODE_ENV?.trim() === \"development\") {",
		  "    return sendErrorDev(err, res);",
		  "  } else if (process.env.NODE_ENV?.trim() === \"production\") {",
		  "    let error = { ...err, message: err.message };",
		  "    if (err.type === \"entity.parse.failed\") error = handleEntityParseFailed();",
		  "    return sendErrorProd(error, res);",
		  "  }",
		  "};",
		  "",
		  "export default globalErrorHandler;",
		  ""
		],
		"description": "dev + prod + json errors"
	  },

	  "new error in if": {
		"prefix": "$new-AppError",
		"body": [
		  "if (${1:!phoneNumber}) return next(new AppError(\"${2:متن}\"), ${3:400});"
		],
		"description": "new error in if"
	  },

	  "alternative validator": {
		"prefix": "$regex",
		"body": [
		  "const regex = new RegExp(\"^09\\\\d{9}$\");",
		  "const isValidNum = regex.test(phoneNumber);",
		  "if (!isValidNum) return next(new AppError(\"شماره موبایل وارد شده معتبر نیست\", 400));"
		],
		"description": "alternative validator"
	  },

	  "random integer": {
		"prefix": "$randomInteger",
		"body": [
		  "//import randomInteger from \"random-int\";",
		  "const verificationCode = randomInteger(100123, 999879);"
		],
		"description": "random integer"
	  },

	  "create new query": {
		"prefix": "$.create",
		"body": [
		  "const newUser = await User.create({ phoneNumber });"
		],
		"description": "create new query"
	  },

	  "uniqueString": {
		"prefix": "$uniqueString",
		"body": [
		  "// import uniqueString from \"unique-string\";",
		  "const string = uniqueString().slice(3, 10);"
		],
		"description": "uniqueString"
	  },

	  "raygan-sms": {
		"prefix": "$raygan-sms-send",
		"body": [
		  "//import TrezSMSClient from \"trez-sms-client\";",
		  "",
		  "const client = new TrezSMSClient(process.env.SMS_USERNAME, process.env.SMS_PASSWORD);",
		  "",
		  "client.manualSendCode(phoneNumber,`وب سایت پازل \\n کد تایید شما: ${ verificationCode } \\n مدت اعتبار این کد ۲ دقیقه می‌باشد` )",
		  ".then(async (messageId) => {",
		  "  if (messageId <= 2000) return next(AppError(\"ارسال کد تایید با خطا مواجه شد لطفا دوباره تلاش نمایید\", 500));",
		  "",
		  "  let user = await User.findOne({ phoneNumber });",
		  "  if (!user) {",
		  "    user = await User.create({ phoneNumber });",
		  "    user.name = uniqueString().slice(3, 10);",
		  "  }",
		  "  user.verificationCode = verificationCode;",
		  "  user.verificationDate = new Date();",
		  "  await user.save();",
		  "",
		  "  return res.status(200).json({",
		  "    message: \"کد تایید به شماره موبایل وارد شده ارسال گردید\",",
		  "    phoneNumber,",
		  "  });",
		  "})",
		  ".catch((err) => {",
		  "  return next(new AppError(\"کد تایید ارسال نشد لطفا دوباره تلاش نمایید\", 500));",
		  "});"
		],
		"description": "raygan-sms"
	  },

	  "router": {
		"prefix": "$router",
		"body": [
		  "router.${1|post,get,put,delete|}(\"/${2:register}\", ${3|registerValidator(),NOTHING|}, userController.${4:register});"
		],
		"description": "router"
	  },

	  "roles list": {
		"prefix": "$roles_list",
		"body": [
		  "const ROLES_LIST = {",
		  "  Admin: 1001,",
		  "  Editor: 1002,",
		  "  User: 1000,",
		  "};",
		  "",
		  "export default ROLES_LIST;",
		  ""
		],
		"description": "roles list"
	  },

	  "exp. admin: true": {
		"prefix": "$get-roles",
		"body": [
		  "const roles = Object.values(foundUser.roles).filter(Boolean); // res => roles && jwt.sign => roles",
		  ""
		],
		"description": "exp. admin: true"
	  },

	  "logout": {
		"prefix": "$conLogout",
		"body": [
		  "async logout(req, res) {",
		  "    const cookies = req.cookies;",
		  "",
		  "    if (!cookies?.jwt) return res.sendStatus(204);",
		  "    ",
		  "    const refreshToken = cookies.jwt;",
		  "    const foundUser = await UserModel.findOne({ refreshToken });",
		  "    if (!foundUser) {",
		  "      res.clearCookie(\"jwt\", {",
		  "        httpOnly: true,",
		  "        sameSite: \"None\",",
		  "        secure: true,",
		  "      });",
		  "      return res.sendStatus(204);",
		  "    }",
		  "",
		  "    foundUser.refreshToken = foundUser.refreshToken.filter(",
		  "      (rt) => rt !== refreshToken",
		  "    );",
		  "    await foundUser.save();",
		  "    res.clearCookie(\"jwt\", { httpOnly: true, sameSite: \"None\", secure: true });",
		  "    return res.sendStatus(204);",
		  "  }",
		  ""
		],
		"description": "logout"
	  },

	  "code model = id + code": {
		"prefix": "$codeModel",
		"body": [
		  "import mongoose from \"mongoose\";",
		  "",
		  "const { ObjectId } = mongoose.Schema;",
		  "",
		  "const codeSchema = new mongoose.Schema(",
		  "  {",
		  "    code: { type: String, required: true },",
		  "    user: { type: ObjectId, ref: \"User\", required: true },",
		  "  },",
		  "  { timestamps: true }",
		  ");",
		  "",
		  "export default mongoose.model(\"Code\", codeSchema);",
		  ""
		],
		"description": "code model = id + code"
	  },

	  "except password": {
		"prefix": "$findOne-select",
		"body": [
		  "const user = await UserModel.findOne({ email }).select(\"-password\");",
		  ""
		],
		"description": "except password"
	  },

	  "findOneAndDelete": {
		"prefix": "$findOneAndDelete",
		"body": [
		  "await CodeModel.findOneAndDelete({ user: foundUser.id });"
		],
		"description": "findOneAndDelete"
	  },

	  "remove from db": {
		"prefix": "$-remove",
		"body": [
		  "await foundUser.remove();"
		],
		"description": "remove from db"
	  },

	  "findUserCon": {
		"prefix": "$findUserCon",
		"body": [
		  "//find user",
		  "  async findUser(req, res) {",
		  "    try {",
		  "      const { email } = req.body;",
		  "      if (!email) return res.status(400).json({ message: \"email is required\" });",
		  "",
		  "      const user = await UserModel.findOne({ email });",
		  "      if (!user) return res.status(400).json({ message: \"user not found\" });",
		  "",
		  "      res.status(200).json({ email: user.email, picture: user.picture });",
		  "    } catch (error) {",
		  "      res.status(500).json({ message: error.message });",
		  "    }",
		  "  }"
		],
		"description": "findUserCon"
	  },

	  "sendResetPasswordCode": {
		"prefix": "$sendResetPasswordCodeCon",
		"body": [
		  "  // send reset password code",
		  "  async sendResetPasswordCode(req, res) {",
		  "    try {",
		  "      const { email } = req.body;",
		  "      if (!email) return res.status(400).json({ message: \"email required\" });",
		  "",
		  "      const foundUser = await UserModel.findOne({ email }).select(\"-password\");",
		  "      if (!foundUser)",
		  "        return res.status(400).json({ message: \"user not found\" });",
		  "      const prevDbCode= await CodeModel.findOne({ user:foundUser.id })",
		  "      if(prevDbCode) await CodeModel.findOneAndDelete({ user: foundUser.id });",
		  "      const code = randomInteger(100123, 999879);",
		  "      await new CodeModel({",
		  "        user: foundUser.id,",
		  "        code: code,",
		  "      }).save();",
		  "      ",
		  "      //sendResetPasswordCode()",
		  "      const info = await sendHtmlEmail(email, foundUser.name, code);",
		  "",
		  "      res.status(200).json({ message: \"email has been sent successfully\" });",
		  "    } catch (error) {",
		  "      res.status(500).json({ message: error.message });",
		  "    }",
		  "  }"
		],
		"description": "sendResetPasswordCode"
	  },

	  "validateResetCode": {
		"prefix": "$validateResetCodeCon",
		"body": [
		  " // validate reset code",
		  "  async validateResetCode(req, res) {",
		  "    try {",
		  "      const { code, email } = req.body;",
		  "      if (!code || !email)",
		  "        return res.status(400).json({ message: \"code and email required\" });",
		  "",
		  "      const foundUser = await UserModel.findOne({ email });",
		  "      if (!foundUser)",
		  "        return res.status(400).json({ message: \"user not found\" });",
		  "",
		  "      const dbCode = await CodeModel.findOne({ user: foundUser.id });",
		  "      if (!dbCode) return res.status(400).json({ message: \"code not found\" });",
		  "      if (dbCode?.code !== code)",
		  "        return res.status(400).json({ message: \"code not valid\" });",
		  "",
		  "      res.status(200).json({ code: code });",
		  "    } catch (error) {",
		  "      res.status(500).json({ message: error.message });",
		  "    }",
		  "  }"
		],
		"description": "validateResetCode"
	  },

	  "changePassword": {
		"prefix": "$changePasswordCon",
		"body": [
		  "  // reset password",
		  "  async changePassword(req, res) {",
		  "    try {",
		  "      const { password, email, code } = req.body;",
		  "      if (!email || !code || !password)",
		  "        return res",
		  "          .status(400)",
		  "          .json({ message: \"cod and email and password is required\" });",
		  "",
		  "      const foundUser = await UserModel.findOne({ email });",
		  "      if (!foundUser)",
		  "        return res.status(400).json({ message: \"user not found\" });",
		  "      const dbCode = await CodeModel.findOne({ user: foundUser.id });",
		  "      if (!dbCode) return res.status(400).json({ message: \"code not found\" });",
		  "      if (dbCode?.code !== code)",
		  "        return res.status(400).json({ message: \"code not valid\" });",
		  "",
		  "      const newPassword = password;",
		  "      const salt = await bcrypt.genSalt(12);",
		  "      foundUser.password = await bcrypt.hash(newPassword, salt);",
		  "      await foundUser.save();",
		  "",
		  "      await CodeModel.findOneAndDelete({ user: foundUser.id });",
		  "",
		  "      res.status(200).json({ message: \"password changed successfully\" });",
		  "    } catch (error) {",
		  "      res.status(500).json({ message: error.message });",
		  "    }",
		  "  }"
		],
		"description": "changePassword"
	  },

	  "": {
  "prefix": "$imageUpload",
  "body": [
    "import fs from \"fs\";",
    "",
    "const imageUpload = async (req, res, next) => {",
    "  try {",
    "    if (!req.files || Object.values(req.files).flat().length === 0) {",
    "      return res.status(400).json({ message: \"No files selected\" });",
    "    }",
    "",
    "    let files = Object.values(req.files).flat();",
    "",
    "    const fileTypes = [\"jpeg\", \"png\", \"gif\", \"webp\"];",
    "    files.forEach((file) => {",
    "      if (!fileTypes.includes(file.mimetype.split(\"/\")[1])) {",
    "        removeTemp(file.tempFilePath);",
    "        throw new Error(\"Unsupported format\");",
    "        // return res.status(400).json({ message: \"Unsupported format\" });",
    "      }",
    "      if (file.size > 1024 * 1024 * 5) {",
    "        removeTemp(file.tempFilePath);",
    "        throw new Error(\"file size is too large\");",
    "",
    "        // return res.status(400).json({ message: \"File size is too large\" });",
    "      }",
    "    });",
    "    next();",
    "  } catch (error) {",
    "    return res.status(500).json({ message: error.message });",
    "  }",
    "};",
    "",
    "const removeTemp = (path) => {",
    "  fs.unlink(path, (error) => {",
    "    if (error) throw error;",
    "  });",
    "};",
    "",
    "export default imageUpload;"
  ],
  "description": ""
},

"imageUpload middleware": {
	"prefix": "$imageUpload",
	"body": [
	  "import fs from \"fs\";",
	  "",
	  "const imageUpload = async (req, res, next) => {",
	  "  try {",
	  "    if (!req.files || Object.values(req.files).flat().length === 0) {",
	  "      return res.status(400).json({ message: \"No files selected\" });",
	  "    }",
	  "",
	  "    let files = Object.values(req.files).flat();",
	  "",
	  "    const fileTypes = [\"jpeg\", \"png\", \"gif\", \"webp\"];",
	  "    files.forEach((file) => {",
	  "      if (!fileTypes.includes(file.mimetype.split(\"/\")[1])) {",
	  "        removeTemp(file.tempFilePath);",
	  "        throw new Error(\"Unsupported format\");",
	  "        // return res.status(400).json({ message: \"Unsupported format\" });",
	  "      }",
	  "      if (file.size > 1024 * 1024 * 5) {",
	  "        removeTemp(file.tempFilePath);",
	  "        throw new Error(\"file size is too large\");",
	  "",
	  "        // return res.status(400).json({ message: \"File size is too large\" });",
	  "      }",
	  "    });",
	  "    next();",
	  "  } catch (error) {",
	  "    return res.status(500).json({ message: error.message });",
	  "  }",
	  "};",
	  "",
	  "const removeTemp = (path) => {",
	  "  fs.unlink(path, (error) => {",
	  "    if (error) throw error;",
	  "  });",
	  "};",
	  "",
	  "export default imageUpload;"
	],
	"description": "middleware"
  },

  "postModel": {
	"prefix": "$postModel",
	"body": [
	  "import mongoose from \"mongoose\";",
	  "import aggregatePaginate from \"mongoose-aggregate-paginate-v2\";",
	  "",
	  "const { ObjectId } = mongoose.Schema;",
	  "",
	  "const postSchema = new mongoose.Schema(",
	  "  {",
	  "    type: {",
	  "      type: String,",
	  "      enum: [\"profilePicture\", \"cover\", null],",
	  "      default: null,",
	  "    },",
	  "    text: {",
	  "      type: String,",
	  "    },",
	  "    images: {",
	  "      type: Array,",
	  "    },",
	  "    user: {",
	  "      type: ObjectId,",
	  "      ref: \"User\",",
	  "      required: true,",
	  "    },",
	  "    background: { type: String },",
	  "    comments: [",
	  "      {",
	  "        comment: {",
	  "          type: String,",
	  "        },",
	  "        image: { type: String },",
	  "        commentBy: {",
	  "          type: ObjectId,",
	  "          ref: \"User\",",
	  "        },",
	  "        commentAt: {",
	  "          type: Date,",
	  "          default: new Date(),",
	  "        },",
	  "      },",
	  "    ],",
	  "  },",
	  "  { timestamps: true }",
	  ");",
	  "postSchema.plugin(aggregatePaginate);",
	  "export default mongoose.model(\"Post\", postSchema);",
	  "",
	  ""
	],
	"description": "postModel"
  },

  "pagination": {
	"prefix": "$pagination",
	"body": [
	  "//import aggregatePaginate from \"mongoose-aggregate-paginate-v2\";",
	  "postSchema.plugin(aggregatePaginate);",
	  ""
	],
	"description": "pagination"
  },

  "upload controller": {
	"prefix": "$conUpload",
	"body": [
	  "import autoBind from \"auto-bind\";",
	  "import cloudinary from \"cloudinary\";",
	  "import fs from \"fs\";",
	  "",
	  "class UploadController {",
	  "  constructor() {",
	  "    autoBind(this); //automatically bind methods to the class instance",
	  "    ",
	  "    cloudinary.config({",
	  "      cloud_name: process.env.CLOUD_NAME,",
	  "      api_key: process.env.CLOUD_API_KEY,",
	  "      api_secret: process.env.CLOUD_API_SECRET,",
	  "    });",
	  "  }",
	  "",
	  "  async uploadImages(req, res) {",
	  "    try {",
	  "      const { path } = req.body;",
	  "      if (!path) return res.status(400).json({ message: \"path is empty\" });",
	  "      let files = Object.values(req.files).flat();",
	  "      let images = [];",
	  "      for (const file of files) {",
	  "        const url = await this.#uploadToCloudinary(file, path);",
	  "        images.push(url);",
	  "        this.#removeTemp(file.tempFilePath);",
	  "      }",
	  "      res.json({ images });",
	  "    } catch (error) {",
	  "      return res.status(500).json({ message: error.message });",
	  "    }",
	  "  }",
	  "",
	  "  //method remove",
	  "  async #removeTemp(path) {",
	  "    fs.unlink(path, (err) => {",
	  "      if (err) throw err;",
	  "    });",
	  "  }",
	  "  //method upload",
	  "  async #uploadToCloudinary(file, path) {",
	  "    return new Promise((resolve, reject) => {",
	  "      cloudinary.v2.uploader.upload(",
	  "        file.tempFilePath,",
	  "        {",
	  "          folder: path,",
	  "        },",
	  "        (err, res) => {",
	  "          if (err) {",
	  "            this.#removeTemp(file.tempFilePath);",
	  "            return reject(err);",
	  "          }",
	  "",
	  "          resolve({",
	  "            url: res.secure_url,",
	  "          });",
	  "        }",
	  "      );",
	  "    });",
	  "  }",
	  "",
	  "  async getListImages(req, res) {",
	  "    const { path, sort, max } = req.body;",
	  "    cloudinary.v2.search",
	  "      .expression(`${ path }`)",
	  "      .sort_by(\"created_at\", `${ sort }`)",
	  "      .max_results(max)",
	  "      .execute()",
	  "      .then((result) => {",
	  "        let images = [];",
	  "        if (result?.resources?.length > 0) {",
	  "          images = result?.resources?.map((item) => {",
	  "            return {",
	  "              url: item.secure_url,",
	  "              id: item.public_id,",
	  "            };",
	  "          });",
	  "        }",
	  "        res.json(images);",
	  "      })",
	  "      .catch((err) => {",
	  "        console.log(err?.message);",
	  "        res.status(500).json({ message: \"Error in get images\" });",
	  "      });",
	  "  }",
	  "}",
	  "",
	  "export default new UploadController();",
	  ""
	],
	"description": "upload controller"
  },
  
  "my Mailer": {
	"prefix": "$myMailer",
	"body": [
	  "// const nodemailer = require('nodemailer');",
	  "import nodemailer from 'nodemailer'",
	  "",
	  "const EMAIL = process.env.EMAIL;",
	  "const PASSWORD = process.env.PASSWORD;",
	  "",
	  "",
	  "// Function to send HTML emails",
	  "async function sendHtmlEmail(to, name, code) {",
	  "  try {",
	  "    // Create a Nodemailer transporter",
	  "    const transporter = nodemailer.createTransport({",
	  "      // Specify your email provider details",
	  "      service: \"gmail\",",
	  "      auth: {",
	  "        user: EMAIL,",
	  "        pass: PASSWORD",
	  "      }",
	  "    });",
	  "",
	  "    // Define the email options",
	  "    const mailOptions = {",
	  "      from: EMAIL,",
	  "      to: to,",
	  "      subject: 'Mehran reset code',",
	  "      html: `<h1>Hello!</h1><p>hi ${ name }, your reset code is ${ code }.</p>`",
	  "    };",
	  "",
	  "    // Send the email",
	  "    const info = await transporter.sendMail(mailOptions);",
	  "    console.log('Email sent: ' + info.response);",
	  "    return info;",
	  "  } catch (error) {",
	  "    console.log(\"an Error:\" + error);",
	  "    throw error;",
	  "  }",
	  "}",
	  "",
	  "export default sendHtmlEmail;",
	  "",
	  "",
	  "// try {",
	  "//     const to = 'recipient@example.com';",
	  "//     const subject = 'Hello from Express Mailer';",
	  "//     const html = '<h1>Hello!</h1><p>This is an HTML email sent from Express Mailer.</p>';",
	  "",
	  "//     // Use the mailer function to send the email",
	  "//     const info = await sendHtmlEmail(to, name, code);",
	  "",
	  "//     res.send('Email sent successfully');",
	  "//   } catch (error) {",
	  "//     res.status(500).send('Error sending email');",
	  "//   }"
	],
	"description": "my Mailer"
  },

  "create post": {
	"prefix": "$conCreatePost",
	"body": [
	  "import PostModel from \"../models/postModel.js\";",
	  "class PostController {",
	  "  constructor() {}",
	  "",
	  "  async createPost(req, res) {",
	  "    try {",
	  "      const { images, text, bg } = req.body;",
	  "      if(!images && !text && !bg) return res.status(400).json({ message: \"image or text or bg is required\" });",
	  "      ",
	  "      const newPost = await new PostModel({",
	  "      ...req.body,",
	  "        user: req.userId,",
	  "      }).save()",
	  "",
	  "      // look at *user* in POST-MODEL =ref=> fetch new field's from USER-MODEL => add new field's",
	  "      const populatedNewPost = await newPost.populate(\"user\", \"first_name last_name picture username\")",
	  "",
	  "      res.status(200).json({populatedNewPost});",
	  "    } catch (error) {",
	  "      res.status(500).json({ message: error.message });",
	  "    }",
	  "}",
	  "",
	  "}",
	  "",
	  "export default new PostController();",
	  ""
	],
	"description": "create post"
  },

  "populate": {
	"prefix": "$-populate",
	"body": [
	  "// in ***res*** => add new fields to *FIRST_ARG* from *ref=FIRST_ARG * model",
	  "// look at *user* in POST-MODEL =ref=> fetch new field's from USER-MODEL => add new field's",
	  "await post.populate(\"user\", \"first_name last_name picture username\")"
	],
	"description": "populate"
  },

  "forEach": {
	"prefix": "$forEach",
	"body": [
	  "images.forEach((img) => {",
	  "      ",
	  "});"
	],
	"description": "forEach"
  },

  "true or false - array and string": {
	"prefix": "$-include",
	"body": [
	  "const numbers = [1, 2, 3, 4, 5];",
	  "console.log(numbers.includes(3)); // Output: true",
	  "",
	  "const message = \"Hello, world!\";",
	  "console.log(message.includes(\"world\")); // Output: true"
	],
	"description": "true or false - array and string"
  },

  "remove image": {
	"prefix": "$conRemoveImage",
	"body": [
	  "// method to remove image from Cloudinary",
	  "async removeImage(req, res) {",
	  "  try {",
	  "    const { publicId } = req.params;",
	  "    const decodedPublicId = decodeURIComponent(publicId); // because of slash's",
	  "    console.log('publicId',publicId);",
	  "    if (!publicId) return res.status(400).json({ message: \"publicId is empty\" });",
	  "",
	  "    cloudinary.v2.uploader.destroy(decodedPublicId, (error, result) => {",
	  "      if (error) return res.status(500).json({ message: \"Error deleting image from Cloudinary\" });",
	  "    });",
	  "    const user = await PostModel.findOneAndDelete({ \"images.publicId\": decodedPublicId });",
	  "    res.json({ message: \"Image deleted successfully\" });",
	  "  } catch (error) {",
	  "    return res.status(500).json({ message: error.message });",
	  "  }",
	  "}"
	],
	"description": "remove image"
  },

  "a string from url": {
	"prefix": "$req-params",
	"body": [
	  "const { publicId } = req.params;"
	],
	"description": "a string from url"
  },

  "create post *action*": {
	"prefix": "$action-createPost",
	"body": [
	  "export const createPost = (axiosPrivate, values, formData=null) => async (dispatch) => {",
	  "    try {",
	  "        dispatch({ type: CLEAR_POST_INFO });",
	  "        if(formData){",
	  "            dispatch({ type: UPLOAD_POST_IMAGES_REQUEST });",
	  "            var res = await axiosPrivate.post('/post/uploadImages', formData, {headers: {'Content-Type': 'multipart/form-data'}}); //UPLOAD MULTI FILE",
	  "            dispatch({ type: UPLOAD_POST_IMAGES_SUCCESS, payload: { images: res?.data?.images }});",
	  "        }",
	  "        dispatch({ type: CREATE_POST_REQUEST });",
	  "        const response = await axiosPrivate.post('/post/createPost', {images: res?.data?.images || [], ...values});",
	  "        dispatch({ type: CREATE_POST_SUCCESS, payload: {postInfo:{images:res?.data?.images || [], ...values}} });",
	  "        dispatch({ type: ADD_NEW_POST, payload: { post: response?.data } });     ",
	  "    } catch (error) {",
	  "        let errorMsg = \"\";",
	  "        if(res?.data?.images[0]?.publicId){",
	  "          res.data.images.map(async (img, index) => {",
	  "            dispatch({ type: REMOVE_UPLOADED_IMAGES_REQUEST });",
	  "            const encodedPublicId = encodeURIComponent(res?.data?.images[index]?.publicId); // because of slash's",
	  "            await axiosPrivate.post(`/post/removeImage/${encodedPublicId}`);",
	  "            dispatch({ type: REMOVE_UPLOADED_IMAGES_SUCCESS });",
	  "          })",
	  "        }else{",
	  "            errorMsg = \"آپلود فایل نا موفق بود\"",
	  "            dispatch({ type: UPLOAD_POST_IMAGES_FAIL, payload: { errorMsg } });",
	  "        }",
	  "        if (!error?.response) {",
	  "          errorMsg = \"سرور پاسخگو نیست\";",
	  "        } else if (error.response?.status === 400) {",
	  "          errorMsg = error?.response?.data?.errors[0]?.msg;",
	  "        } else {",
	  "          errorMsg = \"عملیات موفق آمیز نبود\"",
	  "        }",
	  "        dispatch({ type: CREATE_POST_FAIL, payload: { errorMsg } });",
	  "    } ",
	  "};"
	],
	"description": "create post *action*"
  },

  

  "send Post": {
	"prefix": "$sendPostHandler-func",
	"body": [
	  "const sendPostHandler = () => {",
	  "  if (bg) {",
	  "    dispatch(createPostAction(axiosPrivate, { text, background: bg }));",
	  "  } else if (images?.length) {",
	  "    const postImages = images.map((img) => dataurlToBlob(img));",
	  "    const path = `${user?.userInfo?.username}/post-images`;",
	  "    let formData = new FormData();",
	  "    formData.append(\"path\", path);",
	  "     postImages.forEach((img) => {",
	  "      formData.append(\"file\", img);",
	  "    });",
	  "    console.log(formData);",
	  "    dispatch(createPostAction(axiosPrivate, { text, path }, formData));",
	  "   } else if (text) {",
	  "    dispatch(createPostAction(axiosPrivate, { text }));",
	  "  }",
	  "};"
	],
	"description": "send Post"
  },

  "upload useEffect": {
	"prefix": "$upload-useEffect",
	"body": [
	  "useEffect(() => {",
	  "  if (",
	  "    ( post?.postInfo?.images?.length > 0 ||",
	  "      post?.postInfo?.background ||",
	  "      post?.postInfo?.text ) &&",
	  "    !post?.errorMessage",
	  "  ) {",
	  "    // setVisibleCreatePost(false);",
	  "    // navigate(\"/\");",
	  "  }",
	  "}, [",
	  "  post?.postInfo?.images,",
	  "  post?.postInfo?.background,",
	  "  post?.errorMessage,",
	  "  post?.postInfo?.text,",
	  "]);"
	],
	"description": "upload useEffect"
  },

  "textarea": {
	"prefix": "$input-textarea",
	"body": [
	  "<div className=\"relative px-4\">",
	  "  <textarea",
	  "    className={`w-full bg-gray-100 rounded-md  pl-3 pr-10 py-3 h-20 resize-none overflow-y-scroll scrollbar-thin scrollbar-thumb-gray-200 scrollbar-thumb-rounded-lg text-lg border-none text-gray-700 focus:ring-0`}",
	  "    ref={textRef}",
	  "    value={text}",
	  "    onChange={(e) => setText(e.target.value)}",
	  "    placeholder={`What's on your mind`}",
	  "	   //maxLength={100}",
	  "  />",
	  "  <span className=\"absolute right-6 bottom-1\">",
	  "    <EmojiPicker text={text} setText={setText} textRef={textRef} position = {'top'} />",
	  "  </span>",
	  "</div>"
	],
	"description": "textarea"
  },

  "emojiPicker component": {
	"prefix": "$emojiPicker.jsx",
	"body": [
	  "import Picker from \"emoji-picker-react\";",
	  "import { FaceSmileIcon } from \"@heroicons/react/24/outline\";",
	  "import { useState, useRef, useEffect } from \"react\";",
	  "import useClickOutside from \"../../hooks/useClickOutside\";",
	  "",
	  "const EmojiPicker = ({ textRef, setText, text, position = \"top\" }) => {",
	  "  const [showEmojiPicker, setShowEmojiPicker] = useState(false);",
	  "  const emojiRef = useRef(null);",
	  "  const [cursorPosition, setCursorPosition] = useState();",
	  "",
	  "  useEffect(() => {",
	  "    textRef.current.selectionEnd = cursorPosition;",
	  "  }, [cursorPosition]);",
	  "",
	  "  const handleEmoji = (e, { emoji }) => {",
	  "    const ref = textRef.current;",
	  "    ref.focus();",
	  "    const start = text.substring(0, ref.selectionStart);",
	  "    const end = text.substring(ref.selectionStart);",
	  "    const newText = start + emoji + end;",
	  "    setText(newText);",
	  "    setCursorPosition(start.length + emoji.length);",
	  "  };",
	  "",
	  "  useClickOutside(emojiRef, () => setShowEmojiPicker(false));",
	  "",
	  "  return (",
	  "    <div ref={emojiRef} className=\"relative inline-block \">",
	  "      <div",
	  "        onClick={() => setShowEmojiPicker((prev) => !prev)}",
	  "        className={`${",
	  "          showEmojiPicker ? \"text-blue-500\" : \"text-gray-400\"",
	  "        } w-7 cursor-pointer hover:text-blue-600  transition-colors`}",
	  "      >",
	  "        <FaceSmileIcon />",
	  "      </div>",
	  "      {showEmojiPicker && (",
	  "        <div",
	  "          className={`absolute scale-75 z-40  ${",
	  "            position === \"top\"",
	  "              ? \" top-full -translate-y-11 -translate-x-[82%] \"",
	  "              : \" bottom-full -translate-x-[83%] translate-y-11 \"",
	  "          } `}",
	  "        >",
	  "          <Picker width={300} height={360} onEmojiClick={handleEmoji} />",
	  "        </div>",
	  "      )}",
	  "    </div>",
	  "  );",
	  "};",
	  "",
	  "export default EmojiPicker;",
	  ""
	],
	"description": "emojiPicker component"
  },

  "get aggregate paginate datas": {
	"prefix": "$get-AG-PG",
	"body": [
	  "const pageNum = parseInt(req.query.pageNum) || 1;",
	  "const pageLimit = parseInt(req.query.pageLimit) || 3;",
	  "const options = {",
	  "  page: pageNum,",
	  "  limit: pageLimit,",
	  "};",
	  "",
	  "const postModelAggregate = PostModel.aggregate([",
	  "  // get all posts of a specific user",
	  "  // {",
	  "  //   $${1}match: { user: foundedUser._id }, // user is ref field",
	  "  // },",
	  "  {",
	  "    $${1}lookup: {",
	  "      from: \"users\", // JOINED COLLECTION name",
	  "      localField: \"user\", // CURRENT COLLECTION ref field",
	  "      foreignField: \"_id\", // access to JOINED COLLECTION with a filed => _id is good",
	  "      as: \"user\", // labeling",
	  "      // fields that we want from whole JOINED COLLECTION",
	  "      pipeline: [",
	  "        {",
	  "          $${1}project: {",
	  "            first_name: 1,",
	  "            last_name: 1,",
	  "            username: 1,",
	  "            picture: 1,",
	  "          },",
	  "        },",
	  "      ],",
	  "    },",
	  "  },",
	  "  {",
	  "    $${1}sort: { createdAt: -1 },",
	  "  },",
	  "]);",
	  "",
	  "const posts = await PostModel.aggregatePaginate(postModelAggregate, options);",
	  "res.json(posts);${2}",
	  ""
	],
	"description": "get aggregate paginate datas"
  },

  "data from url": {
	"prefix": "$req-quary",
	"body": [
	  "const pageNum = parseInt(req.query.pageNum) || 1; //data from url + parseInt remove-able"
	],
	"description": "data from url"
  },
  
  "get from cloudinary": {
	"prefix": "$get-from-cloudinary",
	"body": [
	  "// input: path + sort + max",
	  "//output: url's + publicId's",
	  "async getListImages(req, res) {",
	  "    const { path, sort, max } = req.body;",
	  "    cloudinary.v2.search",
	  "      .expression(`${ path }`)",
	  "      .sort_by(\"created_at\", `${ sort }`)",
	  "      .max_results(max)",
	  "      .execute()",
	  "      .then((result) => {",
	  "        let images = [];",
	  "        if (result?.resources?.length > 0) {",
	  "          images = result?.resources?.map((item) => {",
	  "            return {",
	  "              url: item.secure_url,",
	  "              publicId: item.public_id,",
	  "            };",
	  "          });",
	  "        }",
	  "        res.json(images);",
	  "      })",
	  "      .catch((err) => {",
	  "        console.log(err?.message);",
	  "        res.status(500).json({ message: \"Error in get images\" });",
	  "      });",
	  "  }",
	  "}",
	  ""
	],
	"description": "get from cloudinary"
  },

  "updatePicture": {
	"prefix": "$updatePicture",
	"body": [
	  "// input: req.userId + url from req.body",
	  "//output: url",
	  "async updatePicture(req, res) {",
	  "    try {",
	  "      const { url } = req.body;",
	  "      await UserModel.findByIdAndUpdate(req.userId, {",
	  "        picture: url,",
	  "      });",
	  "      res.json(url);",
	  "    } catch (error) {",
	  "      res.status(500).json({ message: error.message });",
	  "    }",
	  "  }"
	],
	"description": "updatePicture"
  },

  "get Profile": {
	"prefix": "$getProfile",
	"body": [
	  "//input: username from req.params",
	  "//output: profile",
	  "  async getProfile(req, res) {",
	  "    try {",
	  "      const { username } = req.params;",
	  "      if (!username)",
	  "        return res.status(400).json({ message: \"username is empty\" });",
	  "      const profile = await UserModel.findOne({ username }).select(",
	  "        \"-password -_id -refreshToken -email\"",
	  "      );",
	  "      if (!profile) return res.status(400).json({ message: \"user not found\" });",
	  "      res.json(profile);",
	  "    } catch (error) {",
	  "      res.status(500).json({ message: \"Error in server\" });",
	  "    }",
	  "  }"
	],
	"description": "get Profile"
  },
  

	  
	  
}
```

</details>
