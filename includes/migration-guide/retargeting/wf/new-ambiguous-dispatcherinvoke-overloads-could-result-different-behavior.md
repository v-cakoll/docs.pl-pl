---
ms.openlocfilehash: 80e61d4dd5b8d4754a39e95e37475fefff57fcbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617169"
---
### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a><span data-ttu-id="61698-101">Nowe (niejednoznaczne) Dyspozytor. Wywołaj przeciążenia mogą spowodować inne zachowanie</span><span class="sxs-lookup"><span data-stu-id="61698-101">New (ambiguous) Dispatcher.Invoke overloads could result in different behavior</span></span>

#### <a name="details"></a><span data-ttu-id="61698-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="61698-102">Details</span></span>

<span data-ttu-id="61698-103">.NET Framework 4,5 dodaje nowe przeciążenia do <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> , które zawierają parametr typu <xref:System.Action> .</span><span class="sxs-lookup"><span data-stu-id="61698-103">The .NET Framework 4.5 adds new overloads to <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> that include a parameter of type <xref:System.Action>.</span></span> <span data-ttu-id="61698-104">Gdy istniejący kod jest ponownie kompilowany, kompilatory mogą rozpoznać wywołania do dyspozytora. Wywołaj metody, które mają <xref:System.Delegate> parametr jako wywołania dyspozytora. Wywołaj metody z <xref:System.Action> parametrem.</span><span class="sxs-lookup"><span data-stu-id="61698-104">When existing code is recompiled, compilers may resolve calls to Dispatcher.Invoke methods that have a <xref:System.Delegate> parameter as calls to Dispatcher.Invoke methods with an <xref:System.Action> parameter.</span></span> <span data-ttu-id="61698-105">W przypadku wywołania dyspozytora. Wywołaj Przeciążenie z <xref:System.Delegate> parametrem, który jest rozpoznawany jako wywołanie dyspozytora. Wywołaj Przeciążenie z <xref:System.Action> parametrem, mogą wystąpić następujące różnice w zachowaniu:</span><span class="sxs-lookup"><span data-stu-id="61698-105">If a call to a Dispatcher.Invoke overload with a  <xref:System.Delegate> parameter is resolved as a call to a Dispatcher.Invoke overload with an <xref:System.Action> parameter, the following differences in behavior may occur:</span></span>

- <span data-ttu-id="61698-106">Jeśli wystąpi wyjątek, <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> <xref:System.Windows.Threading.Dispatcher.UnhandledException> zdarzenia i nie są zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="61698-106">If an exception occurs, the <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> and <xref:System.Windows.Threading.Dispatcher.UnhandledException> events are not raised.</span></span> <span data-ttu-id="61698-107">Zamiast tego wyjątki są obsługiwane przez <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="61698-107">Instead, exceptions are handled by the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> event.</span></span>
- <span data-ttu-id="61698-108">Wywołania do niektórych elementów członkowskich, takie jak <xref:System.Windows.Threading.DispatcherOperation.Result> , bloku do momentu ukończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="61698-108">Calls to some members, such as <xref:System.Windows.Threading.DispatcherOperation.Result>, block until the operation has completed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="61698-109">Sugestia</span><span class="sxs-lookup"><span data-stu-id="61698-109">Suggestion</span></span>

<span data-ttu-id="61698-110">Aby uniknąć niejednoznaczności (i potencjalnych różnic w obsłudze wyjątków lub zachowania blokowania), kod wywołujący wywołania. Invoke może przekazać pusty obiekt [] jako drugi parametr do wywołania wywołania, aby upewnić się, że rozwiązanie do przeciążenia metody .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="61698-110">To avoid ambiguity (and potential differences in exception handling or blocking behaviors), code calling Dispatcher.Invoke can pass an empty object[] as a second parameter to the Invoke call to be sure of resolving to the .NET Framework 4.0 method overload.</span></span>

| <span data-ttu-id="61698-111">Nazwa</span><span class="sxs-lookup"><span data-stu-id="61698-111">Name</span></span>    | <span data-ttu-id="61698-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="61698-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="61698-113">Zakres</span><span class="sxs-lookup"><span data-stu-id="61698-113">Scope</span></span>   | <span data-ttu-id="61698-114">Mały</span><span class="sxs-lookup"><span data-stu-id="61698-114">Minor</span></span>       |
| <span data-ttu-id="61698-115">Wersja</span><span class="sxs-lookup"><span data-stu-id="61698-115">Version</span></span> | <span data-ttu-id="61698-116">4.5</span><span class="sxs-lookup"><span data-stu-id="61698-116">4.5</span></span>         |
| <span data-ttu-id="61698-117">Typ</span><span class="sxs-lookup"><span data-stu-id="61698-117">Type</span></span>    | <span data-ttu-id="61698-118">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="61698-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="61698-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="61698-119">Affected APIs</span></span>

- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
