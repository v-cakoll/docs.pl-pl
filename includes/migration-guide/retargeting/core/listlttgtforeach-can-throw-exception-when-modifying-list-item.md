---
ms.openlocfilehash: 3300a74b81fc9eeba670ee0ceb2c2615fd3925bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617286"
---
### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a><span data-ttu-id="ee713-101">List&lt;T&gt;.ForEach może zgłosić wyjątek podczas modyfikowania elementu listy</span><span class="sxs-lookup"><span data-stu-id="ee713-101">List&lt;T&gt;.ForEach can throw exception when modifying list item</span></span>

#### <a name="details"></a><span data-ttu-id="ee713-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="ee713-102">Details</span></span>

<span data-ttu-id="ee713-103">Począwszy od programu .NET Framework 4.5, moduł wyliczający <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> zgłosi wyjątek <xref:System.InvalidOperationException?displayProperty=fullName>, jeśli element kolekcji wywołującej zostanie zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="ee713-103">Beginning in .NET Framework 4.5, a <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> enumerator will throw an <xref:System.InvalidOperationException?displayProperty=fullName> exception if an element in the calling collection is modified.</span></span> <span data-ttu-id="ee713-104">Wcześniej nie zgłaszał wyjątku, ale mogło to prowadzić do sytuacji wyścigu.</span><span class="sxs-lookup"><span data-stu-id="ee713-104">Previously, this would not throw an exception but could lead to race conditions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ee713-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="ee713-105">Suggestion</span></span>

<span data-ttu-id="ee713-106">Najlepiej nie poprawiać kodu, aby nie modyfikować list podczas wyliczania ich elementów, ponieważ to nigdy nie jest bezpieczna operacja.</span><span class="sxs-lookup"><span data-stu-id="ee713-106">Ideally, code should be fixed to not modify lists while enumerating their elements because that is never a safe operation.</span></span> <span data-ttu-id="ee713-107">Aby przywrócić poprzednie zachowanie, można określić platformę docelową aplikacji jako program .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="ee713-107">To revert to the previous behavior, though, an app may target .NET Framework 4.0.</span></span>

| <span data-ttu-id="ee713-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="ee713-108">Name</span></span>    | <span data-ttu-id="ee713-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="ee713-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ee713-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="ee713-110">Scope</span></span>   | <span data-ttu-id="ee713-111">Brzeg</span><span class="sxs-lookup"><span data-stu-id="ee713-111">Edge</span></span>        |
| <span data-ttu-id="ee713-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="ee713-112">Version</span></span> | <span data-ttu-id="ee713-113">4.5</span><span class="sxs-lookup"><span data-stu-id="ee713-113">4.5</span></span>         |
| <span data-ttu-id="ee713-114">Typ</span><span class="sxs-lookup"><span data-stu-id="ee713-114">Type</span></span>    | <span data-ttu-id="ee713-115">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="ee713-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ee713-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="ee713-116">Affected APIs</span></span>

- <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType>
