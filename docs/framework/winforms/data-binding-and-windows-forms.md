---
title: Powiązanie danych i formularze systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- data [Windows Forms], data binding
- reports [Windows Forms], Windows Forms
- lookup tables [Windows Forms], data binding
- data [Windows Forms], complex data binding
- data binding [Windows Forms], Windows Forms
- data [Windows Forms], simple data binding
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: 419aac5e-819b-4aad-88b0-73a2f8c0bd27
ms.openlocfilehash: ab1b712a2c855bc27236b8b8989ba51054e57358
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="data-binding-and-windows-forms"></a>Powiązanie danych i formularze systemu Windows
W formularzach systemu Windows można powiązać źródła danych nie tylko tradycyjnych, ale także do niemal wszystkich struktury, która zawiera dane. Można powiązać tablicy wartości, które obliczenia w czasie wykonywania, Odczyt z pliku lub pochodzić od wartości innych kontrolek.  
  
 Ponadto można powiązać żadnych właściwości każdego formantu źródła danych. W powiązaniu danych tradycyjnych zwykle powiązanie właściwości wyświetlania — na przykład <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.TextBox> kontroli — ze źródłem danych. Z [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], masz również określanie innych właściwości za pośrednictwem powiązania również. Można na przykład powiązanie umożliwia wykonywanie następujących zadań:  
  
-   Ustawienie grafiki formantu obrazu.  
  
-   Ustawianie koloru tła z co najmniej jeden formant.  
  
-   Ustawianie rozmiaru formantów.  
  
 Powiązanie danych to zasadniczo automatyczny sposób ustawienia dowolnej właściwości dostępny czasu wykonywania żadnych kontrolkę w formularzu.  
  
## <a name="types-of-data-binding"></a>Typy powiązanie danych  
 Formularze systemu Windows można korzystać z dwóch typów wiązania z danymi: proste powiązanie i złożone powiązanie. Każdy oferują różne zalety.  
  
|Typ powiązania danych|Opis|  
|--------------------------|-----------------|  
|Proste powiązanie danych|Możliwość kontrolkę można powiązać do elementu danych, takich jak wartość w kolumnie w tabeli zestawu danych. Jest to typ powiązania, które są typowe dla formantów takich jak <xref:System.Windows.Forms.TextBox> kontroli lub <xref:System.Windows.Forms.Label> Określanie formantów, które zwykle są wyświetlane tylko pojedynczą wartość. W rzeczywistości żadnej właściwości w formancie może być powiązana z polem w bazie danych. Brak kompleksową obsługę tej funkcji w programie Visual Studio.<br /><br /> Aby uzyskać więcej informacji, zobacz:<br /><br /> -   [Interfejsy dotyczące powiązania danych](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)<br />-   [Porady: nawigowanie w danych w formularzach systemu Windows](../../../docs/framework/winforms/how-to-navigate-data-in-windows-forms.md)<br />-   [Porady: Tworzenie prostego formantu powiązanego na formularzu systemu Windows](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)|  
|Złożone powiązanie danych|Możliwość formantu powiązać z więcej niż jeden element danych, zazwyczaj więcej niż jeden rekord w bazie danych. Złożone powiązanie jest również nazywany powiązanie oparte na liście. Przykłady formantów, które obsługują złożone powiązanie <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.ListBox>, i <xref:System.Windows.Forms.ComboBox> kontrolki. Na przykład złożone powiązanie danych zobacz [porady: powiązanie formantu ComboBox formularzy systemu Windows lub kontrolki ListBox z danymi](../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md).|  
  
## <a name="bindingsource-component"></a>BindingSource — Składnik  
 Aby uprościć wiązania z danymi, formularze systemu Windows umożliwia powiązać źródła danych, aby <xref:System.Windows.Forms.BindingSource> składnik, a następnie powiązanie formantów <xref:System.Windows.Forms.BindingSource>. Można użyć <xref:System.Windows.Forms.BindingSource> w wiązania proste lub złożonych scenariuszach. W obu przypadkach <xref:System.Windows.Forms.BindingSource> działa jako pośrednik między źródłem danych i zapewnienie formanty powiązane zmiany powiadomienia waluty zarządzania i innych usług.  
  
