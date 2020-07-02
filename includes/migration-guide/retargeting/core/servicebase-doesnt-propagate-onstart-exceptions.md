---
ms.openlocfilehash: 519de92ca4201d199941afe6382ddf9fc480fbbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614778"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase nie propaguje wyjątków OnStart

#### <a name="details"></a>Szczegóły

W .NET Framework 4,7 i wcześniejszych wersjach wyjątki zgłoszone podczas uruchamiania usługi nie są propagowane do obiektu wywołującego <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> .<br/>Począwszy od aplikacji przeznaczonych dla .NET Framework 4.7.1, środowisko uruchomieniowe propaguje wyjątki do <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> usług, których uruchomienie nie powiodło się.

#### <a name="suggestion"></a>Sugestia

W przypadku uruchomienia usługi, jeśli wystąpi wyjątek, ten wyjątek zostanie rozpropagowany. Powinno to pomóc zdiagnozować przypadki, w których nie można uruchomić usług. <br/>Jeśli takie zachowanie jest niepożądane, można zrezygnować z niego, dodając następujący &lt; element AppContextSwitchOverrides &gt; do &lt; sekcji środowiska uruchomieniowego w &gt; pliku konfiguracyjnym aplikacji:

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true" />
```

Jeśli aplikacja jest przeznaczona dla starszej wersji niż 4.7.1, ale chcesz mieć to zachowanie, Dodaj następujący &lt; element AppContextSwitchOverrides &gt; do &lt; sekcji środowiska uruchomieniowego w &gt; pliku konfiguracyjnym aplikacji:

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false" />
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.7.1       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType>
- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType>
