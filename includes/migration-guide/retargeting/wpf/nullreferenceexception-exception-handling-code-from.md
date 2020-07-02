---
ms.openlocfilehash: 9c9c4ec55143ef991e9b69a389e0f3368263bb4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614847"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>NullReferenceException w kodzie obsługującym wyjątek z ImageSourceConverter. ConvertFrom

#### <a name="details"></a>Szczegóły

Błąd w kodzie obsługi wyjątku dla <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> spowodowany błędem <xref:System.NullReferenceException?displayProperty=fullName> został zgłoszony, zamiast zamierzonego wyjątku ( <xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> lub <xref:System.IO.FileNotFoundException?displayProperty=fullName> ). Ta zmiana koryguje ten błąd, aby Metoda teraz wyrzucał właściwy wyjątek. <p/>Domyślnie wszystkie aplikacje ukierunkowane na .NET Framework 4.6.2 i poprzednie nadal generują <xref:System.NullReferenceException?displayProperty=fullName> zgodność. Deweloperzy ukierunkowani na .NET Framework 4,7 i nowsze powinny zobaczyć właściwe wyjątki.

#### <a name="suggestion"></a>Sugestia

Deweloperzy, którzy chcą wrócić do uzyskania, <xref:System.NullReferenceException?displayProperty=fullName> gdy celem .NET Framework 4,7 lub nowszym będzie Dodawanie/scalanie następujących elementów w pliku App.config aplikacji:

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4,7         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType>
