---
ms.openlocfilehash: 4e81087431091dfa4d5432d5ea5e2b665be2b130
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62091703"
---
### <a name="listtforeach-can-throw-exception-when-modifying-list-item"></a><span data-ttu-id="7bca5-101">Lista\<T >. ForEach może zgłosić wyjątek podczas modyfikowania elementu listy</span><span class="sxs-lookup"><span data-stu-id="7bca5-101">List\<T>.ForEach can throw exception when modifying list item</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7bca5-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7bca5-102">Details</span></span>|<span data-ttu-id="7bca5-103">Począwszy od programu .NET Framework 4.5, moduł wyliczający <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> zgłosi wyjątek <xref:System.InvalidOperationException?displayProperty=name>, jeśli element kolekcji wywołującej zostanie zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="7bca5-103">Beginning in .NET Framework 4.5, a <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> enumerator will throw an <xref:System.InvalidOperationException?displayProperty=name> exception if an element in the calling collection is modified.</span></span> <span data-ttu-id="7bca5-104">Wcześniej nie zgłaszał wyjątku, ale mogło to prowadzić do sytuacji wyścigu.</span><span class="sxs-lookup"><span data-stu-id="7bca5-104">Previously, this would not throw an exception but could lead to race conditions.</span></span>|
|<span data-ttu-id="7bca5-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="7bca5-105">Suggestion</span></span>|<span data-ttu-id="7bca5-106">Najlepiej nie poprawiać kodu, aby nie modyfikować list podczas wyliczania ich elementów, ponieważ to nigdy nie jest bezpieczna operacja.</span><span class="sxs-lookup"><span data-stu-id="7bca5-106">Ideally, code should be fixed to not modify lists while enumerating their elements because that is never a safe operation.</span></span> <span data-ttu-id="7bca5-107">Aby przywrócić poprzednie zachowanie, można określić platformę docelową aplikacji jako program .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="7bca5-107">To revert to the previous behavior, though, an app may target .NET Framework 4.0.</span></span>|
|<span data-ttu-id="7bca5-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="7bca5-108">Scope</span></span>|<span data-ttu-id="7bca5-109">Krawędź</span><span class="sxs-lookup"><span data-stu-id="7bca5-109">Edge</span></span>|
|<span data-ttu-id="7bca5-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="7bca5-110">Version</span></span>|<span data-ttu-id="7bca5-111">4.5</span><span class="sxs-lookup"><span data-stu-id="7bca5-111">4.5</span></span>|
|<span data-ttu-id="7bca5-112">Typ</span><span class="sxs-lookup"><span data-stu-id="7bca5-112">Type</span></span>|<span data-ttu-id="7bca5-113">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="7bca5-113">Retargeting</span></span>|
|<span data-ttu-id="7bca5-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="7bca5-114">Affected APIs</span></span>|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|
