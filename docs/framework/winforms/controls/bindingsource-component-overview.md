---
title: BindingSource — Informacje o składniku
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- controls [Windows Forms], binding to data
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: be838caf-fcb0-4b68-827f-58b2c04b747f
ms.openlocfilehash: 047df677ade3837e167845ace2bdc6ca14738c3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529607"
---
# <a name="bindingsource-component-overview"></a>BindingSource — Informacje o składniku
<xref:System.Windows.Forms.BindingSource> Składnika zaprojektowano w celu uproszczenia procesu powiązania kontroli źródła danych. <xref:System.Windows.Forms.BindingSource> Składnika działa jako prosty kanał i źródła danych dla innych formantów powiązać. Udostępnia abstrakcję połączenie danych formularza podczas przekazywania za pomocą poleceń do podstawowej wykaz danych. Ponadto można dodać danych bezpośrednio do niego, tak aby sam składnik działa jako źródło danych.  
  
## <a name="bindingsource-component-as-an-intermediary"></a>BindingSource — składnik jako pośrednik  
 <xref:System.Windows.Forms.BindingSource> Składnika działa jako źródło danych dla niektórych lub wszystkich kontrolek w formularzu. W programie Visual Studio <xref:System.Windows.Forms.BindingSource> może być powiązana z formantu za pomocą klasy `DataBindings` właściwość, która jest dostępna z **właściwości** okna. Zobacz też [porady: powiązanie formantów formularzy systemu Windows z BindingSource — składnik przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md).  
  
 Możesz powiązać <xref:System.Windows.Forms.BindingSource> składnika obu źródeł danych proste, jak w jednej właściwości obiektu lub kolekcji podstawowych, takich jak <xref:System.Collections.ArrayList>, a źródłami danych złożonych, takie jak tabeli bazy danych. <xref:System.Windows.Forms.BindingSource> Składnika działa jako pośrednik udostępnia powiązania i currency usługi zarządzania. W czasie projektowania lub w czasie wykonywania można powiązać <xref:System.Windows.Forms.BindingSource> składnika ze źródłem danych złożonych, ustawiając jego <xref:System.Windows.Forms.BindingSource.DataSource%2A> i <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwości bazy danych i tabeli, odpowiednio. Poniższa ilustracja przedstawia where <xref:System.Windows.Forms.BindingSource> składnika dopasowuje się do istniejącej architektury powiązania danych.  
  
 ![Powiązania źródła i architektura powiązań danych](../../../../docs/framework/winforms/controls/media/net-bindsrcdatabindarch.gif "NET_BindSrcDataBindArch")  
  
> [!NOTE]
>  W czasie projektowania, niektóre akcje, takie jak przeciąganie tabeli bazy danych z okna danych w formularzu puste, zostanie utworzona <xref:System.Windows.Forms.BindingSource> składnika powiązać źródła danych i Dodaj formantach danych w jednej operacji. Zobacz też [formanty formularzy systemu Windows powiązać z danymi w Visual Studio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio).  
  
## <a name="bindingsource-component-as-a-data-source"></a>BindingSource — składnik jako źródła danych  
 Po uruchomieniu Dodawanie elementów do <xref:System.Windows.Forms.BindingSource> składnika bez określenia listy może być powiązane z składnika będzie działać tak jak styl listy źródła danych i zaakceptuj je dodać elementy.  
  
 Ponadto można napisać kod do zapewnienia funkcji "AddNew" niestandardowych za pomocą klasy <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzenie, które jest wywoływane, gdy <xref:System.Windows.Forms.BindingSource.AddNew%2A> metoda jest wywoływana przed element dodawany do listy. Aby uzyskać więcej informacji, zobacz [architektura składnika BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component-architecture.md).  
  
## <a name="navigation"></a>Nawigacji  
 Dla użytkowników wymagających nawigowanie w danych na formularzu <xref:System.Windows.Forms.BindingNavigator> składnika umożliwia nawigacji i manipulacji danymi w połączeniu z <xref:System.Windows.Forms.BindingSource> składnika. Aby uzyskać więcej informacji, zobacz [formantu BindingNavigator](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md).  
  
## <a name="data-manipulation"></a>Manipulowanie danymi  
 : <xref:System.Windows.Forms.BindingSource> Działa jako <xref:System.Windows.Forms.CurrencyManager> wszystkie jej powiązań i umożliwia, w związku z tym zapewniają dostęp do waluty i pozycji informacji o źródle danych. W poniższej tabeli przedstawiono elementy członkowskie <xref:System.Windows.Forms.BindingSource> składnik zapewnia dostęp i manipulowanie danych.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Current%2A> Właściwość|Pobiera bieżący element źródła danych.|  
|<xref:System.Windows.Forms.BindingSource.Position%2A> Właściwość|Pobiera lub ustawia bieżącą pozycję na liście podstawowej.|  
|<xref:System.Windows.Forms.BindingSource.List%2A> Właściwość|Pobiera listę, który jest ocena <xref:System.Windows.Forms.BindingSource.DataSource%2A> i <xref:System.Windows.Forms.BindingSource.DataMember%2A> oceny. Jeśli <xref:System.Windows.Forms.BindingSource.DataMember%2A> nie jest ustawiona, zwraca listę, określony przez <xref:System.Windows.Forms.BindingSource.DataSource%2A>.|  
|<xref:System.Windows.Forms.BindingSource.Insert%2A> — Metoda|Wstawia element na liście pod określonym indeksem.|  
|<xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> — Metoda|Usuwa bieżący element z listy.|  
|<xref:System.Windows.Forms.BindingSource.EndEdit%2A> — Metoda|Zastosowanie oczekujących zmian źródła danych.|  
|<xref:System.Windows.Forms.BindingSource.CancelEdit%2A> — Metoda|Umożliwia anulowanie bieżącej operacji edycji.|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A> — Metoda|Dodaje nowy element do listy źródłowej. Jeśli źródło danych implementuje <xref:System.ComponentModel.IBindingList> i zwraca element <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzeń, dodaje ten element. W przeciwnym razie żądania są przekazywane do listy <xref:System.ComponentModel.IBindingList.AddNew%2A> metody. Jeżeli lista podstawowa nie jest <xref:System.ComponentModel.IBindingList>, element został automatycznie utworzony przez jego publicznego konstruktora domyślnego.|  
  
## <a name="sorting-and-filtering"></a>Filtrowanie i sortowanie  
 Zazwyczaj powinien współpracować z uporządkowane lub filtrowane widoku źródła danych. W poniższej tabeli przedstawiono elementy członkowskie <xref:System.Windows.Forms.BindingSource> zawiera składnik źródła danych.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A> Właściwość|Jeśli źródło danych jest <xref:System.ComponentModel.IBindingList>, pobiera lub ustawia nazwę kolumny sortowania i informacje o kolejności sortowania. Jeśli źródło danych jest <xref:System.ComponentModel.IBindingListView> i obsługuje sortowanie, zaawansowane pobiera wiele nazw kolumn używana do sortowania i informacje o kolejności sortowania|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A> Właściwość|Jeśli źródło danych jest <xref:System.ComponentModel.IBindingListView>, pobiera lub ustawia wyrażenie używane do filtrowania wierszy, które są wyświetlane.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [BindingSource, składnik — architektura](../../../../docs/framework/winforms/controls/bindingsource-component-architecture.md)  
 [BindingSource, składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [BindingNavigator, kontrolka](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Wiązanie danych formularzy Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
