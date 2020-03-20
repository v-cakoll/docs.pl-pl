---
ms.openlocfilehash: 705e1a22b8a5791c1103dd374a8bab19356cadfb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803270"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a>EF nie zgłasza już dla QueryViews o określonych cechach

|   |   |
|---|---|
|Szczegóły|Entity Framework nie zgłasza <xref:System.StackOverflowException?displayProperty=name> już wyjątek, gdy aplikacja wykonuje kwerendę, która obejmuje QueryView z 0..1 właściwości nawigacji, która próbuje dołączyć jednostek powiązanych jako część kwerendy. Na przykład, <code>.Include(e =&gt; e.RelatedNavProp)</code>dzwoniąc .|
|Sugestia|Ta zmiana dotyczy tylko kodu, który używa QueryViews z relacjami 1-0..1 podczas uruchamiania kwerend wywołujących . Obejmują. Poprawia niezawodność i powinna być przejrzysta dla prawie wszystkich aplikacji. Jeśli jednak powoduje to nieoczekiwane zachowanie, można je wyłączyć, dodając następujący wpis do <code>&lt;appSettings&gt;</code> sekcji pliku konfiguracyjnego aplikacji:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Brzeg|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe|
