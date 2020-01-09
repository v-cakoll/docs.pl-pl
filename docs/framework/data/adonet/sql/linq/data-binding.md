---
title: Powiązanie danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cbec8b02-a1e8-4ae8-a83b-bb5190413ac5
ms.openlocfilehash: c7048d292bdf5c1372d5f8f174f7f0e84efa7593
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634719"
---
# <a name="data-binding"></a>Powiązanie danych

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje powiązania ze wspólnymi kontrolkami, takimi jak kontrolki siatki. W szczególności [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] definiuje podstawowe wzorce do tworzenia powiązań z siatką danych i obsługi powiązań wzorzec-szczegóły, w odniesieniu do wyświetlania i aktualizowania.

## <a name="underlying-principle"></a>Podstawowa zasada

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy zapytania LINQ na SQL w celu wykonania w bazie danych. Wyniki mają silnie wpisane `IEnumerable`. Ponieważ te obiekty są zwykłymi obiektami środowiska uruchomieniowego języka wspólnego (CLR), zwykłe powiązanie danych obiektów może służyć do wyświetlania wyników. Z drugiej strony operacje zmiany (INSERT, Updates i usunięć) wymagają wykonania dodatkowych czynności.

## <a name="operation"></a>Operacja

Niejawnie wiązanie z kontrolkami Windows Forms jest realizowane przez implementację <xref:System.ComponentModel.IListSource>. Źródła danych: ogólne <xref:System.Data.Linq.Table%601> (`Table<T>` C# `Table(Of T)` w Visual Basic) i ogólne `DataQuery` zostały zaktualizowane w celu zaimplementowania <xref:System.ComponentModel.IListSource>. Aparaty powiązań danych (UI) dla interfejsu użytkownika (Windows Forms i Windows Presentation Foundation) sprawdzają, czy ich źródło danych implementuje <xref:System.ComponentModel.IListSource>. W związku z tym zapisywanie bezpośredniego wpływu zapytania do źródła danych kontrolki niejawnie wywołuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generacja kolekcji, jak w poniższym przykładzie:

[!code-csharp[DLinqDataBinding#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#1)]
[!code-vb[DLinqDataBinding#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#1)]

Ten sam problem występuje w przypadku Windows Presentation Foundation:

[!code-csharp[DLinqDataBinding#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#2)]
[!code-vb[DLinqDataBinding#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#2)]

Generacji kolekcji są implementowane przez ogólne <xref:System.Data.Linq.Table%601> i ogólne `DataQuery` w <xref:System.ComponentModel.IListSource.GetList%2A>.

## <a name="ilistsource-implementation"></a>Implementacja IListSource

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje <xref:System.ComponentModel.IListSource> w dwóch lokalizacjach:

- Źródło danych to <xref:System.Data.Linq.Table%601>: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przegląda tabelę, aby wypełnić kolekcję `DataBindingList`, która zachowuje odwołanie do tabeli.

- Źródło danych jest <xref:System.Linq.IQueryable%601>. Istnieją dwa scenariusze:

  - Jeśli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] odnajdzie bazowe <xref:System.Data.Linq.Table%601> z <xref:System.Linq.IQueryable%601>, Źródło zezwala na wersję i sytuacja jest taka sama jak w pierwszym punkcie punktora.

  - Jeśli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie może znaleźć bazowego <xref:System.Data.Linq.Table%601>, źródło nie zezwala na wydanie programu (na przykład `groupby`). [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przegląda zapytanie w celu wypełnienia ogólnego `SortableBindingList`, który jest prostym <xref:System.ComponentModel.BindingList%601>em, który implementuje funkcję sortowania dla jednostek T dla danej właściwości.

## <a name="specialized-collections"></a>Specjalne kolekcje

W przypadku wielu funkcji opisanych wcześniej w tym dokumencie <xref:System.ComponentModel.BindingList%601> była wyspecjalizowana dla niektórych różnych klas. Te klasy są ogólnymi `SortableBindingList`ami i ogólnymi `DataBindingList`. Oba są zadeklarowane jako wewnętrzne.

### <a name="generic-sortablebindinglist"></a>SortableBindingList ogólny

Ta klasa dziedziczy z <xref:System.ComponentModel.BindingList%601>i jest wersją <xref:System.ComponentModel.BindingList%601>do sortowania. Sortowanie jest rozwiązaniem w pamięci i nigdy nie kontaktuje się z samą bazą danych. <xref:System.ComponentModel.BindingList%601> implementuje <xref:System.ComponentModel.IBindingList>, ale nie obsługuje sortowania domyślnie. <xref:System.ComponentModel.BindingList%601> implementuje jednak <xref:System.ComponentModel.IBindingList> przy użyciu metod wirtualnych *Core* . Można łatwo przesłonić te metody. Ogólne `SortableBindingList` przesłania <xref:System.ComponentModel.BindingList%601.SupportsSortingCore%2A>, <xref:System.ComponentModel.BindingList%601.SortPropertyCore%2A>, <xref:System.ComponentModel.BindingList%601.SortDirectionCore%2A>i <xref:System.ComponentModel.BindingList%601.ApplySortCore%2A>. `ApplySortCore` jest wywoływana przez <xref:System.ComponentModel.IBindingList.ApplySort%2A> i sortuje listę elementów T dla danej właściwości.

Wyjątek jest wywoływany, jeśli właściwość nie należy do T.

Aby uzyskać sortowanie, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy klasę generyczną `SortableBindingList.PropertyComparer`, która dziedziczy z generycznego <xref:System.Collections.Generic.Comparer%601.System%23Collections%23IComparer%23Compare%2A> i implementuje domyślną funkcję porównującą dla danego typu T, `PropertyDescriptor`i kierunku. Ta klasa dynamicznie tworzy `Comparer` T, gdzie T jest `PropertyType` `PropertyDescriptor`. Następnie domyślna funkcja porównująca jest pobierana z statycznej `Comparer`ogólnej. Wystąpienie domyślne jest uzyskiwane przy użyciu odbicia.

`SortableBindingList` generyczna jest również klasą bazową dla `DataBindingList`. `SortableBindingList` generyczne oferuje dwie metody wirtualne do zawieszania lub wznawiania elementów Dodaj/Usuń śledzenie. Te dwie metody mogą być używane na potrzeby funkcji podstawowych, takich jak sortowanie, ale w rzeczywistości są implementowane przez wyższe klasy, takie jak ogólne `DataBindingList`.

### <a name="generic-databindinglist"></a>DataBindingList ogólny

Ta klasa dziedziczy z ogólnej `SortableBindingLIst`. Ogólne `DataBindingList` zachowuje odwołanie do podstawowej `Table` ogólnej `IQueryable` używane podczas wstępnego wypełniania kolekcji. Ogólne `DatabindingList` dodaje śledzenie dla elementu Dodaj/Usuń do kolekcji, zastępując `InsertItem`() i `RemoveItem`(). Implementuje także abstrakcyjną funkcję śledzenia wstrzymywania/wznawiania, aby umożliwić śledzenie warunkowe. Ta funkcja sprawia, że ogólne `DataBindingList` korzystać ze wszystkich polimorficznych zastosowań funkcji śledzenia klas nadrzędnych.

## <a name="binding-to-entitysets"></a>Powiązanie z EntitySets

Powiązanie do `EntitySet` jest szczególnym przypadkiem, ponieważ `EntitySet` jest już kolekcją implementującą <xref:System.ComponentModel.IBindingList>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dodaje obsługę sortowania i anulowania (<xref:System.ComponentModel.ICancelAddNew>). Klasa `EntitySet` używa wewnętrznej listy do przechowywania jednostek. Ta lista jest kolekcją niskiego poziomu opartą na tablicy ogólnej, ogólnej klasie `ItemList`.

### <a name="adding-a-sorting-feature"></a>Dodawanie funkcji sortowania

Tablice oferują metodę sortowania (`Array.Sort()`), która może być używana z `Comparer` T. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] używa klasy generycznej `SortableBindingList.PropertyComparer` opisanej wcześniej w tym temacie, aby uzyskać ten `Comparer` właściwości i kierunek sortowania. Metoda `ApplySort` zostanie dodana do generycznego `ItemList` w celu wywołania tej funkcji.

Po stronie `EntitySet` musisz teraz zadeklarować obsługę sortowania:

- <xref:System.ComponentModel.IBindingList.SupportsSorting%2A> zwraca `true`.

- <xref:System.ComponentModel.IBindingList.ApplySort%2A> wywołań `entities.ApplySort()` a następnie `OnListChanged()`.

- Właściwości <xref:System.ComponentModel.IBindingList.SortDirection%2A> i <xref:System.ComponentModel.IBindingList.SortProperty%2A> uwidaczniają bieżącą definicję sortowania, która jest przechowywana w lokalnych elementach członkowskich.

W przypadku używania elementu System. Windows. Forms. BindingSource i powiązania >\<obiektu EntitySet z obiektem system. Windows. Forms. BindingSource. DataSource, należy wywołać > zamiaru obiektu EntitySet\<. GetNewBindingList się z aktualizacją BindingSource. list.

Jeśli używasz elementu System. Windows. Forms. BindingSource i ustawimy właściwość BindingSource. DataMember i ustawimy wartość BindingSource. DataSource dla klasy, która ma właściwość o nazwie w elemencie BindingSource. DataMember, która uwidacznia > zamiaru EntitySet\<, nie musisz wywoływać > zamiaru elementu EntitySet\<. GetNewBindingList zaktualizować element BindingSource. list, ale utracisz możliwość sortowania.

## <a name="caching"></a>Buforowanie

zapytania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementują <xref:System.ComponentModel.IListSource.GetList%2A>. Gdy Klasa BindingSource Windows Forms jest zgodna z tym interfejsem, wywołuje metodę GetList () trzy czasu dla jednego połączenia. Aby obejść tę sytuację, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje pamięć podręczną na wystąpienie do przechowywania i zawsze zwraca tę samą wygenerowaną kolekcję.

## <a name="cancellation"></a>Anulowanie

<xref:System.ComponentModel.IBindingList> definiuje metodę <xref:System.ComponentModel.IBindingList.AddNew%2A>, która jest używana przez kontrolki do tworzenia nowego elementu z kolekcji powiązanej. Kontrolka `DataGridView` wyświetla tę funkcję bardzo dobrze, gdy ostatni widoczny wiersz zawiera gwiazdkę w nagłówku. Gwiazdka pokazuje, że można dodać nowy element.

Oprócz tej funkcji kolekcja może również implementować <xref:System.ComponentModel.ICancelAddNew>. Ta funkcja umożliwia anulowanie przez kontrolki lub zweryfikowanie, czy nowy edytowany element został sprawdzony.

<xref:System.ComponentModel.ICancelAddNew> jest zaimplementowana we wszystkich [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kolekcjach DataBound (ogólne `SortableBindingList` i ogólne `EntitySet`). W obu implementacjach kod wykonuje następujące czynności:

- Umożliwia wstawianie i usuwanie elementów z kolekcji.

- Nie śledzi zmian, o ile nie zostanie zatwierdzona przez interfejs użytkownika.

- Nie śledzi zmian, o ile ta wersja została anulowana (<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>).

- Umożliwia śledzenie podczas zatwierdzania wersji (<xref:System.ComponentModel.ICancelAddNew.EndNew%2A>).

- Pozwala na normalne zachowanie kolekcji, jeśli nowy element nie pochodzi z <xref:System.ComponentModel.IBindingList.AddNew%2A>.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Ta sekcja wywołuje kilka elementów, które mogą pomóc w rozwiązywaniu problemów z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji powiązań danych.

- Musisz użyć właściwości; Używanie tylko pól jest niewystarczające. Windows Forms wymaga tego użycia.

- Domyślnie `image`, `varbinary`i `timestamp` typy baz danych mapują na tablicę bajtową. Ponieważ `ToString()` nie jest obsługiwana w tym scenariuszu, nie można wyświetlić tych obiektów.

- Składowa klasy zamapowana na klucz podstawowy ma metodę ustawiającą, ale [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje zmiany tożsamości obiektu. W związku z tym nie można zaktualizować klucza podstawowego/unikatowego używanego w mapowaniu w bazie danych. Zmiana w siatce powoduje wyjątek podczas wywoływania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.

- Jeśli jednostka jest powiązana w dwóch oddzielnych siatkach (na przykład jeden wzorzec i inne szczegóły), `Delete` w siatce głównej nie są propagowane do siatki szczegółów.

## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](background-information.md)
