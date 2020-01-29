---
title: Tworzenie tabeli odnośników ze składnikiem BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: ccf2bfa6cf3f56a38b55f8c87004c42a46172891
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736816"
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a>Porady: tworzenie tabeli wyszukiwania za pomocą składnika BindingSource formularzy systemu Windows
Tabela wyszukiwania to tabela danych, która zawiera kolumnę, która wyświetla dane z rekordów w powiązanej tabeli. W poniższych procedurach formant <xref:System.Windows.Forms.ComboBox> służy do wyświetlania pola z relacją klucza obcego od elementu nadrzędnego do tabeli podrzędnej.  
  
 Aby ułatwić wizualizację tych dwóch tabel i tę relację, Oto przykład tabeli nadrzędnej i podrzędnej:  
  
 Customers (tabela nadrzędna)  
  
|Identyfikator|customerName|  
|----------------|------------------|  
|712|Paul Koch|  
|713|Tamara Johnston|  
  
 Orders (tabela podrzędna)  
  
|Wartooć|DataZamówienia|Identyfikator|  
|-------------|---------------|----------------|  
|903|12 lutego 2004|712|  
|904|13 lutego 2004|713|  
  
 W tym scenariuszu jedna tabela, Customers, przechowuje rzeczywiste informacje, które mają być wyświetlane i zapisywane. Jednak aby zaoszczędzić miejsce, tabela opuszcza dane, które zwiększają czytelność. Druga tabela, Orders, zawiera tylko informacje dotyczące wyglądu, dla których numer IDENTYFIKACYJNy klienta jest równoważny z datą zamówienia i IDENTYFIKATORem zamówienia. Nie ma wzmianki o nazwach klientów.  
  
 Cztery ważne właściwości są ustawiane w kontrolce [kontrolki ComboBox](combobox-control-windows-forms.md) , aby utworzyć tabelę odnośników.  
  
- Właściwość <xref:System.Windows.Forms.ComboBox.DataSource%2A> zawiera nazwę tabeli.  
  
- Właściwość <xref:System.Windows.Forms.ListControl.DisplayMember%2A> zawiera kolumnę danych tej tabeli, która ma być wyświetlana dla tekstu kontrolki (Nazwa klienta).  
  
- Właściwość <xref:System.Windows.Forms.ListControl.ValueMember%2A> zawiera kolumnę danych tej tabeli zawierającą przechowywane informacje (numer IDENTYFIKACYJNy w tabeli nadrzędnej).  
  
- Właściwość <xref:System.Windows.Forms.ListControl.SelectedValue%2A> udostępnia wartość wyszukiwania dla tabeli podrzędnej na podstawie <xref:System.Windows.Forms.ListControl.ValueMember%2A>.  
  
 Poniższe procedury przedstawiają sposób tworzenia układu formularza jako tabeli odnośników i powiązania danych z kontrolkami na nim. Aby pomyślnie wykonać procedury, musisz mieć źródło danych z tabelami nadrzędnymi i podrzędnymi, które mają relację klucza obcego, jak wspomniano wcześniej.  
  
### <a name="to-create-the-user-interface"></a>Aby utworzyć interfejs użytkownika  
  
1. Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Forms.ComboBox> na formularz.  
  
     Ta kontrolka wyświetli kolumnę z tabeli nadrzędnej.  
  
2. Przeciągnij inne kontrolki, aby wyświetlić szczegóły z tabeli podrzędnej. Format danych w tabeli powinien określać wybrane kontrolki. Aby uzyskać więcej informacji, zobacz [Windows Forms formantów według funkcji](windows-forms-controls-by-function.md).  
  
3. Przeciągnij kontrolkę <xref:System.Windows.Forms.BindingNavigator> na formularz; umożliwi to nawigowanie po danych w tabeli podrzędnej.  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a>Aby nawiązać połączenie z danymi i powiązać je z kontrolkami  
  
1. Wybierz <xref:System.Windows.Forms.ComboBox> i kliknij symbol panel inteligentny, aby wyświetlić okno dialogowe panel inteligentny.  
  
2. Wybierz pozycję **Użyj elementów powiązanych z danymi**.  
  
3. Kliknij strzałkę obok pola listy rozwijanej **Źródło danych** . Jeśli źródło danych zostało wcześniej skonfigurowane dla projektu lub formularza, zostanie wyświetlone. w przeciwnym razie wykonaj następujące czynności (w tym przykładzie są wykorzystywane tabele Customers i Orders w przykładowej bazie danych Northwind i odwołujące się do nich w nawiasach).  
  
    1. Kliknij pozycję **Dodaj źródło danych projektu** , aby połączyć się z danymi i utworzyć źródło danych.  
  
    2. Na stronie powitalnej **Kreatora konfiguracji źródła danych** kliknij przycisk **dalej**.  
  
    3. Wybierz pozycję **baza danych** na stronie **Wybierz typ źródła danych** .  
  
    4. Wybierz połączenie danych z listy dostępnych połączeń na stronie **Wybierz połączenie danych** . Jeśli żądane połączenie danych nie jest dostępne, wybierz pozycję **nowe połączenie** , aby utworzyć nowe połączenie danych.  
  
    5. Kliknij przycisk **tak, Zapisz połączenie,** aby zapisać parametry połączenia w pliku konfiguracyjnym aplikacji.  
  
    6. Wybierz obiekty bazy danych do dołączenia do aplikacji. W takim przypadku wybierz tabelę nadrzędną i tabelę podrzędną (na przykład klienci i zamówienia) z relacją klucza obcego.  
  
    7. W razie potrzeby Zastąp domyślną nazwę zestawu danych.  
  
    8. Kliknij przycisk **Zakończ**.  
  
4. W polu listy rozwijanej **Wyświetl element członkowski** wybierz nazwę kolumny (na przykład ContactName), która ma być wyświetlana w polu kombi.  
  
5. W polu listy rozwijanej **członek wartości** wybierz kolumnę (na przykład CustomerID), aby wykonać operację wyszukiwania w tabeli podrzędnej.  
  
6. W polu listy rozwijanej **wybrana wartość** przejdź do **źródeł danych projektu** i utworzonego zestawu danych, który zawiera tabele nadrzędne i podrzędne. Wybierz tę samą Właściwość tabeli podrzędnej, która jest elementem członkowskim wartości tabeli nadrzędnej (na przykład Orders. IDklienta). Odpowiednie <xref:System.Windows.Forms.BindingSource>, zestaw danych i składniki karty tabeli zostaną utworzone i dodane do formularza.  
  
7. Powiąż formant <xref:System.Windows.Forms.BindingNavigator> z <xref:System.Windows.Forms.BindingSource> tabeli podrzędnej (na przykład `OrdersBindingSource`).  
  
8. Powiąż formanty inne niż <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.BindingNavigator> formantu z polami szczegółów w <xref:System.Windows.Forms.BindingSource> tabeli podrzędnej (na przykład `OrdersBindingSource`), które chcesz wyświetlić.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingSource>
- [BindingSource, składnik](bindingsource-component.md)
- [ComboBox, kontrolka](combobox-control-windows-forms.md)
- [Wiązanie kontrolek z danymi w programie Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
