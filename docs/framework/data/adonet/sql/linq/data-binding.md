---
title: Powiązanie danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cbec8b02-a1e8-4ae8-a83b-bb5190413ac5
ms.openlocfilehash: 79a14e787b4fe1aa1b16ad661b11a43b12bdd718
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247379"
---
# <a name="data-binding"></a>Powiązanie danych

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje powiązanie ze wspólnymi kontrolkami, takimi jak kontrolki siatki. W szczególności [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] definiuje podstawowe wzorce do tworzenia powiązań z siatką danych i obsługi powiązań wzorzec-szczegóły, w odniesieniu do wyświetlania i aktualizowania.

## <a name="underlying-principle"></a>Podstawowa zasada

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]tłumaczy [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytania na SQL na potrzeby wykonywania w bazie danych. Wyniki są jednoznacznie wpisane `IEnumerable`. Ponieważ te obiekty są zwykłymi obiektami środowiska uruchomieniowego języka wspólnego (CLR), zwykłe powiązanie danych obiektów może służyć do wyświetlania wyników. Z drugiej strony operacje zmiany (INSERT, Updates i usunięć) wymagają wykonania dodatkowych czynności.

## <a name="operation"></a>Operacja

Niejawnie wiązanie z kontrolkami Windows Forms jest realizowane przez <xref:System.ComponentModel.IListSource>implementację. Źródła <xref:System.Data.Linq.Table%601> danych `DataQuery` (`Table<T>` C# w <xref:System.ComponentModel.IListSource>VisualBasic)i ogólne zostały zaktualizowane w celu zaimplementowania. `Table(Of T)` Aparaty powiązań danych (UI) dla interfejsu użytkownika (Windows Forms i Windows Presentation Foundation) sprawdzają, czy ich źródło <xref:System.ComponentModel.IListSource>danych implementuje. W związku z tym pisanie bezpośredniego wpływu zapytania do źródła danych kontrolki niejawnie wywołuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generowanie kolekcji, jak w poniższym przykładzie:

[!code-csharp[DLinqDataBinding#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#1)]
[!code-vb[DLinqDataBinding#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#1)]

Ten sam problem występuje w przypadku Windows Presentation Foundation:

[!code-csharp[DLinqDataBinding#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#2)]
[!code-vb[DLinqDataBinding#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#2)]

Generacji kolekcji są implementowane przez <xref:System.Data.Linq.Table%601> ogólne i `DataQuery` ogólne <xref:System.ComponentModel.IListSource.GetList%2A>w.

## <a name="ilistsource-implementation"></a>Implementacja IListSource

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]implementuje <xref:System.ComponentModel.IListSource> w dwóch lokalizacjach:

- Źródło danych to <xref:System.Data.Linq.Table%601>: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przegląda tabelę w celu wypełnienia `DataBindingList` kolekcji, która zachowuje odwołanie do tabeli.

- Źródło danych to <xref:System.Linq.IQueryable%601>. Istnieją dwa scenariusze:

  - Jeśli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Linq.IQueryable%601>program odnajdzie <xref:System.Data.Linq.Table%601> źródłowy z, Źródło zezwala na wydanie wersji, a sytuacja jest taka sama jak w pierwszym punkcie punktora.

  - Jeśli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie można znaleźć bazowego <xref:System.Data.Linq.Table%601>, źródło nie zezwala na `groupby`wydanie programu (na przykład). [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]przegląda zapytanie w celu wypełnienia ogólnego `SortableBindingList`, który jest prosty <xref:System.ComponentModel.BindingList%601> , który implementuje funkcję sortowania dla jednostek T dla danej właściwości.

## <a name="specialized-collections"></a>Specjalne kolekcje

W przypadku wielu funkcji opisanych wcześniej w tym dokumencie <xref:System.ComponentModel.BindingList%601> został on wyspecjalizowany dla niektórych różnych klas. Klasy te są ogólne `SortableBindingList` i ogólne `DataBindingList`. Oba są zadeklarowane jako wewnętrzne.

### <a name="generic-sortablebindinglist"></a>SortableBindingList ogólny

Ta klasa dziedziczy z <xref:System.ComponentModel.BindingList%601>i jest <xref:System.ComponentModel.BindingList%601>wersją do sortowania. Sortowanie jest rozwiązaniem w pamięci i nigdy nie kontaktuje się z samą bazą danych. <xref:System.ComponentModel.BindingList%601>implementuje <xref:System.ComponentModel.IBindingList> , ale nie obsługuje sortowania domyślnie. Jest to jednak <xref:System.ComponentModel.IBindingList> implementowane przy użyciu metod wirtualnych Core <xref:System.ComponentModel.BindingList%601> . Można łatwo przesłonić te metody. Zastąpienia `SortableBindingList` Ogólne,<xref:System.ComponentModel.BindingList%601.SortPropertyCore%2A> ,<xref:System.ComponentModel.BindingList%601.ApplySortCore%2A>i. <xref:System.ComponentModel.BindingList%601.SupportsSortingCore%2A> <xref:System.ComponentModel.BindingList%601.SortDirectionCore%2A> `ApplySortCore`jest wywoływany <xref:System.ComponentModel.IBindingList.ApplySort%2A> przez i sortuje listę T elementów dla danej właściwości.

Wyjątek jest wywoływany, jeśli właściwość nie należy do T.

Aby uzyskać sortowanie, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] program tworzy klasę `SortableBindingList.PropertyComparer` generyczną, która dziedziczy <xref:System.Collections.Generic.Comparer%601.System%23Collections%23IComparer%23Compare%2A> z generycznej i implementuje domyślną funkcję porównującą dla danego typu `PropertyDescriptor`T, a i kierunku. Ta klasa tworzy `Comparer` dynamicznie t, gdzie t `PropertyType` jest `PropertyDescriptor`z. Następnie domyślna funkcja porównująca jest pobierana z statycznego `Comparer`ogólnego. Wystąpienie domyślne jest uzyskiwane przy użyciu odbicia.

Rodzajowy `SortableBindingList` jest również klasą bazową dla `DataBindingList`. Ogólne `SortableBindingList` oferuje dwie metody wirtualne do zawieszania lub wznawiania elementów Dodaj/Usuń śledzenie. Te dwie metody mogą być używane na potrzeby funkcji podstawowych, takich jak sortowanie, ale w rzeczywistości są implementowane przez wyższe `DataBindingList`klasy, takie jak generyczne.

### <a name="generic-databindinglist"></a>DataBindingList ogólny

Ta klasa dziedziczy z generycznego `SortableBindingLIst`. Ogólne `DataBindingList` zachowuje odwołanie do podstawowego ogólnego `Table` elementu ogólnego `IQueryable` używane podczas wstępnego wypełniania kolekcji. Ogólne `DatabindingList` dodaje śledzenie dla elementu Dodaj/Usuń do kolekcji, zastępując `InsertItem`() i `RemoveItem`(). Implementuje także abstrakcyjną funkcję śledzenia wstrzymywania/wznawiania, aby umożliwić śledzenie warunkowe. Ta funkcja sprawia, `DataBindingList` że ogólną zaletą jest użycie polimorficznej funkcji śledzenia klas nadrzędnych.

## <a name="binding-to-entitysets"></a>Powiązanie z EntitySets

Powiązanie z `EntitySet` jest przypadkiem specjalnym `EntitySet` , ponieważ jest już kolekcją <xref:System.ComponentModel.IBindingList>implementującą. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]dodaje obsługę sortowania i anulowania (<xref:System.ComponentModel.ICancelAddNew>). `EntitySet` Klasa używa wewnętrznej listy do przechowywania jednostek. Ta lista jest kolekcją niskiego poziomu opartą na tablicy ogólnej, klasie generycznej `ItemList` .

### <a name="adding-a-sorting-feature"></a>Dodawanie funkcji sortowania

Tablice oferują metodę`Array.Sort()`Sort (), która może być używana `Comparer` z T. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] używa klasy generycznej `SortableBindingList.PropertyComparer` opisanej wcześniej w tym temacie, aby uzyskać tę `Comparer` Właściwość oraz kierunek sortowania. Metoda jest dodawana do elementu `ItemList` ogólnego w celu wywołania tej funkcji. `ApplySort`

`EntitySet` Po stronie należy teraz zadeklarować obsługę sortowania:

- <xref:System.ComponentModel.IBindingList.SupportsSorting%2A>zwraca `true`wartość.

- <xref:System.ComponentModel.IBindingList.ApplySort%2A>wywołania `entities.ApplySort()` , a `OnListChanged()`następnie.

- <xref:System.ComponentModel.IBindingList.SortDirection%2A>i <xref:System.ComponentModel.IBindingList.SortProperty%2A> właściwości uwidaczniają bieżącą definicję sortowania, która jest przechowywana w lokalnych elementach członkowskich.

W przypadku używania elementu System. Windows. Forms. BindingSource i powiązania > zamiaru obiektu EntitySet\<z obiektem system. Windows. Forms. BindingSource. DataSource, należy wywołać zamiar obiektu EntitySet\<>. GetNewBindingList się z aktualizacją BindingSource. list.

Jeśli używasz elementu System. Windows. Forms. BindingSource i ustawimy właściwość BindingSource. DataMember i ustawimy wartość BindingSource. DataSource dla klasy, która ma właściwość o nazwie w elemencie BindingSource. DataMember, która uwidacznia\<> zamiaru obiektu EntitySet, należy nie trzeba wywoływać >\<zamiaru obiektu EntitySet. GetNewBindingList zaktualizować element BindingSource. list, ale utracisz możliwość sortowania.

## <a name="caching"></a>Buforowanie

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]zapytania implementują <xref:System.ComponentModel.IListSource.GetList%2A>. Gdy Klasa BindingSource Windows Forms jest zgodna z tym interfejsem, wywołuje metodę GetList () trzy czasu dla jednego połączenia. Aby obejść tę sytuację, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje pamięć podręczną na wystąpienie do przechowywania i zawsze zwraca tę samą wygenerowaną kolekcję.

## <a name="cancellation"></a>Anulowanie

<xref:System.ComponentModel.IBindingList><xref:System.ComponentModel.IBindingList.AddNew%2A> definiuje metodę, która jest używana przez kontrolki do tworzenia nowego elementu z kolekcji powiązanej. `DataGridView` Kontrolka pokazuje tę funkcję bardzo dobrze, gdy ostatni widoczny wiersz zawiera gwiazdkę w nagłówku. Gwiazdka pokazuje, że można dodać nowy element.

Oprócz tej funkcji kolekcja może również implementować <xref:System.ComponentModel.ICancelAddNew>. Ta funkcja umożliwia anulowanie przez kontrolki lub zweryfikowanie, czy nowy edytowany element został sprawdzony.

<xref:System.ComponentModel.ICancelAddNew>jest zaimplementowany we wszystkich [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kolekcjach DataBound ( `SortableBindingList` rodzajowe `EntitySet`i ogólne). W obu implementacjach kod wykonuje następujące czynności:

- Umożliwia wstawianie i usuwanie elementów z kolekcji.

- Nie śledzi zmian, o ile nie zostanie zatwierdzona przez interfejs użytkownika.

- Nie śledzi zmian, o ile wersja została anulowana (<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>).

- Umożliwia śledzenie podczas zatwierdzania wersji (<xref:System.ComponentModel.ICancelAddNew.EndNew%2A>).

- Pozwala na normalne zachowanie kolekcji, jeśli nie pochodzi <xref:System.ComponentModel.IBindingList.AddNew%2A>nowy element.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Ta sekcja wywołuje kilka elementów, które mogą pomóc w rozwiązywaniu problemów z aplikacjami do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzenia powiązań danych.

- Musisz użyć właściwości; Używanie tylko pól jest niewystarczające. Windows Forms wymaga tego użycia.

- Domyślnie `image` `timestamp` ,, i typy baz danych są mapowane na tablicę bajtową. `varbinary` Ponieważ `ToString()` nie jest to obsługiwane w tym scenariuszu, nie można wyświetlić tych obiektów.

- Składowa klasy zamapowana na klucz podstawowy ma metodę ustawiającą, ale [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje zmiany tożsamości obiektu. W związku z tym nie można zaktualizować klucza podstawowego/unikatowego używanego w mapowaniu w bazie danych. Zmiana w siatce powoduje wyjątek podczas wywoływania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.

- Jeśli jednostka jest powiązana w dwóch oddzielnych siatkach (na przykład jeden wzorzec i inne szczegóły), a `Delete` w siatce głównej nie jest propagowany do siatki szczegółów.

## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](background-information.md)
