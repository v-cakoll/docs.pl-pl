---
title: Panel — Informacje o formancie (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: c346a9b77d49cde007310a2beb13bed3b1f30d71
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501774"
---
# <a name="panel-control-overview-windows-forms"></a>Panel — Informacje o formancie (Formularze systemu Windows)
Windows Forms <xref:System.Windows.Forms.Panel> formantów służą do zapewniania do zidentyfikowania grupowanie dla innych kontrolek. Zazwyczaj używasz paneli, pozwalające na dalszy podział formularza za pomocą funkcji. Na przykład masz formularza zamówienia, określający korespondencyjny opcje, takie jak które przelewy operatora do użycia. Grupowanie wszystkie opcje w panelu zapewnia logiczną oznak wizualnych aktywacji. Na projekt czas wszystkich kontrolek, które mogą zostać przeniesione łatwo — przy przenoszeniu <xref:System.Windows.Forms.Panel> kontrolować, wszystkie jego zawartych w nim formantów, Przenieś zbyt. Kontrolki zgrupowane w panelu jest możliwy za pośrednictwem jego <xref:System.Windows.Forms.Control.Controls%2A> właściwości. Ta właściwość zwraca kolekcję <xref:System.Windows.Forms.Control> wystąpienia, więc zazwyczaj konieczne będzie rzutowania kontrolki pobrać ten sposób dla określonego typu.  
  
## <a name="panel-versus-groupbox"></a>Panel, a pole grupy  
 <xref:System.Windows.Forms.Panel> Kontroli jest podobny do <xref:System.Windows.Forms.GroupBox> kontroli jednak tylko <xref:System.Windows.Forms.Panel> formant może mieć paski przewijania i tylko <xref:System.Windows.Forms.GroupBox> kontrolka Wyświetla podpis.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Wyświetlanie pasków przewijania, ustaw <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> właściwość `true`. Można również dostosować wygląd panelu, ustawiając <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, i <xref:System.Windows.Forms.Panel.BorderStyle%2A> właściwości. Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.Control.BackColor%2A> i <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości, zobacz [jak: Ustawianie tła panelu](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md). <xref:System.Windows.Forms.Panel.BorderStyle%2A> Właściwość określa, jeśli panel jest opisany bez widocznej krawędzi (<xref:System.Windows.Forms.BorderStyle.None>), wiersz zwykły (<xref:System.Windows.Forms.BorderStyle.FixedSingle>), lub zasłonięte wiersza (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.Panel>
- [GroupBox, kontrolka](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
- [Instrukcje: Grupowanie formantów z formantem panelu formularzy Windows przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
- [Instrukcje: Ustawianie tła panelu formularzy Windows przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
