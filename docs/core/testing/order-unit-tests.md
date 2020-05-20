---
title: Zamów testy jednostkowe
description: Dowiedz się, jak zamówić testy jednostkowe za pomocą platformy .NET Core.
author: IEvangelist
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: ce0d01c924075ffcc9ad49ef8aca49222c10c921
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83704560"
---
# <a name="order-unit-tests"></a><span data-ttu-id="ff94e-103">Zamów testy jednostkowe</span><span class="sxs-lookup"><span data-stu-id="ff94e-103">Order unit tests</span></span>

<span data-ttu-id="ff94e-104">Czasami może być konieczne, aby testy jednostkowe były uruchamiane w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="ff94e-104">Occasionally, you may want to have unit tests run in a specific order.</span></span> <span data-ttu-id="ff94e-105">W idealnym przypadku, kolejność, w której testy jednostkowe _nie_ powinny mieć znaczenia i [najlepszym rozwiązaniem](unit-testing-best-practices.md) jest uniknięcie porządkowania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="ff94e-105">Ideally, the order in which unit tests run should _not_ matter, and it is [best practice](unit-testing-best-practices.md) to avoid ordering unit tests.</span></span> <span data-ttu-id="ff94e-106">Bez względu na to, może być konieczne wykonanie tej czynności.</span><span class="sxs-lookup"><span data-stu-id="ff94e-106">Regardless, there may be a need to do so.</span></span> <span data-ttu-id="ff94e-107">W takim przypadku w tym artykule przedstawiono sposób porządkowania przebiegów testowych.</span><span class="sxs-lookup"><span data-stu-id="ff94e-107">In that case, this article demonstrates how to order test runs.</span></span>

<span data-ttu-id="ff94e-108">Jeśli wolisz przeglądać kod źródłowy, zobacz przykładowe repozytorium programu [Order Core Unit Tests](/samples/dotnet/samples/order-unit-tests-cs) .</span><span class="sxs-lookup"><span data-stu-id="ff94e-108">If you prefer to browse the source code, see the [order .NET Core unit tests](/samples/dotnet/samples/order-unit-tests-cs) sample repository.</span></span>

> [!TIP]
> <span data-ttu-id="ff94e-109">Oprócz funkcji zamawiania opisanych w tym artykule warto rozważyć [utworzenie niestandardowych list odtwarzania z programem Visual Studio](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) jako alternatywę.</span><span class="sxs-lookup"><span data-stu-id="ff94e-109">In addition to the ordering capabilities outlined in this article, consider [creating custom playlists with Visual Studio](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) as an alternative.</span></span>

:::zone pivot="mstest"

## <a name="order-alphabetically"></a><span data-ttu-id="ff94e-110">Porządkuj alfabetycznie</span><span class="sxs-lookup"><span data-stu-id="ff94e-110">Order alphabetically</span></span>

<span data-ttu-id="ff94e-111">W przypadku MSTest testy są automatycznie uporządkowane według ich nazwy testowej.</span><span class="sxs-lookup"><span data-stu-id="ff94e-111">With MSTest, tests are automatically ordered by their test name.</span></span>

> [!NOTE]
> <span data-ttu-id="ff94e-112">Test o nazwie `Test14` zostanie uruchomiony przed `Test2` nawet wtedy, gdy liczba `2` jest mniejsza niż `14` .</span><span class="sxs-lookup"><span data-stu-id="ff94e-112">A test named `Test14` will run before `Test2` even though the number  `2` is less than `14`.</span></span> <span data-ttu-id="ff94e-113">Dzieje się tak dlatego, że kolejność nazw testowych używa nazwy tekstu testu.</span><span class="sxs-lookup"><span data-stu-id="ff94e-113">This is because, test name ordering uses the text name of the test.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/MSTest.Project/ByAlphabeticalOrder.cs":::

:::zone-end
:::zone pivot="xunit"

<span data-ttu-id="ff94e-114">Platforma testowa xUnit umożliwia dokładniejsze i precyzyjne sterowanie kolejnością przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="ff94e-114">The xUnit test framework allows for more granularity and control of test run order.</span></span> <span data-ttu-id="ff94e-115">Należy zaimplementować `ITestCaseOrderer` interfejsy i, `ITestCollectionOrderer` Aby kontrolować kolejność przypadków testowych dla klasy lub kolekcje testowe.</span><span class="sxs-lookup"><span data-stu-id="ff94e-115">You implement the `ITestCaseOrderer` and `ITestCollectionOrderer` interfaces to control the order of test cases for a class, or test collections.</span></span>

## <a name="order-by-test-case-alphabetically"></a><span data-ttu-id="ff94e-116">Porządkuj według przypadku testowego alfabetycznie</span><span class="sxs-lookup"><span data-stu-id="ff94e-116">Order by test case alphabetically</span></span>

