---
title: "AutoSize — Przegląd właściwości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sizing [Windows Forms], automatic
- layout [Windows Forms], AutoSize
- automatic sizing
- AutoSizeMode property
ms.assetid: 62fd82a2-9565-4f65-925b-9d1e66dc4e7d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34f92bdc80f62225efe5e008f0893905f49da970
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="autosize-property-overview"></a>AutoSize — Przegląd właściwości
<xref:System.Windows.Forms.Control.AutoSize%2A> Właściwość umożliwia, aby zmienić jego rozmiar, jeśli to konieczne osiągnąć wartość określoną przez <xref:System.Windows.Forms.Control.PreferredSize%2A> właściwości. Dostosuj zachowanie ustalania rozmiaru formantów określonego przez ustawienie `AutoSizeMode` właściwości.  
  
## <a name="autosize-behavior"></a>AutoSize — zachowanie  
 Obsługuje tylko niektóre formanty <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości. Ponadto niektóre formanty obsługujące <xref:System.Windows.Forms.Control.AutoSize%2A> obsługuje również właściwość `AutoSizeMode` właściwości.  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A> Właściwości tworzy nieco inaczej, w zależności od typu określonego formantu i wartość `AutoSizeMode` właściwości, jeśli istnieje właściwość. W poniższej tabeli opisano zachowania, które są zawsze wartość true i zawiera krótki opis każdego z nich:  
  
|Zachowanie zawsze wartość true|Opis|  
|--------------------------|-----------------|  
|Rozmiar automatyczny jest funkcją czasu wykonywania.|Oznacza to, nigdy nie rozwoju ani zmniejsza formantu i następnie nie ma dalszych wpływu.|  
|W przypadku formantu zmiany rozmiaru, od wartości jego <xref:System.Windows.Forms.Control.Location%2A> właściwość zawsze pozostaje stała.|Gdy zawartość formantu spowodować powiększania, formantu rozwoju prawo i w dół. Formanty nie zwiększa w lewo.|  
|<xref:System.Windows.Forms.Control.Dock%2A> i <xref:System.Windows.Forms.Control.Anchor%2A> właściwości są go uznać, gdy <xref:System.Windows.Forms.Control.AutoSize%2A> jest `true`.|Wartość formantu <xref:System.Windows.Forms.Control.Location%2A> właściwości jest dostosowana do poprawnej wartości.<br /><br /> **Uwaga** <xref:System.Windows.Forms.Label> formant jest wyjątkiem od tej reguły. Przypadku ustawienia wartości zadokowanych <xref:System.Windows.Forms.Label> formantu <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości `true`, <xref:System.Windows.Forms.Label> nie rozciąga formantu.|  
|Formantu <xref:System.Windows.Forms.Control.MaximumSize%2A> i <xref:System.Windows.Forms.Control.MinimumSize%2A> właściwości zawsze są zachowywane, niezależnie od wartości jego <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości.|<xref:System.Windows.Forms.Control.MaximumSize%2A> i <xref:System.Windows.Forms.Control.MinimumSize%2A> nie dotyczy właściwości <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości.|  
|Minimalny rozmiar domyślnie nie jest.|Oznacza to, że jeśli formant ma ustawioną wartość zmniejszyć w obszarze <xref:System.Windows.Forms.Control.AutoSize%2A> i nie zawiera żadnych zawartość wartość jego <xref:System.Windows.Forms.Control.Size%2A> właściwość jest 0,0. W takim przypadku formantu zmniejsza się do punktu, i nie będzie łatwo widoczna.|  
|Jeśli formant nie implementuje <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metody <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metoda zwraca ostatnią wartość przypisana do <xref:System.Windows.Forms.Control.Size%2A> właściwości.|Oznacza to, że ustawienie <xref:System.Windows.Forms.Control.AutoSize%2A> do `true` nie odniesie żadnego skutku.|  
|Formant w <xref:System.Windows.Forms.TableLayoutPanel> komórki zawsze zmniejsza mieści się w komórce aż do jego <xref:System.Windows.Forms.Control.MinimumSize%2A> zostanie osiągnięty.|Ten rozmiar jest wymuszana, jako maksymalny rozmiar. To nie jest to komórka jest częścią <xref:System.Windows.Forms.SizeType.AutoSize> wierszy lub kolumn.|  
  
## <a name="autosizemode-property"></a>AutoSizeMode właściwość  
 `AutoSizeMode` Właściwość zapewnia bardziej precyzyjną kontrolę nad domyślnie <xref:System.Windows.Forms.Control.AutoSize%2A> zachowanie. `AutoSizeMode` Właściwość określa, jak formantu rozmiary się do jego zawartości. Zawartość, na przykład może być tekst <xref:System.Windows.Forms.Button> formantów podrzędnych kontenera.  
  
 W poniższej tabeli przedstawiono <xref:System.Windows.Forms.AutoSizeMode> ustawienia i opis zachowania elicits każdego ustawienia.  
  
