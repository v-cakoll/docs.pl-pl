---
title: "Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w formancie DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a830c11e8df73b71f16c1b9dfd1007461d910f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w formancie DataGridView formularzy systemu Windows
Jedną z przyczyn Implementowanie trybu wirtualnego w <xref:System.Windows.Forms.DataGridView> formant jest do pobierania danych tylko wtedy, gdy jest to potrzebne. Ta metoda jest wywoływana *ładowanie danych just in time*.  
  
 Podczas pracy z bardzo dużych tabel w zdalnej bazy danych, na przykład można uniknąć opóźnienia uruchomienia przez pobranie danych, które są niezbędne do wyświetlania i pobierania dodatkowych danych, tylko wtedy, gdy użytkownik przewija widok nowych wierszy do wyświetlenia. Jeśli komputery klienckie z systemem aplikacji ma ograniczoną ilość pamięci dostępnej dla przechowywania danych, można również odrzucić nieużywanych danych podczas pobierania nowych wartości z bazy danych.  
  
 W poniższych sekcjach opisano sposób użycia <xref:System.Windows.Forms.DataGridView> kontrolki z pamięci podręcznej w czasie.  
  
 Aby skopiować kod w tym temacie na jednej liście, zobacz [porady: Implementowanie trybu wirtualnego just in time w formancie DataGridView formularzy systemu Windows podczas ładowania danych](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="the-form"></a>Formularz  
 Poniższy przykładowy kod definiuje formularz zawierający tylko do odczytu <xref:System.Windows.Forms.DataGridView> formant, który współdziała z `Cache` obiektu za pomocą <xref:System.Windows.Forms.DataGridView.CellValueNeeded> obsługi zdarzeń. `Cache` Obiektu zarządza wartości przechowywane lokalnie i używa `DataRetriever` obiektu można pobrać wartości z tabeli zamówienia przykładowej bazy danych Northwind. `DataRetriever` Obiektu, który implementuje `IDataPageRetriever` interfejsu wymaganego przez `Cache` klasy, również służy do inicjowania <xref:System.Windows.Forms.DataGridView> kontrolować wierszy i kolumn.  
  
 `IDataPageRetriever`, `DataRetriever`, I `Cache` typy są opisane w dalszej części tego tematu.  
  
> [!NOTE]
>  Przechowywanie poufne informacje, takie jak hasła, w ciągu połączenia może mieć wpływ na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>Interfejs IDataPageRetriever  
 Poniższy przykładowy kod definiuje `IDataPageRetriever` interfejs, który jest implementowany przez `DataRetriever` klasy. Jedyną metodą zadeklarowany w tym interfejsie jest `SupplyPageOfData` metodę, która wymaga indeks wiersza początkowego oraz liczbę liczbę wierszy w jednej strony danych. Te wartości są używane przez implementujący pobrać podzbiór danych ze źródła danych.  
  
 A `Cache` obiekt używa implementację tego interfejsu podczas konstruowania załadować dwie strony początkowej danych. Zawsze, gdy wartość bez buforowania jest potrzebna, pamięci podręcznej odrzuca jedną z tych stron i żąda nową stronę zawierającą wartości z `IDataPageRetriever`.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>Klasa DataRetriever  
 Poniższy przykładowy kod definiuje `DataRetriever` klasy, która implementuje `IDataPageRetriever` interfejsu można pobrać strony danych z serwera. `DataRetriever` Klasa udostępnia także `Columns` i `RowCount` właściwości, które <xref:System.Windows.Forms.DataGridView> formant używa do tworzenia niezbędne kolumn i dodaj odpowiednią liczbę puste wiersze do <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji. Dodawanie puste wiersze jest niezbędne, aby formant będą zachowywać się tak, jakby zawiera wszystkie dane w tabeli. Oznacza to, że pole przewijania na pasku przewijania mają odpowiedni rozmiar, a użytkownik będzie mógł uzyskać dostęp każdy wiersz w tabeli. Wiersze są wypełniane przez <xref:System.Windows.Forms.DataGridView.CellValueNeeded> obsługi zdarzeń tylko wtedy, gdy są one przewijane w widoku.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>Klasa pamięci podręcznej  
 Poniższy przykładowy kod definiuje `Cache` klasy, która zarządza dwie strony dane wprowadzane przy użyciu `IDataPageRetriever` implementacji. `Cache` Klasa definiuje wewnętrzny `DataPage` struktury, która zawiera <xref:System.Data.DataTable> do przechowywania wartości w jednej pamięci podręcznej strony i który oblicza indeksuje wiersza, który reprezentuje górne i dolne granice strony.  
  
 `Cache` Klasy ładuje dwóch stronach danych w czasie tworzenia. Zawsze, gdy <xref:System.Windows.Forms.DataGridView.CellValueNeeded> wartość, żądanie zdarzenie `Cache` określa obiekt, jeśli wartość jest dostępna w jednej z jego dwóch stron i, jeśli tak, zwraca go. Jeśli wartość nie jest dostępna lokalnie, `Cache` obiektu określa, które jego dwie strony znajduje się najdalej od aktualnie wyświetlanych wierszy i zastępuje strony nową zawierający Żądana wartość, która następnie zwraca.  
  
 Przy założeniu, że liczba wierszy na stronie danych jest taka sama jak liczba wierszy, które mogą być jednocześnie wyświetlane na ekranie, ten model umożliwia stronicowania za pośrednictwem tabeli wydajnie powrót do ostatniego przeglądanej strony.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>Dodatkowe uwagi  
 W poprzednich przykładach kodu podano jako pokaz ładowania danych just in time. Należy zmodyfikować kod dla potrzeb osiągnąć maksymalną wydajność. Co najmniej należy wybrać odpowiednią wartość liczby wierszy na stronie danych w pamięci podręcznej. Ta wartość jest przekazywana do `Cache` konstruktora. Liczba wierszy na stronie powinien być nie mniejszy niż liczba wierszy, które mogą być wyświetlane jednocześnie w Twojej <xref:System.Windows.Forms.DataGridView> formantu.  
  
 Aby uzyskać najlepsze rezultaty należy przeprowadzić test wydajności i użyteczność test, aby ustalić wymagania systemu i użytkownika. Kilka czynników, które należy wziąć pod uwagę dołączenie komputerów klienckich z aplikacji, dostępnej przepustowości połączenia sieciowego, użyty i opóźnienia serwera używanego ilość pamięci. Przepustowości i opóźnień powinny być określone w czasie szczytowego wykorzystania.  
  
 Aby zwiększyć wydajność przewijania aplikacji, można zwiększyć ilość danych przechowywanych lokalnie. Jednak aby zwiększyć czas uruchamiania, należy unikać, początkowo ładowania zbyt dużej ilości danych. Chcesz zmodyfikować `Cache` klasę, aby zwiększyć liczbę stron danych mogą być przechowywane. Za pomocą więcej stron danych może poprawić wydajność przewijania, ale musisz określić idealne liczbę wierszy na stronie danych, w zależności od dostępnej przepustowości i opóźnień serwera. W mniejszych stron serwera uzyskuje się częściej, ale trwa krócej, aby zwrócić żądanych danych. Jeśli opóźnienie jest więcej niż przepustowość problemu, można używać większych stron danych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 [Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Tryb wirtualny w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 [Instrukcje: implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)
