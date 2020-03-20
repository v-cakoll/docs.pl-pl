---
ms.openlocfilehash: e5d81d791e1a2f1a2dbdafc787dec1227423883d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803263"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>Zrezygnuj z przerwy, aby powrócić z różnych generacji SQL 4.5 do prostszego generowania SQL 4.0

|   |   |
|---|---|
|Szczegóły|Kwerendy, które produkują join instrukcji i zawierają wywołanie operacji ograniczania bez uprzedniego użycia OrderBy teraz produkować prostsze SQL. Po uaktualnieniu do programu .NET Framework 4.5 te zapytania wywołały bardziej skomplikowany sql niż poprzednie wersje.|
|Sugestia|Ta funkcja jest domyślnie wyłączona. Jeśli entity framework generuje dodatkowe instrukcje JOIN, które powodują obniżenie wydajności, można <code>&lt;appSettings&gt;</code> włączyć tę funkcję, dodając następujący wpis do sekcji pliku konfiguracji aplikacji (app.config):<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Przezroczyste|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe|
