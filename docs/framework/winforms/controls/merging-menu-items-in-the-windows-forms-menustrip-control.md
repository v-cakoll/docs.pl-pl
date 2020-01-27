---
title: Scalanie elementów menu w formancie MenuStrip
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
ms.openlocfilehash: 9fc2b40ef23d72db51853c124095b734a7646cda
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739042"
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>Scalanie elementów menu w formancie MenuStrip formularzy systemu Windows
Jeśli masz aplikację interfejsu wielu dokumentów (MDI), możesz scalić elementy menu lub całe menu z formularza podrzędnego do menu formularza nadrzędnego.  
  
 W tym temacie opisano podstawowe koncepcje związane z scalaniem elementów menu w aplikacji MDI.  
  
## <a name="general-concepts"></a>Pojęcia ogólne  
 Scalanie procedur dotyczy zarówno elementu docelowego, jak i kontroli źródła:  
  
- Obiektem docelowym jest formant <xref:System.Windows.Forms.MenuStrip> w głównym lub MDI formularzu nadrzędnym, do którego są scalane elementy menu.  
  
- Źródłem jest formant <xref:System.Windows.Forms.MenuStrip> w formularzu podrzędnym MDI zawierający elementy menu, które mają zostać scalone w menu cel.  
  
 Właściwość <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> identyfikuje element menu, którego lista rozwijana zostanie wypełniona z tytułami elementów podrzędnych MDI formularza nadrzędnego MDI. Na przykład zazwyczaj wyświetla się listę elementów podrzędnych MDI, które są aktualnie otwarte w menu **okno** .  
  
 Właściwość <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A> określa, które elementy menu pochodzą z <xref:System.Windows.Forms.MenuStrip> w formularzu podrzędnym MDI.  
  
 Elementy menu można scalać ręcznie lub automatycznie. Elementy menu są scalane w taki sam sposób w obu metodach, ale scalanie jest aktywowane inaczej, jak to opisano w sekcjach "scalanie ręczne" i "automatyczne scalanie" w dalszej części tego tematu. W przypadku ręcznego i automatycznego scalania każda akcja scalania ma wpływ na następną akcję scalania.  
  
 <xref:System.Windows.Forms.MenuStrip> scalanie przenosi elementy menu z jednego <xref:System.Windows.Forms.ToolStrip> do innego zamiast klonowania, tak jak w przypadku <xref:System.Windows.Forms.MainMenu>.  
  
## <a name="mergeaction-values"></a>MergeAction wartości  
 Akcję scalania ustawia się w elementach menu w <xref:System.Windows.Forms.MenuStrip> źródłowym przy użyciu właściwości <xref:System.Windows.Forms.MergeAction>.  
  
 W poniższej tabeli opisano znaczenie i typowe użycie dostępnych akcji scalania.  
  
|MergeAction wartość|Opis|Typowym zastosowaniem|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|Wartooć Dodaje element źródłowy na końcu kolekcji elementów docelowych.|Dodawanie elementów menu na końcu menu po aktywowaniu pewnej części programu.|  
|<xref:System.Windows.Forms.MergeAction.Insert>|Dodaje element źródłowy do kolekcji elementów docelowych w lokalizacji określonej przez właściwość <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> ustawioną dla elementu źródłowego.|Dodawanie elementów menu do środka lub początek menu po aktywowaniu pewnej części programu.<br /><br /> Jeśli wartość <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> jest taka sama dla obu elementów menu, są one dodawane w odwrotnej kolejności. Ustaw odpowiednio <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>, aby zachować oryginalną kolejność.|  
|<xref:System.Windows.Forms.MergeAction.Replace>|Znajduje dopasowanie tekstu lub używa wartości <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>, jeśli nie zostanie znalezione dopasowanie tekstu, a następnie zastąpi pasujący element menu docelowego z elementem menu Źródło.|Zamienianie elementu menu docelowego na element menu źródła o tej samej nazwie, która coś się różni.|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|Znajduje dopasowanie tekstu lub używa wartości <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>, jeśli nie odnaleziono dopasowania tekstu, a następnie doda wszystkie elementy listy rozwijanej ze źródła do obiektu docelowego.|Tworzenie struktury menu, która wstawia lub dodaje elementy menu do podmenu, lub usuwa elementy menu z podmenu. Na przykład można dodać element menu z elementu podrzędnego MDI do głównego menu <xref:System.Windows.Forms.MenuStrip>**Zapisz jako** .<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly> umożliwia nawigowanie po strukturze menu bez podejmowania żadnych działań. Umożliwia ona ocenę kolejnych elementów.|  
|<xref:System.Windows.Forms.MergeAction.Remove>|Znajduje dopasowanie tekstu lub używa wartości <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>, jeśli nie odnaleziono dopasowania tekstu, a następnie usuwa element z obiektu docelowego.|Usuwanie elementu menu z <xref:System.Windows.Forms.MenuStrip>docelowej.|  
  
## <a name="manual-merging"></a>Scalanie ręczne  
 Tylko kontrolki <xref:System.Windows.Forms.MenuStrip> uczestniczą w scalaniu automatycznym. Aby połączyć elementy innych kontrolek, takich jak <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.StatusStrip>, należy scalić je ręcznie, wywołując metody <xref:System.Windows.Forms.ToolStripManager.Merge%2A> i <xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A> w kodzie zgodnie z wymaganiami.  
  
## <a name="automatic-merging"></a>Automatyczne scalanie  
 Możesz użyć automatycznego scalania aplikacji MDI, aktywując formularz źródłowy. Aby użyć <xref:System.Windows.Forms.MenuStrip> w aplikacji MDI, należy ustawić właściwość <xref:System.Windows.Forms.Form.MainMenuStrip%2A> na docelowy <xref:System.Windows.Forms.MenuStrip> tak, aby akcje scalania wykonywane na <xref:System.Windows.Forms.MenuStrip> źródłowym były odzwierciedlone w <xref:System.Windows.Forms.MenuStrip>docelowym.  
  
 Automatyczne scalanie można wyzwolić, aktywując <xref:System.Windows.Forms.MenuStrip> w źródle MDI. Po aktywacji <xref:System.Windows.Forms.MenuStrip> źródłowa zostanie scalona z elementem docelowym MDI. Gdy nowy formularz zostanie uaktywniony, scalanie zostanie przywrócone w ostatnim formularzu i wyzwolone na nowym formularzu. Możesz kontrolować to zachowanie, ustawiając właściwość <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> zgodnie z wymaganiami dla każdej <xref:System.Windows.Forms.ToolStripItem>i ustawiając właściwość <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> na każdym <xref:System.Windows.Forms.MenuStrip>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- [MenuStrip, kontrolka](menustrip-control-windows-forms.md)
- [Instrukcje: tworzenie list okien MDI za pomocą elementu MenuStrip](how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)
- [Instrukcje: konfigurowanie automatycznego scalania menu dla aplikacji MDI](how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
