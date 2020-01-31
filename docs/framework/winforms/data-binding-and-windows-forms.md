---
title: Powiązanie danych
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
ms.openlocfilehash: c5cb16d57dde35ca3b243191f27ea118cf19a680
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742317"
---
# <a name="data-binding-and-windows-forms"></a>Wiązanie danych i formularze systemu Windows
W Windows Forms można powiązać nie tylko z tradycyjnymi źródłami danych, ale również z niemal każdą strukturą zawierającą dane. Można powiązać z tablicą wartości obliczanych w czasie wykonywania, odczytywać z pliku lub dziedziczyć z wartości innych kontrolek.  
  
 Ponadto można powiązać dowolną Właściwość dowolnej kontrolki ze źródłem danych. W tradycyjnym powiązaniu danych zazwyczaj wiąże się z właściwością wyświetlania — na przykład <xref:System.Windows.Forms.Control.Text%2A> właściwości kontrolki <xref:System.Windows.Forms.TextBox> — do źródła danych. Za pomocą .NET Framework można również ustawić inne właściwości za pomocą powiązania. Możesz użyć powiązania, aby wykonać następujące zadania:  
  
- Ustawianie grafiki kontrolki obrazu.  
  
- Ustawianie koloru tła co najmniej jednej kontrolki.  
  
- Ustawianie rozmiaru kontrolek.  
  
 Zasadniczo wiązanie danych jest automatycznym sposobem ustawienia właściwości dostępnych w czasie wykonywania dowolnej kontrolki w formularzu.  
  
## <a name="types-of-data-binding"></a>Typy powiązań danych  
 Windows Forms może korzystać z dwóch typów powiązań danych: prostego powiązania i powiązania złożonego. Każda z nich oferuje różne zalety.  
  
|Typ powiązania danych|Opis|  
|--------------------------|-----------------|  
|Proste powiązanie danych|Możliwość powiązania formantu z pojedynczym elementem danych, takim jak wartość w kolumnie w tabeli dataset. Jest to typ powiązania typowy dla kontrolek, takich jak kontrolka <xref:System.Windows.Forms.TextBox> lub kontrolka <xref:System.Windows.Forms.Label>, które są kontrolkami, które zwykle wyświetlają tylko jedną wartość. W rzeczywistości każda właściwość kontrolki może być powiązana z polem w bazie danych. W programie Visual Studio jest dostępna szeroka obsługa tej funkcji.<br /><br /> Aby uzyskać więcej informacji, zobacz:<br /><br /> [interfejsy -   powiązane z powiązaniem danych](interfaces-related-to-data-binding.md)<br />-   [: nawigowanie po danych w Windows Forms](how-to-navigate-data-in-windows-forms.md)<br />-   [jak utworzyć prostą kontrolkę w formularzu systemu Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md)|  
|Złożone powiązanie danych|Możliwość powiązania formantu z więcej niż jednym elementem danych, zwykle więcej niż jeden rekord w bazie danych. Złożone powiązanie jest również nazywane powiązaniem opartym na liście. Przykłady formantów, które obsługują złożone powiązania są kontrolkami <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.ListBox>i <xref:System.Windows.Forms.ComboBox>. Aby zapoznać się z przykładem złożonego powiązania danych, zobacz [How to: bind a Windows Forms ComboBox lub ListBox formant do danych](./controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md).|  
  
## <a name="bindingsource-component"></a>BindingSource — Składnik  
 Aby uprościć powiązanie danych, Windows Forms pozwala powiązać źródło danych ze składnikiem <xref:System.Windows.Forms.BindingSource>, a następnie powiązać kontrolki z <xref:System.Windows.Forms.BindingSource>. <xref:System.Windows.Forms.BindingSource> można użyć w prostych lub złożonych scenariuszach powiązań. W obu przypadkach <xref:System.Windows.Forms.BindingSource> pełni rolę pośrednika między źródłem danych i formantami związanymi z zarządzaniem walutą powiadomień o zmianach i innymi usługami.  
  
