---
title: "TableLayoutPanel — Informacje o formancie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TableLayoutPanel
helpviewer_keywords:
- controls [Windows Forms], resizing
- resizable controls [Windows Forms]
- Windows Forms controls, proportional resizing
- Windows Forms, proportional resizing of controls
- layout [Windows Forms], TableLayoutPanel control
- TableLayoutPanel control [Windows Forms], about TableLayoutPanel control
ms.assetid: 337661c8-61cb-44ee-93e0-3662bddec327
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 614887524a49e1163b3049111895166995fdace4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="tablelayoutpanel-control-overview"></a>TableLayoutPanel — Informacje o formancie
<xref:System.Windows.Forms.TableLayoutPanel> Kontroli rozmieszcza jego zawartość w siatce. Ponieważ układ jest wykonywane zarówno w czasie projektowania i czas wykonywania, może zmieniać dynamicznie jako zmian środowiska aplikacji. To umożliwia formantów w panelu proporcjonalnie zmiany rozmiaru, dlatego mogą one odpowiadać na zmiany, takie jak zmiana rozmiaru kontrolki nadrzędnej lub tekst długość zmianę z powodu lokalizacji.  
  
 Wszystkie kontrolki formularza systemu Windows może być elementem podrzędnym elementu <xref:System.Windows.Forms.TableLayoutPanel> formantu, łącznie z innymi wystąpieniami <xref:System.Windows.Forms.TableLayoutPanel>. Dzięki temu można tworzyć zaawansowane układy dostosować do zmian w czasie wykonywania.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Formantu można rozwinąć w celu uwzględnienia nowych formantów, gdy zostaną dodane, w zależności od wartości <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, i <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> właściwości. Ustawienie albo <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> lub <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> właściwości na wartość 0 oznacza, że <xref:System.Windows.Forms.TableLayoutPanel> zostanie anulowane w odpowiednich kierunku.  
  
 Można również sterować kierunek rozwoju (poziomą lub pionową) po <xref:System.Windows.Forms.TableLayoutPanel> formant jest pełna formantów podrzędnych. Domyślnie <xref:System.Windows.Forms.TableLayoutPanel> kontroli dół rozszerza przez dodanie wierszy.  
  
 Jeśli chcesz wierszy i kolumn, które działają inaczej niż domyślne zachowanie właściwości wierszy i kolumn można kontrolować przy użyciu <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> i <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> właściwości. Można ustawić właściwości wierszy lub kolumn pojedynczo.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Kontroli dodaje następujące właściwości do jej kontrolkach podrzędnych: `Cell`, `Column`, `Row`, `ColumnSpan`, i `RowSpan`.  
  
 Można scalać komórek w <xref:System.Windows.Forms.TableLayoutPanel> kontroli przez ustawienie `ColumnSpan` lub `RowSpan` właściwości kontrolki podrzędnej.  
  
1.  [Instrukcje: wyrównywanie i rozciąganie kontrolki w kontrolce TableLayoutPanel](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))  
  
2.  [Instrukcje: obejmowanie rzędów i kolumn w kontrolce TableLayoutPanel](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))  
  
3.  [Instrukcje: edytowanie rzędów i kolumn w kontrolce TableLayoutPanel](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))  
  
4.  [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 [Instrukcje: projektowanie układu formularzy Windows Forms dobrze reagującego na lokalizację](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Instrukcje: tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 [Najlepsze praktyki dotyczące kontrolki TableLayoutPanel](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
