---
ms.openlocfilehash: 824d75585efd40937c1a48376ec7862cba1a8fa3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235604"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>NullReferenceException w kodzie obsługi wyjątków z ImageSourceConverter.ConvertFrom

|   |   |
|---|---|
|Szczegóły|Błąd w kodzie obsługi <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> wyjątków <xref:System.NullReferenceException?displayProperty=name> spowodował, że zamiast zamierzonego <xref:System.IO.DirectoryNotFoundException?displayProperty=name> <xref:System.IO.FileNotFoundException?displayProperty=name>wyjątku ( lub ). Ta zmiana poprawia ten błąd, tak aby metoda teraz zgłasza odpowiedni wyjątek. <p/>Domyślnie wszystkie aplikacje przeznaczone dla platformy .NET Framework 4.6.2 i wcześniej nadal zgłaszają <xref:System.NullReferenceException?displayProperty=name> się ze zgodnością. Deweloperzy kierowani na program .NET Framework 4.7 i powyżej powinni zobaczyć odpowiednie wyjątki.|
|Sugestia|Deweloperzy, którzy chcą <xref:System.NullReferenceException?displayProperty=name> powrócić do uzyskiwania podczas kierowania .NET Framework 4.7 lub nowszych można dodać/scalić następujące do pliku App.config aplikacji:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Brzeg|
|Wersja|4.7|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|
