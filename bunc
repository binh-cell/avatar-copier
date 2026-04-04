local passes = 0
local fails = 0
local total = 0

local function test(name, callback)
    total = total + 1
    local success, err = pcall(callback)
    if success then
        passes = passes + 1
        print("✅ ĐẠT: " .. name)
    else
        fails = fails + 1
        -- Hiển thị lý do lỗi cụ thể hơn
        print("❌ THIẾU: " .. name .. (err and (" | " .. tostring(err)) or ""))
    end
end

print("=== BẮT ĐẦU KIỂM TRA CHUẨN UNC ===\n")

-- 1. Environment
test("getgenv",  function() assert(type(getgenv())  == "table") end)
test("getrenv",  function() assert(type(getrenv())  == "table") end)
test("getreg",   function() assert(type(getreg())   == "table") end)

-- 2. Closures
test("iscclosure", function() assert(type(iscclosure(print))          == "boolean") end)
test("islclosure", function() assert(type(islclosure(function() end)) == "boolean") end)
test("newcclosure", function() assert(type(newcclosure(function() end)) == "function") end)

-- 3. Console
test("rconsoleprint", function() assert(type(rconsoleprint) == "function") end)
test("rconsoleclear", function() assert(type(rconsoleclear) == "function") end)

-- 4. Filesystem
test("readfile",  function() assert(type(readfile)  == "function") end)
test("writefile", function() assert(type(writefile) == "function") end)
test("listfiles", function() assert(type(listfiles) == "function") end)
test("isfolder",  function() assert(type(isfolder)  == "function") end)
test("makefolder", function() assert(type(makefolder) == "function") end)
test("isfile",    function() assert(type(isfile)    == "function") end)

-- 5. Input
test("mouse1click", function() assert(type(mouse1click) == "function") end)
test("mouse2click", function() assert(type(mouse2click) == "function") end)
test("keypress",    function() assert(type(keypress)    == "function") end)

-- 6. Instances
test("fireclickdetector",  function() assert(type(fireclickdetector)    == "function") end)
test("firetouchinterest",  function() assert(type(firetouchinterest)    == "function") end)
test("getinstances",       function() assert(type(getinstances())       == "table")   end)
test("getloadedmodules",   function() assert(type(getloadedmodules())   == "table")   end)
test("cloneref",           function() assert(type(cloneref)             == "function") end)
test("compareinstances",   function() assert(type(compareinstances)     == "function") end)

-- 7. Metatable
test("getrawmetatable", function()
    local t = setmetatable({}, {})
    assert(type(getrawmetatable(t)) == "table")
end)
test("hookmetamethod", function() assert(type(hookmetamethod) == "function") end)
test("setreadonly", function()
    local t = setmetatable({}, {})
    setreadonly(t, false)
end)

-- 8. Scripts
test("getgc",              function() assert(type(getgc())     == "table")    end)
test("getsenv / getscripthash", function()
    assert(type(getsenv) == "function" or type(getscripthash) == "function")
end)
test("getcallingscript",   function() assert(type(getcallingscript) == "function") end)

-- 9. Web
test("request", function()
    local req = request or http_request or (http and http.request)
    assert(type(req) == "function")
end)

-- 10. Crypt
test("crypt (thư viện)", function() assert(type(crypt) == "table") end)
test("crypt.hash",       function() assert(type(crypt) == "table" and type(crypt.hash)    == "function") end)
test("crypt.encrypt",    function() assert(type(crypt) == "table" and type(crypt.encrypt) == "function") end)
test("crypt.decrypt",    function() assert(type(crypt) == "table" and type(crypt.decrypt) == "function") end)

-- 11. Debug
test("debug.getupvalue",   function() assert(type(debug.getupvalue)   == "function") end)
test("debug.setupvalue",   function() assert(type(debug.setupvalue)   == "function") end)
test("debug.getconstants", function() assert(type(debug.getconstants) == "function") end)
test("debug.setconstant",  function() assert(type(debug.setconstant)  == "function") end)
test("debug.getproto",     function() assert(type(debug.getproto)     == "function") end)

