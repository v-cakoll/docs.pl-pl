---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394112"
---
### <a name="logging-debuglogger-class-made-internal"></a>Rejestrowanie: DebugLogger klasy wykonane wewnętrzne

Przed ASP.NET Core 3.0 `DebugLogger`modyfikator `public`dostępu był . W ASP.NET Core 3.0 modyfikator dostępu został zmieniony na `internal`.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="reason-for-change"></a>Przyczyna zmiany

Zmiana jest dokonywana w celu:

* Wymuszanie spójności z innymi implementacjami rejestratora, takimi jak `ConsoleLogger`.
* Zmniejsz powierzchnię interfejsu API.

#### <a name="recommended-action"></a>Zalecana akcja

Użyj <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` metody rozszerzenia, aby włączyć rejestrowanie debugowania. <xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider>jest również `public` nadal w przypadku, gdy usługa musi być zarejestrowana ręcznie.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
