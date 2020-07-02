---
ms.openlocfilehash: c557f1cb65a675446bc77c57ef91972df92712bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617157"
---
### <a name="iasyncresultcompletedsynchronously-property-must-be-correct-for-the-resulting-task-to-complete"></a><span data-ttu-id="df730-101">Właściwość IAsyncResult. CompletedSynchronously musi być poprawna, aby wynikowe zadanie zostało ukończone</span><span class="sxs-lookup"><span data-stu-id="df730-101">IAsyncResult.CompletedSynchronously property must be correct for the resulting task to complete</span></span>

#### <a name="details"></a><span data-ttu-id="df730-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="df730-102">Details</span></span>

<span data-ttu-id="df730-103">Podczas wywoływania metody TaskFactory. wywołaniach metody FromAsync implementacja <xref:System.IAsyncResult.CompletedSynchronously> właściwości musi być prawidłowa dla zadania, które ma zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="df730-103">When calling TaskFactory.FromAsync, the implementation of the <xref:System.IAsyncResult.CompletedSynchronously> property must be correct for the resulting task to complete.</span></span> <span data-ttu-id="df730-104">Oznacza to, że właściwość musi zwracać wartość true, jeśli i tylko wtedy, gdy implementacja została ukończona synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="df730-104">That is, the property must return true if, and only if, the implementation completed synchronously.</span></span> <span data-ttu-id="df730-105">Uprzednio ta właściwość nie była sprawdzana.</span><span class="sxs-lookup"><span data-stu-id="df730-105">Previously, the property was not checked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="df730-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="df730-106">Suggestion</span></span>

<span data-ttu-id="df730-107">Jeśli <xref:System.IAsyncResult?displayProperty=fullName> implementacje prawidłowo zwracają wartość true dla <xref:System.IAsyncResult.CompletedSynchronously?displayProperty=fullName> właściwości tylko wtedy, gdy zadanie zostało ukończone synchronicznie, nie zostanie zaobserwowane żadne przerwanie.</span><span class="sxs-lookup"><span data-stu-id="df730-107">If <xref:System.IAsyncResult?displayProperty=fullName> implementations correctly return true for the <xref:System.IAsyncResult.CompletedSynchronously?displayProperty=fullName> property only when a task completed synchronously, then no break will be observed.</span></span> <span data-ttu-id="df730-108">Użytkownicy powinni przejrzeć <xref:System.IAsyncResult?displayProperty=fullName> implementacje (jeśli istnieją), aby upewnić się, że prawidłowo oceniają, czy zadanie zostało wykonane synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="df730-108">Users should review <xref:System.IAsyncResult?displayProperty=fullName> implementations they own (if any) to ensure that they correctly evaluate whether a task completed synchronously or not.</span></span>

| <span data-ttu-id="df730-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="df730-109">Name</span></span>    | <span data-ttu-id="df730-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="df730-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="df730-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="df730-111">Scope</span></span>   | <span data-ttu-id="df730-112">Brzeg</span><span class="sxs-lookup"><span data-stu-id="df730-112">Edge</span></span>        |
| <span data-ttu-id="df730-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="df730-113">Version</span></span> | <span data-ttu-id="df730-114">4.5</span><span class="sxs-lookup"><span data-stu-id="df730-114">4.5</span></span>         |
| <span data-ttu-id="df730-115">Typ</span><span class="sxs-lookup"><span data-stu-id="df730-115">Type</span></span>    | <span data-ttu-id="df730-116">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="df730-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="df730-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="df730-117">Affected APIs</span></span>

- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.IAsyncResult,System.Action{System.IAsyncResult})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.IAsyncResult,System.Action{System.IAsyncResult},System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.IAsyncResult,System.Action{System.IAsyncResult},System.Threading.Tasks.TaskCreationOptions,System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.IAsyncResult,System.Func{System.IAsyncResult,%60%600})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%600},System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%600},System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.IAsyncResult,System.Func{System.IAsyncResult,%60%600},System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.IAsyncResult,System.Func{System.IAsyncResult,%60%600},System.Threading.Tasks.TaskCreationOptions,System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%601},%60%600,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%601},%60%600,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%602},%60%600,%60%601,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,%60%602,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,%60%602,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%602},%60%600,%60%601,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%603},%60%600,%60%601,%60%602,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%603},%60%600,%60%601,%60%602,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
