---
title: DataGridView — Architektura formantu (Formularze systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: a9fc1707b1691266d1844c411a08e7e8f35514ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529485"
---
# <a name="datagridview-control-architecture-windows-forms"></a>DataGridView — Architektura formantu (Formularze systemu Windows)
<xref:System.Windows.Forms.DataGridView> Kontroli oraz ich powiązanymi klasami, które są zaprojektowane jako elastyczny i rozszerzalny system do wyświetlania i edytowania danych tabelarycznych. Te klasy są zawarte w <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw, a ich są nazywane z prefiksem "DataGridView".  
  
## <a name="architecture-elements"></a>Elementy architektury  
 Podstawowy <xref:System.Windows.Forms.DataGridView> pochodną klasy Pomocnika <xref:System.Windows.Forms.DataGridViewElement>. Przedstawiono w następujących modelu obiektów <xref:System.Windows.Forms.DataGridViewElement> hierarchii dziedziczenia.  
  
 ![Model obiektu DataGridViewElement](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")  
Model obiektu DataGridViewElement  
  
 <xref:System.Windows.Forms.DataGridViewElement> Klasy zawiera odwołanie do elementu nadrzędnego <xref:System.Windows.Forms.DataGridView> kontroli i ma <xref:System.Windows.Forms.DataGridViewElement.State%2A> właściwość, która zawiera wartość, która reprezentuje kombinację wartości z <xref:System.Windows.Forms.DataGridViewElementStates> wyliczenia.  
  
 W poniższych sekcjach opisano <xref:System.Windows.Forms.DataGridView> pomocniczy klasy bardziej szczegółowo.  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 <xref:System.Windows.Forms.DataGridViewElementStates> Wyliczenie zawiera następujące wartości:  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 Wartości tego wyliczenia można łączyć z bitowego operatorów logicznych, więc <xref:System.Windows.Forms.DataGridViewElement.State%2A> właściwości można wyrazić więcej niż jednego stanu na raz. Na przykład <xref:System.Windows.Forms.DataGridViewElement> mogą być jednocześnie <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, i <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.  
  
### <a name="cells-and-bands"></a>Komórek i paski  
 <xref:System.Windows.Forms.DataGridView> Kontroli składa się z dwóch podstawowych typów obiektów: komórek i grup. Wszystkie komórki pochodzi od <xref:System.Windows.Forms.DataGridViewCell> klasy podstawowej. Dwa rodzaje grup, <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.Windows.Forms.DataGridViewRow>, zarówno pochodzi od <xref:System.Windows.Forms.DataGridViewBand> klasy podstawowej.  
  
 <xref:System.Windows.Forms.DataGridView> Kontroli współdziała z kilku klas, ale są najczęściej spotykanych <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, i <xref:System.Windows.Forms.DataGridViewRow>.  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 Komórka jest podstawową jednostkę interakcji dla <xref:System.Windows.Forms.DataGridView>. Wyświetl skupia się na komórek i wprowadzania danych zwykle odbywa się za pośrednictwem komórek. Dostęp do komórki za pomocą <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> zbiór <xref:System.Windows.Forms.DataGridViewRow> klasy, a mogą uzyskiwać dostęp do zaznaczonych komórek przy użyciu <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> kolekcję <xref:System.Windows.Forms.DataGridView> formantu. Następujące modelu obiektów przedstawiono użycia i przedstawia <xref:System.Windows.Forms.DataGridViewCell> hierarchii dziedziczenia.  
  
 ![Obiekt DataGridViewCell modelu](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")  
Model obiektu DataGridViewCell  
  
 <xref:System.Windows.Forms.DataGridViewCell> Typu jest abstrakcyjna klasa podstawowa, z którego pochodzi wszystkie typy komórki. <xref:System.Windows.Forms.DataGridViewCell> i jego typów pochodnych nie są formanty formularzy systemu Windows, ale niektóre formanty formularzy systemu Windows hosta. Wszystkie funkcje edytowania obsługiwane przez komórki jest zazwyczaj obsługiwane przez formant hostowanej.  
  
 <xref:System.Windows.Forms.DataGridViewCell> obiekty nie kontroli własnych wygląd i funkcje malowania w taki sam sposób jak formanty formularzy systemu Windows. Zamiast tego <xref:System.Windows.Forms.DataGridView> jest odpowiedzialny za wygląd jego <xref:System.Windows.Forms.DataGridViewCell> obiektów. Użytkownik może znacząco wpłynąć na wygląd i zachowanie komórki za pomocą <xref:System.Windows.Forms.DataGridView> właściwości i zdarzeń formantu. Jeśli masz specjalne wymagania dotyczące dostosowania, które są poza możliwościami <xref:System.Windows.Forms.DataGridView> sterowania, można zaimplementować własne klasy, która pochodzi z <xref:System.Windows.Forms.DataGridViewCell> lub jednej z jej klas podrzędnych.  
  
 Poniższa lista zawiera klasy pochodne od <xref:System.Windows.Forms.DataGridViewCell>:  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewImageCell>  
  
-   <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
-   Z typów niestandardowych komórki  
  
### <a name="datagridviewcolumn"></a>DataGridViewColumn  
 Schemat <xref:System.Windows.Forms.DataGridView> magazynu dołączonych danych formantu jest wyrażona w <xref:System.Windows.Forms.DataGridView> kolumn formantu. Dostęp można uzyskać <xref:System.Windows.Forms.DataGridView> kolumn formantu przy użyciu <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekcji. Dostęp do wybranych kolumn za pomocą <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> kolekcji. Następujące modelu obiektów przedstawiono użycia i przedstawia <xref:System.Windows.Forms.DataGridViewColumn> hierarchii dziedziczenia.  
  
 ![Model obiektu DataGridViewColumn](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")  
Model obiektu DataGridViewColumn  
  
 Niektóre typy komórka klucza mają odpowiednie typy kolumn. Te pochodzą od <xref:System.Windows.Forms.DataGridViewColumn> klasy podstawowej.  
  
 Poniższa lista zawiera klasy pochodne od <xref:System.Windows.Forms.DataGridViewColumn>:  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   Z typów kolumn niestandardowych  
  
### <a name="datagridview-editing-controls"></a>Formanty edycji DataGridView  
 Komórki, które zwykle obsługuje zaawansowane funkcje edytowania Użyj hostowanej kontrolkę, która pochodzi z formantu formularzy systemu Windows. Formanty także implementować <xref:System.Windows.Forms.IDataGridViewEditingControl> interfejsu. Następujące model obiektów przedstawiono sposób użycia tych kontrolek.  
  
 ![Edytowania modelu obiektu formant DataGridView](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")  
Formant DataGridView edycji model obiektu  
  
 Następujące formantów edycji są dostarczane z <xref:System.Windows.Forms.DataGridView> sterowania:  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 Informacji o tworzeniu własnych edycji formantów, zobacz [porady: formanty hosta w komórkach DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
 W poniższej tabeli przedstawiono relacje między formantów edycji komórki typów i typy kolumn.  
  
|Typ komórki|Obsługiwanego formantu|Typ kolumny|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|n/d|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|n/d|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|n/d|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|n/d|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a>DataGridViewRow  
 <xref:System.Windows.Forms.DataGridViewRow> Pola rekordu danych z danych wyświetla klasy magazynu do której <xref:System.Windows.Forms.DataGridView> kontroli jest dołączony. Dostęp można uzyskać <xref:System.Windows.Forms.DataGridView> wierszy formantu przy użyciu <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji. Dostęp do zaznaczonych wierszy za pomocą <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> kolekcji. Następujące modelu obiektów przedstawiono użycia i przedstawia <xref:System.Windows.Forms.DataGridViewRow> hierarchii dziedziczenia.  
  
 ![Model obiektu DataGridViewRow](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")  
Model obiektu DataGridViewRow  
  
 Mogą pochodzić własnych typów z <xref:System.Windows.Forms.DataGridViewRow> klasy, mimo że zwykle nie będzie to konieczne. <xref:System.Windows.Forms.DataGridView> Formant ma kilka zdarzeń związanych z wiersza i właściwości dostosowywania zachowania jego <xref:System.Windows.Forms.DataGridViewRow> obiektów.  
  
 Po włączeniu <xref:System.Windows.Forms.DataGridView> formantu <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> właściwość specjalne wiersz dodawania nowych wierszy jest wyświetlana jako ostatni wiersz. Ten wiersz jest częścią <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji, ale ma specjalne funkcje, które mogą wymagać Twojej uwagi. Aby uzyskać więcej informacji, zobacz [używanie wiersza dla nowych rekordów w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 [DataGridView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [Używanie wiersza dla nowych rekordów w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
