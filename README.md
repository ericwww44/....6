local Settings = {
    JoinTeam = "Pirates", -- Pirates / Marines
    Translator = true     -- true / false
}

-- Validação dos valores
local validTeams = { Pirates = true, Marines = true }
if not validTeams[Settings.JoinTeam] then
    warn("[ERRO] JoinTeam inválido. Use 'Pirates' ou 'Marines'.")
    return
end

if type(Settings.Translator) ~= "boolean" then
    warn("[ERRO] Translator deve ser true ou false.")
    return
end

-- Carregamento seguro do script externo
local success, scriptCode = pcall(function()
    return game:HttpGet("https://raw.githubusercontent.com/tlredz/Scripts/refs/heads/main/main.luau")
end)

if success then
    local runScript = loadstring(scriptCode)
    if typeof(runScript) == "function" then
        runScript(Settings)
    else
        warn("[ERRO] Falha ao compilar o script carregado.")
    end
else
    warn("[ERRO] Falha ao buscar o script externo: " .. tostring(scriptCode))
end# ....6
I