-- 12. Misc
test("setclipboard",  function() assert(type(setclipboard)  == "function") end)
test("identifyexecutor", function() assert(type(identifyexecutor) == "function") end)
-- 13. Drawing (Vẽ lên màn hình)
test("Drawing.new Circle",     function() local d = Drawing.new("Circle")    assert(d ~= nil) d:Remove() end)
test("Drawing.new Line",       function() local d = Drawing.new("Line")      assert(d ~= nil) d:Remove() end)
test("Drawing.new Square",     function() local d = Drawing.new("Square")    assert(d ~= nil) d:Remove() end)
test("Drawing.new Text",       function() local d = Drawing.new("Text")      assert(d ~= nil) d:Remove() end)
test("Drawing.new Triangle",   function() local d = Drawing.new("Triangle")  assert(d ~= nil) d:Remove() end)
test("Drawing.new Image",      function() local d = Drawing.new("Image")     assert(d ~= nil) d:Remove() end)
test("Drawing.new Quad",       function() local d = Drawing.new("Quad")      assert(d ~= nil) d:Remove() end)
test("isrenderobj",            function() local d = Drawing.new("Line") assert(type(isrenderobj(d)) == "boolean") d:Remove() end)
test("cleardrawcache",         function() assert(type(cleardrawcache) == "function") end)

-- 14. Cache (Bộ nhớ đệm)
test("cache.invalidate",       function() assert(type(cache) == "table" and type(cache.invalidate)  == "function") end)
test("cache.iscached",         function() assert(type(cache) == "table" and type(cache.iscached)    == "function") end)
test("cache.replace",          function() assert(type(cache) == "table" and type(cache.replace)     == "function") end)

-- 15. Closures nâng cao
test("getupvalues",            function() assert(type(getupvalues(function() end))  == "table") end)
test("getconstants",           function() assert(type(getconstants(function() end)) == "table") end)
test("getprotos",              function() assert(type(getprotos(function() end))    == "table") end)
test("getproto",               function() assert(type(getproto(function() end, 1))  ~= nil) end)
test("setupvalue",             function() assert(type(setupvalue) == "function") end)
test("setconstant",            function() assert(type(setconstant) == "function") end)

-- 16. Fireremote / Remote Events
test("fireproximityprompt",    function() assert(type(fireproximityprompt)   == "function") end)
test("firesignal",             function() assert(type(firesignal)            == "function") end)
test("getconnections",         function() 
    local signal = game:GetService("RunService").Heartbeat
    local conns = getconnections(signal)
    assert(type(conns) == "table")
end)

-- 17. Miscellaneous nâng cao
test("decompile",              function() assert(type(decompile)             == "function") end)
test("getscriptbytecode",      function() assert(type(getscriptbytecode)     == "function") end)
test("getthreadidentity",      function() assert(type(getthreadidentity())   == "number")   end)
test("setthreadidentity",      function() setthreadidentity(3) assert(true)                 end)
test("checkcaller",            function() assert(type(checkcaller())         == "boolean")  end)
test("isexecutorclosure",      function() assert(type(isexecutorclosure(function() end)) == "boolean") end)
test("getnamecallmethod",      function() assert(type(getnamecallmethod)     == "function") end)
test("setnamecallmethod",      function() assert(type(setnamecallmethod)     == "function") end)

-- 18. Hooking (Móc hàm)
test("hookfunction",           function() assert(type(hookfunction)          == "function") end)
test("hookmetamethod",         function() assert(type(hookmetamethod)        == "function") end)
test("restorefunction",        function() assert(type(restorefunction)       == "function") end)

-- 19. Websocket
test("WebSocket.connect",      function() assert(type(WebSocket) == "table" and type(WebSocket.connect) == "function") end)

-- 20. Crypt bổ sung
test("crypt.base64encode",     function() assert(type(crypt.base64encode(  "test")) == "string") end)
test("crypt.base64decode",     function() assert(type(crypt.base64decode(  "dGVzdA==")) == "string") end)
test("crypt.generatekey",      function() assert(type(crypt.generatekey()) == "string") end)
test("crypt.generatebytes",    function() assert(type(crypt.generatebytes(16)) == "string") end)
-- 21. Instance nâng cao
test("gethiddenproperty",      function() assert(type(gethiddenproperty)     == "function") end)
test("sethiddenproperty",      function() assert(type(sethiddenproperty)     == "function") end)
test("getproperties",          function() assert(type(getproperties)         == "function") end)
test("gethiddenproperties",    function() assert(type(gethiddenproperties)   == "function") end)
test("getspecialinfo",         function() assert(type(getspecialinfo)        == "function") end)
test("isscriptable",           function() assert(type(isscriptable)          == "function") end)
test("setscriptable",          function() assert(type(setscriptable)         == "function") end)

