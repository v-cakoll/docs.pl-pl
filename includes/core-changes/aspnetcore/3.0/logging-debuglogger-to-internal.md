---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394112"
---
### <a name="logging-debuglogger-class-made-internal"></a>Rejestrowanie: Klasa DebugLogger wykonana wewnętrznie

Przed ASP.NET Core 3,0, modyfikator dostępu `DebugLogger` został `public`. W ASP.NET Core 3,0 modyfikator dostępu został zmieniony na `internal`.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="reason-for-change"></a>Przyczyna zmiany

Trwa zmiana:

* Wymuszaj spójność z innymi implementacjami rejestratora, takimi jak `ConsoleLogger`.
* Zmniejsz powierzchnię interfejsu API.

#### <a name="recommended-action"></a>Zalecana akcja

Aby włączyć rejestrowanie debugowania, użyj metody rozszerzenia <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder`. <xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> również nadal `public` w przypadku, gdy usługa musi zostać zarejestrowana ręcznie.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
