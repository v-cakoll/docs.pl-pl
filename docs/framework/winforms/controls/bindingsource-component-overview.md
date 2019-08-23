---
title: BindingSource — Informacje o składniku
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- controls [Windows Forms], binding to data
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: be838caf-fcb0-4b68-827f-58b2c04b747f
ms.openlocfilehash: bd1b38b434f9932a575745d7a1761ff18b009115
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917811"
---
# <a name="bindingsource-component-overview"></a>BindingSource — Informacje o składniku
<xref:System.Windows.Forms.BindingSource> Składnik został zaprojektowany, aby uprościć proces powiązań formantów do bazowego źródła danych. <xref:System.Windows.Forms.BindingSource> Składnik działa jako kanał i źródło danych dla innych formantów do powiązania. Zapewnia abstrakcję połączenia danych formularza podczas przekazywania poleceń do podstawowej listy danych. Ponadto można dodać bezpośrednio do niego dane, tak aby sam składnik funkcjonuje jako źródło danych.  
  
## <a name="bindingsource-component-as-an-intermediary"></a>Składnik BindingSource jako pośrednik  
 <xref:System.Windows.Forms.BindingSource> Składnik działa jako źródło danych dla niektórych lub wszystkich kontrolek w formularzu. W programie Visual Studio <xref:System.Windows.Forms.BindingSource> można powiązać kontrolkę za `DataBindings` pomocą właściwości, która jest dostępna z okna **Właściwości** . Zapoznaj [się również z tematem: Powiązywanie formantów Windows Forms ze składnikiem BindingSource przy użyciu narzędzia](bind-wf-controls-with-the-bindingsource.md)Projektant.  
  
 Można powiązać <xref:System.Windows.Forms.BindingSource> składnik z prostymi źródłami danych, takimi jak pojedyncza właściwość obiektu lub Kolekcja podstawowa, taka jak <xref:System.Collections.ArrayList>i złożone źródła danych, takie jak tabela bazy danych. <xref:System.Windows.Forms.BindingSource> Składnik działa jako pośrednik, który zapewnia usługi dotyczące powiązań i zarządzania walutą. W czasie projektowania lub czasie wykonywania można powiązać <xref:System.Windows.Forms.BindingSource> składnik ze złożonym źródłem danych, ustawiając jego <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości i <xref:System.Windows.Forms.BindingSource.DataMember%2A> odpowiednio do bazy danych i tabeli. Na poniższej ilustracji przedstawiono, <xref:System.Windows.Forms.BindingSource> gdzie składnik mieści się w istniejącej architekturze powiązania danych.  
  
 ![Architektura powiązania źródła i danych](./media/net-bindsrcdatabindarch.gif "NET_BindSrcDataBindArch")  
  
> [!NOTE]
> W czasie projektowania niektóre akcje, takie jak przeciąganie tabeli bazy danych z okna danych do pustego formularza, spowodują utworzenie <xref:System.Windows.Forms.BindingSource> składnika, powiązanie go z źródłowym źródłem danych i dodanie kontrolek obsługujących dane w jednej operacji. Zapoznaj [się również z kontrolkami Windows Forms powiązań z danymi w programie Visual Studio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio).  
  
## <a name="bindingsource-component-as-a-data-source"></a>BindingSource — składnik jako źródło danych  
 Jeśli zaczniesz dodawać elementy do <xref:System.Windows.Forms.BindingSource> składnika bez wcześniejszego określenia listy, z którą chcesz powiązać, składnik będzie działał jak źródło danych w stylu listy i akceptuje te dodane elementy.  
  
 Ponadto można napisać kod, aby zapewnić niestandardowe funkcje "AddNew" przy <xref:System.Windows.Forms.BindingSource.AddingNew> użyciu zdarzenia, które jest zgłaszane, <xref:System.Windows.Forms.BindingSource.AddNew%2A> gdy metoda jest wywoływana przed dodaniem elementu do listy. Aby uzyskać więcej informacji, zobacz temat [Architektura składnika BindingSource](bindingsource-component-architecture.md).  
  
