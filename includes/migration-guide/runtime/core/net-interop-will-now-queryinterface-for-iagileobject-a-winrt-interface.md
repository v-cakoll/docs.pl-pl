---
ms.openlocfilehash: 0036fc2b03dde64d24d883e55b9f00c931f0c218
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997682"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>.NET Interop będzie teraz QueryInterface dla IAgileObject (interfejs WinRT)

|   |   |
|---|---|
|Szczegóły|Podczas korzystania ze zdarzenia WinRT z delegatem .NET, system Windows będzie QI dla IAgileObject począwszy od .NET Framework 4.8.  W poprzednich wersjach programu .NET Framework środowisko wykonawcze zakończy się niepowodzeniem tego QI i nie można subskrybować zdarzenia.<ul><li>[ x ] Dziwaczne</li></ul>|
|Sugestia|Jeśli włączenie QI dla IAgileObject przerywa wykonywanie, można wyłączyć ten kod, ustawiając następującą konfigurację. <h4>Metoda 1: Zmienna środowiskowa</h4> Ustaw następującą zmienną środowiskową:COMPLUS_DisableCCWSupportIAgileObject=1Najedna metoda wpływa na każde środowisko, które dziedziczy tę zmienną środowiskową. Może to być tylko pojedyncza sesja konsoli lub może mieć wpływ na cały komputer, jeśli ustawisz zmienną środowiskową globalnie. W nazwie zmiennej środowiskowej nie jest rozróżniana wielkość liter. <h4>Metoda 2: Rejestr</h4> Za pomocą Edytora rejestru (regedit.exe) znajdź jeden z następujących podkluczy:HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER\SOFTWARE\Microsoft.NETFrameworkNastępnie dodaj następującą nazwę:Nazwa: DisableCCWSupportIAgileObject Typ: DWORD (32-bitowy) Wartość (nazywana również REG_WORD) Wartość: 1Mówkasz użyć reg systemu Windows. Narzędzie EXE do dodawania tej wartości ze środowiska wiersza polecenia lub skryptów. Przykład:<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>W takim <code>HKLM</code> przypadku jest używany <code>HKEY_LOCAL_MACHINE</code>zamiast . Użyj, <code>reg add /?</code> aby wyświetlić pomoc dotyczącą tej składni. W nazwie wartości rejestru nie jest rozróżniana wielkość liter.|
|Zakres|Brzeg|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
