---
title: Panel — Informacje o formancie (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: 1ba766629f923b091459531ce74d28dca4b4ea0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539352"
---
# <a name="panel-control-overview-windows-forms"></a>Panel — Informacje o formancie (Formularze systemu Windows)
Formularze systemu Windows <xref:System.Windows.Forms.Panel> formantów służą do zapewniania do zidentyfikowania grupowania dla innych formantów. Zwykle Użyj paneli do podziału formularza przez funkcję. Na przykład może być formularzu zamówienia określający wysyłkowy opcje, takie jak które liczbę operator do użycia. Grupowanie wszystkich opcji w panelu daje użytkownikowi logicznej wizualnie. Na projekt czasu wszystkie formanty, które mogą zostać przeniesione łatwo — po przeniesieniu <xref:System.Windows.Forms.Panel> sterowania wszystkie jego formanty zawarte Przenieś zbyt. Formanty są pogrupowane w panelu jest możliwy za pośrednictwem jego <xref:System.Windows.Forms.Control.Controls%2A> właściwości. Ta właściwość zwraca kolekcję <xref:System.Windows.Forms.Control> wystąpień, dzięki czemu zwykle trzeba rzutowania formantu pobrać ten sposób jego określonego typu.  
  
## <a name="panel-versus-groupbox"></a>Panel i GroupBox  
 <xref:System.Windows.Forms.Panel> Formant jest podobny do <xref:System.Windows.Forms.GroupBox> kontrolować; jednak tylko <xref:System.Windows.Forms.Panel> formant może mieć paski przewijania i tylko <xref:System.Windows.Forms.GroupBox> formant zawiera nagłówek.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Wyświetlanie pasków przewijania, należy ustawić <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> właściwości `true`. Można również dostosować wygląd panelu, ustawiając <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, i <xref:System.Windows.Forms.Panel.BorderStyle%2A> właściwości. Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.Control.BackColor%2A> i <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości, zobacz [porady: Ustawianie tła panelu](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md). <xref:System.Windows.Forms.Panel.BorderStyle%2A> Właściwość określa, czy panel jest opisane bez widoczna krawędzi (<xref:System.Windows.Forms.BorderStyle.None>), wiersz zwykły (<xref:System.Windows.Forms.BorderStyle.FixedSingle>), lub zasłonięty wiersza (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Panel>  
 [GroupBox, kontrolka](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)  
 [Instrukcje: grupowanie kontrolek za pomocą kontrolki Panel formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)  
 [Instrukcje: ustawianie tła panelu formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
