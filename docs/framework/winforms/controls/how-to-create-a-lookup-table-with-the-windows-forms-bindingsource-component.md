---
title: 'Porady: tworzenie tabeli wyszukiwania za pomocą składnika BindingSource formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: 83a34c9d1a4b3d1c2e9950d3c5427567022326b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a>Porady: tworzenie tabeli wyszukiwania za pomocą składnika BindingSource formularzy systemu Windows
Tabela odnośników jest tabelą danych, która zawiera kolumnę wyświetlającą z rekordów w powiązanej tabeli. W poniższych procedurach <xref:System.Windows.Forms.ComboBox> formantu służy do wyświetlania pola z relacji klucza obcego z elementu nadrzędnego z tabelą podrzędną.  
  
 Aby wizualizacji tych dwóch tabel i tę relację, Oto przykład tabeli nadrzędnej i podrzędnej:  
  
 CustomersTable (Tabela nadrzędna)  
  
|CustomerID|CustomerName|  
|----------------|------------------|  
|712|Koch Pawła|  
|713|Tamara Johnston|  
  
 OrdersTable (tabeli podrzędnej)  
  
|OrderID|OrderDate|CustomerID|  
|-------------|---------------|----------------|  
|903|12 lutego 2004|712|  
|904|13 lutego 2004|713|  
  
 W tym scenariuszu jednej tabeli, CustomersTable, przechowuje aktualne informacje, które chcesz wyświetlić, a następnie zapisz. Ale aby zaoszczędzić miejsce, tabeli powoduje, że dane, które dodaje przejrzystości. Drugiej tabeli OrdersTable, zawiera tylko informacje związane z wygląd, o których odbiorcy numer identyfikacyjny jest odpowiednikiem które Data zamówienia i kolejność identyfikatora. Nie ma nie wymieniono nazwy klientów.  
  
 Cztery ważne właściwości są ustawione na [formantu ComboBox](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md) formantu można utworzyć tabeli odnośników.  
  
-   <xref:System.Windows.Forms.ComboBox.DataSource%2A> Właściwość zawiera nazwę tabeli.  
  
-   <xref:System.Windows.Forms.ListControl.DisplayMember%2A> Właściwość zawiera kolumny danych tej tabeli, które mają być wyświetlane dla tekstu formantu (nazwy klienta).  
  
-   <xref:System.Windows.Forms.ListControl.ValueMember%2A> Właściwość zawiera kolumny danych tej tabeli z przechowywanych informacji (identyfikator tabeli nadrzędnej).  
  
-   <xref:System.Windows.Forms.ListControl.SelectedValue%2A> Właściwość zawiera wartość wyszukiwania dla tabeli podrzędnej, na podstawie <xref:System.Windows.Forms.ListControl.ValueMember%2A>.  
  
 W poniższej procedurze pokazano, jak określenie układu formularza jako tabela odnośnika i powiązanie formantów na nim danych. Aby pomyślnie wykonać procedury, musi mieć źródło danych z tabelą nadrzędną i podrzędną, które mają relację klucza obcego, jak wspomniano wcześniej.  
  
### <a name="to-create-the-user-interface"></a>Aby utworzyć interfejs użytkownika  
  
1.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.ComboBox> sterowania do formularza.  
  
     Ten formant wyświetli kolumny z tabeli nadrzędnej.  
  
2.  Przeciągnij inne formanty, aby wyświetlić szczegóły z tabelą podrzędną. Format danych w tabeli należy określić, które kontrolki, możesz wybrać. Aby uzyskać więcej informacji, zobacz [formantów formularzy systemu Windows przez funkcję](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md).  
  
3.  Przeciągnij <xref:System.Windows.Forms.BindingNavigator> sterowania do formularza; to umożliwia nawigowanie w danych w tabeli podrzędnej.  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a>Aby połączyć się z danymi i powiąż go z formantami  
  
1.  Wybierz <xref:System.Windows.Forms.ComboBox> i kliknij przycisk symbolu inteligentne zadań, aby wyświetlić okno dialogowe inteligentne zadań.  
  
2.  Wybierz **powiązanych elementów danych użycia**.  
  
3.  Kliknij strzałkę obok pozycji **źródła danych** pole listy rozwijanej. Jeśli wcześniej została skonfigurowana dla projektu lub formularza źródła danych, zostanie ona wyświetlona; w przeciwnym razie wykonaj następujące czynności (w tym przykładzie używa tabel Klienci i zamówienia przykładowej bazy danych Northwind i odwołuje się do nich w nawiasach).  
  
    1.  Kliknij przycisk **Dodaj źródło danych projektu** Aby podłączyć się do danych i Utwórz źródło danych.  
  
    2.  Na **Kreator konfiguracji źródła danych** stronie powitalnej kliknij **dalej**.  
  
    3.  Wybierz **bazy danych** na **wybierz typ źródła danych** strony.  
  
    4.  Wybierz połączenie danych z listy dostępnych połączeń na **wybierz połączenie danych** strony. Jeśli połączenie żądanych danych nie jest dostępna, zaznacz **nowe połączenie** można utworzyć nowego połączenia danych.  
  
    5.  Kliknij przycisk **tak, Zapisz połączenie** Aby zapisać parametry połączenia w pliku konfiguracyjnym aplikacji.  
  
    6.  Wybierz obiekty bazy danych do wprowadzenia w aplikacji. W takim przypadku wybierz tabelą nadrzędną a tabelą podrzędną (na przykład klienci i zamówienia) z relacji klucza obcego.  
  
    7.  Zastąp domyślną nazwę zestawu danych, jeśli chcesz.  
  
    8.  Kliknij przycisk **Zakończ**.  
  
4.  W **członkiem wyświetlania** listy rozwijanej wybierz pozycję Nazwa kolumny (na przykład nazwa kontaktu), który będzie wyświetlany w polu kombi.  
  
5.  W **wartość elementu członkowskiego** listy rozwijanej wybierz kolumny (na przykład identyfikator klienta) do wykonania operacji wyszukiwania w tabeli podrzędnej.  
  
6.  W **wybrana wartość** listy rozwijanej wybierz opcję **źródła danych projektu** i zestawie danych właśnie utworzony, który zawiera tabelą nadrzędną i podrzędną. Wybierz tę samą właściwość tabeli podrzędnej, który jest członkiem wartości w tabeli nadrzędnej (na przykład zamówienia.IDklienta). Odpowiednie <xref:System.Windows.Forms.BindingSource> zestawu danych i składników karty tabeli zostanie utworzona i dodany do formularza.  
  
7.  Powiąż <xref:System.Windows.Forms.BindingNavigator> formant <xref:System.Windows.Forms.BindingSource> tabeli podrzędnej (na przykład `OrdersBindingSource`).  
  
8.  Inne niż powiązanie formantów <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.BindingNavigator> formantu do pól szczegółów z tabelą podrzędną <xref:System.Windows.Forms.BindingSource> (na przykład `OrdersBindingSource`), który chcesz wyświetlić.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.BindingSource>  
 [BindingSource, składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [ComboBox, kontrolka](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)  
 [Powiązywanie formantów z danymi w Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
