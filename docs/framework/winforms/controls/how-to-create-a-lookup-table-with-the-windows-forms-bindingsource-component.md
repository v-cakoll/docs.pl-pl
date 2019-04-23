---
title: 'Instrukcje: tworzenie tabeli wyszukiwania za pomocą składnika BindingSource formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: 481774e9127531bb38df0cc71ac8e7eab76da695
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321903"
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a>Instrukcje: tworzenie tabeli wyszukiwania za pomocą składnika BindingSource formularzy systemu Windows
Tabela odnośników znajduje się tabela danych, która zawiera kolumnę, która wyświetla dane z rekordów w powiązanej tabeli. W poniższych procedurach <xref:System.Windows.Forms.ComboBox> formantu służy do wyświetlania pól z relacji klucza obcego z obiektu nadrzędnego do tabeli podrzędnej.  
  
 Aby wizualizować tymi dwiema tabelami i tę relację, Oto przykład tabeli nadrzędnej i podrzędnej:  
  
 CustomersTable (tabeli nadrzędnej)  
  
|CustomerID|CustomerName|  
|----------------|------------------|  
|712|Paul Koch|  
|713|Tamara Johnston|  
  
 OrdersTable (tabeli podrzędnej)  
  
|OrderID|DataZamówienia.|CustomerID|  
|-------------|---------------|----------------|  
|903|12 lutego 2004|712|  
|904|13 lutego 2004|713|  
  
 W tym scenariuszu jednej tabeli, CustomersTable, przechowuje aktualne informacje, które chcesz wyświetlić, a następnie zapisz. Ale aby zaoszczędzić przestrzeń, tabeli powoduje, że dane, które dodaje przejrzystości. Drugiej tabeli OrdersTable, zawiera tylko informacje związane z wygląd, o których odbiorcy numer identyfikacyjny jest odpowiednikiem których data zamówienia i kolejność identyfikatora. Nie wymieniono nazwy klientów nie istnieje.  
  
 Cztery ważne właściwości są ustawione na [ComboBox, kontrolka](combobox-control-windows-forms.md) kontroli można utworzyć tabeli odnośników.  
  
-   <xref:System.Windows.Forms.ComboBox.DataSource%2A> Właściwość zawiera nazwę tabeli.  
  
-   <xref:System.Windows.Forms.ListControl.DisplayMember%2A> Właściwość zawiera kolumny danych tej tabeli, którą chcesz wyświetlić tekst formantu (nazwy klienta).  
  
-   <xref:System.Windows.Forms.ListControl.ValueMember%2A> Właściwość zawiera kolumny danych tej tabeli przy użyciu przechowywanych informacji (identyfikator tabeli nadrzędnej).  
  
-   <xref:System.Windows.Forms.ListControl.SelectedValue%2A> Właściwość zawiera wartość wyszukiwania dla tabeli podrzędnej na podstawie <xref:System.Windows.Forms.ListControl.ValueMember%2A>.  
  
 Poniższe procedury pokazują, jak określić układ formularza jako tabela odnośnika i powiązać dane z formantów na nim. Aby pomyślnie wykonać procedury, musi mieć źródło danych o tabele nadrzędne i podrzędne, które mają relacji klucza obcego, jak wspomniano wcześniej.  
  
### <a name="to-create-the-user-interface"></a>Aby utworzyć interfejs użytkownika  
  
1. Z **przybornika**, przeciągnij <xref:System.Windows.Forms.ComboBox> formant na formularzu.  
  
     Ta kontrolka będzie wyświetlać kolumny z tabeli nadrzędnej.  
  
2. Przeciągnij inne kontrolki, aby wyświetlić szczegółowe informacje z tabeli podrzędnej. Format danych w tabeli należy określić, które kontrolki, możesz wybrać. Aby uzyskać więcej informacji, zobacz [formantów formularzy Windows za pomocą funkcji](windows-forms-controls-by-function.md).  
  
3. Przeciągnij <xref:System.Windows.Forms.BindingNavigator> formant na formularzu; to umożliwia nawigowanie po danych w tabeli podrzędnej.  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a>Aby połączyć się z danymi i powiąż go z kontrolkami  
  
1. Wybierz <xref:System.Windows.Forms.ComboBox> i kliknij symbol inteligentne zadań, aby wyświetlić okno dialogowe inteligentne zadania.  
  
2. Wybierz **elementów powiązanych danych użycia**.  
  
3. Kliknij strzałkę obok pozycji **źródła danych** pole listy rozwijanej. Jeśli wcześniej skonfigurowano źródła danych dla projektu lub formularza, pojawi się; w przeciwnym razie wykonaj następujące czynności (w tym przykładzie używa tabele Customers i Orders z przykładowej bazy danych Northwind i odwołuje się do nich w nawiasach).  
  
    1.  Kliknij przycisk **Dodaj źródło danych projektu** do nawiązywania połączeń z danymi i Utwórz źródło danych.  
  
    2.  Na **Kreatora konfiguracji źródła danych** strona powitalna, kliknij przycisk **dalej**.  
  
    3.  Wybierz **bazy danych** na **wybierz typ źródła danych** strony.  
  
    4.  Wybierz połączenie danych z listy dostępnych połączeń na **wybierz połączenie danych** strony. Jeśli żądane połączenie danych nie jest dostępna, wybierz **nowe połączenie** Aby utworzyć nowe połączenie danych.  
  
    5.  Kliknij przycisk **tak, Zapisz połączenie** można zapisać parametry połączenia w pliku konfiguracyjnym aplikacji.  
  
    6.  Wybierz obiekty bazy danych w celu dostosowania do aplikacji. W takim przypadku wybierz tabelę nadrzędną i tabeli podrzędnej (na przykład klienci i zamówienia) z relacji klucza obcego.  
  
    7.  Zastąp domyślną nazwę zestawu danych, jeśli chcesz.  
  
    8.  Kliknij przycisk **Zakończ**.  
  
4. W **członkiem wyświetlania** listy rozwijanej wybierz pozycję Nazwa kolumny (na przykład nazwa kontaktu) mają być wyświetlane w polu kombi.  
  
5. W **wartość elementu członkowskiego** listy rozwijanej wybierz kolumnę (na przykład identyfikator klienta) do wykonywania operacji wyszukiwania w tabeli podrzędnej.  
  
6. W **wybrana wartość** listy rozwijanej, przejdź do **zdroje dat projektu** i zestaw danych został utworzony, który zawiera tabele nadrzędnymi i podrzędnymi. Wybierz tę samą właściwość tabeli podrzędnej, który jest członkiem wartość tabeli nadrzędnej (na przykład zamówienia.IDklienta). Odpowiednie <xref:System.Windows.Forms.BindingSource> zestawu danych i składników karty tabeli zostanie utworzona i dodany do formularza.  
  
7. Powiąż <xref:System.Windows.Forms.BindingNavigator> kontrolę <xref:System.Windows.Forms.BindingSource> tabeli podrzędnej (na przykład `OrdersBindingSource`).  
  
8. Powiązywanie kontrolek innych niż <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.BindingNavigator> kontrolki pola informacji z tabeli podrzędnej <xref:System.Windows.Forms.BindingSource> (na przykład `OrdersBindingSource`), którą chcesz wyświetlić.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingSource>
- [BindingSource, składnik](bindingsource-component.md)
- [ComboBox, kontrolka](combobox-control-windows-forms.md)
- [Wiązanie kontrolek z danymi w programie Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
