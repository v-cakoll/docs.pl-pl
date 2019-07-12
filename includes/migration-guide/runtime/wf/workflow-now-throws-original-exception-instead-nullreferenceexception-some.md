---
ms.openlocfilehash: 6e5e90a4cfb862b3bfd74ac5a3715e97a736f598
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802513"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="860b0-101">Przepływ pracy zgłasza teraz oryginalnego wyjątku zamiast obiektu NullReferenceException w niektórych przypadkach</span><span class="sxs-lookup"><span data-stu-id="860b0-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

|   |   |
|---|---|
|<span data-ttu-id="860b0-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="860b0-102">Details</span></span>|<span data-ttu-id="860b0-103">W .NET Framework 4.6.2 i wcześniejszymi wersjami, gdy metoda wykonania działania przepływu pracy zgłasza wyjątek z <code>null</code> wartość <xref:System.Exception.Message> właściwości środowiska uruchomieniowego przepływu pracy System.Activities zgłasza <xref:System.NullReferenceException?displayProperty=name>, maskowania Oryginalny wyjątek. W programie .NET Framework 4.7 wcześniej maskowanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="860b0-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=name>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>|
|<span data-ttu-id="860b0-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="860b0-104">Suggestion</span></span>|<span data-ttu-id="860b0-105">Jeśli kod opiera się na obsłudze <xref:System.NullReferenceException?displayProperty=name>, zmień ją na przechwytywać wyjątki, które może być wyrzucanych z działania niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="860b0-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=name>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>|
|<span data-ttu-id="860b0-106">Scope</span><span class="sxs-lookup"><span data-stu-id="860b0-106">Scope</span></span>|<span data-ttu-id="860b0-107">Mały</span><span class="sxs-lookup"><span data-stu-id="860b0-107">Minor</span></span>|
|<span data-ttu-id="860b0-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="860b0-108">Version</span></span>|<span data-ttu-id="860b0-109">4.7</span><span class="sxs-lookup"><span data-stu-id="860b0-109">4.7</span></span>|
|<span data-ttu-id="860b0-110">Typ</span><span class="sxs-lookup"><span data-stu-id="860b0-110">Type</span></span>|<span data-ttu-id="860b0-111">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="860b0-111">Runtime</span></span>|
|<span data-ttu-id="860b0-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="860b0-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|

