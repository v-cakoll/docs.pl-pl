---
ms.openlocfilehash: ae0c7322b7415157838278b5568e6e49936e9a93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621241"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="e9189-101">Przepływ pracy teraz zgłasza oryginalny wyjątek zamiast NullReferenceException w niektórych przypadkach</span><span class="sxs-lookup"><span data-stu-id="e9189-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

#### <a name="details"></a><span data-ttu-id="e9189-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e9189-102">Details</span></span>

<span data-ttu-id="e9189-103">W .NET Framework 4.6.2 i starszych wersjach, gdy metoda Execute działania przepływu pracy zgłasza wyjątek z <code>null</code> wartością <xref:System.Exception.Message> właściwości, środowisko uruchomieniowe przepływu pracy system. Activities generuje <xref:System.NullReferenceException?displayProperty=fullName> , maskowanie oryginalnego wyjątku. W .NET Framework 4,7 został zgłoszony poprzednio zamaskowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e9189-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=fullName>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e9189-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="e9189-104">Suggestion</span></span>

<span data-ttu-id="e9189-105">Jeśli Twój kod opiera się na obsłudze <xref:System.NullReferenceException?displayProperty=fullName> , zmień go, aby przechwytywać wyjątki, które mogą zostać zgłoszone przez działania niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="e9189-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=fullName>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>

| <span data-ttu-id="e9189-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e9189-106">Name</span></span>    | <span data-ttu-id="e9189-107">Wartość</span><span class="sxs-lookup"><span data-stu-id="e9189-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e9189-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="e9189-108">Scope</span></span>   |<span data-ttu-id="e9189-109">Mały</span><span class="sxs-lookup"><span data-stu-id="e9189-109">Minor</span></span>|
|<span data-ttu-id="e9189-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="e9189-110">Version</span></span>|<span data-ttu-id="e9189-111">4,7</span><span class="sxs-lookup"><span data-stu-id="e9189-111">4.7</span></span>|
|<span data-ttu-id="e9189-112">Typ</span><span class="sxs-lookup"><span data-stu-id="e9189-112">Type</span></span>|<span data-ttu-id="e9189-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e9189-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e9189-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="e9189-114">Affected APIs</span></span>

-<xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
