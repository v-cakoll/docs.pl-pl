---
title: Wiązanie danych i formularze systemu Windows
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
ms.openlocfilehash: 3d420e5cb4d9e7f2ad6f8136b8dd33f5901326d2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095493"
---
# <a name="data-binding-and-windows-forms"></a>Wiązanie danych i formularze systemu Windows
W formularzach Windows Forms można powiązać źródła danych nie jest po prostu tradycyjnych, ale także do niemal wszystkich struktury, która zawiera dane. Możesz powiązać tablicę wartości, które obliczania w czasie wykonywania, Odczyt z pliku lub pochodzić od wartości innych kontrolek.  
  
 Ponadto można powiązać dowolnej właściwości dowolną kontrolkę źródle danych. W powiązaniu danych tradycyjnych zwykle powiązanie właściwości wyświetlania — na przykład <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.TextBox> kontroli — do źródła danych. Za pomocą [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], możesz również możliwość ustawienia innych właściwości, za pośrednictwem powiązania także. Powiązanie można używać do wykonywania następujących zadań:  
  
-   Ustawianie grafiki kontrolkę typu obraz.  
  
-   Ustawianie koloru tła w co najmniej jedną kontrolkę.  
  
-   Ustawianie rozmiaru formantów.  
  
 Powiązanie danych to zasadniczo automatyczny sposób ustawienia dowolnej właściwości dostępne środowiska wykonawczego dowolną kontrolkę w formularzu.  
  
## <a name="types-of-data-binding"></a>Typy powiązanie danych  
 Formularze Windows mogą korzystać z dwóch typów powiązań danych: proste powiązanie i złożone powiązanie. Każda oferuje różne korzyści.  
  
|Typ wiązania danych|Opis|  
|--------------------------|-----------------|  
|Proste powiązanie danych|Możliwość kontroli można powiązać elementu danych jednego, takiego jak wartość w kolumnie w tabeli zestawu danych. Jest to typ powiązania, które są typowe dla formantów takich jak <xref:System.Windows.Forms.TextBox> kontroli lub <xref:System.Windows.Forms.Label> kontrolki, które są kontrolkami, które zwykle wyświetla tylko jedną wartość. W rzeczywistości wszystkie właściwości kontrolki może być powiązana z polem w bazie danych. Brak zaawansowaną obsługę dla tej funkcji w programie Visual Studio.<br /><br /> Aby uzyskać więcej informacji, zobacz:<br /><br /> -   [Interfejsy dotyczące powiązania danych](interfaces-related-to-data-binding.md)<br />-   [Jak: Nawigowanie po danych w formularzach Windows Forms](how-to-navigate-data-in-windows-forms.md)<br />-   [Jak: Tworzenie prostego formantu powiązanego na formularzu Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md)|  
|Złożone powiązanie danych|Możliwość kontroli powiązać więcej niż jednego elementu danych, zazwyczaj więcej niż jeden rekord w bazie danych. Złożone powiązanie jest również nazywany powiązaniu opartym na liście. Przykłady formantów, które obsługują złożone powiązanie <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.ListBox>, i <xref:System.Windows.Forms.ComboBox> kontrolki. Na przykład złożone powiązanie danych zobacz [jak: Powiąż Windows Forms kontrolki ComboBox lub ListBox z danymi](./controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md).|  
  
## <a name="bindingsource-component"></a>BindingSource — Składnik  
 Aby uprościć wiązania danych, Windows Forms umożliwia można powiązać źródła danych, aby <xref:System.Windows.Forms.BindingSource> składnik, a następnie kontrolki powiązania <xref:System.Windows.Forms.BindingSource>. Możesz użyć <xref:System.Windows.Forms.BindingSource> w scenariuszach powiązania proste lub złożone. W obu przypadkach <xref:System.Windows.Forms.BindingSource> działa jako pośrednik między źródłem danych i formanty powiązane dostarczanie powiadomień waluty zarządzaniu zmianami i innych usług.  
  