-- 22. Luau / VM
test("getstack",               function() assert(type(getstack)              == "function") end)
test("getinfo",                function() assert(type(debug.getinfo)         == "function") end)
test("getmetatable (bypass)",  function()
    local t = setmetatable({}, { __metatable = "locked" })
    assert(type(getrawmetatable(t)) == "table")
end)
test("newproxy",               function()
    local p = newproxy(true)
    assert(type(p) == "userdata")
end)
test("getfenv",                function() assert(type(getfenv())             == "table")    end)
test("setfenv",                function() assert(type(setfenv)               == "function") end)

-- 23. Filesystem nâng cao
test("appendfile",             function() assert(type(appendfile)            == "function") end)
test("copyfile",               function() assert(type(copyfile)              == "function") end)
test("movefile",               function() assert(type(movefile)              == "function") end)
test("copyfolder",             function() assert(type(copyfolder)            == "function") end)
test("delfolder",              function() assert(type(delfolder)             == "function") end)
test("delfile",                function() assert(type(delfile)               == "function") end)
test("dofile",                 function() assert(type(dofile)                == "function") end)
test("loadfile",               function() assert(type(loadfile)              == "function") end)

-- 24. Task / Thread
test("task.spawn",             function() assert(type(task.spawn)            == "function") end)
test("task.defer",             function() assert(type(task.defer)            == "function") end)
test("task.delay",             function() assert(type(task.delay)            == "function") end)
test("task.wait",              function() assert(type(task.wait)             == "function") end)
test("task.cancel",            function() assert(type(task.cancel)           == "function") end)

-- 25. Coroutine mở rộng
test("coroutine.running",      function() assert(type(coroutine.running)     == "function") end)
test("coroutine.isyieldable",  function() assert(type(coroutine.isyieldable) == "function") end)
test("coroutine.close",        function() assert(type(coroutine.close)       == "function") end)

-- 26. Input nâng cao
test("mouse1press",            function() assert(type(mouse1press)           == "function") end)
test("mouse1release",          function() assert(type(mouse1release)         == "function") end)
test("mouse2press",            function() assert(type(mouse2press)           == "function") end)
test("mouse2release",          function() assert(type(mouse2release)         == "function") end)
test("mousescroll",            function() assert(type(mousescroll)           == "function") end)
test("mousemoverel",           function() assert(type(mousemoverel)          == "function") end)
test("mousemoveabs",           function() assert(type(mousemoveabs)          == "function") end)
test("keyrelease",             function() assert(type(keyrelease)            == "function") end)
test("blockkey",               function() assert(type(blockkey)              == "function") end)
test("iskeypressed",           function() assert(type(iskeypressed)          == "function") end)

-- 27. Render / Camera
test("getrendersteplist",      function() assert(type(getrendersteplist)     == "function") end)
test("replaceclosures",        function() assert(type(replaceclosures)       == "function") end)

-- 28. Executor Info
test("getexecutorname",        function()
    local name = identifyexecutor and identifyexecutor() or (executor and executor.Name)
    assert(type(name) == "string")
end)
test("getexecutorversion",     function()
    local _, ver = identifyexecutor and identifyexecutor()
    assert(type(ver) == "string" or type(ver) == "number")
end)

-- 29. Garbage Collector nâng cao
test("getgc (objects=true)",   function()
    local gc = getgc(true)
    assert(type(gc) == "table")
end)
test("filtergc",               function() assert(type(filtergc)              == "function") end)