|Ustawienie AutoSizeMode|Zachowanie|  
|--------------------------|--------------|  
|GrowAndShrink|Formant rozwoju lub zmniejsza się jego zawartość.<br /><br /> <xref:System.Windows.Forms.Control.MinimumSize%2A> i <xref:System.Windows.Forms.Control.MaximumSize%2A> wartości są honorowane, ale bieżąca wartość <xref:System.Windows.Forms.Control.Size%2A> właściwość jest ignorowana.<br /><br /> To jest takie samo zachowanie jako formantów z <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości i nie `AutoSizeMode` właściwości.|  
|GrowOnly|Formant rozwoju jak niezbędne wszystkie jego zawartość, ale nie będzie mniejsza niż wartość określoną przez zmniejszyć jego <xref:System.Windows.Forms.Control.Size%2A> właściwości.<br /><br /> Jest to wartość domyślna dla `AutoSizeMode`.|  
  
## <a name="controls-that-support-the-autosize-property"></a>Formanty, które obsługują AutoSize właściwość  
 W poniższej tabeli wymieniono formantów, które obsługują <xref:System.Windows.Forms.Control.AutoSize%2A> i `AutoSizeMode` właściwości.  
  
|Obsługa automatycznego dopasowania rozmiaru|Typ formantu|  
|----------------------|------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A>Właściwość jest obsługiwana.<br />-Nie `AutoSizeMode` właściwości.|<xref:System.Windows.Forms.CheckBox><br /><br /> <xref:System.Windows.Forms.DomainUpDown><br /><br /> <xref:System.Windows.Forms.Label><br /><br /> <xref:System.Windows.Forms.LinkLabel><br /><br /> <xref:System.Windows.Forms.MaskedTextBox>(<xref:System.Windows.Forms.TextBox> podstawowy)<br /><br /> <xref:System.Windows.Forms.NumericUpDown><br /><br /> <xref:System.Windows.Forms.RadioButton><br /><br /> <xref:System.Windows.Forms.TextBox><br /><br /> <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A>Właściwość jest obsługiwana.<br />-   `AutoSizeMode`Właściwość jest obsługiwana.|<xref:System.Windows.Forms.Button><br /><br /> <xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.FlowLayoutPanel><br /><br /> <xref:System.Windows.Forms.Form><br /><br /> <xref:System.Windows.Forms.GroupBox><br /><br /> <xref:System.Windows.Forms.Panel><br /><br /> <xref:System.Windows.Forms.TableLayoutPanel>|  
|-Nie <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości.|<xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.ComboBox><br /><br /> <xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DateTimePicker><br /><br /> <xref:System.Windows.Forms.ListBox><br /><br /> <xref:System.Windows.Forms.ListView><br /><br /> <xref:System.Windows.Forms.MaskedTextBox><br /><br /> <xref:System.Windows.Forms.MonthCalendar><br /><br /> <xref:System.Windows.Forms.ProgressBar><br /><br /> <xref:System.Windows.Forms.PropertyGrid><br /><br /> <xref:System.Windows.Forms.RichTextBox><br /><br /> <xref:System.Windows.Forms.SplitContainer><br /><br /> <xref:System.Windows.Forms.TabControl><br /><br /> <xref:System.Windows.Forms.TabPage><br /><br /> <xref:System.Windows.Forms.TreeView><br /><br /> <xref:System.Windows.Forms.WebBrowser><br /><br /> <xref:System.Windows.Forms.ScrollBar>|  
  
## <a name="autosize-in-the-design-environment"></a>AutoSize w środowisku projektowania programu  
 W poniższej tabeli opisano zachowanie ustalania rozmiaru formantu w czasie projektowania, na podstawie wartości z jej <xref:System.Windows.Forms.Control.AutoSize%2A> i `AutoSizeMode` właściwości.  
  
 Zastąpienie <xref:System.Windows.Forms.Design.ControlDesigner.SelectionRules%2A> właściwości w celu określenia, czy dany formant jest w stanie o zmiennym rozmiarze użytkownika. W poniższej tabeli "nie" oznacza <xref:System.Windows.Forms.Design.SelectionRules.Moveable> tylko "można" oznacza <xref:System.Windows.Forms.Design.SelectionRules.AllSizeable> i <xref:System.Windows.Forms.Design.SelectionRules.Moveable>.  
  
|Ustawienia automatycznego dopasowania rozmiaru|Gest zmiany rozmiaru w czasie projektowania|  
|-----------------------|---------------------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-Nie `AutoSizeMode` właściwości.|Użytkownik nie może zmienić rozmiaru formantu w czasie projektowania, z wyjątkiem następujących kontrolek:<br /><br /> -   <xref:System.Windows.Forms.TextBox><br />-   <xref:System.Windows.Forms.MaskedTextBox><br />-   <xref:System.Windows.Forms.RichTextBox><br />-   <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>|Użytkownik nie może zmienić rozmiaru formantu w czasie projektowania.|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>|Użytkownik może zmienić rozmiar formantu w czasie projektowania. Gdy <xref:System.Windows.Forms.Control.Size%2A> właściwość jest ustawiona, użytkownik może tylko zwiększyć rozmiar formantu.|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `false`, lub <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości jest ukryty.|Użytkownik może zmienić rozmiar formantu w czasie projektowania.|  
  
> [!NOTE]
>  Aby zmaksymalizować wydajność, shadows Projektant formularzy systemu Windows <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość <xref:System.Windows.Forms.Form> klasy. W czasie projektowania, działanie formularza jako <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość jest ustawiona na `false`, niezależnie od jego rzeczywistego ustawienia. W czasie wykonywania, staje się nie specjalne zakwaterowania i <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość jest stosowana określone przez ustawienie właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.Control.PreferredSize%2A>  
 <xref:System.Windows.Forms.Control.GetPreferredSize%2A>
