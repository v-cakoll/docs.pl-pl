---
title: AutoSize — Przegląd właściwości
ms.date: 03/30/2017
helpviewer_keywords:
- sizing [Windows Forms], automatic
- layout [Windows Forms], AutoSize
- automatic sizing
- AutoSizeMode property
ms.assetid: 62fd82a2-9565-4f65-925b-9d1e66dc4e7d
ms.openlocfilehash: 6d5c4a22f186ddc5811c4a4d5e79776decea9e50
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173631"
---
# <a name="autosize-property-overview"></a>AutoSize — Przegląd właściwości
<xref:System.Windows.Forms.Control.AutoSize%2A> Właściwości umożliwia zmianę rozmiaru, jeśli to konieczne osiągnąć wartość określoną przez <xref:System.Windows.Forms.Control.PreferredSize%2A> właściwości. Można dostosować zachowanie zmiany rozmiaru kontrolek, ustawiając `AutoSizeMode` właściwości.  
  
## <a name="autosize-behavior"></a>Zachowanie AutoSize  
 Obsługuje tylko niektóre formanty <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości. Ponadto niektóre formanty obsługujące <xref:System.Windows.Forms.Control.AutoSize%2A> obsługują również właściwość `AutoSizeMode` właściwości.  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A> Właściwości powoduje zachowanie nieco inny, w zależności od typu określonego formantu i wartość `AutoSizeMode` właściwość, jeśli właściwość istnieje. Poniższej tabeli opisano zachowania, które są zawsze true i krótki opis każdego z nich:  
  
|Zawsze true zachowanie|Opis|  
|--------------------------|-----------------|  
|Automatycznej zmiany rozmiaru jest funkcją czasu wykonywania.|Oznacza to, nigdy nie zwiększa się ani zmniejsza kontrolki i następnie nie ma dalszych wpływu.|  
|Jeśli formant zmianę rozmiaru, wartość jego <xref:System.Windows.Forms.Control.Location%2A> właściwość zawsze pozostaje na stałym poziomie.|Gdy zawartość formantu powodują jej rozwoju, kontrolka rozszerza się w prawo i w dół. Kontrolki nie powiększyć po lewej stronie.|  
|<xref:System.Windows.Forms.Control.Dock%2A> i <xref:System.Windows.Forms.Control.Anchor%2A> właściwości są uwzględniane, gdy <xref:System.Windows.Forms.Control.AutoSize%2A> jest `true`.|Wartość formantu <xref:System.Windows.Forms.Control.Location%2A> właściwość jest dostosowywana do poprawnej wartości.<br /><br /> **Uwaga** <xref:System.Windows.Forms.Label> formant jest wyjątkiem od tej reguły. Po ustawieniu wartości zadokowany <xref:System.Windows.Forms.Label> kontrolki <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości `true`, <xref:System.Windows.Forms.Label> nie rozciąga formant.|  
|Kontrolki <xref:System.Windows.Forms.Control.MaximumSize%2A> i <xref:System.Windows.Forms.Control.MinimumSize%2A> właściwości są zawsze zachowywane, niezależnie od wartości jego <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości.|<xref:System.Windows.Forms.Control.MaximumSize%2A> i <xref:System.Windows.Forms.Control.MinimumSize%2A> właściwości nie ma wpływu <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości.|  
|Minimalny rozmiar domyślnie nie jest.|Oznacza to, że jeśli kontrolki jest ustawiona na zmniejszanie mocy <xref:System.Windows.Forms.Control.AutoSize%2A> i ma zawartość, nie wartość jego <xref:System.Windows.Forms.Control.Size%2A> właściwość jest 0,0. W tym przypadku formant będzie się zmniejszać do punktu, a nie będzie łatwo widoczna.|  
|Jeśli formant nie implementuje <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metody <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metoda zwraca ostatnią wartość przypisana do <xref:System.Windows.Forms.Control.Size%2A> właściwości.|Oznacza to, że ustawienie <xref:System.Windows.Forms.Control.AutoSize%2A> do `true` odniesie żadnego skutku.|  
|Kontrolki w <xref:System.Windows.Forms.TableLayoutPanel> komórki zawsze spadek, aby zmieścić ją w komórce aż do jego <xref:System.Windows.Forms.Control.MinimumSize%2A> zostanie osiągnięty.|Ten rozmiar jest wymuszana, jako maksymalny rozmiar. To nie jest to komórka jest częścią <xref:System.Windows.Forms.SizeType.AutoSize> wiersza lub kolumny.|  
  
## <a name="autosizemode-property"></a>AutoSizeMode właściwość  
 `AutoSizeMode` Właściwość zapewnia bardziej precyzyjną kontrolę nad domyślnie <xref:System.Windows.Forms.Control.AutoSize%2A> zachowanie. `AutoSizeMode` Właściwość określa, jak formant rozciąga się do jego zawartości. Zawartość, na przykład może być tekst <xref:System.Windows.Forms.Button> formantów podrzędnych dla kontenera.  
  
 W poniższej tabeli przedstawiono <xref:System.Windows.Forms.AutoSizeMode> ustawienia i opis zachowania elicits każdego ustawienia.  
  
