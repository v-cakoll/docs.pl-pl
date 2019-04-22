---
title: Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: c2a052b9-423c-4ff7-91dc-d8c7c79345f6
ms.openlocfilehash: 641db19cc6493a20c9f9a34622f466e3623c32ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088655"
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w formancie DataGridView formularzy systemu Windows
Jednym z powodów Implementowanie trybu wirtualnego w <xref:System.Windows.Forms.DataGridView> formant jest pobrać dane tylko wtedy, gdy jest to konieczne. Jest to nazywane *ładowania danych just-in-time*.  
  
 Jeśli pracujesz z bardzo dużych tabel w zdalnej bazy danych, na przykład, możesz zechcieć w celu uniknięcia opóźnień uruchamiania przez pobieranie tylko dane, które są niezbędne do wyświetlania i pobierania dodatkowych danych, tylko wtedy, gdy użytkownik przewija widok nowych wierszy w widoku. Jeśli na komputerach klienckich, uruchamiania aplikacji istnieje ograniczona ilość pamięci dostępna do przechowywania danych, można również odrzucić niewykorzystane dane podczas pobierania nowych wartości z bazy danych.  
  
 W poniższych sekcjach opisano sposób użycia <xref:System.Windows.Forms.DataGridView> kontrolki z pamięcią podręczną just-in-time.  
  
 Aby skopiować kod, w tym temacie na jednej liście, zobacz [jak: Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w Windows formantu DataGridView formularzy](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="the-form"></a>Formularz  
 Poniższy przykład kodu przedstawia formularz zawierający tylko do odczytu <xref:System.Windows.Forms.DataGridView> formant, który wchodzi w interakcję z `Cache` obiektu za pomocą <xref:System.Windows.Forms.DataGridView.CellValueNeeded> programu obsługi zdarzeń. `Cache` Obiektu zarządza wartości przechowywanych lokalnie i używa `DataRetriever` obiektu do pobrania wartości z tabeli Orders z przykładowej bazy danych Northwind. `DataRetriever` Obiektu, który implementuje `IDataPageRetriever` interfejsu wymaganego przez `Cache` klasy, jest również używane do zainicjowania <xref:System.Windows.Forms.DataGridView> kontrolować wierszy i kolumn.  
  
 `IDataPageRetriever`, `DataRetriever`, I `Cache` typy są opisane w dalszej części tego tematu.  
  
> [!NOTE]
>  Przechowywanie poufnych informacji, takich jak hasła, w ciągu połączenia mogą wpływać na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>Interfejs IDataPageRetriever  
 Poniższy przykład kodu przedstawia `IDataPageRetriever` interfejs, który jest implementowany przez `DataRetriever` klasy. Jedyną metodą zadeklarowany w tym interfejsie jest `SupplyPageOfData` metody, która wymaga indeks wiersza początkowego i liczbę wierszy w pojedynczej strony danych. Te wartości są używane przez implementujący pobrać podzbiór danych ze źródła danych.  
  
 A `Cache` obiekt używa implementację tego interfejsu podczas konstruowania załadować dwie strony początkowej danych. Zawsze wtedy, gdy potrzebna jest wartością bez buforowania, bufor odrzuca jedną z tych stron i żąda nową stronę zawierającą wartości z `IDataPageRetriever`.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>Klasa DataRetriever  
 Poniższy przykład kodu przedstawia `DataRetriever` klasy, która implementuje `IDataPageRetriever` interfejsu można pobrać strony danych z serwera. `DataRetriever` Klasa udostępnia także `Columns` i `RowCount` właściwości, które <xref:System.Windows.Forms.DataGridView> kontroli używa do tworzenia wymaganych kolumn i dodać odpowiednią liczbę pustych wierszy do <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji. Dodawanie pustych wierszy jest niezbędne, tak aby kontrolka będą zachowywać się tak, jakby zawiera wszystkie dane w tabeli. Oznacza to, że pole przewijania na pasku przewijania będzie mieć odpowiedni rozmiar, a użytkownik będzie mógł uzyskać dostęp każdy wiersz w tabeli. Wiersze są wypełniane przez <xref:System.Windows.Forms.DataGridView.CellValueNeeded> program obsługi zdarzeń tylko wtedy, gdy są one przewijane do widoku.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>Klasa pamięci podręcznej  
 Poniższy przykład kodu przedstawia `Cache` klasy, która zarządza dwie strony danych wypełnione za pośrednictwem `IDataPageRetriever` implementacji. `Cache` Klasa definiuje wewnętrznego `DataPage` struktury, która zawiera <xref:System.Data.DataTable> do przechowywania wartości w jednej pamięci podręcznej strony i — oblicza wiersz indeksy, które reprezentują granice górnej i dolnej części strony.  
  
 `Cache` Klasy ładuje dwie strony danych podczas konstruowania. Zawsze, gdy <xref:System.Windows.Forms.DataGridView.CellValueNeeded> zdarzeń żąda wartość `Cache` określa obiekt, jeśli wartość jest dostępna w jednej z jego dwóch stron i, jeśli tak, zwraca go. Jeśli wartość nie jest dostępna lokalnie, `Cache` obiektu określa, które jego dwie strony znajduje się najdalej od aktualnie wyświetlane wiersze i zastępuje strony nową, zawierający Żądana wartość, która następnie zwraca.  
  
 Przy założeniu, że liczba wierszy na stronie danych jest taka sama jak liczba wierszy, które mogą być wyświetlane jednocześnie na ekranie, ten model umożliwia użytkownikom stronicowanie tabeli efektywnie wrócić do ostatnio wyświetlane strony.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>Dodatkowe zagadnienia  
 W poprzednich przykładach kodu są dostarczane jako pokaz ładowania danych just-in-time. Należy zmodyfikować kod do własnych potrzeb osiągnąć maksymalną wydajność. Minimum należy wybrać odpowiednią wartość liczby wierszy na stronie dane w pamięci podręcznej. Ta wartość jest przekazywana do `Cache` konstruktora. Liczba wierszy na stronie powinno być nie mniejszy niż liczba wierszy, które mogą być wyświetlane jednocześnie w swojej <xref:System.Windows.Forms.DataGridView> kontroli.  
  
 Aby uzyskać najlepsze wyniki należy przeprowadzić testowanie wydajności i użyteczności testów w celu określenia wymagań systemu i użytkowników. Kilka czynników, które należy wziąć pod uwagę dołączyć ilość pamięci na komputerach klienckich z aplikacji, dostępną przepustowość połączenia sieciowego używane i czas oczekiwania serwera używanego. Przepustowość i czas oczekiwania powinna zostać określona w czasie szczytowego wykorzystania.  
  
 Aby poprawić wydajność aplikacji, można zwiększyć ilość danych przechowywanych lokalnie. Jednak aby poprawić czas uruchamiania, należy unikać, początkowo ładowania zbyt dużej ilości danych. Możesz chcieć zmodyfikować `Cache` klasy, aby zwiększyć liczbę stron danych, które mogą być przechowywane. Za pomocą więcej stron danych może zwiększyć wydajność przewijania, ale musisz określić idealne liczba wierszy na stronie danych w zależności od dostępnej przepustowości i opóźnień serwera. Za pomocą mniejszej stron serwera uzyskuje się częściej, ale trwa krócej, aby zwrócić żądanych danych. Jeśli opóźnienie jest więcej niż przepustowość problemu, można używać większej stron danych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Tryb wirtualny w kontrolce DataGridView formularzy Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Przewodnik: Implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)
- [Instrukcje: Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)
