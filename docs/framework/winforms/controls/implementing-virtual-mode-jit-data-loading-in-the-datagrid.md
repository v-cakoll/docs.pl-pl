---
title: Implementowanie trybu wirtualnego przy użyciu ładowania danych just-in-Time w formancie DataGridView
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
ms.openlocfilehash: 85c6877a9fc6a92752eb039da9d36e34811f8b77
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745070"
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w formancie DataGridView formularzy systemu Windows
Jednym z powodów wdrożenia trybu wirtualnego w kontrolce <xref:System.Windows.Forms.DataGridView> jest pobieranie danych tylko w razie potrzeby. Jest to nazywane *ładowaniem danych just-in-Time*.  
  
 Jeśli pracujesz z bardzo dużą tabelą w zdalnej bazie danych, na przykład możesz chcieć uniknąć opóźnień uruchamiania, pobierając tylko te dane, które są niezbędne do wyświetlania i pobierania dodatkowych danych tylko wtedy, gdy użytkownik przewinie nowe wiersze do widoku. Jeśli komputery klienckie z uruchomioną aplikacją mają ograniczoną ilość pamięci do przechowywania danych, można również odrzucić nieużywane dane podczas pobierania nowych wartości z bazy danych.  
  
 W poniższych sekcjach opisano sposób używania kontrolki <xref:System.Windows.Forms.DataGridView> z pamięcią podręczną just-in-Time.  
  
 Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [jak: implementowanie trybu wirtualnego przy użyciu ładowania danych just-in-Time w kontrolce DataGridView Windows Forms](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="the-form"></a>Formularz  
 Poniższy przykład kodu definiuje formularz zawierający formant <xref:System.Windows.Forms.DataGridView> tylko do odczytu, który współdziała z obiektem `Cache` za pomocą procedury obsługi zdarzeń <xref:System.Windows.Forms.DataGridView.CellValueNeeded>. Obiekt `Cache` zarządza przechowywanymi lokalnie wartościami i używa obiektu `DataRetriever` do pobierania wartości z tabeli Orders w przykładowej bazie danych Northwind. Obiekt `DataRetriever`, który implementuje interfejs `IDataPageRetriever` wymagany przez klasę `Cache`, jest również używany do inicjowania <xref:System.Windows.Forms.DataGridView> wierszy formantów i kolumn.  
  
 Typy `IDataPageRetriever`, `DataRetriever`i `Cache` są opisane w dalszej części tego tematu.  
  
> [!NOTE]
> Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>Interfejs IDataPageRetriever  
 Poniższy przykład kodu definiuje interfejs `IDataPageRetriever`, który jest implementowany przez klasę `DataRetriever`. Jedyną metodą zadeklarowaną w tym interfejsie jest metoda `SupplyPageOfData`, która wymaga początkowego indeksu wierszy i liczby wierszy na pojedynczej stronie danych. Te wartości są używane przez realizatora do pobierania podzestawu danych ze źródła danych.  
  
 Obiekt `Cache` używa implementacji tego interfejsu podczas konstruowania w celu załadowania dwóch początkowych stron danych. Za każdym razem, gdy wymagana jest niebuforowana wartość, pamięć podręczna odrzuca jedną z tych stron i żąda nowej strony zawierającej wartość z `IDataPageRetriever`.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>Klasa datapobierającej  
 Poniższy przykład kodu definiuje klasę `DataRetriever`, która implementuje interfejs `IDataPageRetriever` do pobierania stron danych z serwera. Klasa `DataRetriever` udostępnia również właściwości `Columns` i `RowCount`, których formant <xref:System.Windows.Forms.DataGridView> używa do tworzenia niezbędnych kolumn i dodawania odpowiedniej liczby pustych wierszy do kolekcji <xref:System.Windows.Forms.DataGridView.Rows%2A>. Dodanie pustych wierszy jest konieczne, aby formant zachowywać się tak, jakby zawierał wszystkie dane w tabeli. Oznacza to, że pole przewijania na pasku przewijania będzie miało odpowiedni rozmiar, a użytkownik będzie mógł uzyskać dostęp do dowolnego wiersza w tabeli. Wiersze są wypełniane przez program obsługi zdarzeń <xref:System.Windows.Forms.DataGridView.CellValueNeeded> tylko wtedy, gdy są przewijane do widoku.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>Klasa pamięci podręcznej  
 Poniższy przykład kodu definiuje klasę `Cache`, która zarządza dwiema stronami danych wypełnianych za pomocą `IDataPageRetriever` implementacji. Klasa `Cache` definiuje wewnętrzną strukturę `DataPage`, która zawiera <xref:System.Data.DataTable> do przechowywania wartości na jednej stronie pamięci podręcznej, a następnie oblicza indeksy wierszy reprezentujące górne i dolne granice strony.  
  
 Klasa `Cache` ładuje dwie strony danych w czasie konstruowania. Za każdym razem, gdy zdarzenie <xref:System.Windows.Forms.DataGridView.CellValueNeeded> żąda wartości, obiekt `Cache` określa, czy wartość jest dostępna na jednej z jej dwóch stron, a jeśli tak, zwraca ją. Jeśli wartość nie jest dostępna lokalnie, obiekt `Cache` określa, które z dwóch stron są najdalej z aktualnie wyświetlanych wierszy i zastępuje stronę nową, zawierającą żądaną wartość, która następnie zwraca.  
  
 Przy założeniu, że liczba wierszy na stronie danych jest taka sama jak liczba wierszy, które mogą być wyświetlane na ekranie jednocześnie, ten model pozwala użytkownikom na stronicowanie tabeli w celu efektywnego powrotu do ostatnio wyświetlanej strony.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>Dodatkowe zagadnienia  
 Poprzednie przykłady kodu są dostępne jako pokaz ładowania danych just-in-Time. Musisz zmodyfikować kod dla własnych potrzeb, aby osiągnąć maksymalną wydajność. Minimalnym wymaganiem jest wybranie odpowiedniej wartości liczby wierszy na stronę danych w pamięci podręcznej. Ta wartość jest przenoszona do konstruktora `Cache`. Liczba wierszy na stronę powinna być nie mniejsza niż liczba wierszy, które mogą być wyświetlane jednocześnie w kontrolce <xref:System.Windows.Forms.DataGridView>.  
  
 Aby uzyskać najlepsze wyniki, należy przeprowadzić testowanie wydajności i testowanie użyteczności, aby określić wymagania systemu i użytkowników. Należy rozważyć kilka czynników, które należy wziąć pod uwagę, obejmują ilość pamięci na komputerach klienckich z uruchomioną aplikacją, dostępną przepustowość używanego połączenia sieciowego oraz czas opóźnienia używany przez serwer. Przepustowość i opóźnienie należy określić w godzinach szczytowego użycia.  
  
 Aby zwiększyć wydajność przewijania aplikacji, można zwiększyć ilość przechowywanych lokalnie danych. Aby skrócić czas uruchamiania, należy jednak unikać ładowania zbyt dużej ilości danych. Warto zmodyfikować klasę `Cache`, aby zwiększyć liczbę stron danych, które mogą być przechowywane. Użycie większej liczby stron danych może poprawić wydajność przewijania, ale w zależności od dostępnej przepustowości i opóźnienia serwera należy określić idealną liczbę wierszy na stronie danych. W przypadku mniejszych stron serwer będzie dostępny częściej, ale w celu zwrócenia żądanych danych będzie trwać krótszy czas. Jeśli opóźnienie jest większe niż przepustowość, warto użyć większych stron danych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Tryb wirtualny w kontrolce DataGridView formularzy Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)
- [Instrukcje: implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)
