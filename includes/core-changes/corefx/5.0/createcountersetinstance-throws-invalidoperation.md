---
ms.openlocfilehash: fabbc9a51f61a703ce97db50ab251e7a13ffe348
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144487"
---
### <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a><span data-ttu-id="fa8c8-101">Element CounterSet. CreateCounterSetInstance teraz zgłasza InvalidOperationException, jeśli wystąpienie już istnieje</span><span class="sxs-lookup"><span data-stu-id="fa8c8-101">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exists</span></span>

<span data-ttu-id="fa8c8-102">Począwszy od programu .NET 5,0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> zgłasza <xref:System.InvalidOperationException> zamiast tego, <xref:System.ArgumentException> czy zestaw liczników już istnieje.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-102">Starting in .NET 5.0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> throws an <xref:System.InvalidOperationException> instead of an <xref:System.ArgumentException> if the counter set already exists.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fa8c8-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="fa8c8-103">Change description</span></span>

<span data-ttu-id="fa8c8-104">W .NET Framework i .NET Core 1,0 do 3,1 można utworzyć wystąpienie zestawu liczników przez wywołanie <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> .</span><span class="sxs-lookup"><span data-stu-id="fa8c8-104">In .NET Framework and .NET Core 1.0 to 3.1, you can create an instance of the counter set by calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>.</span></span> <span data-ttu-id="fa8c8-105">Jeśli jednak zestaw liczników już istnieje, metoda zgłasza <xref:System.ArgumentException> wyjątek.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-105">However, if the counter set already exists, the method throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="fa8c8-106">W przypadku programu .NET 5,0 i jego nowszych wersji, gdy wywoływany <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> jest zestaw liczników, <xref:System.InvalidOperationException> zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-106">In .NET 5.0 and later versions, when you call <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> and the counter set exists, an <xref:System.InvalidOperationException> exception is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fa8c8-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="fa8c8-107">Version introduced</span></span>

<span data-ttu-id="fa8c8-108">5,0 wersja zapoznawcza 5</span><span class="sxs-lookup"><span data-stu-id="fa8c8-108">5.0 Preview 5</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fa8c8-109">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="fa8c8-109">Recommended action</span></span>

<span data-ttu-id="fa8c8-110">W przypadku przechwytywania <xref:System.ArgumentException> wyjątków w aplikacji podczas wywoływania <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> należy rozważyć również przechwycenie <xref:System.InvalidOperationException> wyjątków.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-110">If you catch <xref:System.ArgumentException> exceptions in your app when calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>, consider also catching <xref:System.InvalidOperationException> exceptions.</span></span>

> [!NOTE]
> <span data-ttu-id="fa8c8-111"><xref:System.ArgumentException>Nie zaleca się przechwytywania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="fa8c8-111">Catching <xref:System.ArgumentException> exceptions is not recommended.</span></span>

#### <a name="category"></a><span data-ttu-id="fa8c8-112">Kategoria</span><span class="sxs-lookup"><span data-stu-id="fa8c8-112">Category</span></span>

<span data-ttu-id="fa8c8-113">Podstawowe biblioteki platformy .NET</span><span class="sxs-lookup"><span data-stu-id="fa8c8-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fa8c8-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="fa8c8-114">Affected APIs</span></span>

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
