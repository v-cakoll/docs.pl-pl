---
ms.openlocfilehash: 0036fc2b03dde64d24d883e55b9f00c931f0c218
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997682"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>Platforma .NET Interop będzie teraz w języku QueryInterface dla IAgileObject (interfejs WinRT)

|   |   |
|---|---|
|Szczegóły|W przypadku użycia zdarzenia WinRT z delegatem platformy .NET system Windows będzie QI do IAgileObject, począwszy od .NET Framework 4,8.  W poprzednich wersjach .NET Framework środowisko uruchomieniowe zakończy się niepowodzeniem i nie będzie mogło subskrybować tego zdarzenia.<ul><li>[x] Quirked</li></ul>|
|Sugestia|W przypadku włączenia QI na potrzeby wykonywania przerwań IAgileObject można wyłączyć ten kod, ustawiając poniższą konfigurację. <h4>Metoda 1: Zmienna środowiskowa</h4> Ustaw następujące zmienne środowiskowe: COMPLUS_DisableCCWSupportIAgileObject = 1This Metoda ma wpływ na dowolne środowisko, które dziedziczy tę zmienną środowiskową. Może to być tylko jedna sesja konsoli lub może mieć wpływ na całą maszynę, jeśli zmienna środowiskowa jest ustawiona globalnie. W nazwie zmiennej środowiskowej nie jest rozróżniana wielkość liter. <h4>Metoda 2. Rejestr</h4> Korzystając z edytora rejestru (regedit. exe), Znajdź jeden z następujących podkluczy: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER\SOFTWARE\Microsoft.NETFrameworkThen Dodaj następujące: value Name: Typ DisableCCWSupportIAgileObject: Wartość DWORD (32-bitowa) (zwana również REG_WORD): 1You może używać systemu Windows REG. Narzędzie EXE do dodawania tej wartości z poziomu wiersza polecenia lub skryptów. Przykład:<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>W tym przypadku <code>HKLM</code> jest używany <code>HKEY_LOCAL_MACHINE</code>zamiast. Użyj <code>reg add /?</code> , aby wyświetlić pomoc dotyczącą tej składni. W nazwie wartości rejestru nie jest rozróżniana wielkość liter.|
|Scope|Krawędź|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
