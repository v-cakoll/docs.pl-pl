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
ms.openlocfilehash: 260146cd901fe2b80a73c01060ccd55958cd169e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011323"
---
# <a name="flowlayoutpanel-control-overview"></a>FlowLayoutPanel — Informacje o formancie
<xref:System.Windows.Forms.FlowLayoutPanel> Kontroli rozmieszcza jego zawartość w kierunku przepływu poziomej lub pionowej. Może zawijać się zawartość formantu z jeden wiersz do następnego lub z jednej kolumny do następnego. Alternatywnie można przyciąć zamiast zawijania jego zawartość.  
  
 Można określić kierunek przepływu, ustawiając wartość <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> właściwości. <xref:System.Windows.Forms.FlowLayoutPanel> Kontroli poprawnie odwraca kierunku przepływu w układy od prawej do lewej (RTL). Można również określić, czy <xref:System.Windows.Forms.FlowLayoutPanel> zawartość kontrolki jest opakowana lub przycięty, ustawiając wartość <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> właściwości.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Automatycznie kontrolowania rozmiarów do jego zawartości, po ustawieniu <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość `true`. Zapewnia także **FlowBreak** właściwości do jego formantów podrzędnych. Ustawienie wartości właściwości FlowBreak `true` powoduje, że <xref:System.Windows.Forms.FlowLayoutPanel> formantu, aby zatrzymać układu kontrolek w bieżącym kierunek przepływu i zawijania do następnego wiersza lub kolumny.  
  
 Wszystkie kontrolki Windows Forms może być elementem podrzędnym <xref:System.Windows.Forms.FlowLayoutPanel> formantu, łącznie z innymi wystąpieniami <xref:System.Windows.Forms.FlowLayoutPanel>. Dzięki tej możliwości można skonstruować układy zaawansowane dostosowania do formularza wymiarów w czasie wykonywania.  
  
 Zobacz też [instruktażu: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [FlowLayoutPanel, kontrolka](flowlayoutpanel-control-windows-forms.md)
