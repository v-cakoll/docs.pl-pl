---
ms.openlocfilehash: 72d48d1daa85b6891c122f2fcc5279642253b926
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614838"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>Sumy kontrolne przepływu pracy zmieniły się z MD5 na SHA1

#### <a name="details"></a>Szczegóły

Aby można było obsługiwać debugowanie za pomocą programu Visual Studio, środowisko uruchomieniowe przepływu pracy generuje sumę kontrolną wystąpienia przepływu pracy przy użyciu algorytmu wyznaczania wartości skrótu. W .NET Framework 4.6.2 i starszych wersjach funkcja tworzenia skrótów sum kontrolnych przepływu pracy użyła algorytmu MD5, który spowodował problemy z systemami z obsługą FIPS. Począwszy od .NET Framework 4,7, algorytm jest SHA1. Jeśli kod spowodował utrwalenie tych sum kontrolnych, nie będą one zgodne.

#### <a name="suggestion"></a>Sugestia

Jeśli kod nie może załadować wystąpień przepływu pracy z powodu błędu sumy kontrolnej, spróbuj ustawić `AppContext` przełącznik &quot;Switch.System. Activities. UseMD5ForWFDebugger &quot; na wartość true. W kodzie:

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseMD5ForWFDebugger", true);
```

Lub w konfiguracji:

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseMD5ForWFDebugger=true" />
  </runtime>
</configuration>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4,7         |
| Typ    | Przekierowanie |
