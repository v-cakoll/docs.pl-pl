---
title: "Scalanie elementów menu w formancie MenuStrip formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cd54855f7ee618915fea4fcb8f465cc8c1a68164
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>Scalanie elementów menu w formancie MenuStrip formularzy systemu Windows
Jeśli masz aplikację interfejsu wielu dokumentów (MDI), w menu formularza nadrzędnego można scalać elementów menu lub menu całego formularza podrzędnego.  
  
 W tym temacie opisano podstawowe pojęcia związane z scalanie elementów menu w aplikacji MDI.  
  
## <a name="general-concepts"></a>Koncepcje ogólne  
 Scalania procedury dotyczą zarówno obiekt docelowy i kontroli źródła:  
  
-   Element docelowy jest <xref:System.Windows.Forms.MenuStrip> formantu głównego lub formularza nadrzędnego MDI, do którego są scalanie elementów menu.  
  
-   Źródło jest <xref:System.Windows.Forms.MenuStrip> formantu formularz podrzędny MDI, który zawiera elementy menu, które chcesz scalić menu docelowego.  
  
 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> Właściwość identyfikuje element menu, w których listy rozwijanej zostanie wypełnione tytuły bieżącego MDI nadrzędne elementy podrzędne MDI formularza. Na przykład, zwykle listę aktualnie otwartych na elementy podrzędne MDI **okna** menu.  
  
 <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A> Właściwość identyfikuje pochodzące z elementów menu <xref:System.Windows.Forms.MenuStrip> na formularz podrzędny MDI.  
  
 Elementy menu można scalać ręcznie lub automatycznie. Scalanie elementów menu w taki sam sposób dla obu metod, ale scalania jest aktywny w różny sposób, zgodnie z opisem w sekcji "Scalanie ręczne" i "Automatycznego scalania" w dalszej części tego tematu. Zarówno ręcznego i automatycznego scalania, każda akcja scalania może mieć wpływ następnej akcji scalania.  
  
 <xref:System.Windows.Forms.MenuStrip>scalanie elementów menu są przenoszone z jednego <xref:System.Windows.Forms.ToolStrip> do innego zamiast klonowania, jak w przypadku <xref:System.Windows.Forms.MainMenu>.  
  
## <a name="mergeaction-values"></a>Wartości MergeAction  
 Ustaw akcji scalania dla elementów menu w źródle <xref:System.Windows.Forms.MenuStrip> przy użyciu <xref:System.Windows.Forms.MergeAction> właściwości.  
  
 W poniższej tabeli opisano, co oznacza i typowych stosowania akcji dostępnych scalania.  
  
|Wartość MergeAction|Opis|Typowym zastosowaniem|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|(Ustawienie domyślne) Dodaje element źródłowy na końcu kolekcji elementów docelowych.|Dodawanie elementów menu na końcu menu, po aktywowaniu niektórych części programu.|  
|<xref:System.Windows.Forms.MergeAction.Insert>|Dodaje element źródłowy do kolekcji element docelowy, w lokalizacji określonej przez <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> ustawiona w elemencie źródła.|Dodawanie elementów menu do środka lub menu na początku, po aktywowaniu niektórych części programu.<br /><br /> Jeśli wartość <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> jest taka sama dla obu elementów menu są dodawane w odwrotnej kolejności. Ustaw <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> odpowiednio w celu zachowania kolejności.|  
|<xref:System.Windows.Forms.MergeAction.Replace>|Znalezienia dopasowania tekstu lub używa <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> wartość, gdy brak dopasowania tekst zostanie znaleziony, a następnie zastępuje element menu zgodnego docelowego źródła elementu menu.|Zastępując element menu docelowego elementu menu Źródło o takiej samej nazwie, który jest inny.|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|Znalezienia dopasowania tekstu lub używa <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> wartość, jeśli brak dopasowania tekstu zostanie znaleziony, a następnie dodaje wszystkie elementy z listy rozwijanej ze źródła do obiektu docelowego.|Tworzenie struktury menu, która wstawia dodaje elementy menu do podmenu lub usuwa elementów menu z podmenu. Na przykład można dodać elementu menu z podrzędnych MDI dla metody main <xref:System.Windows.Forms.MenuStrip> **Zapisz jako** menu.<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly>Umożliwia przeglądanie struktury menu bez podejmowania żadnych działań. Zapewnia sposób oceny kolejnych elementów.|  
|<xref:System.Windows.Forms.MergeAction.Remove>|Znalezienia dopasowania tekstu lub używa <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> wartość, gdy brak dopasowania tekst zostanie znaleziony, a następnie usuwa element z obiektu docelowego.|Usunięcie elementu menu z elementem docelowym <xref:System.Windows.Forms.MenuStrip>.|  
  
## <a name="manual-merging"></a>Scalanie ręczne  
 Tylko <xref:System.Windows.Forms.MenuStrip> formanty uczestniczyć w automatycznego scalania. Aby połączyć elementy inne formanty, takie jak <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.StatusStrip> formantów, użytkownik musi je ręczne scalenie, przez wywołanie metody <xref:System.Windows.Forms.ToolStripManager.Merge%2A> i <xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A> metody w kodzie zgodnie z potrzebami.  
  
## <a name="automatic-merging"></a>Automatyczne scalanie  
 Można użyć automatycznego scalania dla aplikacji MDI aktywując formularza źródła. Aby użyć <xref:System.Windows.Forms.MenuStrip> w aplikacji MDI ustawić <xref:System.Windows.Forms.Form.MainMenuStrip%2A> właściwości do obiektu docelowego <xref:System.Windows.Forms.MenuStrip> tak, aby scalanie akcje wykonywane w źródle <xref:System.Windows.Forms.MenuStrip> są uwzględniane w celu <xref:System.Windows.Forms.MenuStrip>.  
  
 Możesz wyzwolić automatycznego scalania aktywując <xref:System.Windows.Forms.MenuStrip> w źródle MDI. Po aktywacji, źródło <xref:System.Windows.Forms.MenuStrip> jest została scalona z elementem docelowym MDI. Podczas aktywowania nowego formularza scalania jest przywrócone na ostatni formularz i wyzwalane na nowy formularz. To zachowanie można kontrolować przez ustawienie <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> właściwości zgodnie z potrzebami każdego <xref:System.Windows.Forms.ToolStripItem>i ustawiając <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwości na każdym <xref:System.Windows.Forms.MenuStrip>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.MenuStrip>  
 [MenuStrip, kontrolka](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [Instrukcje: tworzenie list okien MDI za pomocą elementu MenuStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)  
 [Instrukcje: konfigurowanie automatycznego scalania menu dla aplikacji MDI](../../../../docs/framework/winforms/controls/how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
