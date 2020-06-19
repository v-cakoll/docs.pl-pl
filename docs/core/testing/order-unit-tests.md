---
title: Zamów testy jednostkowe
description: Dowiedz się, jak zamówić testy jednostkowe za pomocą platformy .NET Core.
author: IEvangelist
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: 3400ae440a828054624d67c14807ee72783e466a
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989258"
---
# <a name="order-unit-tests"></a>Zamów testy jednostkowe

Czasami może być konieczne, aby testy jednostkowe były uruchamiane w określonej kolejności. W idealnym przypadku, kolejność, w której testy jednostkowe _nie_ powinny mieć znaczenia i [najlepszym rozwiązaniem](unit-testing-best-practices.md) jest uniknięcie porządkowania testów jednostkowych. Bez względu na to, może być konieczne wykonanie tej czynności. W takim przypadku w tym artykule przedstawiono sposób porządkowania przebiegów testowych.

Jeśli wolisz przeglądać kod źródłowy, zobacz przykładowe repozytorium programu [Order Core Unit Tests](/samples/dotnet/samples/order-unit-tests-cs) .

> [!TIP]
> Oprócz funkcji zamawiania opisanych w tym artykule warto rozważyć [utworzenie niestandardowych list odtwarzania z programem Visual Studio](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) jako alternatywę.

:::zone pivot="mstest"

## <a name="order-alphabetically"></a>Porządkuj alfabetycznie

W przypadku MSTest testy są automatycznie uporządkowane według ich nazwy testowej.

> [!NOTE]
> Test o nazwie `Test14` zostanie uruchomiony przed `Test2` nawet wtedy, gdy liczba `2` jest mniejsza niż `14` . Dzieje się tak dlatego, że kolejność nazw testowych używa nazwy tekstu testu.

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/MSTest.Project/ByAlphabeticalOrder.cs":::

:::zone-end
:::zone pivot="xunit"

Platforma testowa xUnit umożliwia dokładniejsze i precyzyjne sterowanie kolejnością przebiegu testu. Należy zaimplementować `ITestCaseOrderer` interfejsy i, `ITestCollectionOrderer` Aby kontrolować kolejność przypadków testowych dla klasy lub kolekcje testowe.

## <a name="order-by-test-case-alphabetically"></a>Porządkuj według przypadku testowego alfabetycznie

Aby zamówić przypadki testowe według nazwy metody, należy zaimplementować `ITestCaseOrderer` i udostępnić mechanizm porządkowania.

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/AlphabeticalOrderer.cs":::

Następnie w klasie testowej ustawia się kolejność przypadków testowych przy użyciu `TestCaseOrdererAttribute` .

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByAlphabeticalOrder.cs":::

## <a name="order-by-collection-alphabetically"></a>Kolejność według kolekcji alfabetycznie

Aby zamówić kolekcje testowe według ich nazwy wyświetlanej, należy zaimplementować `ITestCollectionOrderer` i udostępnić mechanizm porządkowania.

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/DisplayNameOrderer.cs":::

Ze względu na to, że kolekcje testowe mogą działać równolegle, należy jawnie wyłączyć test przetwarzanie równoległe kolekcji przy użyciu `CollectionBehaviorAttribute` . Następnie określ implementację programu `TestCollectionOrdererAttribute` .

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByDisplayName.cs":::

## <a name="order-by-custom-attribute"></a>Order by — atrybut niestandardowy

Aby zamówić testy xUnit z atrybutami niestandardowymi, musisz najpierw mieć atrybut, który jest zależny od. Zdefiniuj w `TestPriorityAttribute` następujący sposób:

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Attributes/TestPriorityAttribute.cs":::

Następnie należy wziąć pod uwagę następujące `PriorityOrderer` implementacje `ITestCaseOrderer` interfejsu.

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/Orderers/PriorityOrderer.cs":::

Następnie w klasie testowej ustawia się kolejność przypadków testowych z `TestCaseOrdererAttribute` do `PriorityOrderer` .

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/XUnit.TestProject/ByPriorityOrder.cs":::

:::zone-end
:::zone pivot="nunit"

## <a name="order-by-priority"></a>Zamówienie według priorytetu

Aby jawnie zamówić testy, NUnit udostępnia [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute) . Testy z tym atrybutem są uruchamiane przed testami bez. Wartość Order służy do określenia kolejności uruchamiania testów jednostkowych.

:::code language="csharp" source="~/dotnet-samples/csharp/unit-testing/NUnit.TestProject/ByOrder.cs":::

:::zone-end

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Pokrycie kodu testu jednostkowego](unit-testing-code-coverage.md)
