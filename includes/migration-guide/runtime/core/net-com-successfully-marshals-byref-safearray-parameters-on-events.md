---
ms.openlocfilehash: 2f4f92c8615b328caee2ad0b90028c76048026f4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802647"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET, COM pomyślnie kieruje parametrów ByRef SafeArray zdarzeń

|   |   |
|---|---|
|Szczegóły|.NET Framework 4.7.2 i wcześniejszych wersjach, ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parametrem w zdarzenia modelu COM może zakończyć się niepowodzeniem do organizowania powrót do kodu natywnego.  Dzięki tej zmianie [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) teraz jest skierowany pomyślnie.<ul><li>[x] quirked</li></ul>|
|Sugestia|Jeśli poprawnie kierowania parametrów ByRef SafeArray zdarzeń COM przerywa wykonywanie, możesz wyłączyć ten kod, dodając następujący przełącznik konfiguracji do pliku config aplikacji:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Scope|Mały|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|

