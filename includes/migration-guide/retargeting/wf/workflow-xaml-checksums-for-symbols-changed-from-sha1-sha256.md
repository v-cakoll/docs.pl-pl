---
ms.openlocfilehash: 946e71f2f466664c8f9fcf4811288ce693a872eb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616294"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a>Sumy kontrolne XAML przepływu pracy dla symboli zmienionych z SHA1 na SHA256

#### <a name="details"></a>Szczegóły

Aby można było obsługiwać debugowanie za pomocą programu Visual Studio, środowisko uruchomieniowe przepływu pracy generuje sumę kontrolną dla pliku XAML przepływu pracy przy użyciu algorytmu wyznaczania wartości skrótu. W .NET Framework 4.6.2 i starszych wersjach funkcja tworzenia skrótów sum kontrolnych przepływu pracy użyła algorytmu MD5, który spowodował problemy z systemami z obsługą FIPS. Począwszy od .NET Framework 4,7, domyślny algorytm został zmieniony na SHA1. Począwszy od .NET Framework 4,8, domyślny algorytm został zmieniony na SHA256.

#### <a name="suggestion"></a>Sugestia

Jeśli kod nie może załadować wystąpień przepływu pracy lub znaleźć odpowiednich symboli ze względu na błąd sumy kontrolnej, spróbuj ustawić `AppContext` przełącznik "Switch.System. Activities. UseSHA1HashForDebuggerSymbols "do `true` . W kodzie:

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseSHA1HashForDebuggerSymbols", true);
```

Lub w konfiguracji:

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true" />
  </runtime>
</configuration>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4,8         |
| Typ    | Przekierowanie |
