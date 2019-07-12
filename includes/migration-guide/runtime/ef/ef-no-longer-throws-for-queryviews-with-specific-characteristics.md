---
ms.openlocfilehash: bc33266bb2af639d7d0d1cb532ed73abd7f1ba9a
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803270"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a>EF nie zgłasza już dla QueryViews o konkretnych cechach

|   |   |
|---|---|
|Szczegóły|Entity Framework nie zgłasza już <xref:System.StackOverflowException?displayProperty=name> wyjątku, gdy aplikacja wykonuje kwerendę, która obejmuje QueryView o od 0 do 1 właściwość nawigacji, który próbuje dołączyć powiązane obiekty jako część zapytania. Na przykład przez wywołanie metody <code>.Include(e =&gt; e.RelatedNavProp)</code>.|
|Sugestia|Ta zmiana ma wpływ tylko na kod, który używa QueryViews z 1-od 0 do 1 relacje podczas uruchamiania zapytania to wywołanie. Obejmują. Ona zwiększa niezawodność i powinny być przezroczyste do niemal wszystkich aplikacji. Jednak jeśli spowoduje wygenerowanie nieoczekiwanego zachowania, można je wyłączyć, dodając następujący wpis do <code>&lt;appSettings&gt;</code> sekcję pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>|
|Scope|Krawędź|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe|

