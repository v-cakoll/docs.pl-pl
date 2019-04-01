---
ms.openlocfilehash: bae7d11f29609acddaf9f6391983176ccaa9ebcb
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760378"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>Obiektu NullReferenceException w kodu z ImageSourceConverter.ConvertFrom obsługi wyjątków

|   |   |
|---|---|
|Szczegóły|Wystąpił błąd podczas obsługi kodu dla wyjątków <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> spowodował nieprawidłowe <xref:System.NullReferenceException?displayProperty=name> zostanie wygenerowany zamiast zamierzony wyjątku (np. <xref:System.IO.DirectoryNotFoundException?displayProperty=name>, <xref:System.IO.FileNotFoundException?displayProperty=name>). Ta zmiana poprawia ten błąd, tak aby metoda zgłasza teraz poprawny wyjątek. <p/>Przez domyślne wszystkich aplikacji przeznaczonych dla platformy .NET Framework 4.6.2 i wcześniej w dalszym ciągu throw <xref:System.NullReferenceException?displayProperty=name> zgodności. Deweloperom platformy .NET Framework 4.7 i powinien zostać wyświetlony powyżej odpowiednie wyjątki.|
|Sugestia|Deweloperzy, którzy chcesz, aby powrócić do pobierania <xref:System.NullReferenceException?displayProperty=name> po przeznaczonych dla platformy .NET Framework 4.7 można dodać/merge następujące polecenie, aby ich stosowania pliku App.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.7|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|

