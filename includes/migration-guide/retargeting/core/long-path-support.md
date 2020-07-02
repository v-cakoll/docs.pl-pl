---
ms.openlocfilehash: 67e3ff5000ebd38064ed8a57e4fe561afa31f8d8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614711"
---
### <a name="long-path-support"></a>Obsługa długich ścieżek

#### <a name="details"></a>Szczegóły

Począwszy od aplikacji, które są przeznaczone dla .NET Framework 4.6.2, obsługiwane są długie ścieżki (od do 32 znaków), a 260-znak (lub `MAX_PATH` ) ograniczenie długości ścieżki zostało usunięte. W przypadku aplikacji, które są ponownie kompilowane do .NET Framework 4.6.2, ścieżki kodu, które wcześniej wywołały, <xref:System.IO.PathTooLongException?displayProperty=fullName> ponieważ ścieżka przekroczyła 260 znaków, zostanie teraz zgłoszony <xref:System.IO.PathTooLongException?displayProperty=fullName> tylko w następujących warunkach:

- Długość ścieżki przekracza <xref:System.Int16.MaxValue> (32 767) znaków.
- System operacyjny zwraca `COR_E_PATHTOOLONG` lub jego odpowiednik.
W przypadku aplikacji, które są przeznaczone dla .NET Framework 4.6.1 i wcześniejszych wersji, środowisko uruchomieniowe automatycznie zgłasza, <xref:System.IO.PathTooLongException?displayProperty=fullName> gdy ścieżka przekracza 260 znaków.

#### <a name="suggestion"></a>Sugestia

W przypadku aplikacji przeznaczonych dla .NET Framework 4.6.2 możesz zrezygnować z obsługi długiej ścieżki, jeśli nie jest to pożądane, dodając następujący element do `<runtime>` sekcji `app.config` pliku:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />
</runtime>
```

W przypadku aplikacji, które są przeznaczone dla wcześniejszych wersji .NET Framework ale działają na .NET Framework 4.6.2 lub nowszych, możesz zrezygnować z obsługi ścieżek długich, dodając następujące elementy do `<runtime>` sekcji `app.config` pliku:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />
</runtime>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.6.2       |
| Typ    | Przekierowanie |
