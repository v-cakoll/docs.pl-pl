---
ms.openlocfilehash: 7252936bd716752208abc54b4ae4bc9e23be092f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665690"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>.NET współdziałanie będzie teraz QueryInterface dla IAgileObject (interfejs WinRT)

|   |   |
|---|---|
|Szczegóły|Korzystając z delegatem .NET zdarzeń WinRT, Windows będzie QI dla IAgileObject począwszy od .NET Framework 4.8.  W poprzednich wersjach programu .NET Framework środowisko uruchomieniowe może zakończyć się niepowodzeniem tego QI, a nie być subskrybowane zdarzenia.<ul><li>[x] quirked</li></ul>|
|Sugestia|Włączanie QI IAgileObject podziału wykonywania, można wyłączyć ten kod, ustawiając następującą konfigurację. <h4>Metoda 1. Zmienna środowiskowa</h4> Ustaw następujące zmiennej środowiska: COMPLUS_DisableCCWSupportIAgileObject = 1Ten metoda ma wpływ na dowolnym środowisku, która dziedziczy tej zmiennej środowiskowej. Może to być tylko jednej konsoli sesji lub może wpłynąć na całą maszynę, jeśli wartość zmiennej środowiskowej globalnie. Zmienna środowiskowa nie jest rozróżniana wielkość liter. <h4>Metoda 2. Rejestr</h4> Za pomocą Edytora rejestru (regedit.exe), Znajdź jedną z następujących subkeys:HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER\SOFTWARE\Microsoft.NETFrameworkThen dodać nazwę następujące czynności: wartości: Typ DisableCCWSupportIAgileObject: DWORD (32-bitowy) (nazywane również REG_WORD) wartość: 1Nie można użyć Windows REG. Narzędzie EXE, aby dodać tę wartość przy użyciu środowiska wiersza polecenia lub skryptów. Na przykład:<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>W tym przypadku <code>HKLM</code> jest używana zamiast <code>HKEY_LOCAL_MACHINE</code>. Użyj <code>reg add /?</code> Aby wyświetlić Pomoc dotyczącą składni. Nazwa wartości rejestru nie jest rozróżniana wielkość liter.|
|Zakres|Krawędź|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
