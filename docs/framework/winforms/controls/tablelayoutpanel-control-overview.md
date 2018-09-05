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
ms.openlocfilehash: be7ef4055d809349fe97a3d48e29158c5449576b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562145"
---
# <a name="tablelayoutpanel-control-overview"></a>TableLayoutPanel — Informacje o formancie
<xref:System.Windows.Forms.TableLayoutPanel> Kontroli rozmieszcza jego zawartość w siatce. Ponieważ układ jest wykonywane zarówno w czasie projektowania, a czas wykonywania, może zmienić dynamicznie jako zmiany środowiska aplikacji. Zapewnia kontrolki w panelu, możliwości, aby zmienić rozmiar proporcjonalnie, ich pozwalające reagować na zmiany, takie jak zmiana rozmiaru kontrolki nadrzędnej lub tekstu długości zmiana z powodu lokalizacji.  
  
 Wszystkie kontrolki Windows Forms może być elementem podrzędnym <xref:System.Windows.Forms.TableLayoutPanel> formantu, łącznie z innymi wystąpieniami <xref:System.Windows.Forms.TableLayoutPanel>. Dzięki temu można tworzyć złożone układy reagowanie na zmiany w czasie wykonywania.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Kontroli można rozwinąć w celu uwzględnienia nowych formantów, gdy zostaną dodane, w zależności od wartości <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, i <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> właściwości. Ustawienie albo <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> lub <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> właściwości na wartość 0 określa, że <xref:System.Windows.Forms.TableLayoutPanel> zostanie anulowane w odpowiedniej kierunku.  
  
 Możesz również kontrolować kierunek rozwoju (poziomą lub pionową) po <xref:System.Windows.Forms.TableLayoutPanel> kontroli jest pełny formantów podrzędnych. Domyślnie <xref:System.Windows.Forms.TableLayoutPanel> kontroli stawki rabatowe rozwija się przez dodawanie wierszy.  
  
 Jeśli chcesz, wierszy i kolumn, które działają inaczej niż domyślne zachowanie, można kontrolować właściwości wierszy i kolumn za pomocą <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> i <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> właściwości. Można ustawić właściwości wierszy lub kolumn indywidualnie.  
  
 <xref:System.Windows.Forms.TableLayoutPanel> Kontroli dodaje następujące właściwości do jego formantów podrzędnych: `Cell`, `Column`, `Row`, `ColumnSpan`, i `RowSpan`.  
  
 Można scalać komórek w <xref:System.Windows.Forms.TableLayoutPanel> kontroli przez ustawienie `ColumnSpan` lub `RowSpan` właściwości kontrolki podrzędnej.  
  
1.  [Instrukcje: wyrównywanie i rozciąganie kontrolki w kontrolce TableLayoutPanel](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [Instrukcje: obejmowanie rzędów i kolumn w kontrolce TableLayoutPanel](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3.  [Instrukcje: edytowanie rzędów i kolumn w kontrolce TableLayoutPanel](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4.  [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 [Instrukcje: projektowanie układu formularzy Windows Forms dobrze reagującego na lokalizację](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Instrukcje: tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 [Najlepsze praktyki dotyczące kontrolki TableLayoutPanel](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
