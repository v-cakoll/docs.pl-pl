---
title: FlowLayoutPanel — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- FlowLayoutPanel
helpviewer_keywords:
- forms [Windows Forms], dynamic layout
- layout [Windows Forms], dynamic
- Windows Forms, dynamic layout
- FlowLayoutPanel control [Windows Forms], about FlowLayoutPanel control
ms.assetid: 3883e024-f5a0-456d-9c27-b4dfa1cc9045
ms.openlocfilehash: 58d95c2238687b4822155916177172a34c3abb87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526728"
---
# <a name="flowlayoutpanel-control-overview"></a>FlowLayoutPanel — Informacje o formancie
<xref:System.Windows.Forms.FlowLayoutPanel> Kontroli rozmieszcza jego zawartość w kierunku przepływu pozioma lub pionowa. Można zawijać zawartość formantu z jednego wiersza do następnego lub jedną kolumnę do następnego. Alternatywnie można przyciąć zamiast zawijania jego zawartość.  
  
 Określ kierunek przepływu, ustawiając wartość <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> właściwości. <xref:System.Windows.Forms.FlowLayoutPanel> Kontroli poprawnie cofa jego kierunek przepływu układów od prawej do lewej (od prawej do lewej). Można również określić, czy <xref:System.Windows.Forms.FlowLayoutPanel> zawartość formantu jest zawijany lub przycinana przez ustawienie wartości <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> właściwości.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Automatycznie kontrolować rozmiary, do jego zawartości po ustawieniu <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości `true`. Zapewnia także **FlowBreak** właściwości formantów podrzędnych. Ustawienie wartości dla właściwości FlowBreak `true` powoduje, że <xref:System.Windows.Forms.FlowLayoutPanel> formant przestanie układania formantów w bieżącym kierunek przepływu i zawijania do następnego wiersza lub kolumny.  
  
 Wszystkie kontrolki formularza systemu Windows może być elementem podrzędnym elementu <xref:System.Windows.Forms.FlowLayoutPanel> formantu, łącznie z innymi wystąpieniami <xref:System.Windows.Forms.FlowLayoutPanel>. Dzięki tej możliwości można utworzyć układy zaawansowane dostosowania formularza wymiarów w czasie wykonywania.  
  
 Zobacz też [wskazówki: rozmieszczanie formantów w Windows Forms za pomocą FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [FlowLayoutPanel, kontrolka](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-windows-forms.md)