## <a name="common-scenarios-that-employ-data-binding"></a>Typowe scenariusze, korzystających z powiązania danych  
 Prawie w każdym komercyjnych aplikacja korzysta z informacji o odczytu ze źródeł danych w jednym typie lub innym, zwykle za pomocą powiązania danych. Na poniższej liście przedstawiono niektóre z najbardziej typowych scenariuszy, które wykorzystują powiązanie danych jako metody prezentacji danych i manipulowania.  
  
|Scenariusz|Opis|  
|--------------|-----------------|  
|Raportowanie|Raporty zapewniają elastyczne możliwości wyświetlania i podsumowują dane w dokumencie przeznaczonym do wydrukowania. Jest ono często, aby utworzyć raport, który wyświetla zawartość wybranego źródła danych do ekranu lub do drukarki. Typowe raporty zawierają listy, faktur i podsumowania. Elementy są zazwyczaj sformatowane do kolumn list, podelementów zorganizowane w ramach każdego elementu listy, ale należy wybrać układ, który najlepiej pasujące do danych.|  
|Wprowadzanie danych|Jest typową metodą do wprowadzania dużych ilości danych powiązanych lub w celu monitowania użytkowników o informacje za pomocą formularza zgłoszenia danych. Użytkownikom można wprowadzić informacje lub wybrać opcje przy użyciu pola tekstowe, przyciski opcji, listy rozwijane i pola wyboru. Informacje są następnie przesyłane i przechowywane w bazie danych, której strukturę zależy od wartości wprowadzonej.|  
|Relacja wzorzec/szczegół|Aplikacja wzorzec/szczegół jest jednego formatu do wyszukiwania u pokrewne dane. Istnieją dwie tabele danych przy użyciu relacji, łącząc je — w przykład klasycznego biznesowych, tabeli "Klienci" i tabeli "Orders" przy użyciu relacji między danymi ich połączeń klientów i ich odpowiednich zamówień. Aby uzyskać więcej informacji na temat tworzenia aplikacji wzorzec/szczegół z dwoma formularzami Windows <xref:System.Windows.Forms.DataGridView> formantów, zobacz [jak: Tworzenie formularza wzorzec/szczegół za pomocą dwóch kontrolek DataGridView formularzy Windows Forms](./controls/create-a-master-detail-form-using-two-datagridviews.md)|  
|Tabela odnośników|Inny typowy scenariusz prezentacji/manipulowanie danych jest tabela odnośników. Często większych wyświetlania danych, w ramach <xref:System.Windows.Forms.ComboBox> formant jest używany do wyświetlania i manipulowania danymi. Klucz jest, że dane wyświetlane w <xref:System.Windows.Forms.ComboBox> kontroli różni się od danych zapisanych w bazie danych. Na przykład, jeśli masz <xref:System.Windows.Forms.ComboBox> kontroli wyświetlanie elementów dostępnych w sklepie połówce, prawdopodobnie chcesz zobaczyć nazwy produktów (chleb, mleka potrawach). Jednak do jej obsługi ułatwiają realizację pobierania informacji w bazie danych i normalizacji bazy danych, będzie prawdopodobnie przechowujesz dane dla określonych elementów w podanej kolejności jako elementu liczby (#501, #603 i tak dalej). W związku z tym, ma niejawne połączenia między "Przyjazna nazwa" w elemencie połówce <xref:System.Windows.Forms.ComboBox> kontrolkę w formularzu i liczbę elementów pokrewnych, który znajduje się w kolejności. Jest to kwintesencja działania wyszukiwania tabeli. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie tabeli wyszukiwania za pomocą składnika BindingSource formularzy Windows](./controls/how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component.md).|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Binding>
- [Powiązywanie danych formularzy systemu Windows](windows-forms-data-binding.md)
- [Instrukcje: wiązanie kontrolki DataGrid formularzy systemu Windows ze źródłem danych](./controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [BindingSource — Składnik](./controls/bindingsource-component.md)
