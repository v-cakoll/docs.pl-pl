---
ms.openlocfilehash: 9c72bc686e014a0bffdf272e3813358d1b29cc66
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65199309"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET, COM pomyślnie kieruje parametrów ByRef SafeArray zdarzeń

|   |   |
|---|---|
|Szczegóły|.NET Framework 4.7.2 i wcześniejszych wersjach, ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parametrem w zdarzenia modelu COM może zakończyć się niepowodzeniem do organizowania powrót do kodu natywnego.  Dzięki tej zmianie [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) teraz jest organizowana pomyślnie.<ul><li>[x] quirked</li></ul>|
|Sugestia|Jeśli poprawnie marshaling parametrów ByRef SafeArray zdarzeń COM przerywa wykonywanie, możesz wyłączyć ten kod, dodając następujący przełącznik konfiguracji do pliku config aplikacji:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Scope|Mały|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
