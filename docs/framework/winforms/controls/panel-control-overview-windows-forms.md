---
title: Panel, kontrolka — omówienie
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: 3ea86e898e8a3e1ca90ba8e0a6240414702a1a73
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744308"
---
# <a name="panel-control-overview-windows-forms"></a>Panel — Informacje o formancie (Formularze systemu Windows)
Kontrolki <xref:System.Windows.Forms.Panel> Windows Forms są używane do zapewniania możliwej do zidentyfikowania grupowania dla innych formantów. Zazwyczaj można używać paneli do podzielenia formularza przez funkcję. Na przykład możesz mieć formularz zamówienia, który określa opcje wysyłania, takie jak używany przez przewoźnik nocny. Grupowanie wszystkich opcji w panelu daje użytkownikowi logiczną wizualną wizualizację. W czasie projektowania wszystkie kontrolki mogą być łatwo przenoszone — po przeniesieniu kontrolki <xref:System.Windows.Forms.Panel> wszystkie zawarte w niej kontrolki są również przenoszone. Do kontrolek zgrupowanych w panelu można uzyskać dostęp za pomocą właściwości <xref:System.Windows.Forms.Control.Controls%2A>. Ta właściwość zwraca kolekcję wystąpień <xref:System.Windows.Forms.Control>, więc zazwyczaj trzeba rzutować kontrolkę pobraną w ten sposób do określonego typu.  
  
## <a name="panel-versus-groupbox"></a>Panel a pole grupy  
 Kontrolka <xref:System.Windows.Forms.Panel> jest podobna do kontrolki <xref:System.Windows.Forms.GroupBox>; jednak tylko formant <xref:System.Windows.Forms.Panel> może mieć paski przewijania i tylko formant <xref:System.Windows.Forms.GroupBox> wyświetla podpis.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Aby wyświetlić paski przewijania, ustaw właściwość <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> na `true`. Możesz również dostosować wygląd panelu przez ustawienie właściwości <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>i <xref:System.Windows.Forms.Panel.BorderStyle%2A>. Aby uzyskać więcej informacji na temat właściwości <xref:System.Windows.Forms.Control.BackColor%2A> i <xref:System.Windows.Forms.Control.BackgroundImage%2A>, zobacz [jak to zrobić: Ustawianie tła panelu](how-to-set-the-background-of-a-windows-forms-panel.md). Właściwość <xref:System.Windows.Forms.Panel.BorderStyle%2A> określa, czy panel jest podkreślony bez widocznego obramowania (<xref:System.Windows.Forms.BorderStyle.None>), zwykłego wiersza (<xref:System.Windows.Forms.BorderStyle.FixedSingle>) ani linii zacieniowanej (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Panel>
- [GroupBox, kontrolka](groupbox-control-windows-forms.md)
- [Instrukcje: grupowanie kontrolek za pomocą kontrolki Panel formularzy Windows Forms przy użyciu narzędzia Projektant](group-controls-with-wf-panel-control-using-the-designer.md)
- [Instrukcje: ustawianie tła panelu formularzy Windows Forms przy użyciu narzędzia Projektant](how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