## <a name="common-scenarios-that-employ-data-binding"></a>Typowe scenariusze, które wykorzystują powiązanie danych  
 Niemal każda aplikacja komercyjna korzysta z informacji odczytywanych ze źródeł danych jednego typu lub innych, zazwyczaj za pośrednictwem powiązań danych. Na poniższej liście przedstawiono kilka typowych scenariuszy, które wykorzystują powiązanie danych jako metody prezentacji i manipulowania danymi.  
  
|Scenariusz|Opis|  
|--------------|-----------------|  
|Raportowanie|Raporty zapewniają elastyczny sposób wyświetlania i podsumowywania danych w wydrukowanym dokumencie. Często istnieje możliwość utworzenia raportu, który drukuje wybraną zawartość źródła danych na ekranie lub do drukarki. Typowe raporty obejmują listy, faktury i podsumowania. Elementy są zwykle sformatowane do kolumn list, z elementami podrzędnymi zorganizowanymi pod każdym elementem listy, ale należy wybrać układ, który najlepiej odpowiada danym.|  
|Wprowadzanie danych|Typowym sposobem wprowadzania dużych ilości powiązanych danych lub monitowania użytkowników o informacje jest użycie formularza wprowadzania danych. Użytkownicy mogą wprowadzać informacje lub wybierać opcje przy użyciu pól tekstowych, przycisków opcji, list rozwijanych i pól wyboru. Informacje są następnie przesyłane i przechowywane w bazie danych, której struktura jest oparta na wprowadzonych informacjach.|  
|Wzorzec/szczegóły relacji|Aplikacja master/detail ma jeden format do przeglądania powiązanych danych. W konkretnym przypadku istnieją dwie tabele danych z relacją łączącą je — w klasycznym przykładzie biznesowym, tabela "Customers" i tabela "Orders" z relacją między nimi łączącymi się z klientami i ich odpowiednimi zleceniami. Aby uzyskać więcej informacji na temat tworzenia aplikacji wzorzec/szczegóły przy użyciu dwóch kontrolek <xref:System.Windows.Forms.DataGridView> Windows Forms, zobacz [How to: Create a master/detail form przy użyciu dwóch kontrolek DataGridView Windows Forms](./controls/create-a-master-detail-form-using-two-datagridviews.md)|  
|Tabela wyszukiwania|Innym typowym scenariuszem prezentacji/manipulowania danymi jest wyszukiwanie w tabeli. Często w ramach większego wyświetlania danych formant <xref:System.Windows.Forms.ComboBox> służy do wyświetlania i manipulowania danymi. Klucz polega na tym, że dane wyświetlane w kontrolce <xref:System.Windows.Forms.ComboBox> są inne niż dane zapisywane w bazie danych. Na przykład jeśli masz formant <xref:System.Windows.Forms.ComboBox> wyświetlający elementy dostępne ze sklepu spożywczego, prawdopodobnie chcesz zobaczyć nazwy produktów (chleb, mleko, jaja). Aby jednak ułatwić pobieranie informacji w bazie danych i normalizacji baz danych, prawdopodobnie dane dla konkretnych elementów danego zamówienia są przechowywane w postaci numerów elementów (#501, #603 itd.). W związku z tym istnieje niejawne połączenie między "przyjazną nazwą" elementu spożywczego w kontrolce <xref:System.Windows.Forms.ComboBox> w formularzu i numerem powiązanego elementu, który jest obecny w kolejności. Jest to istota wyszukiwania tabeli. Aby uzyskać więcej informacji, zobacz [How to: Create a Lookup Table with the Windows Forms BindingSource składnik](./controls/how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component.md).|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Binding>
- [Wiązanie danych formularzy Windows Forms](windows-forms-data-binding.md)
- [Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych](./controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [BindingSource, składnik](./controls/bindingsource-component.md)
