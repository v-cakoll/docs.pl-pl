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
ms.openlocfilehash: fa40f1657a433f5f4ade3de25648ca04c37dfa67
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962604"
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w formancie DataGridView formularzy systemu Windows
Jednym z powodów wdrożenia trybu wirtualnego w <xref:System.Windows.Forms.DataGridView> kontrolce jest pobieranie danych tylko w razie potrzeby. Jest to nazywane *ładowaniem danych just-in-Time*.  
  
 Jeśli pracujesz z bardzo dużą tabelą w zdalnej bazie danych, na przykład możesz chcieć uniknąć opóźnień uruchamiania, pobierając tylko te dane, które są niezbędne do wyświetlania i pobierania dodatkowych danych tylko wtedy, gdy użytkownik przewinie nowe wiersze do widoku. Jeśli komputery klienckie z uruchomioną aplikacją mają ograniczoną ilość pamięci do przechowywania danych, można również odrzucić nieużywane dane podczas pobierania nowych wartości z bazy danych.  
  
 W poniższych sekcjach opisano sposób używania <xref:System.Windows.Forms.DataGridView> kontrolki z pamięcią podręczną just-in-Time.  
  
 Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: Implementowanie trybu wirtualnego przy użyciu ładowania danych just-in-Time w kontrolce](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)DataGridView Windows Forms.  
  
## <a name="the-form"></a>Formularz  
 Poniższy przykład kodu definiuje formularz zawierający formant tylko <xref:System.Windows.Forms.DataGridView> do odczytu, który współdziała `Cache` z obiektem za pomocą <xref:System.Windows.Forms.DataGridView.CellValueNeeded> programu obsługi zdarzeń. Obiekt zarządza przechowywanymi lokalnie wartościami i `DataRetriever` używa obiektu do pobierania wartości z tabeli Orders w przykładowej bazie danych Northwind. `Cache` Obiekt, który `IDataPageRetriever` implementuje interfejs wymagany przez `Cache` <xref:System.Windows.Forms.DataGridView> klasę, jest również używany do inicjowania wierszy formantów i kolumn. `DataRetriever`  
  
 Typy `IDataPageRetriever`, `DataRetriever` i`Cache` są opisane w dalszej części tego tematu.  
  
> [!NOTE]
> Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>Interfejs IDataPageRetriever  
 Poniższy przykład kodu definiuje `IDataPageRetriever` interfejs, który jest implementowany `DataRetriever` przez klasę. Jedyną metodą zadeklarowaną w tym interfejsem jest `SupplyPageOfData` Metoda, która wymaga początkowego indeksu wierszy i liczby wierszy na pojedynczej stronie danych. Te wartości są używane przez realizatora do pobierania podzestawu danych ze źródła danych.  
  
 `Cache` Obiekt używa implementacji tego interfejsu podczas konstruowania w celu załadowania dwóch początkowych stron danych. Zawsze, gdy wymagana jest niebuforowana wartość, pamięć podręczna odrzuca jedną z tych stron i żąda nowej strony zawierającej wartość z `IDataPageRetriever`.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>Klasa datapobierającej  
 Poniższy przykład kodu definiuje `DataRetriever` klasę, która `IDataPageRetriever` implementuje interfejs do pobierania stron danych z serwera. <xref:System.Windows.Forms.DataGridView.Rows%2A> <xref:System.Windows.Forms.DataGridView> Klasa zawiera `Columns` również właściwości i `RowCount` , które są wykorzystywane przez formant do tworzenia niezbędnych kolumn i dodawania odpowiedniej liczby pustych wierszy do kolekcji. `DataRetriever` Dodanie pustych wierszy jest konieczne, aby formant zachowywać się tak, jakby zawierał wszystkie dane w tabeli. Oznacza to, że pole przewijania na pasku przewijania będzie miało odpowiedni rozmiar, a użytkownik będzie mógł uzyskać dostęp do dowolnego wiersza w tabeli. Wiersze są wypełniane przez <xref:System.Windows.Forms.DataGridView.CellValueNeeded> program obsługi zdarzeń tylko wtedy, gdy są przewijane do widoku.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>Klasa pamięci podręcznej  
 Poniższy przykład kodu definiuje `Cache` klasę, która zarządza dwiema stronami danych wypełnianych `IDataPageRetriever` przez implementację. Klasa definiuje `DataPage` wewnętrzną<xref:System.Data.DataTable> strukturę, która zawiera wartości do przechowywania na jednej stronie pamięci podręcznej, która oblicza indeksy wierszy reprezentujące górne i dolne granice strony. `Cache`  
  
 `Cache` Klasa ładuje dwie strony danych w czasie konstruowania. Za każdym razem, gdy `Cache` zdarzenieżądawartości,obiektOkreśla,czywartośćjestdostępnanajednejzjejdwóchstron,ajeślitak,zwracają.<xref:System.Windows.Forms.DataGridView.CellValueNeeded> Jeśli wartość nie jest dostępna lokalnie, `Cache` obiekt Określa, która z dwóch stron jest najdalej z aktualnie wyświetlanych wierszy i zastępuje stronę nową, zawierającą żądaną wartość, która następnie zwraca.  
  
 Przy założeniu, że liczba wierszy na stronie danych jest taka sama jak liczba wierszy, które mogą być wyświetlane na ekranie jednocześnie, ten model pozwala użytkownikom na stronicowanie tabeli w celu efektywnego powrotu do ostatnio wyświetlanej strony.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>Dodatkowe zagadnienia  
 Poprzednie przykłady kodu są dostępne jako pokaz ładowania danych just-in-Time. Musisz zmodyfikować kod dla własnych potrzeb, aby osiągnąć maksymalną wydajność. Minimalnym wymaganiem jest wybranie odpowiedniej wartości liczby wierszy na stronę danych w pamięci podręcznej. Ta wartość jest przenoszona do `Cache` konstruktora. Liczba wierszy na stronę nie powinna być mniejsza niż liczba wierszy, które mogą być wyświetlane jednocześnie w <xref:System.Windows.Forms.DataGridView> formancie.  
  
 Aby uzyskać najlepsze wyniki, należy przeprowadzić testowanie wydajności i testowanie użyteczności, aby określić wymagania systemu i użytkowników. Należy rozważyć kilka czynników, które należy wziąć pod uwagę, obejmują ilość pamięci na komputerach klienckich z uruchomioną aplikacją, dostępną przepustowość używanego połączenia sieciowego oraz czas opóźnienia używany przez serwer. Przepustowość i opóźnienie należy określić w godzinach szczytowego użycia.  
  
 Aby zwiększyć wydajność przewijania aplikacji, można zwiększyć ilość przechowywanych lokalnie danych. Aby skrócić czas uruchamiania, należy jednak unikać ładowania zbyt dużej ilości danych. Możesz chcieć zmodyfikować `Cache` klasę, aby zwiększyć liczbę stron danych, które mogą być przechowywane. Użycie większej liczby stron danych może poprawić wydajność przewijania, ale w zależności od dostępnej przepustowości i opóźnienia serwera należy określić idealną liczbę wierszy na stronie danych. W przypadku mniejszych stron serwer będzie dostępny częściej, ale w celu zwrócenia żądanych danych będzie trwać krótszy czas. Jeśli opóźnienie jest większe niż przepustowość, warto użyć większych stron danych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Tryb wirtualny w kontrolce DataGridView formularzy Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Przewodnik: Implementowanie trybu wirtualnego w kontrolce DataGridView Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)
- [Instrukcje: Implementowanie trybu wirtualnego przy użyciu ładowania danych just-in-Time w kontrolce DataGridView Windows Forms](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)
