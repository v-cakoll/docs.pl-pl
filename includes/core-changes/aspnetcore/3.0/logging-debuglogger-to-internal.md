---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394112"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="bbea2-101">Rejestrowanie: Klasa DebugLogger wykonana wewnętrznie</span><span class="sxs-lookup"><span data-stu-id="bbea2-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="bbea2-102">Przed ASP.NET Core 3,0, modyfikator dostępu `DebugLogger` został `public`.</span><span class="sxs-lookup"><span data-stu-id="bbea2-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="bbea2-103">W ASP.NET Core 3,0 modyfikator dostępu został zmieniony na `internal`.</span><span class="sxs-lookup"><span data-stu-id="bbea2-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bbea2-104">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="bbea2-104">Version introduced</span></span>

<span data-ttu-id="bbea2-105">3.0</span><span class="sxs-lookup"><span data-stu-id="bbea2-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="bbea2-106">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="bbea2-106">Reason for change</span></span>

<span data-ttu-id="bbea2-107">Trwa zmiana:</span><span class="sxs-lookup"><span data-stu-id="bbea2-107">The change is being made to:</span></span>

* <span data-ttu-id="bbea2-108">Wymuszaj spójność z innymi implementacjami rejestratora, takimi jak `ConsoleLogger`.</span><span class="sxs-lookup"><span data-stu-id="bbea2-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="bbea2-109">Zmniejsz powierzchnię interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="bbea2-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bbea2-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="bbea2-110">Recommended action</span></span>

<span data-ttu-id="bbea2-111">Aby włączyć rejestrowanie debugowania, użyj metody rozszerzenia <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder`.</span><span class="sxs-lookup"><span data-stu-id="bbea2-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="bbea2-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> również nadal `public` w przypadku, gdy usługa musi zostać zarejestrowana ręcznie.</span><span class="sxs-lookup"><span data-stu-id="bbea2-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="bbea2-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="bbea2-113">Category</span></span>

<span data-ttu-id="bbea2-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bbea2-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bbea2-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="bbea2-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
