---
title: Powiązanie danych
description: Dowiedz się, jak powiązać z tablicą wartości obliczanych w czasie wykonywania, odczytywać z pliku lub dziedziczyć z wartości innych kontrolek w Windows Forms.
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
ms.openlocfilehash: 78e8a3287c565cfa7dae56b68c0eb57f48c30ea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619666"
---
# <a name="data-binding-and-windows-forms"></a>Wiązanie danych i formularze systemu Windows
W Windows Forms można powiązać nie tylko z tradycyjnymi źródłami danych, ale również z niemal każdą strukturą zawierającą dane. Można powiązać z tablicą wartości obliczanych w czasie wykonywania, odczytywać z pliku lub dziedziczyć z wartości innych kontrolek.  
  
 Ponadto można powiązać dowolną Właściwość dowolnej kontrolki ze źródłem danych. W tradycyjnym powiązaniu danych zazwyczaj wiąże się z właściwością wyświetlania — na przykład z <xref:System.Windows.Forms.Control.Text%2A> właściwością <xref:System.Windows.Forms.TextBox> kontrolki — do źródła danych. Za pomocą .NET Framework można również ustawić inne właściwości za pomocą powiązania. Możesz użyć powiązania, aby wykonać następujące zadania:  
  
- Ustawianie grafiki kontrolki obrazu.  
  
- Ustawianie koloru tła co najmniej jednej kontrolki.  
  
- Ustawianie rozmiaru kontrolek.  
  
 Zasadniczo wiązanie danych jest automatycznym sposobem ustawienia właściwości dostępnych w czasie wykonywania dowolnej kontrolki w formularzu.  
  
## <a name="types-of-data-binding"></a>Typy powiązań danych  
 Windows Forms może korzystać z dwóch typów powiązań danych: prostego powiązania i powiązania złożonego. Każda z nich oferuje różne zalety.  
  
|Typ powiązania danych|Opis|  
|--------------------------|-----------------|  
|Proste powiązanie danych|Możliwość powiązania formantu z pojedynczym elementem danych, takim jak wartość w kolumnie w tabeli dataset. Jest to typ powiązania typowy dla kontrolek, takich jak <xref:System.Windows.Forms.TextBox> kontrolka lub <xref:System.Windows.Forms.Label> kontrolka, które są kontrolkami, które zwykle wyświetlają tylko jedną wartość. W rzeczywistości każda właściwość kontrolki może być powiązana z polem w bazie danych. W programie Visual Studio jest dostępna szeroka obsługa tej funkcji.<br /><br /> Aby uzyskać więcej informacji, zobacz:<br /><br /> -   [Interfejsy związane z powiązaniem danych](interfaces-related-to-data-binding.md)<br />-   [Instrukcje: nawigowanie po danych w Windows Forms](how-to-navigate-data-in-windows-forms.md)<br />-   [Instrukcje: Tworzenie prostego formantu powiązanego w formularzu systemu Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md)|  
|Złożone powiązanie danych|Możliwość powiązania formantu z więcej niż jednym elementem danych, zwykle więcej niż jeden rekord w bazie danych. Złożone powiązanie jest również nazywane powiązaniem opartym na liście. Przykłady formantów, które obsługują złożone powiązania, to <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.ListBox> <xref:System.Windows.Forms.ComboBox> kontrolki, i. Aby zapoznać się z przykładem złożonego powiązania danych, zobacz [How to: bind a Windows Forms ComboBox lub ListBox formant do danych](./controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md).|  
  
## <a name="bindingsource-component"></a>BindingSource — Składnik  
 Aby uprościć powiązanie danych, Windows Forms umożliwia powiązanie źródła danych ze <xref:System.Windows.Forms.BindingSource> składnikiem, a następnie powiązanie kontrolek z <xref:System.Windows.Forms.BindingSource> . Możesz użyć <xref:System.Windows.Forms.BindingSource> prostych lub złożonych scenariuszy powiązań. W każdym z tych przypadków <xref:System.Windows.Forms.BindingSource> działa jako pośrednik między źródłem danych i formantami związanymi z zarządzaniem walutą powiadomień o zmianach i innymi usługami.  
  
