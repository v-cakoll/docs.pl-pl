---
title: Scalanie elementów menu w formancie MenuStrip formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
ms.openlocfilehash: 96168c197771cbfebf3a090ac236b21e487cb3a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551855"
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>Scalanie elementów menu w formancie MenuStrip formularzy systemu Windows
W przypadku aplikacji interfejsu wielu dokumentów (MDI) w menu formularz nadrzędny można scalać elementy menu lub menu całego formularza podrzędnego.  
  
 W tym temacie opisano podstawowe pojęcia związane z scalanie elementów menu w aplikacji MDI.  
  
## <a name="general-concepts"></a>Pojęcia ogólne  
 Scalanie procedury dotyczą zarówno do obiektu docelowego, jak i do kontroli źródła:  
  
-   Element docelowy jest <xref:System.Windows.Forms.MenuStrip> formantu main lub formularza nadrzędnego MDI, do którego są scalanie elementów menu.  
  
-   Obiekt źródłowy ma <xref:System.Windows.Forms.MenuStrip> formantu na formularz podrzędny MDI, która zawiera elementy menu, które chcesz scalić w menu Cel.  
  
 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> Właściwość identyfikuje element menu, w których listy rozwijanej zostanie wypełniona tytuły bieżącego MDI nadrzędne elementy podrzędne MDI formularza. Na przykład zazwyczaj liście elementów podrzędnych MDI, które są aktualnie otwarte na **okna** menu.  
  
 <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A> Właściwość identyfikuje, które pochodzą elementów menu <xref:System.Windows.Forms.MenuStrip> na formularz podrzędny MDI.  
  
 Można scalać elementy menu, ręcznie lub automatycznie. Scalanie elementów menu, tak samo jak w przypadku obu metod, ale scalania została aktywowana w różny sposób, zgodnie z opisem w sekcji "Ręczna scalania" i "Automatycznego scalenia" w dalszej części tego tematu. Ręczne i automatyczne scalanie, każda akcja scalania może mieć wpływ następnej akcji scalania.  
  
 <xref:System.Windows.Forms.MenuStrip> scalanie elementów menu są przenoszone z jednej <xref:System.Windows.Forms.ToolStrip> do innego zamiast klonowania, jak w przypadku <xref:System.Windows.Forms.MainMenu>.  
  
## <a name="mergeaction-values"></a>Wartości MergeAction  
 Ustaw akcję scalanie elementów menu w źródle <xref:System.Windows.Forms.MenuStrip> przy użyciu <xref:System.Windows.Forms.MergeAction> właściwości.  
  
 W poniższej tabeli opisano, co oznacza i typowego użycia Akcje dostępne scalania.  
  
|Wartość MergeAction|Opis|Typowym zastosowaniem|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|(Ustawienie domyślne) Dodaje element źródłowy w celu pobrania elementu docelowego.|Dodawanie elementów menu w celu menu, po aktywowaniu niektórych części programu.|  
|<xref:System.Windows.Forms.MergeAction.Insert>|Element źródłowy są dodawane do kolekcji element docelowy w lokalizacji określonej przez <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> właściwość ustawioną na elementu źródłowego.|Dodawanie elementów menu do środka lub na początku menu, po aktywowaniu niektórych części programu.<br /><br /> Jeśli wartość <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> jest taka sama dla obu elementów menu, zostaną one dodane w odwrotnej kolejności. Ustaw <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> odpowiednio zachować pierwotną kolejność.|  
|<xref:System.Windows.Forms.MergeAction.Replace>|Wyszukuje dopasowania tekstu. natomiast przy użyciu <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> wartość, jeśli brak dopasowania tekstu zostanie znaleziony, a następnie zastępuje pasujący element docelowy w menu z elementem menu źródła.|Zastępowanie docelowego elementu menu z elementem menu Źródło o takiej samej nazwie, która wykonuje coś innego.|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|Wyszukuje dopasowania tekstu. natomiast przy użyciu <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> wartość, jeśli dopasowanie tekst nie zostanie znaleziony, a następnie dodaje wszystkie elementy z listy rozwijanej ze źródła do docelowego.|Tworzenie struktury menu, który wstawia dodaje elementy menu w podmenu lub usuwa elementy menu z podmenu. Na przykład można dodać element menu z podrzędnym MDI dla metody main <xref:System.Windows.Forms.MenuStrip> **Zapisz jako** menu.<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly> umożliwia nawigowanie po struktury menu bez podejmowania żadnych działań. Zapewnia sposób, aby ocenić kolejne elementy.|  
|<xref:System.Windows.Forms.MergeAction.Remove>|Wyszukuje dopasowania tekstu. natomiast przy użyciu <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> wartość, jeśli brak dopasowania tekstu zostanie znaleziony, a następnie usuwa element z obiektu docelowego.|Usunięcie elementu menu, element docelowy odpowiedziałby <xref:System.Windows.Forms.MenuStrip>.|  
  
## <a name="manual-merging"></a>Ręczne scalanie  
 Tylko <xref:System.Windows.Forms.MenuStrip> kontrolek należą automatycznego scalenia. Aby połączyć elementy inne formanty, takie jak <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.StatusStrip> formantów, musisz scalić je ręcznie, wywołując <xref:System.Windows.Forms.ToolStripManager.Merge%2A> i <xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A> metody w kodzie, zgodnie z potrzebami.  
  
## <a name="automatic-merging"></a>Automatyczne scalanie  
 Można użyć automatycznego scalania dla aplikacji MDI, aktywując formy źródłowej. Aby użyć <xref:System.Windows.Forms.MenuStrip> w aplikacji MDI, ustaw <xref:System.Windows.Forms.Form.MainMenuStrip%2A> właściwości do obiektu docelowego <xref:System.Windows.Forms.MenuStrip> tak, aby scalanie akcje wykonywane w źródle <xref:System.Windows.Forms.MenuStrip> są odzwierciedlane w celu <xref:System.Windows.Forms.MenuStrip>.  
  
 Możesz wyzwolić automatyczne scalanie, aktywując <xref:System.Windows.Forms.MenuStrip> w źródle MDI. Po aktywacji, źródło <xref:System.Windows.Forms.MenuStrip> zostanie scalona z docelowym MDI. Gdy nowy formularz stanie się aktywny, scalania jest przywrócony na formularzu ostatniego i wyzwalane na formularzu nowy. To zachowanie można kontrolować przez ustawienie <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> właściwości zgodnie z potrzebami każdego <xref:System.Windows.Forms.ToolStripItem>i ustawiając <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> właściwości na każdym <xref:System.Windows.Forms.MenuStrip>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- [MenuStrip, kontrolka](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
- [Instrukcje: Tworzenie List okien MDI za pomocą elementu MenuStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)
- [Instrukcje: Konfigurowanie automatycznego scalania Menu dla aplikacji MDI](../../../../docs/framework/winforms/controls/how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
