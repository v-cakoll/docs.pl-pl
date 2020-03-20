---
ms.openlocfilehash: 6ff23bbe8c48235770d39cb7d35a1df7de6c5201
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "68440279"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM pomyślnie marszałków ByRef SafeArray parametry na zdarzenia

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.7.2 i wcześniejszych wersjach ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parametru w przypadku COM nie można zorganizować z powrotem do kodu macierzystego.  Dzięki tej zmianie [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) jest teraz kierowane pomyślnie.<ul><li>[ x ] Dziwaczne</li></ul>|
|Sugestia|Jeśli poprawnie kierowanie ByRef SafeArray parametry na zdarzenia COM przerywa wykonywanie, można wyłączyć ten kod, dodając następujący przełącznik konfiguracji do konfiguracji aplikacji:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
