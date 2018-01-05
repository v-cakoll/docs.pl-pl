---
title: "Powiązanie danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: cbec8b02-a1e8-4ae8-a83b-bb5190413ac5
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 99aa438c64fdb8f2d14207e6afb06afa8e5f014a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="data-binding"></a>Powiązanie danych
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje powiązanie z formanty standardowe, takie jak formanty siatki. W szczególności [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] definiuje wzorców podstawowych dla powiązania do siatki danych i ich obsługi główny szczegółowy powiązanie, zarówno w odniesieniu do wyświetlanie i aktualizowanie.  
  
## <a name="underlying-principle"></a>Podstawowe zasady  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]wykonuje translację [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytania do bazy danych SQL do wykonania na bazie danych. Wyniki są silnie typizowane `IEnumerable`. Ponieważ te obiekty są zwykłej wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) obiektów, powiązanie danych zwykłego obiektu można używać do wyświetlania wyników. Z drugiej strony operacje zmiany (wstawienia, aktualizacje i usunięcia) wymagają dodatkowych czynności.  
  
## <a name="operation"></a>Operacja  
 Niejawnie powiązanie z kontrolkami formularzy systemu Windows odbywa się zaimplementowanie <xref:System.ComponentModel.IListSource>. Źródła danych jest ogólnym <xref:System.Data.Linq.Table%601> (`Table<T>` w języku C# lub `Table(Of T)` w [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) i rodzajowy `DataQuery` zostały zaktualizowane do zaimplementowania <xref:System.ComponentModel.IListSource>. Użytkownika interfejsu wiązania danych aparaty (formularze systemu Windows i Windows Presentation Foundation) zarówno test sprawdzający, czy źródło ich danych implementuje <xref:System.ComponentModel.IListSource>. W związku z tym zapisywania bezpośredniego przejęcie zapytania ze źródłem danych formantu niejawnie wywołania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generowania kolekcji, jak w poniższym przykładzie:  
  
 [!code-csharp[DLinqDataBinding#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#1)]
 [!code-vb[DLinqDataBinding#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#1)]  
  
 Taki sam występuje o Windows Presentation Foundation:  
  
 [!code-csharp[DLinqDataBinding#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#2)]
 [!code-vb[DLinqDataBinding#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#2)]  
  
 Generacje kolekcji są implementowane przez ogólny <xref:System.Data.Linq.Table%601> i rodzajowy `DataQuery` w <xref:System.ComponentModel.IListSource.GetList%2A>.  
  
## <a name="ilistsource-implementation"></a>Element IListSource implementacji  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]implementuje <xref:System.ComponentModel.IListSource> w dwóch miejscach:  
  
-   Źródło danych jest <xref:System.Data.Linq.Table%601>: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przejdzie do wypełnienia tabeli `DataBindingList` kolekcja, która przechowuje odwołanie do tabeli.  
  
-   Źródło danych jest <xref:System.Linq.IQueryable%601>. Istnieją dwa scenariusze:  
  
    -   Jeśli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] znajdzie odpowiadającego <xref:System.Data.Linq.Table%601> z <xref:System.Linq.IQueryable%601>, źródło umożliwia edition i sytuacji jest taki sam jak pierwszy punkt punktor.  
  
    -   Jeśli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie można znaleźć odpowiadającego <xref:System.Data.Linq.Table%601>, źródło nie umożliwia edition (na przykład `groupby`). [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Umożliwia wyszukanie zapytania, aby wypełnić ogólnego `SortableBindingList`, która jest prostą <xref:System.ComponentModel.BindingList%601> implementującej funkcję sortowania dla jednostek T dla danej właściwości.  
  
## <a name="specialized-collections"></a>Specjalne kolekcje  
 Wiele funkcji opisanych wcześniej w tym dokumencie <xref:System.ComponentModel.BindingList%601> specjalizacja została określona na kilka różnych klas. Te klasy są ogólne `SortableBindingList` i rodzajowy `DataBindingList`. Zarówno został zadeklarowany jako wewnętrzne.  
  
### <a name="generic-sortablebindinglist"></a>Ogólny SortableBindingList  
 Ta klasa dziedziczy <xref:System.ComponentModel.BindingList%601>, i jest to wersja sortowanie <xref:System.ComponentModel.BindingList%601>. Sortowanie jest rozwiązaniem w pamięci i nigdy nie kontaktuje się z bazy danych. <xref:System.ComponentModel.BindingList%601>implementuje <xref:System.ComponentModel.IBindingList> , ale nie obsługuje sortowania domyślnie. Jednak <xref:System.ComponentModel.BindingList%601> implementuje <xref:System.ComponentModel.IBindingList> z wirtualnego *core* metody. Można łatwo zastępować te metody. Ogólny `SortableBindingList` zastępuje <xref:System.ComponentModel.BindingList%601.SupportsSortingCore%2A>, <xref:System.ComponentModel.BindingList%601.SortPropertyCore%2A>, <xref:System.ComponentModel.BindingList%601.SortDirectionCore%2A>, i <xref:System.ComponentModel.BindingList%601.ApplySortCore%2A>. `ApplySortCore`Metoda jest wywoływana przez <xref:System.ComponentModel.IBindingList.ApplySort%2A> i sortuje listę elementów T dla danej właściwości.  
  
 Zgłoszony wyjątek, jeśli właściwość nie należy do T.  
  
 Do osiągnięcia, sortowania, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy ogólnego `SortableBindingList.PropertyComparer` klasy, która dziedziczy ogólny <xref:System.Collections.Generic.Comparer%601.System%23Collections%23IComparer%23Compare%2A> i implementuje domyślna funkcja porównująca dla danego typu T, `PropertyDescriptor`i kierunku. Ta klasa dynamicznie tworzy `Comparer` t, gdzie T jest `PropertyType` z `PropertyDescriptor`. Następnie, domyślna funkcja porównująca są pobierane z ogólnego statycznych `Comparer`. Wystąpienie domyślne są uzyskiwane przy użyciu odbicia.  
  
 Ogólny `SortableBindingList` jest również klasę podstawową dla `DataBindingList`. Ogólny `SortableBindingList` oferuje dwie metody wirtualne do wstrzymywania i wznawiania elementów dodawania i usuwania śledzenia. Te dwie metody mogą służyć do podstawowej funkcji, takich jak sortowanie, ale naprawdę będą wykonywane przez wielką klas takich jak zwykły `DataBindingList`.  
  
### <a name="generic-databindinglist"></a>Ogólny DataBindingList  
 Ta klasa dziedziczy ogólny `SortableBindingLIst`. Ogólny `DataBindingList` przechowuje odwołanie odpowiadającego ogólnego `Table` z ogólnego `IQueryable` używane do początkowego wypełnianie kolekcji. Ogólny `DatabindingList` dodaje śledzenia dla usunąć element do kolekcji przez zastąpienie `InsertItem`() i `RemoveItem`(). Implementuje abstrakcyjny wstrzymanie/wznowienie śledzenia funkcję śledzenia warunkowego. Ta funkcja umożliwia ogólne `DataBindingList` zalet polimorficznych użycie funkcji śledzenia nadrzędnej klasy.  
  
## <a name="binding-to-entitysets"></a>Powiązanie do obiektów EntitySets  
 Powiązanie z `EntitySet` jest szczególnych przypadkach, ponieważ `EntitySet` jest już kolekcji, który implementuje <xref:System.ComponentModel.IBindingList>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]dodaje sortowania i anulowania (<xref:System.ComponentModel.ICancelAddNew>) obsługuje. `EntitySet` Klasy używa wewnętrznej listy do przechowywania obiektów. Ta lista jest kolekcją niskiego poziomu, oparte na ogólna tablica ogólnego `ItemList` klasy.  
  
### <a name="adding-a-sorting-feature"></a>Dodawanie funkcji sortowania  
 Tablice oferują sort — metoda (`Array.Sort()`), który może być używany z `Comparer` z T. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] korzysta z ogólnego `SortableBindingList.PropertyComparer` klasy opisem we wcześniejszej części tego tematu, aby uzyskać `Comparer` właściwość i kierunek sortowania na. `ApplySort` Metoda jest dodawana do zwykłego `ItemList` do wywołania tej funkcji.  
  
 Na `EntitySet` stronie, teraz należy zadeklarować sortowania pomocy technicznej:  
  
-   <xref:System.ComponentModel.IBindingList.SupportsSorting%2A>Zwraca `true`.  
  
-   <xref:System.ComponentModel.IBindingList.ApplySort%2A>wywołania `entities.ApplySort()` , a następnie `OnListChanged()`.  
  
-   <xref:System.ComponentModel.IBindingList.SortDirection%2A>i <xref:System.ComponentModel.IBindingList.SortProperty%2A> właściwości ujawnia bieżącej definicji sortowania, który jest przechowywany w lokalnym elementów członkowskich.  
  
 Kiedy używać System.Windows.Forms.BindingSource i powiązać obiektu EntitySet\<TEntity > Aby System.Windows.Forms.BindingSource.DataSource, należy wywołać element EntitySet\<Tentity >. GetNewBindingList BindingSource.List aktualizacji.  
  
 Jeśli użyć System.Windows.Forms.BindingSource i ustaw właściwość BindingSource.DataMember i ustawić BindingSource.DataSource do klasy, która ma właściwość o nazwie w BindingSource.DataMember, który ujawnia EntitySet\<TEntity >, możesz nie trzeba wywoływać EntitySet\<Tentity >. GetNewBindingList zaktualizować BindingSource.List, ale utratę możliwości sortowanie.  
  
## <a name="caching"></a>Buforowanie  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Implementowanie zapytania <xref:System.ComponentModel.IListSource.GetList%2A>. Jeśli klasa formantu BindingSource formularzy systemu Windows spełnia ten interfejs, wywołuje GetList() trzy godziny dla pojedynczego połączenia. Aby obejść ten problem, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje pamięci podręcznej na każde wystąpienie do przechowywania i zawsze zwracać taki sam wygenerować kolekcji.  
  
## <a name="cancellation"></a>Anulowanie  
 <xref:System.ComponentModel.IBindingList>definiuje <xref:System.ComponentModel.IBindingList.AddNew%2A> metodę, która jest używana przez formanty do utworzenia nowego elementu z powiązanej kolekcji. `DataGridView` Pokazuje kontroli tej funkcji bardzo dobrze, gdy widoczny ostatni wiersz zawiera gwiazdy w nagłówku. Gwiazdy pokazuje, że można dodać nowego elementu.  
  
 Oprócz tej funkcji, można też wdrożyć kolekcji <xref:System.ComponentModel.ICancelAddNew>. Ta funkcja umożliwia formantów do anulować albo do sprawdzania, czy edytować nowy lub nie została zweryfikowana elementu.  
  
 <xref:System.ComponentModel.ICancelAddNew>zaimplementowano we wszystkich [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kolekcje z danymi (ogólnego `SortableBindingList` i rodzajowy `EntitySet`). W obu wdrożeniach kod wykonuje w następujący sposób:  
  
-   Umożliwia elementów można wstawiać, a następnie usunięte z kolekcji.  
  
-   Nie śledzi zmiany, tak długo, jak interfejsu użytkownika nie zatwierdzić wersji.  
  
-   Nie śledzi zmiany tak długo, jak wersja została anulowana (<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>).  
  
-   Umożliwia śledzenie gdy dba wersji (<xref:System.ComponentModel.ICancelAddNew.EndNew%2A>).  
  
-   Umożliwia zachowują się normalnie, jeśli nowy element nie pochodzi z kolekcji <xref:System.ComponentModel.IBindingList.AddNew%2A>.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 W tej sekcji uwidacznia kilka elementów, które mogą ułatwić rozwiązywanie problemów z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji powiązania danych.  
  
-   Należy użyć właściwości; używanie tylko pola nie jest wystarczające. Formularze systemu Windows wymagają użycia.  
  
-   Domyślnie `image`, `varbinary`, i `timestamp` mapowania typów bazy danych do tablicy typu byte. Ponieważ `ToString()` nie jest obsługiwany w tym scenariuszu nie można wyświetlić te obiekty.  
  
-   Element członkowski klasy mapowany na klucz podstawowy ma metody ustawiającej, ale [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje zmieniania tożsamości obiektu. Podstawowy/unikalny klucz, który jest używany w mapowaniu nie może zostać uaktualnione w bazie danych. Zmiany w siatce powoduje Wystąpił wyjątek podczas wywoływania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
-   Jeśli jednostka jest powiązana w dwóch oddzielnych siatki (na przykład jeden z nich i szczegóły innego), `Delete` w siatce głównego nie są propagowane do siatki szczegółów.  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
