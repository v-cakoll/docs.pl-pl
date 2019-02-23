---
title: TableLayoutPanel — Informacje o formancie
ms.date: 03/30/2017
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
ms.openlocfilehash: a0971fd02e27ea718af7fafe2404cd77d5946e25
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748690"
---
# <a name="tablelayoutpanel-control-overview"></a>TableLayoutPanel — Informacje o formancie
<xref:System.Windows.Forms.TableLayoutPanel> Kontroli rozmieszcza jego zawartość w siatce. Ponieważ układ jest wykonywane zarówno w czasie projektowania, a czas wykonywania, może zmienić dynamicznie jako zmiany środowiska aplikacji. Zapewnia kontrolki w panelu, możliwości, aby zmienić rozmiar proporcjonalnie, ich pozwalające reagować na zmiany, takie jak zmiana rozmiaru kontrolki nadrzędnej lub tekstu długości zmiana z powodu lokalizacji.  
  
 Wszystkie kontrolki Windows Forms może być elementem podrzędnym <xref:System.Windows.Forms.TableLayoutPanel> formantu, łącznie z innymi wystąpieniami <xref:System.Windows.Forms.TableLayoutPanel>. Dzięki temu można tworzyć złożone układy reagowanie na zmiany w czasie wykonywania.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Kontroli można rozwinąć w celu uwzględnienia nowych formantów, gdy zostaną dodane, w zależności od wartości <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, i <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> właściwości. Ustawienie albo <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> lub <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> właściwości na wartość 0 określa, że <xref:System.Windows.Forms.TableLayoutPanel> zostanie anulowane w odpowiedniej kierunku.  
  
 Możesz również kontrolować kierunek rozwoju (poziomą lub pionową) po <xref:System.Windows.Forms.TableLayoutPanel> kontroli jest pełny formantów podrzędnych. Domyślnie <xref:System.Windows.Forms.TableLayoutPanel> kontroli stawki rabatowe rozwija się przez dodawanie wierszy.  
  
 Jeśli chcesz, wierszy i kolumn, które działają inaczej niż domyślne zachowanie, można kontrolować właściwości wierszy i kolumn za pomocą <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> i <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> właściwości. Można ustawić właściwości wierszy lub kolumn indywidualnie.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Kontroli dodaje następujące właściwości do jego formantów podrzędnych: `Cell`, `Column`, `Row`, `ColumnSpan`, i `RowSpan`.  
  
 Można scalać komórek w <xref:System.Windows.Forms.TableLayoutPanel> kontroli przez ustawienie `ColumnSpan` lub `RowSpan` właściwości kontrolki podrzędnej.  
  
1.  [Instrukcje: Wyrównaj i rozciągnij kontrolki w kontrolce TableLayoutPanel](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [Instrukcje: Obejmowanie rzędów i kolumn w formancie TableLayoutPanel](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3.  [Instrukcje: Edytowanie rzędów i kolumn w formancie TableLayoutPanel](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4.  [Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutSettings>
- [Instrukcje: Projektowanie układu formularzy Windows dobrze reagującego na lokalizację](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [Instrukcje: Tworzenie formularza Windows o zmiennych rozmiarach dla wpisywania danych](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)
- [Najlepsze praktyki dotyczące kontrolki TableLayoutPanel](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
