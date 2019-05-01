---
title: Powiązanie danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cbec8b02-a1e8-4ae8-a83b-bb5190413ac5
ms.openlocfilehash: 66964497159c5c03a9070090ee60b43fa7d31abf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032889"
---
# <a name="data-binding"></a>Powiązanie danych

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Obsługa powiązań do wspólnych formantów, takich jak formanty siatki. W szczególności [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] definiuje wzorców podstawowych dla powiązania do siatki danych i obsługiwania wzorzec / szczegół powiązanie, zarówno w odniesieniu do wyświetlania i aktualizowania.

## <a name="underlying-principle"></a>Podstawowe zasady

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wykonuje translację [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytania do bazy danych SQL do wykonania w bazie danych. Wyniki są silnie typizowane `IEnumerable`. Ponieważ te obiekty są zwykłe obiekty środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego, powiązanie danych obiektu zwykłych może służyć do wyświetlania wyników. Z drugiej strony zmiana operations (operacje wstawiania, aktualizacji i usunięć) wymagają wykonania dodatkowych czynności.

## <a name="operation"></a>Operacja

Niejawnie powiązywanie kontrolek formularzy Windows Forms odbywa się przez zaimplementowanie <xref:System.ComponentModel.IListSource>. Źródła danych ogólnych <xref:System.Data.Linq.Table%601> (`Table<T>` w C# lub `Table(Of T)` w języku Visual Basic) i ogólny `DataQuery` zostały zaktualizowanie, aby zaimplementować <xref:System.ComponentModel.IListSource>. Użytkownika interfejsie powiązania danych aparatów (Windows Forms i programu Windows Presentation Foundation) zarówno Przetestuj swoje dane źródłowe implementuje <xref:System.ComponentModel.IListSource>. W związku z tym, zapisywanie bezpośrednie przejęcie zapytania ze źródłem danych w kontrolce niejawnie wywołania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generacjach, jak w poniższym przykładzie:

[!code-csharp[DLinqDataBinding#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#1)]
[!code-vb[DLinqDataBinding#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#1)]

Taki sam odbywa się za pomocą programu Windows Presentation Foundation:

[!code-csharp[DLinqDataBinding#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#2)]
[!code-vb[DLinqDataBinding#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#2)]

Kolekcja pokoleń są implementowane przez ogólny <xref:System.Data.Linq.Table%601> i ogólny `DataQuery` w <xref:System.ComponentModel.IListSource.GetList%2A>.

## <a name="ilistsource-implementation"></a>Implementacja IListSource

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje <xref:System.ComponentModel.IListSource> w dwóch miejscach:

- Źródło danych jest <xref:System.Data.Linq.Table%601>: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przegląda tabeli, aby wypełnić `DataBindingList` kolekcji, która przechowuje odwołania w tabeli.

- Źródło danych jest <xref:System.Linq.IQueryable%601>. Istnieją dwa scenariusze:

  - Jeśli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] znajduje podstawowe <xref:System.Data.Linq.Table%601> z <xref:System.Linq.IQueryable%601>źródła umożliwia edition i ta sytuacja jest taki sam jak w pierwszym punkcie.

  - Jeśli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie można odnaleźć bazowej <xref:System.Data.Linq.Table%601>, źródło nie zezwala na wersji (na przykład `groupby`). [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przegląda zapytanie, aby wypełnić ogólnego `SortableBindingList`, czyli prostego <xref:System.ComponentModel.BindingList%601> implementującej funkcję sortowania dla jednostek T dla danej właściwości.

## <a name="specialized-collections"></a>Specjalne kolekcje

Dla wielu funkcji, które opisano wcześniej w tym dokumencie <xref:System.ComponentModel.BindingList%601> wyspecjalizowane kilka różnych klas. Te klasy są rodzajowe `SortableBindingList` i ogólny `DataBindingList`. Oba są deklarowane jako wewnętrzne.

### <a name="generic-sortablebindinglist"></a>Ogólny SortableBindingList

Ta klasa dziedziczy <xref:System.ComponentModel.BindingList%601>, i jest sortowanie wersją <xref:System.ComponentModel.BindingList%601>. Sortowanie to rozwiązanie w pamięci i nigdy nie kontaktuje się sama baza danych. <xref:System.ComponentModel.BindingList%601> implementuje <xref:System.ComponentModel.IBindingList> , ale nie obsługuje sortowania domyślnie. Jednak <xref:System.ComponentModel.BindingList%601> implementuje <xref:System.ComponentModel.IBindingList> za pomocą wirtualnego *core* metody. Można łatwo zastąpić te metody. Ogólny `SortableBindingList` zastępuje <xref:System.ComponentModel.BindingList%601.SupportsSortingCore%2A>, <xref:System.ComponentModel.BindingList%601.SortPropertyCore%2A>, <xref:System.ComponentModel.BindingList%601.SortDirectionCore%2A>, i <xref:System.ComponentModel.BindingList%601.ApplySortCore%2A>. `ApplySortCore` jest wywoływana przez <xref:System.ComponentModel.IBindingList.ApplySort%2A> i sortuje listę elementów T dla danej właściwości.

Wyjątek jest zgłaszany, jeśli właściwość nie należy do T.

Do osiągnięcia, sortowanie, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy ogólnego `SortableBindingList.PropertyComparer` klasy, która dziedziczy z ogólnego <xref:System.Collections.Generic.Comparer%601.System%23Collections%23IComparer%23Compare%2A> i implementuje domyślny moduł porównujący dla danego typu T, `PropertyDescriptor`i kierunek. Ta klasa dynamicznie tworzy `Comparer` t, gdzie T jest `PropertyType` z `PropertyDescriptor`. Następnie, domyślny moduł porównujący jest pobierana z ogólnej statycznej `Comparer`. Wystąpienie domyślne są uzyskiwane przy użyciu odbicia.

Ogólny `SortableBindingList` jest również klasę bazową dla `DataBindingList`. Ogólny `SortableBindingList` oferuje dwie metody wirtualnej zawieszanie lub wznawianie elementów dodawania/usuwania śledzenia. Te dwie metody mogą służyć do podstawowych funkcji, takich jak sortowanie, ale tak naprawdę będą wykonywane przez klasy górnego, takie jak ogólny `DataBindingList`.

### <a name="generic-databindinglist"></a>Ogólny DataBindingList

Ta klasa dziedziczy ogólny `SortableBindingLIst`. Ogólny `DataBindingList` przechowuje odwołanie na podstawowych ogólny `Table` z ogólnego `IQueryable` używane do początkowego wypełnianie kolekcji. Ogólny `DatabindingList` śledzenia dla elementu Dodawanie/usuwanie są dodawane do kolekcji przez zastąpienie `InsertItem`() i `RemoveItem`(). Implementuje także abstrakcyjne wstrzymań/wznowień śledzenia funkcję śledzenia warunkowego. Ta funkcja sprawia, że ogólny `DataBindingList` zalet polimorficznych użycie funkcji śledzenia nadrzędnej klasy.

## <a name="binding-to-entitysets"></a>Powiązania do obiektów Entityset

Powiązanie z `EntitySet` jest szczególnym przypadkiem, ponieważ `EntitySet` jest już kolekcji, która implementuje <xref:System.ComponentModel.IBindingList>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dodaje sortowania i anulowania (<xref:System.ComponentModel.ICancelAddNew>) pomocy technicznej. `EntitySet` Klasa używa wewnętrznej listy do przechowywania obiektów. Ta lista jest niskiego poziomu kolekcji, oparte na ogólna tablica ogólnego `ItemList` klasy.

### <a name="adding-a-sorting-feature"></a>Dodanie funkcji sortowania

Tablice oferują sort — metoda (`Array.Sort()`), które mogą być używane z `Comparer` z T. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] korzysta z ogólnego `SortableBindingList.PropertyComparer` klasy opisane we wcześniejszej części tego tematu, aby uzyskać `Comparer` dla właściwości i kierunek sortowania na. `ApplySort` Metoda jest dodawana do ogólnego `ItemList` do wywołania tej funkcji.

Na `EntitySet` stronie, teraz należy zadeklarować sortowania pomocy technicznej:

- <xref:System.ComponentModel.IBindingList.SupportsSorting%2A> Zwraca `true`.

- <xref:System.ComponentModel.IBindingList.ApplySort%2A> wywołania `entities.ApplySort()` i następnie `OnListChanged()`.

- <xref:System.ComponentModel.IBindingList.SortDirection%2A> i <xref:System.ComponentModel.IBindingList.SortProperty%2A> właściwości ujawnić bieżącej definicji sortowania są przechowywane w lokalnych elementów.

Kiedy używać System.Windows.Forms.BindingSource i powiązać obiektu EntitySet\<TEntity > Aby System.Windows.Forms.BindingSource.DataSource, należy wywołać element EntitySet\<TEntity >. GetNewBindingList można zaktualizować BindingSource.List.

Jeśli możesz użyć System.Windows.Forms.BindingSource i ustaw właściwość BindingSource.DataMember i ustawić BindingSource.DataSource do klasy, która ma właściwość o nazwie w BindingSource.DataMember, który udostępnia obiekt EntitySet\<TEntity >, możesz nie trzeba wywołać obiekt EntitySet\<TEntity >. GetNewBindingList można zaktualizować BindingSource.List, ale możesz utracić możliwość sortowania.

## <a name="caching"></a>Buforowanie

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Implementowanie zapytań <xref:System.ComponentModel.IListSource.GetList%2A>. Jeśli klasa kontrolki BindingSource formularzy Windows Forms spełnia ten interfejs, wywołuje GetList() trzy czasu dla pojedynczego połączenia. Aby obejść tę sytuację [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje pamięci podręcznej dla każdego wystąpienia do przechowywania i zawsze zwracają takie same generowane kolekcji.

## <a name="cancellation"></a>Anulowanie

<xref:System.ComponentModel.IBindingList> definiuje <xref:System.ComponentModel.IBindingList.AddNew%2A> metodę, która jest używany przez formanty, aby utworzyć nowy element w powiązanej kolekcji. `DataGridView` Kontrolka pokaże to funkcji bardzo dobrze, jeśli ostatni wiersz widoczne zawiera gwiazdki w jej nagłówku. Gwiazdka dowiesz się, że można dodać nowego elementu.

Oprócz tej funkcji można też wdrożyć kolekcję <xref:System.ComponentModel.ICancelAddNew>. Ta funkcja umożliwia formantów do anulowania lub weryfikacji, aby edytować nową, czy element został zweryfikowany, czy nie.

<xref:System.ComponentModel.ICancelAddNew> jest implementowane w wszystkie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kolekcji powiązanych z danymi (ogólny `SortableBindingList` i ogólny `EntitySet`). W obu implementacjach kod wykonuje w następujący sposób:

- Umożliwia elementy można wstawić, a następnie usuwane z kolekcji.

- Nie śledzi zmiany, tak długo, jak interfejs użytkownika nie zatwierdzić wersję.

- Nie śledzi zmiany, tak długo, jak wersja zostanie anulowane (<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>).

- Umożliwia śledzenie, gdy wersja jest zatwierdzona (<xref:System.ComponentModel.ICancelAddNew.EndNew%2A>).

- Umożliwia zbieranie działać prawidłowo, jeśli nowy element nie pochodzi z <xref:System.ComponentModel.IBindingList.AddNew%2A>.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

W tej sekcji wywołuje kilka elementów, które mogą pomóc w rozwiązaniu usługi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji do powiązania danych.

- Należy użyć właściwości; Korzystanie tylko z pól, nie jest wystarczające. Formularze Windows wymagają tego użycia.

- Domyślnie `image`, `varbinary`, i `timestamp` mapowania typów bazy danych do tablicy typu byte. Ponieważ `ToString()` nie jest obsługiwany w tym scenariuszu nie można wyświetlić te obiekty.

- Element członkowski klasy mapowane na klucz podstawowy ma metody ustawiającej, ale [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje zmiany tożsamości obiektu. W związku z tym podstawowy/unikalny klucz, który jest używany w mapowaniu nie można zaktualizować w bazie danych. Zmiany w siatce, powoduje wyjątek podczas wywoływania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.

- Jeśli jednostka jest powiązana w dwóch oddzielnych siatkach (na przykład jednego serwera głównego i innym szczegółów) `Delete` w siatce wzorca nie są propagowane do siatki szczegółów.

## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