<span data-ttu-id="ff94e-117">Aby zamówić przypadki testowe według nazwy metody, należy zaimplementować `ITestCaseOrderer` i udostępnić mechanizm porządkowania.</span><span class="sxs-lookup"><span data-stu-id="ff94e-117">To order test cases by their method name, you implement the `ITestCaseOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/AlphabeticalOrderer.cs":::

<span data-ttu-id="ff94e-118">Następnie w klasie testowej ustawia się kolejność przypadków testowych przy użyciu `TestCaseOrdererAttribute` .</span><span class="sxs-lookup"><span data-stu-id="ff94e-118">Then in a test class you set the test case order with the `TestCaseOrdererAttribute`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByAlphabeticalOrder.cs":::

## <a name="order-by-collection-alphabetically"></a><span data-ttu-id="ff94e-119">Kolejność według kolekcji alfabetycznie</span><span class="sxs-lookup"><span data-stu-id="ff94e-119">Order by collection alphabetically</span></span>

<span data-ttu-id="ff94e-120">Aby zamówić kolekcje testowe według ich nazwy wyświetlanej, należy zaimplementować `ITestCollectionOrderer` i udostępnić mechanizm porządkowania.</span><span class="sxs-lookup"><span data-stu-id="ff94e-120">To order test collections by their display name, you implement the `ITestCollectionOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/DisplayNameOrderer.cs":::

<span data-ttu-id="ff94e-121">Ze względu na to, że kolekcje testowe mogą działać równolegle, należy jawnie wyłączyć test przetwarzanie równoległe kolekcji przy użyciu `CollectionBehaviorAttribute` .</span><span class="sxs-lookup"><span data-stu-id="ff94e-121">Since test collections potentially run in parallel, you must explicitly disable test parallelization of the collections with the `CollectionBehaviorAttribute`.</span></span> <span data-ttu-id="ff94e-122">Następnie określ implementację programu `TestCollectionOrdererAttribute` .</span><span class="sxs-lookup"><span data-stu-id="ff94e-122">Then specify the implementation to the `TestCollectionOrdererAttribute`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByDisplayName.cs":::

## <a name="order-by-custom-attribute"></a><span data-ttu-id="ff94e-123">Order by — atrybut niestandardowy</span><span class="sxs-lookup"><span data-stu-id="ff94e-123">Order by custom attribute</span></span>

<span data-ttu-id="ff94e-124">Aby zamówić testy xUnit z atrybutami niestandardowymi, musisz najpierw mieć atrybut, który jest zależny od.</span><span class="sxs-lookup"><span data-stu-id="ff94e-124">To order xUnit tests with custom attributes, you first need an attribute to rely on.</span></span> <span data-ttu-id="ff94e-125">Zdefiniuj w `TestPriorityAttribute` następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ff94e-125">Define a `TestPriorityAttribute` as follows:</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Attributes/TestPriorityAttribute.cs":::

<span data-ttu-id="ff94e-126">Następnie należy wziąć pod uwagę następujące `PriorityOrderer` implementacje `ITestCaseOrderer` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ff94e-126">Next, consider the following `PriorityOrderer` implementation of the `ITestCaseOrderer` interface.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/PriorityOrderer.cs":::

<span data-ttu-id="ff94e-127">Następnie w klasie testowej ustawia się kolejność przypadków testowych z `TestCaseOrdererAttribute` do `PriorityOrderer` .</span><span class="sxs-lookup"><span data-stu-id="ff94e-127">Then in a test class you set the test case order with the `TestCaseOrdererAttribute` to the `PriorityOrderer`.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByPriorityOrder.cs":::

:::zone-end
:::zone pivot="nunit"

## <a name="order-by-priority"></a><span data-ttu-id="ff94e-128">Zamówienie według priorytetu</span><span class="sxs-lookup"><span data-stu-id="ff94e-128">Order by priority</span></span>

<span data-ttu-id="ff94e-129">Aby jawnie zamówić testy, NUnit udostępnia [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute) .</span><span class="sxs-lookup"><span data-stu-id="ff94e-129">To order tests explicitly, NUnit provides an [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute).</span></span> <span data-ttu-id="ff94e-130">Testy z tym atrybutem są uruchamiane przed testami bez.</span><span class="sxs-lookup"><span data-stu-id="ff94e-130">Tests with this attribute are started before tests without.</span></span> <span data-ttu-id="ff94e-131">Wartość Order służy do określenia kolejności uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="ff94e-131">The order value is used to determined the order to run the unit tests.</span></span>

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/NUnit.TestProject/ByOrder.cs":::

:::zone-end

## <a name="next-steps"></a><span data-ttu-id="ff94e-132">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ff94e-132">Next Steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ff94e-133">Najlepsze rozwiązania dotyczące testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="ff94e-133">Unit testing best practices</span></span>](unit-testing-best-practices.md)
