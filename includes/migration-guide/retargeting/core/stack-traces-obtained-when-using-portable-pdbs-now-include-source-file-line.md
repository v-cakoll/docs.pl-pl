---
ms.openlocfilehash: c7500550cd9714a9788a7dea68af04823f000f7f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614796"
---
### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a>Ślady stosu uzyskane podczas korzystania z przenośnego plików PDB teraz obejmują plik źródłowy i informacje o wierszu, jeśli jest to wymagane

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4.7.2, ślady stosu uzyskany podczas korzystania z przenośnego plików PDB Dołącz plik źródłowy i informacje o wierszu, gdy jest to wymagane. W wersjach wcześniejszych niż .NET Framework 4.7.2, plik źródłowy i informacje o wierszu byłyby niedostępne w przypadku używania przenośnych plików PDB, nawet jeśli zostały jawnie zażądane.

#### <a name="suggestion"></a>Sugestia

W przypadku aplikacji przeznaczonych dla .NET Framework 4.7.2 można zrezygnować z pliku źródłowego i informacji o wierszu w przypadku używania przenośnego plików PDB, jeśli nie jest to pożądane, dodając następujący element do `<runtime>` sekcji `app.config` pliku:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true" />
</runtime>
```

W przypadku aplikacji, które są przeznaczone dla wcześniejszych wersji .NET Framework ale są uruchamiane na .NET Framework 4.7.2 lub nowszych, można zrezygnować z pliku źródłowego i informacje o wierszu w przypadku używania przenośnego plików PDB przez dodanie następujących `<runtime>` elementów do sekcji `app.config` pliku:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false" />
</runtime>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.7.2       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)>