## <a name="navigation"></a>Nawigacja  
 W przypadku użytkowników, którzy chcą nawigować po danych w formularzu, składnik <xref:System.Windows.Forms.BindingNavigator> ten umożliwia nawigowanie i manipulowanie danymi w ramach koordynacji <xref:System.Windows.Forms.BindingSource> z składnikiem. Aby uzyskać więcej informacji, zobacz [BindingNavigator — kontrolka](bindingnavigator-control-windows-forms.md).  
  
## <a name="data-manipulation"></a>Manipulowanie danymi  
 : <xref:System.Windows.Forms.BindingSource> Działa<xref:System.Windows.Forms.CurrencyManager> jako dla wszystkich powiązań i może, w związku z tym, zapewnić dostęp do waluty i informacje o pozycji dotyczące źródła danych. W poniższej tabeli przedstawiono członków, których <xref:System.Windows.Forms.BindingSource> składnik zapewnia do uzyskiwania dostępu do danych źródłowych i manipulowania nimi.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Current%2A>wartość|Pobiera bieżący element źródła danych.|  
|<xref:System.Windows.Forms.BindingSource.Position%2A>wartość|Pobiera lub ustawia bieżącą pozycję na liście podstawowej.|  
|<xref:System.Windows.Forms.BindingSource.List%2A>wartość|Pobiera listę, która jest oszacowaniem <xref:System.Windows.Forms.BindingSource.DataSource%2A> i <xref:System.Windows.Forms.BindingSource.DataMember%2A> oszacowaniem. Jeśli <xref:System.Windows.Forms.BindingSource.DataMember%2A> nie jest ustawiona, zwraca listę określoną przez <xref:System.Windows.Forms.BindingSource.DataSource%2A>.|  
|<xref:System.Windows.Forms.BindingSource.Insert%2A>Method|Wstawia element na liście pod określonym indeksem.|  
|<xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A>Method|Usuwa bieżący element z listy.|  
|<xref:System.Windows.Forms.BindingSource.EndEdit%2A>Method|Stosuje oczekujące zmiany do bazowego źródła danych.|  
|<xref:System.Windows.Forms.BindingSource.CancelEdit%2A>Method|Anuluje bieżącą operację edycji.|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A>Method|Dodaje nowy element do listy podstawowej. Jeśli źródło danych implementuje <xref:System.ComponentModel.IBindingList> i zwraca element <xref:System.Windows.Forms.BindingSource.AddingNew> ze zdarzenia, dodaje ten element. W przeciwnym razie żądanie jest przesyłane do <xref:System.ComponentModel.IBindingList.AddNew%2A> metody listy. Jeśli podstawowa lista nie <xref:System.ComponentModel.IBindingList>jest, element jest automatycznie tworzony za pomocą publicznego konstruktora bez parametrów.|  
  
## <a name="sorting-and-filtering"></a>sortowanie i filtrowanie  
 Zazwyczaj należy współpracować z widokiem uporządkowanym lub filtrowanym źródła danych. W poniższej tabeli przedstawiono elementy członkowskie <xref:System.Windows.Forms.BindingSource> udostępniane przez źródło danych składnika.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A>wartość|Jeśli źródło danych to <xref:System.ComponentModel.IBindingList>, Pobiera lub ustawia nazwę kolumny służącą do sortowania i sortowania informacji. Jeśli źródło danych jest obsługiwane przez <xref:System.ComponentModel.IBindingListView> funkcję sortowania zaawansowanego, pobiera wiele nazw kolumn używanych do sortowania i sortowania informacji o kolejności|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A>wartość|Jeśli źródło danych jest <xref:System.ComponentModel.IBindingListView>, Pobiera lub ustawia wyrażenie używane do filtrowania wierszy, które są wyświetlane.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [BindingSource, składnik — architektura](bindingsource-component-architecture.md)
- [BindingSource, składnik](bindingsource-component.md)
- [BindingNavigator, kontrolka](bindingnavigator-control-windows-forms.md)
- [Wiązanie danych formularzy Windows Forms](../windows-forms-data-binding.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
