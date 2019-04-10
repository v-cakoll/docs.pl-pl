---
ms.openlocfilehash: 705e1a22b8a5791c1103dd374a8bab19356cadfb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236656"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a>EF nie zgłasza już dla QueryViews o konkretnych cechach

|   |   |
|---|---|
|Szczegóły|Entity Framework nie zgłasza już <xref:System.StackOverflowException?displayProperty=name> wyjątku, gdy aplikacja wykonuje kwerendę, która obejmuje QueryView o od 0 do 1 właściwość nawigacji, który próbuje dołączyć powiązane obiekty jako część zapytania. Na przykład przez wywołanie metody <code>.Include(e =&gt; e.RelatedNavProp)</code>.|
|Sugestia|Ta zmiana ma wpływ tylko na kod, który używa QueryViews z 1-od 0 do 1 relacje podczas uruchamiania zapytania to wywołanie. Obejmują. Ona zwiększa niezawodność i powinny być przezroczyste do niemal wszystkich aplikacji. Jednak jeśli spowoduje wygenerowanie nieoczekiwanego zachowania, można je wyłączyć, dodając następujący wpis do <code>&lt;appSettings&gt;</code> sekcję pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe|
