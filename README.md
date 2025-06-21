# Bypassed-Virage-Macro
I just bypass virage macro for fun even though I don't play grow a garden anymore

I know making this stuff will make Virage Developers make the security even harder but they just add code and code is really easy to remove

Even though this looks sus I'm more dumb than a normal person so I dont even know how to put malware on this stuff, like getting malware from script/code looks pretty hard to make, I'm not onto that stuff. I don't even code, I just remove codes to get stuff for free 🤑🤑🤑🤑🤑🤑


if you dont trust me just remove


function1(username) {
    global GAME_PASS_ID
    username := Trim(username)

    reqBody := "{""usernames"":[""" username """],""excludeBannedUsers"":true}"
    whr := ComObjCreate("WinHttp.WinHttpRequest.5.1")
    whr.Open("POST","https://users.roblox.com/v1/usernames/users",false)
    whr.SetRequestHeader("Content-Type","application/json")
    whr.Send(reqBody),  whr.WaitForResponse()
    if (whr.Status!=200 || !RegExMatch(whr.ResponseText,"""id"":\s*(\d+)",m))
        return 0
    userId := m1

    ownURL := "https://inventory.roblox.com/v1/users/" userId
           .  "/items/GamePass/" GAME_PASS_ID
    whr2 := ComObjCreate("WinHttp.WinHttpRequest.5.1")
    whr2.Open("GET",ownURL,false), whr2.Send(), whr2.WaitForResponse()
    if (whr2.Status!=200)                        ; request itself failed
        return 0

    return !RegExMatch(whr2.ResponseText, """data"":\s*\[\s*\]")
}


IniRead, isVerified, %settingsFile%, Main, %VERIFIED_KEY%, 0
if (!isVerified) {
    InputBox, rbUser, Premium Access, Please enter your Roblox username:
    if (ErrorLevel)
        ExitApp   ; user cancelled

    if (function1(rbUser)) {
        IniWrite, 1,              %settingsFile%, Main, %VERIFIED_KEY%
        IniWrite, %rbUser%,       %settingsFile%, Main, VerifiedUsername
        MsgBox, 0, Success, Verification successful, enjoy the macro!
    } else {
        MsgBox, 16, Access Denied, Sorry, that account does not own the required game-pass.
        ExitApp
    }
}
