---
title: DataGridView — Architektura formantu (Formularze systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: c57f7d22219c0cda91dad174be4e225808a9949d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494928"
---
# <a name="datagridview-control-architecture-windows-forms"></a>DataGridView — Architektura formantu (Formularze systemu Windows)
<xref:System.Windows.Forms.DataGridView> Kontroli oraz ich powiązanymi klasami, które są przeznaczone do elastyczny i rozszerzalny system do wyświetlania i edytowania danych tabelarycznych. Te klasy są zawarte w <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw, dlatego są nazywane z prefiksem "DataGridView".  
  
## <a name="architecture-elements"></a>Elementy architektury  
 Podstawowy <xref:System.Windows.Forms.DataGridView> klasy pomocnika pochodzić od <xref:System.Windows.Forms.DataGridViewElement>. Ilustruje następujące modelu obiektów <xref:System.Windows.Forms.DataGridViewElement> hierarchii dziedziczenia.  
  
 ![Model obiektu DataGridViewElement](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")  
Model obiektu DataGridViewElement  
  
 <xref:System.Windows.Forms.DataGridViewElement> Klasy zawiera odwołanie do elementu nadrzędnego <xref:System.Windows.Forms.DataGridView> kontroli i ma <xref:System.Windows.Forms.DataGridViewElement.State%2A> właściwość, która przechowuje wartość, która reprezentuje kombinację wartości z <xref:System.Windows.Forms.DataGridViewElementStates> wyliczenia.  
  
 W poniższych sekcjach opisano <xref:System.Windows.Forms.DataGridView> pomocnika klasy bardziej szczegółowo.  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 <xref:System.Windows.Forms.DataGridViewElementStates> Wyliczenie zawiera następujące wartości:  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 Wartości tego wyliczenia można łączyć z operatory logiczne bitowe, więc <xref:System.Windows.Forms.DataGridViewElement.State%2A> właściwości można wyrazić jednocześnie więcej niż jednego stanu. Na przykład <xref:System.Windows.Forms.DataGridViewElement> mogą być jednocześnie <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, i <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.  
  
### <a name="cells-and-bands"></a>Komórki i paski  
 <xref:System.Windows.Forms.DataGridView> Obejmuje dwa podstawowe rodzaje obiektów: komórek i grup. Dziedziczyć wszystkie komórki <xref:System.Windows.Forms.DataGridViewCell> klasy bazowej. Dwa rodzaje grup, <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.Windows.Forms.DataGridViewRow>, zarówno dziedziczyć <xref:System.Windows.Forms.DataGridViewBand> klasy bazowej.  
  
 <xref:System.Windows.Forms.DataGridView> Kontroli współdziała z kilku klas, ale są najczęściej spotykanych <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, i <xref:System.Windows.Forms.DataGridViewRow>.  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 Komórka jest podstawową jednostką interakcji dla <xref:System.Windows.Forms.DataGridView>. Wyświetlanie skupia się na komórki i wprowadzania danych często odbywa się za pośrednictwem komórek. Dostęp do komórki za pomocą <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> zbiór <xref:System.Windows.Forms.DataGridViewRow> klasy, a dostęp zaznaczonych komórek przy użyciu <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> zbiór <xref:System.Windows.Forms.DataGridView> kontroli. Poniższy model obiektów ilustruje użycie tych i pokazuje <xref:System.Windows.Forms.DataGridViewCell> hierarchii dziedziczenia.  
  
 ![Model obiektu DataGridViewCell](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")  
Model obiektu DataGridViewCell  
  
 <xref:System.Windows.Forms.DataGridViewCell> Typ jest abstrakcyjna klasa bazowa, z której pochodzą wszystkie typy komórki. <xref:System.Windows.Forms.DataGridViewCell> i jego typów pochodnych nie kontrolek formularzy Windows Forms, ale niektóre formanty Windows Forms hosta. Żadnych funkcji dotyczących edytowania objęte komórki jest zazwyczaj obsługiwana przez kontrolkę hostowanej.  
  
 <xref:System.Windows.Forms.DataGridViewCell> obiekty nie mają kontroli nad ich wygląd i funkcje malowania w taki sam sposób jak kontrolek formularzy Windows. Zamiast tego <xref:System.Windows.Forms.DataGridView> jest odpowiedzialny za wyglądu jego <xref:System.Windows.Forms.DataGridViewCell> obiektów. Użytkownik może znacząco wpłynąć na wygląd i zachowanie komórek przez interakcję z <xref:System.Windows.Forms.DataGridView> właściwości i zdarzenia formantu. Jeśli masz specjalne wymagania dotyczące dostosowań, które wykraczają poza możliwości <xref:System.Windows.Forms.DataGridView> kontrolki, można zaimplementować własną klasę pochodzącą od <xref:System.Windows.Forms.DataGridViewCell> lub jednej z jej klas podrzędnych.  
  
 Na poniższej liście przedstawiono klasy pochodne od elementu <xref:System.Windows.Forms.DataGridViewCell>:  
  
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
  
-   Komórka niestandardowych typów  
  
### <a name="datagridviewcolumn"></a>DataGridViewColumn  
 Schemat <xref:System.Windows.Forms.DataGridView> kontrolki dołączonych danych magazynu danych jest wyrażona w <xref:System.Windows.Forms.DataGridView> kolumn formantu. Możesz uzyskać dostęp <xref:System.Windows.Forms.DataGridView> kolumn do formantu za pomocą <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekcji. Dostęp do wybranych kolumn przy użyciu <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> kolekcji. Poniższy model obiektów ilustruje użycie tych i pokazuje <xref:System.Windows.Forms.DataGridViewColumn> hierarchii dziedziczenia.  
  
 ![Model obiektu DataGridViewColumn](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")  
Model obiektu DataGridViewColumn  
  
 Niektóre typy kluczy komórki mają odpowiednie typy kolumn. Te są uzyskiwane z <xref:System.Windows.Forms.DataGridViewColumn> klasy bazowej.  
  
 Na poniższej liście przedstawiono klasy pochodne od elementu <xref:System.Windows.Forms.DataGridViewColumn>:  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   Typów kolumny niestandardowej  
  
### <a name="datagridview-editing-controls"></a>Formanty edycji DataGridView  
 Komórki, które zazwyczaj obsługują zaawansowane funkcje edycji, użyj obsługiwanego formantu, który pochodzi z kontrolki formularzy Windows Forms. Te kontrolki także implementować <xref:System.Windows.Forms.IDataGridViewEditingControl> interfejsu. Poniższy model obiektów ilustruje użycie tych kontrolek.  
  
 ![Edytowanie modelu obiektu formantu DataGridView](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")  
Model obiektów usługi edycji kontrolki DataGridView  
  
 Następujące elementy sterujące edycji są dostarczane z <xref:System.Windows.Forms.DataGridView> sterowania:  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 Aby uzyskać informacje dotyczące tworzenia własnych do edycji kontrolek, zobacz [jak: Kontrolki hosta w formularzach Windows Forms komórkach DataGridView](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
 W poniższej tabeli przedstawiono relację między komórki typy, typy kolumn i formanty edycji.  
  
|Typ komórki|Obsługiwanego formantu|Typ kolumny|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|n/d|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|n/d|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|n/d|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|n/d|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a>DataGridViewRow  
 <xref:System.Windows.Forms.DataGridViewRow> Klasy wyświetla rekord danych pola z danych przechowywania, do której <xref:System.Windows.Forms.DataGridView> związana jest kontrola. Możesz uzyskać dostęp <xref:System.Windows.Forms.DataGridView> wierszy formantu za pomocą <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji. Dostęp do wybranych wierszy przy użyciu <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> kolekcji. Poniższy model obiektów ilustruje użycie tych i pokazuje <xref:System.Windows.Forms.DataGridViewRow> hierarchii dziedziczenia.  
  
 ![Model obiektów DataGridViewRow](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")  
Model obiektowy DataGridViewRow  
  
 Uzyskujesz własnych typów z <xref:System.Windows.Forms.DataGridViewRow> klasy, chociaż zazwyczaj nie będzie to konieczne. <xref:System.Windows.Forms.DataGridView> Kontrolka ma kilka zdarzeń związanych z wierszy, jak i właściwości dostosowywania zachowania jego <xref:System.Windows.Forms.DataGridViewRow> obiektów.  
  
 Po włączeniu <xref:System.Windows.Forms.DataGridView> kontrolki <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> właściwości specjalne wiersz awanie nowych wierszy jest wyświetlany jako ostatni wiersz. Ten wiersz jest częścią <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji, ale ma specjalne funkcje, które mogą wymagać Twojej uwagi. Aby uzyskać więcej informacji, zobacz [używanie wiersza dla nowych rekordów w formancie DataGridView formularzy Windows](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także
- [DataGridView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)
- [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
- [Używanie wiersza dla nowych rekordów w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