|Ustawienie AutoSizeMode|Zachowanie|  
|--------------------------|--------------|  
|GrowAndShrink|Kontrolka powiększa się lub zmniejsza się jego zawartość.<br /><br /> <xref:System.Windows.Forms.Control.MinimumSize%2A> i <xref:System.Windows.Forms.Control.MaximumSize%2A> wartości są uznawane, ale bieżąca wartość <xref:System.Windows.Forms.Control.Size%2A> właściwość jest ignorowana.<br /><br /> To jest takie samo zachowanie, jak za pomocą <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości i nie `AutoSizeMode` właściwości.|  
|GrowOnly|Kontrolka rozszerza się w możliwie największym stopniu, wszystkie jego zawartość, ale nie będzie mniejszy niż wartość określoną przez zmniejszyć jego <xref:System.Windows.Forms.Control.Size%2A> właściwości.<br /><br /> Jest to wartość domyślna dla `AutoSizeMode`.|  
  
## <a name="controls-that-support-the-autosize-property"></a>Formanty, które obsługują właściwości AutoSize  
 Poniższa tabela zawiera listę formantów, które obsługują <xref:System.Windows.Forms.Control.AutoSize%2A> i `AutoSizeMode` właściwości.  
  
|Obsługa AutoSize|Typ formantu|  
|----------------------|------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> Właściwość jest obsługiwana.<br />-Nie `AutoSizeMode` właściwości.|<xref:System.Windows.Forms.CheckBox><br /><br /> <xref:System.Windows.Forms.DomainUpDown><br /><br /> <xref:System.Windows.Forms.Label><br /><br /> <xref:System.Windows.Forms.LinkLabel><br /><br /> <xref:System.Windows.Forms.MaskedTextBox> (<xref:System.Windows.Forms.TextBox> podstawowy)<br /><br /> <xref:System.Windows.Forms.NumericUpDown><br /><br /> <xref:System.Windows.Forms.RadioButton><br /><br /> <xref:System.Windows.Forms.TextBox><br /><br /> <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> Właściwość jest obsługiwana.<br />-   `AutoSizeMode` Właściwość jest obsługiwana.|<xref:System.Windows.Forms.Button><br /><br /> <xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.FlowLayoutPanel><br /><br /> <xref:System.Windows.Forms.Form><br /><br /> <xref:System.Windows.Forms.GroupBox><br /><br /> <xref:System.Windows.Forms.Panel><br /><br /> <xref:System.Windows.Forms.TableLayoutPanel>|  
|-Nie <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości.|<xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.ComboBox><br /><br /> <xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DateTimePicker><br /><br /> <xref:System.Windows.Forms.ListBox><br /><br /> <xref:System.Windows.Forms.ListView><br /><br /> <xref:System.Windows.Forms.MaskedTextBox><br /><br /> <xref:System.Windows.Forms.MonthCalendar><br /><br /> <xref:System.Windows.Forms.ProgressBar><br /><br /> <xref:System.Windows.Forms.PropertyGrid><br /><br /> <xref:System.Windows.Forms.RichTextBox><br /><br /> <xref:System.Windows.Forms.SplitContainer><br /><br /> <xref:System.Windows.Forms.TabControl><br /><br /> <xref:System.Windows.Forms.TabPage><br /><br /> <xref:System.Windows.Forms.TreeView><br /><br /> <xref:System.Windows.Forms.WebBrowser><br /><br /> <xref:System.Windows.Forms.ScrollBar>|  
  
## <a name="autosize-in-the-design-environment"></a>AutoSize w środowisku projektowania  
 W poniższej tabeli opisano zachowanie rozmiaru formantu w czasie projektowania na podstawie wartości jego <xref:System.Windows.Forms.Control.AutoSize%2A> i `AutoSizeMode` właściwości.  
  
 Zastąp <xref:System.Windows.Forms.Design.ControlDesigner.SelectionRules%2A> właściwości w celu określenia, czy określonej kontrolki jest w stanie o zmiennych rozmiarach dla użytkownika. W poniższej tabeli "nie" oznacza, że <xref:System.Windows.Forms.Design.SelectionRules.Moveable> tylko "mogą" oznacza, że <xref:System.Windows.Forms.Design.SelectionRules.AllSizeable> i <xref:System.Windows.Forms.Design.SelectionRules.Moveable>.  
  
|Ustawienia AutoSize|Gest zmiany rozmiaru w czasie projektowania|  
|-----------------------|---------------------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-Nie `AutoSizeMode` właściwości.|Użytkownik nie może zmienić rozmiar formantu w czasie projektowania, z wyjątkiem następujących formantów:<br /><br /> -   <xref:System.Windows.Forms.TextBox><br />-   <xref:System.Windows.Forms.MaskedTextBox><br />-   <xref:System.Windows.Forms.RichTextBox><br />-   <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>|Użytkownik nie może zmienić rozmiar formantu w czasie projektowania.|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>|Użytkownik może zmienić rozmiar formantu w czasie projektowania. Gdy <xref:System.Windows.Forms.Control.Size%2A> właściwość jest ustawiona, użytkownik może tylko zwiększyć rozmiar formantu.|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `false`, lub <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość jest ukryty.|Użytkownik może zmienić rozmiar formantu w czasie projektowania.|  
  
> [!NOTE]
>  Aby zmaksymalizować wydajność, cieniami Windows Forms Designer <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość <xref:System.Windows.Forms.Form> klasy. W czasie projektowania formularza zachowuje się tak, jakby <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość jest ustawiona na `false`, niezależnie od jej rzeczywistego ustawienia. W czasie wykonywania, dokonuje się nie specjalne zakwaterowanie i <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość jest stosowana jako określony przez ustawienie właściwości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.PreferredSize%2A>
- <xref:System.Windows.Forms.Control.GetPreferredSize%2A>