## <a name="common-scenarios-that-employ-data-binding"></a>Typowe scenariusze, które wykorzystują powiązanie danych  
 Niemal każda aplikacja komercyjna korzysta z informacji odczytywanych ze źródeł danych jednego typu lub innych, zazwyczaj za pośrednictwem powiązań danych. Na poniższej liście przedstawiono kilka typowych scenariuszy, które wykorzystują powiązanie danych jako metody prezentacji i manipulowania danymi.  
  
|Scenariusz|Opis|  
|--------------|-----------------|  
|Raportowanie|Raporty zapewniają elastyczny sposób wyświetlania i podsumowywania danych w wydrukowanym dokumencie. Często istnieje możliwość utworzenia raportu, który drukuje wybraną zawartość źródła danych na ekranie lub do drukarki. Typowe raporty obejmują listy, faktury i podsumowania. Elementy są zwykle sformatowane do kolumn list, z elementami podrzędnymi zorganizowanymi pod każdym elementem listy, ale należy wybrać układ, który najlepiej odpowiada danym.|  
|Wprowadzanie danych|Typowym sposobem wprowadzania dużych ilości powiązanych danych lub monitowania użytkowników o informacje jest użycie formularza wprowadzania danych. Użytkownicy mogą wprowadzać informacje lub wybierać opcje przy użyciu pól tekstowych, przycisków opcji, list rozwijanych i pól wyboru. Informacje są następnie przesyłane i przechowywane w bazie danych, której struktura jest oparta na wprowadzonych informacjach.|  
|Wzorzec/szczegóły relacji|Aplikacja master/detail ma jeden format do przeglądania powiązanych danych. W konkretnym przypadku istnieją dwie tabele danych z relacją łączącą je — w klasycznym przykładzie biznesowym, tabela "Customers" i tabela "Orders" z relacją między nimi łączącymi się z klientami i ich odpowiednimi zleceniami. Aby uzyskać więcej informacji na temat tworzenia aplikacji wzorzec/szczegóły z dwoma <xref:System.Windows.Forms.DataGridView> kontrolkami Windows Forms, zobacz [How to: Create a master/detail form przy użyciu dwóch Windows Forms formantów DataGridView](./controls/create-a-master-detail-form-using-two-datagridviews.md)|  
|Tabela wyszukiwania|Innym typowym scenariuszem prezentacji/manipulowania danymi jest wyszukiwanie w tabeli. Często w ramach większego wyświetlania danych <xref:System.Windows.Forms.ComboBox> kontrolka służy do wyświetlania i manipulowania danymi. Klucz polega na tym, że dane wyświetlane w <xref:System.Windows.Forms.ComboBox> formancie są inne niż dane zapisywane w bazie danych. Na przykład jeśli masz <xref:System.Windows.Forms.ComboBox> kontrolkę wyświetlającą elementy dostępne ze sklepu spożywczego, prawdopodobnie chcesz zobaczyć nazwy produktów (chleb, mleko, jaja). Aby jednak ułatwić pobieranie informacji w bazie danych i normalizacji baz danych, prawdopodobnie dane dla konkretnych elementów danego zamówienia są przechowywane w postaci numerów elementów (#501, #603 itd.). W związku z tym istnieje niejawne połączenie między "przyjazną nazwą" elementu w <xref:System.Windows.Forms.ComboBox> formancie w formularzu i numerem powiązanego elementu, który jest obecny w kolejności. Jest to istota wyszukiwania tabeli. Aby uzyskać więcej informacji, zobacz [How to: Create a Lookup Table with the Windows Forms BindingSource składnik](./controls/how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component.md).|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Binding>
- [Powiązywanie danych formularzy systemu Windows](windows-forms-data-binding.md)
- [Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych](./controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [BindingSource, składnik](./controls/bindingsource-component.md)
