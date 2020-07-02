---
ms.openlocfilehash: 22b5abbe769733e8d5ca3e78dd9e6e13b2363737
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620308"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>Cofnięcie zgody na przywrócenie z różnych 4,5 generacji SQL do 4,0 prostszej generacji SQL

#### <a name="details"></a>Szczegóły

Zapytania, które tworzą instrukcje JOIN i zawierają wywołanie operacji ograniczającej bez wcześniejszego użycia polecenia OrderBy teraz generują prostsze SQL. Po uaktualnieniu do .NET Framework 4,5 te zapytania wygenerowały bardziej skomplikowane SQL niż poprzednie wersje.

#### <a name="suggestion"></a>Sugestia

Ta funkcja jest domyślnie wyłączona. Jeśli Entity Framework generuje dodatkowe instrukcje JOIN, które powodują spadek wydajności, możesz włączyć tę funkcję, dodając następujący wpis do <code>&lt;appSettings&gt;</code> sekcji pliku konfiguracji aplikacji (app.config):<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Przezroczyste|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe|
