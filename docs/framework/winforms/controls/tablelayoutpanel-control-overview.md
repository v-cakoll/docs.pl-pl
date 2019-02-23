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
# <a name="tablelayoutpanel-control-overview"></a><span data-ttu-id="6f3a4-102">TableLayoutPanel — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="6f3a4-102">TableLayoutPanel Control Overview</span></span>
<span data-ttu-id="6f3a4-103"><xref:System.Windows.Forms.TableLayoutPanel> Kontroli rozmieszcza jego zawartość w siatce.</span><span class="sxs-lookup"><span data-stu-id="6f3a4-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="6f3a4-104">Ponieważ układ jest wykonywane zarówno w czasie projektowania, a czas wykonywania, może zmienić dynamicznie jako zmiany środowiska aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f3a4-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="6f3a4-105">Zapewnia kontrolki w panelu, możliwości, aby zmienić rozmiar proporcjonalnie, ich pozwalające reagować na zmiany, takie jak zmiana rozmiaru kontrolki nadrzędnej lub tekstu długości zmiana z powodu lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="6f3a4-105">This gives the controls in the panel the ability to proportionally resize, so they can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
 <span data-ttu-id="6f3a4-106">Wszystkie kontrolki Windows Forms może być elementem podrzędnym <xref:System.Windows.Forms.TableLayoutPanel> formantu, łącznie z innymi wystąpieniami <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="6f3a4-106">Any Windows Forms control can be a child of the <xref:System.Windows.Forms.TableLayoutPanel> control, including other instances of <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="6f3a4-107">Dzięki temu można tworzyć złożone układy reagowanie na zmiany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6f3a4-107">This allows you to construct sophisticated layouts that adapt to changes at run time.</span></span>  
  
 <span data-ttu-id="6f3a4-108"><xref:System.Windows.Forms.TableLayoutPanel> Kontroli można rozwinąć w celu uwzględnienia nowych formantów, gdy zostaną dodane, w zależności od wartości <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, i <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6f3a4-108">The <xref:System.Windows.Forms.TableLayoutPanel> control can expand to accommodate new controls when they are added, depending on the value of the <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, and <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> properties.</span></span> <span data-ttu-id="6f3a4-109">Ustawienie albo <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> lub <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> właściwości na wartość 0 określa, że <xref:System.Windows.Forms.TableLayoutPanel> zostanie anulowane w odpowiedniej kierunku.</span><span class="sxs-lookup"><span data-stu-id="6f3a4-109">Setting either the <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> or <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> property to a value of 0 specifies that the <xref:System.Windows.Forms.TableLayoutPanel> will be unbound in the corresponding direction.</span></span>  
  
 <span data-ttu-id="6f3a4-110">Możesz również kontrolować kierunek rozwoju (poziomą lub pionową) po <xref:System.Windows.Forms.TableLayoutPanel> kontroli jest pełny formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="6f3a4-110">You can also control the direction of expansion (horizontal or vertical) after the <xref:System.Windows.Forms.TableLayoutPanel> control is full of child controls.</span></span> <span data-ttu-id="6f3a4-111">Domyślnie <xref:System.Windows.Forms.TableLayoutPanel> kontroli stawki rabatowe rozwija się przez dodawanie wierszy.</span><span class="sxs-lookup"><span data-stu-id="6f3a4-111">By default, the <xref:System.Windows.Forms.TableLayoutPanel> control expands downward by adding rows.</span></span>  
  
 <span data-ttu-id="6f3a4-112">Jeśli chcesz, wierszy i kolumn, które działają inaczej niż domyślne zachowanie, można kontrolować właściwości wierszy i kolumn za pomocą <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> i <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6f3a4-112">If you want rows and columns that behave differently from the default behavior, you can control the properties of rows and columns by using the <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> and <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> properties.</span></span> <span data-ttu-id="6f3a4-113">Można ustawić właściwości wierszy lub kolumn indywidualnie.</span><span class="sxs-lookup"><span data-stu-id="6f3a4-113">You can set the properties of rows or columns individually.</span></span>  
  
 <span data-ttu-id="6f3a4-114"><xref:System.Windows.Forms.TableLayoutPanel> Kontroli dodaje następujące właściwości do jego formantów podrzędnych: `Cell`, `Column`, `Row`, `ColumnSpan`, i `RowSpan`.</span><span class="sxs-lookup"><span data-stu-id="6f3a4-114">The <xref:System.Windows.Forms.TableLayoutPanel> control adds the following properties to its child controls: `Cell`, `Column`, `Row`, `ColumnSpan`, and `RowSpan`.</span></span>  
  
 <span data-ttu-id="6f3a4-115">Można scalać komórek w <xref:System.Windows.Forms.TableLayoutPanel> kontroli przez ustawienie `ColumnSpan` lub `RowSpan` właściwości kontrolki podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="6f3a4-115">You can merge cells in the <xref:System.Windows.Forms.TableLayoutPanel> control by setting the `ColumnSpan` or `RowSpan` properties on a child control.</span></span>  
  
1.  [<span data-ttu-id="6f3a4-116">Instrukcje: Wyrównaj i rozciągnij kontrolki w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6f3a4-116">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [<span data-ttu-id="6f3a4-117">Instrukcje: Obejmowanie rzędów i kolumn w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6f3a4-117">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3.  [<span data-ttu-id="6f3a4-118">Instrukcje: Edytowanie rzędów i kolumn w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6f3a4-118">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4.  [<span data-ttu-id="6f3a4-119">Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6f3a4-119">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
  
## <a name="see-also"></a><span data-ttu-id="6f3a4-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f3a4-120">See also</span></span>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutSettings>
- [<span data-ttu-id="6f3a4-121">Instrukcje: Projektowanie układu formularzy Windows dobrze reagującego na lokalizację</span><span class="sxs-lookup"><span data-stu-id="6f3a4-121">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [<span data-ttu-id="6f3a4-122">Instrukcje: Tworzenie formularza Windows o zmiennych rozmiarach dla wpisywania danych</span><span class="sxs-lookup"><span data-stu-id="6f3a4-122">How to: Create a Resizable Windows Form for Data Entry</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)
- [<span data-ttu-id="6f3a4-123">Najlepsze praktyki dotyczące kontrolki TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6f3a4-123">Best Practices for the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
