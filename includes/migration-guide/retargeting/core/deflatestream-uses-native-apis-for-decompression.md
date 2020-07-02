---
ms.openlocfilehash: 7e42a294b151d07a6fdc61308cdf92df7a31a1d6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614723"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a>DeflateStream używa natywnych interfejsów API do dekompresji

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4.7.2, implementacja dekompresji w `T:System.IO.Compression.DeflateStream` klasie została zmieniona tak, aby domyślnie używała natywnych interfejsów API systemu Windows. Zwykle powoduje to znaczne zwiększenie wydajności. Wszystkie aplikacje .NET ukierunkowane na .NET Framework w wersji 4.7.2 lub nowszej używają natywnej implementacji. Ta zmiana może spowodować pewne różnice w działaniu, takie jak:

- Komunikaty o wyjątkach mogą się różnić. Jednak typ zgłoszonego wyjątku pozostaje taki sam.
- Niektóre specjalne sytuacje, takie jak brak wystarczającej ilości pamięci do ukończenia operacji, mogą być obsługiwane inaczej.
- Istnieją znane różnice dotyczące analizowania nagłówka gzip (Uwaga: dotyczy tylko `GZipStream` zestawu dla dekompresji):
- Wyjątki podczas analizowania nieprawidłowych nagłówków można zgłaszać w różnym czasie.
- Implementacja natywna wymusza, że wartości niektórych zarezerwowanych flag wewnątrz nagłówka gzip (tj. [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) są ustawiane zgodnie ze specyfikacją, co może spowodować zgłoszenie wyjątku w przypadku zignorowania poprzednio nieprawidłowych wartości.

#### <a name="suggestion"></a>Sugestia

Jeśli dekompresja z natywnymi interfejsami API ma negatywny wpływ na zachowanie aplikacji, możesz zrezygnować z tej funkcji, dodając `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` przełącznik do `runtime` sekcji pliku app.config i ustawiając go na `true` :

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true" />
  </runtime>
</configuration>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.7.2       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType>
- <xref:System.IO.Compression.GZipStream?displayProperty=nameWithType>
