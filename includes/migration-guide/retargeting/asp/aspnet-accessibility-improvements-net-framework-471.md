---
ms.openlocfilehash: 418bcdca1e9a325894891d7b0e080ce035e2d1b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614682"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>Udoskonalenia ułatwień dostępu ASP.NET w programie .NET Framework 4.7.1

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4.7.1, ASP.NET ulepszono sposób, w jaki formanty sieci Web ASP.NET współpracują z technologią ułatwień dostępu w programie Visual Studio, aby lepiej obsługiwać klientów ASP.NET.  Należą do nich następujące zmiany:

- Zmiany w celu zaimplementowania brakujących wzorców dostępności interfejsu użytkownika w kontrolkach, takich jak okno dialogowe Dodawanie pola w Kreatorze widoku szczegółów lub okno dialogowe Konfiguruj widok ListView kreatora ListView.
- Zmiany w celu usprawnienia wyświetlania w trybie duży kontrast, takie jak edytor pól modułu stronicowania danych.
- Zmiany w celu ulepszenia środowiska nawigacji klawiatury dla kontrolek, takich jak okno dialogowe pola w Kreatorze Edytuj pola modułu stronicowania kontrolki formantu DataPager, okno dialogowe Konfigurowanie obiektu ObjectContext lub okno dialogowe Konfigurowanie wyboru danych Kreatora konfiguracji źródła danych.

#### <a name="suggestion"></a>Sugestia

**Jak wybrać lub wycofać te zmiany** Aby projektant programu Visual Studio mógł korzystać z tych zmian, musi on działać na .NET Framework 4.7.1 lub nowszym. Aplikacja sieci Web może korzystać z tych zmian w jeden z następujących sposobów:

- Zainstaluj program Visual Studio 2017 15,3 lub nowszy, który obsługuje nowe funkcje ułatwień dostępu domyślnie z następującym przełącznikiem AppContext.
- Zrezygnuj ze starszych zachowań ułatwień dostępu, dodając `Switch.UseLegacyAccessibilityFeatures` przełącznik AppContext do `<runtime>` sekcji w pliku devenv.exe.config i ustawiając go na `false` , jak pokazano w poniższym przykładzie.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
<runtime>
...
<!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false'  -->
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
...
</runtime>
</configuration>
```

Aplikacje, które są przeznaczone dla .NET Framework 4.7.1 lub nowszych i chcą zachować starsze zachowanie ułatwień dostępu, mogą zrezygnować z używania starszych funkcji ułatwień dostępu przez jawne ustawienie tego przełącznika AppContext na `true` .

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.7.1       |
| Typ    | Przekierowanie |