## <a name="common-scenarios-that-employ-data-binding"></a>Typowych scenariuszy korzystających z powiązanie danych  
 Prawie każdej aplikacji komercyjnych używa informacji odczytywać źródła danych jednego typu lub innego, zwykle za pośrednictwem powiązania danych. Poniższa lista zawiera kilka najbardziej typowych scenariuszy wykorzystujące wiązania danych jako metody prezentacji danych i manipulowania nimi.  
  
|Scenariusz|Opis|  
|--------------|-----------------|  
|Raportowanie|Raporty zapewniają elastyczny sposób wyświetlania i podsumowywania danych wydrukowane w dokumencie. Często zdarza się, aby utworzyć raport, który wyświetla zawartość wybranego źródła danych do ekranu lub do drukarki. Typowe raporty zawierają listy, faktury i podsumowania. Elementy są zazwyczaj sformatowane na kolumny list, podelementów zorganizowane w ramach każdego elementu listy, ale należy wybrać układ, który najlepiej odpowiada danych.|  
|Wpisanie danych|Jest to często stosowana metoda do wprowadzania dużych ilości danych powiązanych lub monitowania użytkowników, aby uzyskać informacje za pomocą formularza wprowadzania danych. Użytkownicy można wprowadzić informacje lub wybrać opcje przy użyciu pól tekstowych, przycisków opcji listy rozwijane i pola wyboru. Informacje są następnie przesłane i przechowywane w bazie danych, której strukturę opiera się na wartości wprowadzonej.|  
|Relacja wzorzec/szczegół|Aplikacja wzorzec/szczegół jest jednego formatu na potrzeby wyszukiwania powiązanych danych. W szczególności, istnieją dwie tabele danych z relacji, łącząc je — przykład klasycznego biznesowy, tabeli "Klientów" i tabeli "Zamówienia" w relacji między nimi połączeń klientów i ich odpowiednich zleceń. Aby uzyskać więcej informacji o tworzeniu aplikacji wzorzec/szczegół z dwóch formularzy systemu Windows <xref:System.Windows.Forms.DataGridView> formantów, zobacz [porady: tworzenie wzorzec/szczegół formularza za pomocą dwóch formantów formularzy systemu Windows formantu DataGridView](../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md)|  
|Tabela wyszukiwania|Inny typowy scenariusz prezentacji/manipulowanie danych jest wyszukiwanie w tabeli. Często większy wyświetlania danych w ramach <xref:System.Windows.Forms.ComboBox> formant jest używany do wyświetlania i modyfikowania danych. Klucz jest, że dane wyświetlane w <xref:System.Windows.Forms.ComboBox> formant jest inne niż dane zapisane w bazie danych. Na przykład, jeśli masz <xref:System.Windows.Forms.ComboBox> kontroli wyświetlanie elementów dostępnych w sklepie spożywczych, prawdopodobnie chcesz zobaczyć nazwy produktów (chleb, mleka, które). Jednak do jej obsługi ułatwiają pobierania informacji w bazie danych i normalizacji bazy danych, czy prawdopodobnie przechowywać informacje o określonych pozycji podanej kolejności jako liczby elementów (#501, #603 itd.). W związku z tym ma niejawne połączenie między "przyjazną nazwę" w elemencie spożywczych w <xref:System.Windows.Forms.ComboBox> kontrolki w formularzu i liczba elementów pokrewnych, która znajduje się w określonym porządku. Jest to właśnie wyszukiwanie w tabeli. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie tabeli wyszukiwania za pomocą składnika BindingSource formularzy systemu Windows](../../../docs/framework/winforms/controls/how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component.md).|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Binding>  
 [Wiązanie danych formularzy Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych](../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [BindingSource, składnik](../../../docs/framework/winforms/controls/bindingsource-component.md)
