---
title: DataGridView — Architektura formantu
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 2e1884383cca87f8d4ff84f486e2b29761a0c55d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742529"
---
# <a name="datagridview-control-architecture-windows-forms"></a>DataGridView — Architektura formantu (Formularze systemu Windows)
Formant <xref:System.Windows.Forms.DataGridView> i powiązane z nim klasy zostały zaprojektowane jako elastyczny, rozszerzalny system do wyświetlania i edytowania danych tabelarycznych. Wszystkie te klasy są zawarte w przestrzeni nazw <xref:System.Windows.Forms?displayProperty=nameWithType> i są wszystkie nazwane z prefiksem "DataGridView".  
  
## <a name="architecture-elements"></a>Elementy architektury  
 Klasy pomocnika podstawowego <xref:System.Windows.Forms.DataGridView> pochodzą z <xref:System.Windows.Forms.DataGridViewElement>. Poniższy model obiektów ilustruje hierarchię dziedziczenia <xref:System.Windows.Forms.DataGridViewElement>.  
  
 ![Diagram przedstawiający hierarchię modeli obiektów DataGridViewelement.](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 Klasa <xref:System.Windows.Forms.DataGridViewElement> zawiera odwołanie do kontrolki nadrzędnej <xref:System.Windows.Forms.DataGridView> i ma właściwość <xref:System.Windows.Forms.DataGridViewElement.State%2A>, która przechowuje wartość, która reprezentuje kombinację wartości z wyliczenia <xref:System.Windows.Forms.DataGridViewElementStates>.  
  
 W poniższych sekcjach opisano klasy pomocnika <xref:System.Windows.Forms.DataGridView> bardziej szczegółowo.  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 Wyliczenie <xref:System.Windows.Forms.DataGridViewElementStates> zawiera następujące wartości:  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 Wartości tego wyliczenia można łączyć z bitowymi operatorami logicznymi, więc Właściwość <xref:System.Windows.Forms.DataGridViewElement.State%2A> może jawnie wyznaczać więcej niż jeden stan. Na przykład <xref:System.Windows.Forms.DataGridViewElement> może być jednocześnie <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>i <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.  
  
### <a name="cells-and-bands"></a>Komórki i paski  
 Formant <xref:System.Windows.Forms.DataGridView> składa się z dwóch podstawowych rodzajów obiektów: komórek i grup. Wszystkie komórki pochodzą z klasy bazowej <xref:System.Windows.Forms.DataGridViewCell>. Dwa rodzaje grup, <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.Windows.Forms.DataGridViewRow>, są pochodną od klasy bazowej <xref:System.Windows.Forms.DataGridViewBand>.  
  
 Formant <xref:System.Windows.Forms.DataGridView> współdziała z kilkoma klasami, ale najczęściej spotykane są <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>i <xref:System.Windows.Forms.DataGridViewRow>.  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 Komórka jest podstawową jednostką interakcji dla <xref:System.Windows.Forms.DataGridView>. Wyświetlacz jest wyśrodkowany w komórkach, a wpis danych jest często wykonywany za poorednictwem komórek. Możesz uzyskać dostęp do komórek przy użyciu kolekcji <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> klasy <xref:System.Windows.Forms.DataGridViewRow> i można uzyskać dostęp do wybranych komórek przy użyciu kolekcji <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> kontrolki <xref:System.Windows.Forms.DataGridView>. Poniższy model obiektów ilustruje to użycie i pokazuje hierarchię dziedziczenia <xref:System.Windows.Forms.DataGridViewCell>.  
  
 ![Diagram przedstawiający hierarchię modeli obiektów DataGridViewCell.](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 Typ <xref:System.Windows.Forms.DataGridViewCell> jest abstrakcyjną klasą bazową, z której są wyprowadzane wszystkie typy komórek. <xref:System.Windows.Forms.DataGridViewCell> i jego typy pochodne nie są Windows Forms kontrolkami, ale niektóre kontrolki Windows Forms hosta. Wszystkie funkcje edycji obsługiwane przez komórkę są zwykle obsługiwane przez obsługiwaną kontrolę.  
  
 obiekty <xref:System.Windows.Forms.DataGridViewCell> nie kontrolują własnych funkcji wyglądu i malowania w taki sam sposób jak kontrolki Windows Forms. Zamiast tego <xref:System.Windows.Forms.DataGridView> jest odpowiedzialny za wygląd obiektów <xref:System.Windows.Forms.DataGridViewCell>. Możesz znacząco wpłynąć na wygląd i zachowanie komórek, współpracując z właściwościami i zdarzeniami kontrolki <xref:System.Windows.Forms.DataGridView>. Jeśli istnieją specjalne wymagania dotyczące dostosowań, które wykraczają poza możliwości formantu <xref:System.Windows.Forms.DataGridView>, można zaimplementować własną klasę, która pochodzi od <xref:System.Windows.Forms.DataGridViewCell> lub jednej z jej klas podrzędnych.  
  
 Na poniższej liście przedstawiono klasy pochodne <xref:System.Windows.Forms.DataGridViewCell>:  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
- <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewImageCell>  
  
- <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
- Niestandardowe typy komórek  
  
### <a name="datagridviewcolumn"></a>DataGridViewColumn  
 Schemat dołączonego magazynu danych kontrolki <xref:System.Windows.Forms.DataGridView> jest wyrażony w kolumnach kontrolki <xref:System.Windows.Forms.DataGridView>. Dostęp do kolumn kontrolki <xref:System.Windows.Forms.DataGridView> można uzyskać przy użyciu kolekcji <xref:System.Windows.Forms.DataGridView.Columns%2A>. Dostęp do wybranych kolumn można uzyskać przy użyciu kolekcji <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>. Poniższy model obiektów ilustruje to użycie i pokazuje hierarchię dziedziczenia <xref:System.Windows.Forms.DataGridViewColumn>.  
  
 ![Diagram przedstawiający hierarchię modeli obiektów DataGridViewColumn.](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 Niektóre typy komórek klucza mają odpowiednie typy kolumn. Są one uzyskiwane z klasy bazowej <xref:System.Windows.Forms.DataGridViewColumn>.  
  
 Na poniższej liście przedstawiono klasy pochodne <xref:System.Windows.Forms.DataGridViewColumn>:  
  
- <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
- Niestandardowe typy kolumn  
  
### <a name="datagridview-editing-controls"></a>Kontrolki edycji DataGridView  
 Komórki obsługujące zaawansowane funkcje edycji zwykle korzystają z hostowanej kontrolki, która jest pochodną formantu Windows Forms. Te formanty również implementują interfejs <xref:System.Windows.Forms.IDataGridViewEditingControl>. Poniższy model obiektów ilustruje użycie tych kontrolek.  
  
 ![Diagram przedstawiający hierarchię modelu obiektów sterujących kontrolki DataGridView.](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 Następujące kontrolki edycji są dostępne z kontrolką <xref:System.Windows.Forms.DataGridView>:  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 Aby uzyskać informacje na temat tworzenia własnych kontrolek edycji, zobacz [How to: Host Controls in Windows Forms Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
 W poniższej tabeli przedstawiono relacje między typami komórek, typami kolumn i kontrolkami edycji.  
  
|Typ komórki|Formant hostowany|Typ kolumny|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|n/d|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|n/d|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|n/d|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|n/d|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a>DataGridViewRow  
 Klasa <xref:System.Windows.Forms.DataGridViewRow> wyświetla pola danych rekordu z magazynu danych, do którego jest dołączona kontrolka <xref:System.Windows.Forms.DataGridView>. Możesz uzyskać dostęp do wierszy kontrolki <xref:System.Windows.Forms.DataGridView> przy użyciu kolekcji <xref:System.Windows.Forms.DataGridView.Rows%2A>. Możesz uzyskać dostęp do wybranych wierszy przy użyciu kolekcji <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>. Poniższy model obiektów ilustruje to użycie i pokazuje hierarchię dziedziczenia <xref:System.Windows.Forms.DataGridViewRow>.  
  
 ![Diagram przedstawiający hierarchię modeli obiektów DataGridViewRow.](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 Można utworzyć własne typy z klasy <xref:System.Windows.Forms.DataGridViewRow>, chociaż zwykle nie jest to konieczne. Kontrolka <xref:System.Windows.Forms.DataGridView> ma kilka zdarzeń związanych z wierszami i właściwości służące do dostosowywania zachowania obiektów <xref:System.Windows.Forms.DataGridViewRow>.  
  
 Jeśli włączysz Właściwość <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> kontrolki <xref:System.Windows.Forms.DataGridView>, w ostatnim wierszu zostanie wyświetlony specjalny wiersz służący do dodawania nowych wierszy. Ten wiersz jest częścią kolekcji <xref:System.Windows.Forms.DataGridView.Rows%2A>, ale ma specjalne funkcje, które mogą wymagać Twojej uwagi. Aby uzyskać więcej informacji, zobacz [używanie wiersza dla nowych rekordów w kontrolce DataGridView Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- [DataGridView, kontrolka — omówienie](datagridview-control-overview-windows-forms.md)
- [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [Używanie wiersza dla nowych rekordów w kontrolce DataGridView formularzy Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