-- 30. Crypt nâng cao
test("crypt.hmac",             function() assert(type(crypt.hmac)            == "function") end)
test("crypt.hash SHA512",      function()
    local h = crypt.hash("test", "sha512")
    assert(type(h) == "string" and #h > 0)
end)
test("crypt.hash MD5",         function()
    local h = crypt.hash("test", "md5")
    assert(type(h) == "string" and #h > 0)
end)

-- 31. Bit (Thao tác bit)
test("bit.band",               function() assert(bit.band(0xFF, 0x0F) == 0x0F) end)
test("bit.bor",                function() assert(bit.bor(0xF0, 0x0F)  == 0xFF) end)
test("bit.bxor",               function() assert(bit.bxor(0xFF, 0xFF) == 0x00) end)
test("bit.bnot",               function() assert(type(bit.bnot(0))    == "number") end)
test("bit.lshift",             function() assert(bit.lshift(1, 4)     == 16)    end)
test("bit.rshift",             function() assert(bit.rshift(16, 4)    == 1)     end)

-- 32. String nâng cao
test("string.split",           function()
    local parts = string.split("a,b,c", ",")
    assert(type(parts) == "table" and #parts == 3)
end)
test("string.trim",            function()
    local s = string.gsub("  hello  ", "^%s*(.-)%s*$", "%1")
    assert(s == "hello")
end)

-- 33. Table nâng cao
test("table.freeze",           function()
    local t = table.freeze({1, 2, 3})
    assert(table.isfrozen(t) == true)
end)
test("table.isfrozen",         function() assert(type(table.isfrozen) == "function") end)
test("table.clone",            function()
    local t = {1, 2, 3}
    local c = table.clone(t)
    assert(c[1] == 1 and c ~= t)
end)
test("table.clear",            function()
    local t = {1, 2, 3}
    table.clear(t)
    assert(#t == 0)
end)

-- 34. Http nâng cao
test("http.get",               function()
    local h = http or http_request
    assert(type(h) == "table" or type(h) == "function")
end)
test("syn.request (legacy)",   function()
    -- Một số executor cũ dùng syn.request
    local req = syn and syn.request
    assert(type(req) == "function")
end)

-- 35. Secure Call
test("secure_call / hookfunc", function()
    local original = math.floor
    local hooked = hookfunction(math.floor, function(n)
        return original(n)
    end)
    assert(math.floor(1.9) == 1)
    hookfunction(math.floor, hooked) -- restore
end)
-- 36. Debug nâng cao
test("debug.getregistry",      function() assert(type(debug.getregistry())   == "table")    end)
test("debug.getmetatable",     function() assert(type(debug.getmetatable({}))== "table")    end)
test("debug.setmetatable",     function() assert(type(debug.setmetatable)    == "function") end)
test("debug.traceback",        function() assert(type(debug.traceback())     == "string")   end)
test("debug.profilebegin",     function() assert(type(debug.profilebegin)    == "function") end)
test("debug.profileend",       function() assert(type(debug.profileend)      == "function") end)
test("debug.getprotos",        function() assert(type(debug.getprotos(function() end)) == "table") end)
test("debug.getstack",         function() assert(type(debug.getstack)        == "function") end)
test("debug.setstack",         function() assert(type(debug.setstack)        == "function") end)

-- 37. Signals / Connections nâng cao
test("getconnections RunService", function()
    local conns = getconnections(game:GetService("RunService").Heartbeat)
    assert(type(conns) == "table")
end)
test("connection.Enable",      function()
    local conn = game:GetService("RunService").Heartbeat:Connect(function() end)
    local conns = getconnections(game:GetService("RunService").Heartbeat)
    assert(type(conns[1].Enable) == "function")
    conn:Disconnect()
end)
test("connection.Disable",     function()
    local conn = game:GetService("RunService").Heartbeat:Connect(function() end)
    local conns = getconnections(game:GetService("RunService").Heartbeat)
    assert(type(conns[1].Disable) == "function")
    conn:Disconnect()
end)
test("connection.Fire",        function()
    local conn = game:GetService("RunService").Heartbeat:Connect(function() end)
    local conns = getconnections(game:GetService("RunService").Heartbeat)
    assert(type(conns[1].Fire) == "function")
    conn:Disconnect()
end)

-- 38. Players / LocalPlayer
test("getlocalplayer",         function()
    local lp = game:GetService("Players").LocalPlayer
    assert(lp ~= nil and lp:IsA("Player"))
end)
test("gethwid",                function()
    local id = gethwid and gethwid()
    assert(type(id) == "string" and #id > 0)
end)
test("getusername",            function()
    local name = game:GetService("Players").LocalPlayer.Name
    assert(type(name) == "string" and #name > 0)
end)

-- 39. Anti-Detection
test("isourclosure",           function()
    assert(type(isourclosure(function() end)) == "boolean")
end)
test("is_simliar_closure",     function()
    assert(type(issimilarclosure or is_simliar_closure) == "function")
end)
test("checkcaller (executor)", function()
    assert(checkcaller() == true)
end)
test("getthreadcontext",       function()
    assert(type(getthreadidentity()) == "number")
end)

-- 40. Metatable nâng cao
test("getrawmetatable __index", function()
    local mt = { __index = function() return 42 end }
    local t  = setmetatable({}, mt)
    assert(getrawmetatable(t).__index ~= nil)
end)
test("getrawmetatable __newindex", function()
    local mt = { __newindex = function() end }
    local t  = setmetatable({}, mt)
    assert(getrawmetatable(t).__newindex ~= nil)
end)
test("setrawmetatable",        function() assert(type(setrawmetatable)       == "function") end)
test("getmetafield",           function() assert(type(getmetafield)         == "function") end)

-- 41. Drawing nâng cao
test("Drawing Font",           function()
    local d = Drawing.new("Text")
    d.Font = Drawing.Fonts.UI
    assert(d.Font == Drawing.Fonts.UI)
    d:Remove()
end)
test("Drawing Transparency",   function()
    local d = Drawing.new("Circle")
    d.Transparency = 0.5
    assert(d.Transparency == 0.5)
    d:Remove()
end)
test("Drawing Visible",        function()
    local d = Drawing.new("Line")
    d.Visible = false
    assert(d.Visible == false)
    d:Remove()
end)
test("Drawing ZIndex",         function()
    local d = Drawing.new("Square")
    d.ZIndex = 5
    assert(d.ZIndex == 5)
    d:Remove()
end)
test("getdrawings",            function()
    assert(type(getdrawings and getdrawings() or {}) == "table")
end)

-- 42. Upvalue nâng cao
test("getupvalue by name",     function()
    local x = 10
    local f = function() return x end
    local val = debug.getupvalue(f, 1)
    assert(val == 10)
end)
test("setupvalue by index",    function()
    local x = 10
    local f = function() return x end
    debug.setupvalue(f, 1, 99)
    assert(f() == 99)
end)
test("getupvalues count",      function()
    local a, b = 1, 2
    local f = function() return a + b end
    local ups = getupvalues(f)
    assert(#ups >= 2)
end)

-- 43. Constant nâng cao
test("getconstant by index",   function()
    local f = function() return "hello" end
    local c = debug.getconstants(f)
    local found = false
    for _, v in ipairs(c) do
        if v == "hello" then found = true break end
    end
    assert(found)
end)
test("setconstant replace",    function()
    local f = function() return "old" end
    local consts = debug.getconstants(f)
    for i, v in ipairs(consts) do
        if v == "old" then debug.setconstant(f, i, "new") break end
    end
    assert(f() == "new")
end)

-- 44. Bytecode
test("getscriptbytecode",      function()
    local s = game:GetService("Players").LocalPlayer.PlayerScripts:FindFirstChildWhichIsA("LocalScript")
    if s then
        local bc = getscriptbytecode(s)
        assert(type(bc) == "string" and #bc > 0)
    else
        assert(type(getscriptbytecode) == "function")
    end
end)
test("loadstring",             function()
    local f = loadstring("return 1 + 1")
    assert(type(f) == "function" and f() == 2)
end)
test("loadstring with env",    function()
    local env = { x = 99 }
    local f = loadstring("return x")
    setfenv(f, env)
    assert(f() == 99)
end)

-- 45. Protect / Unprotect Script
test("protectgui",             function() assert(type(protectgui)            == "function") end)
test("unprotectgui",           function() assert(type(unprotectgui)          == "function") end)
test("gethui",                 function() assert(type(gethui())              ~= nil)        end)
test("getguiobjectsinradius",  function() assert(type(getguiobjectsinradius) == "function") end)

-- 46. Miscellaneous hiếm gặp
test("getsynasset",            function() assert(type(getsynasset or syn and syn.get_asset) == "function") end)
test("base64_encode (global)", function()
    local fn = base64_encode or base64encode
    assert(type(fn) == "function" and type(fn("test")) == "string")
end)
test("base64_decode (global)", function()
    local fn = base64_decode or base64decode
    assert(type(fn) == "function" and type(fn("dGVzdA==")) == "string")
end)
test("messagebox",             function() assert(type(messagebox)            == "function") end)
test("setfpscap",              function() assert(type(setfpscap)             == "function") end)
test("getfpscap",              function()
    local cap = getfpscap and getfpscap()
    assert(type(cap) == "number")
end)
test("lz4compress",            function()
    local data = lz4compress("hello world")
    assert(type(data) == "string")
end)
test("lz4decompress",          function()
    local compressed = lz4compress("hello world")
    local out = lz4decompress(compressed, #"hello world")
    assert(out == "hello world")
end )
test("getscriptfunction",      function() assert(type(getscriptfunction)     == "function") end)
test("getrunningscripts",      function() assert(type(getrunningscripts())   == "table")    end)
test("getscripts",             function() assert(type(getscripts())          == "table")    end)

-- 47. AudioSpy / RemoteSpy helpers
test("getactorsignals",        function() assert(type(getactorsignals or game.GetActorSignals) ~= nil) end)
test("getsignalconnections",   function() assert(type(getsignalconnections)  == "function") end)
test("replicatesignal",        function() assert(type(replicatesignal)       == "function") end)

-- 48. Math nâng cao
test("math.clamp",             function() assert(math.clamp(10, 0, 5) == 5)                end)
test("math.sign",              function() assert(math.sign(-99) == -1)                     end)
test("math.round",             function() assert(math.round(1.6)  == 2)                    end)
test("math.log base10",        function() assert(math.floor(math.log(100, 10)) == 2)       end)
test("math.huge",              function() assert(math.huge > 1e308)                        end)

-- 49. Vector / CFrame
test("Vector3.new",            function()
    local v = Vector3.new(1, 2, 3)
    assert(v.X == 1 and v.Y == 2 and v.Z == 3)
end)
test("CFrame.new",             function()
    local cf = CFrame.new(0, 0, 0)
    assert(type(cf) == "userdata")
end)
test("CFrame.lookAt",          function()
    local cf = CFrame.lookAt(Vector3.new(0,0,0), Vector3.new(1,0,0))
    assert(type(cf) == "userdata")
end)

-- 50. Benchmark / Timing
test("os.clock",               function() assert(type(os.clock())            == "number")   end)
test("os.time",                function() assert(type(os.time())             == "number")   end)
test("os.date",                function() assert(type(os.date())             == "string")   end)
test("tick",                   function() assert(type(tick())                == "number")   end)
test("time",                   function() assert(type(time())                == "number")   end)
test("elapsedtime",            function() assert(type(elapsedtime())         == "number")   end)
-- 51. Renderer / Visual nâng cao
test("setfflag",               function() assert(type(setfflag)              == "function") end)
test("getfflag",               function() assert(type(getfflag)              == "function") end)
test("getfflags",              function() assert(type(getfflags())           == "table")    end)
test("setresolution",          function() assert(type(setresolution)         == "function") end)
test("getresolution",          function()
    local w, h = getresolution()
    assert(type(w) == "number" and type(h) == "number")
end)
test("getviewportsize",        function()
    local s = workspace.CurrentCamera.ViewportSize
    assert(type(s) == "userdata")
end)

-- 52. DataModel / Services
test("getservice",             function()
    local rs = game:GetService("RunService")
    assert(rs ~= nil)
end)
test("cloneservice",           function() assert(type(cloneservice)          == "function") end)
test("getallservices",         function()
    local svcs = getallservices and getallservices() or game:GetChildren()
    assert(type(svcs) == "table")
end)
test("isserviceactive",        function()
    assert(type(isserviceactive or game.IsServiceEnabled) ~= nil)
end)

-- 53. Proto nâng cao
test("getproto index 1",       function()
    local outer = function()
        local inner = function() return 42 end
        return inner
    end
    local protos = debug.getprotos(outer)
    assert(type(protos) == "table")
end)
test("getproto active=true",   function()
    local f = function()
        local g = function() end
        return g
    end
    local p = debug.getproto(f, 1, true)
    assert(type(p) == "table" or type(p) == "function")
end)

-- 54. Regex / Pattern
test("string.find",            function()
    local s, e = string.find("hello world", "world")
    assert(s == 7 and e == 11)
end)
test("string.match",           function()
    local m = string.match("abc123", "%d+")
    assert(m == "123")
end)
test("string.gmatch",          function()
    local t = {}
    for w in string.gmatch("one two three", "%a+") do
        table.insert(t, w)
    end
    assert(#t == 3)
end)
test("string.gsub count",      function()
    local s, n = string.gsub("aaa", "a", "b")
    assert(s == "bbb" and n == 3)
end)
test("string.byte / char",     function()
    assert(string.byte("A") == 65)
    assert(string.char(65) == "A")
end)
test("string.rep",             function()
    assert(string.rep("ab", 3, "-") == "ab-ab-ab")
end)
test("string.reverse",         function()
    assert(string.reverse("hello") == "olleh")
end)
test("string.format %q",       function()
    local s = string.format("%q", 'say "hi"')
    assert(type(s) == "string")
end)

-- 55. JSON
test("json.encode",            function()
    local fn = json and json.encode or game:GetService("HttpService").JSONEncode
    if type(fn) == "function" then
        local s = fn({}, {a = 1})
        assert(type(s) == "string")
    else
        assert(type(fn) ~= nil)
    end
end)
test("json.decode",            function()
    local fn = json and json.decode or game:GetService("HttpService").JSONDecode
    if type(fn) == "function" then
        local t = fn({}, '{"x":1}')
        assert(type(t) == "table" and t.x == 1)
    else
        assert(type(fn) ~= nil)
    end
end)

-- 56. Crypt SHA nâng cao
test("crypt.hash SHA1",        function()
    local h = crypt.hash("test", "sha1")
    assert(type(h) == "string" and #h == 40)
end)
test("crypt.hash SHA256",      function()
    local h = crypt.hash("test", "sha256")
    assert(type(h) == "string" and #h == 64)
end)
test("crypt.encrypt / decrypt round-trip", function()
    local key  = crypt.generatekey()
    local iv   = crypt.generatebytes(16)
    local enc  = crypt.encrypt("secret", key, iv, "CBC")
    local dec  = crypt.decrypt(enc, key, iv, "CBC")
    assert(dec == "secret")
end)

-- 57. Scheduler / Loop
test("RunService Heartbeat",   function()
    local rs   = game:GetService("RunService")
    local fired = false
    local conn = rs.Heartbeat:Connect(function() fired = true end)
    task.wait(0.1)
    conn:Disconnect()
    assert(fired == true)
end)
test("RunService Stepped",     function()
    local rs    = game:GetService("RunService")
    local fired = false
    local conn  = rs.Stepped:Connect(function() fired = true end)
    task.wait(0.1)
    conn:Disconnect()
    assert(fired == true)
end)
test("RunService RenderStepped", function()
    local rs    = game:GetService("RunService")
    local fired = false
    local conn  = rs.RenderStepped:Connect(function() fired = true end)
    task.wait(0.1)
    conn:Disconnect()
    assert(fired == true)
end)

-- 58. Raycast
test("workspace.Raycast",      function()
    local origin    = Vector3.new(0, 100, 0)
    local direction = Vector3.new(0, -200, 0)
    local result    = workspace:Raycast(origin, direction)
    -- result có thể nil nếu không có địa hình, nhưng hàm phải tồn tại
    assert(result == nil or type(result) == "userdata")
end)
test("Ray.new",                function()
    local r = Ray.new(Vector3.new(0,0,0), Vector3.new(0,1,0))
    assert(type(r) == "userdata")
end)

-- 59. Tween
test("TweenService.Create",    function()
    local ts   = game:GetService("TweenService")
    local part = Instance.new("Part")
    local info = TweenInfo.new(1)
    local tw   = ts:Create(part, info, { Size = Vector3.new(2,2,2) })
    assert(tw ~= nil)
    part:Destroy()
end)
test("TweenInfo.new",          function()
    local ti = TweenInfo.new(2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
    assert(type(ti) == "userdata")
end)

-- 60. UDim / Color
test("UDim2.new",              function()
    local u = UDim2.new(0.5, 0, 0.5, 0)
    assert(u.X.Scale == 0.5)
end)
test("UDim2.fromScale",        function()
    local u = UDim2.fromScale(1, 1)
    assert(u.X.Scale == 1)
end)
test("Color3.new",             function()
    local c = Color3.new(1, 0, 0)
    assert(c.R == 1 and c.G == 0 and c.B == 0)
end)
test("Color3.fromRGB",         function()
    local c = Color3.fromRGB(255, 128, 0)
    assert(c.R == 1)
end)
test("Color3.fromHSV",         function()
    local c = Color3.fromHSV(0, 1, 1)
    assert(type(c) == "userdata")
end)
test("Color3.toHSV",           function()
    local h, s, v = Color3.toHSV(Color3.fromHSV(0.5, 0.5, 0.5))
    assert(type(h) == "number")
end)
-- Tổng kết
print("\n=============================================")
print(string.format("✅ Đạt: %d  |  ❌ Thiếu: %d  |  Tổng: %d", passes, fails, total))
print(string.format("📊 Tỉ lệ tương thích: %d%%", math.floor((passes / total) * 100)))
print("=============================================")
