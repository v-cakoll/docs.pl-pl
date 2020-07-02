---
ms.openlocfilehash: 9a2d6a25a8ab1b8bf65b947557802e0805a7f826
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617197"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a><span data-ttu-id="864ba-101">Zmienna iteratora foreach jest teraz objęta zakresem iteracji, więc semantyka przechwytywania zamknięć jest różna (w języku C# 5)</span><span class="sxs-lookup"><span data-stu-id="864ba-101">Foreach iterator variable is now scoped within the iteration, so closure capturing semantics are different (in C#5)</span></span>

#### <a name="details"></a><span data-ttu-id="864ba-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="864ba-102">Details</span></span>

<span data-ttu-id="864ba-103">Począwszy od języka C# 5 (Visual Studio 2012), `foreach` zmienne iteratora są objęte zakresem iteracji.</span><span class="sxs-lookup"><span data-stu-id="864ba-103">Beginning with C# 5 (Visual Studio 2012), `foreach` iterator variables are scoped within the iteration.</span></span> <span data-ttu-id="864ba-104">Może to spowodować przerwanie, jeśli kod był wcześniej w zależności od zmiennych, które nie zostaną uwzględnione w `foreach` zamknięciu.</span><span class="sxs-lookup"><span data-stu-id="864ba-104">This can cause breaks if code was previously depending on the variables to not be included in the `foreach`'s closure.</span></span> <span data-ttu-id="864ba-105">Objawem tej zmiany jest to, że zmienna iteratora przeniesiona do delegata jest traktowana jako wartość, którą ma w momencie utworzenia delegata, a nie wartość, która ma w momencie wywołania obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="864ba-105">The symptom of this change is that an iterator variable passed to a delegate is treated as the value it has at the time the delegate is created, rather than the value it has at the time the delegate is invoked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="864ba-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="864ba-106">Suggestion</span></span>

<span data-ttu-id="864ba-107">W idealnym przypadku należy zaktualizować kod, aby oczekiwać na nowe zachowanie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="864ba-107">Ideally, code should be updated to expect the new compiler behavior.</span></span> <span data-ttu-id="864ba-108">Jeśli stara semantyka jest wymagana, zmienna iteratora może zostać zastąpiona oddzielną zmienną, która jest jawnie umieszczona poza zakresem pętli.</span><span class="sxs-lookup"><span data-stu-id="864ba-108">If the old semantics are required, the iterator variable can be replaced with a separate variable which is explicitly placed outside of the loop's scope.</span></span>

| <span data-ttu-id="864ba-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="864ba-109">Name</span></span>    | <span data-ttu-id="864ba-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="864ba-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="864ba-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="864ba-111">Scope</span></span>   | <span data-ttu-id="864ba-112">Duży</span><span class="sxs-lookup"><span data-stu-id="864ba-112">Major</span></span>       |
| <span data-ttu-id="864ba-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="864ba-113">Version</span></span> | <span data-ttu-id="864ba-114">4.5</span><span class="sxs-lookup"><span data-stu-id="864ba-114">4.5</span></span>         |
| <span data-ttu-id="864ba-115">Typ</span><span class="sxs-lookup"><span data-stu-id="864ba-115">Type</span></span>    | <span data-ttu-id="864ba-116">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="864ba-116">Retargeting</span></span> |
