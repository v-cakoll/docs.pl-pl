---
title: "TableLayoutPanel — Formant (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms]
- controls [Windows Forms], sizing
- sizing [Windows Forms], automatic
- layout [Windows Forms], TableLayoutPanel control
- automatic sizing
ms.assetid: f55175c6-424e-4782-a86e-3f79c1550235
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6f8f949edcf637f4b56ab0bcfdd121c5cb29e543
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="tablelayoutpanel-control-windows-forms"></a><span data-ttu-id="92e01-102">TableLayoutPanel — Formant (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="92e01-102">TableLayoutPanel Control (Windows Forms)</span></span>
<span data-ttu-id="92e01-103"><xref:System.Windows.Forms.TableLayoutPanel> Kontroli rozmieszcza jego zawartość w siatce.</span><span class="sxs-lookup"><span data-stu-id="92e01-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="92e01-104">Ponieważ układ jest wykonywane zarówno w czasie projektowania i czas wykonywania, może zmieniać dynamicznie jako zmian środowiska aplikacji.</span><span class="sxs-lookup"><span data-stu-id="92e01-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="92e01-105">To umożliwia formantów w panelu proporcjonalnie zmiany rozmiaru, dlatego może odpowiadać na zmiany, takie jak zmiana rozmiaru kontrolki nadrzędnej lub tekst długość zmianę z powodu lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="92e01-105">This gives the controls in the panel the ability to proportionally resize, so it can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92e01-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="92e01-106">In This Section</span></span>  
 [<span data-ttu-id="92e01-107">Informacje o formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="92e01-107">TableLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)  
 <span data-ttu-id="92e01-108">Ogólne pojęcia związane z <xref:System.Windows.Forms.TableLayoutPanel> kontroli, co pozwala na tworzenie układu z wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="92e01-108">Introduces the general concepts of the <xref:System.Windows.Forms.TableLayoutPanel> control, which allows you to create a layout with rows and columns.</span></span>  
  
 [<span data-ttu-id="92e01-109">Najlepsze praktyki dotyczące formantu TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="92e01-109">Best Practices for the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="92e01-110">Przedstawiono zalecenia ułatwiające maksymalne wykorzystanie funkcji układu <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="92e01-110">Outlines recommendations to help you get the most out of the layout features of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="92e01-111">Zachowanie AutoSize w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="92e01-111">AutoSize Behavior in the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/autosize-behavior-in-the-tablelayoutpanel-control.md)  
 <span data-ttu-id="92e01-112">Wyjaśnia sposób, w którym <xref:System.Windows.Forms.TableLayoutPanel> sterowanie obsługuje zachowanie automatycznej zmiany rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="92e01-112">Explains the ways in which the <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior.</span></span>  
  
 [<span data-ttu-id="92e01-113">Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="92e01-113">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 <span data-ttu-id="92e01-114">Pokazuje, jak zakotwiczenie i dokowanie formantów podrzędnych w <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="92e01-114">Shows how to anchor and dock child controls in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [<span data-ttu-id="92e01-115">Porady: Projektowanie układu, który dobrze reagującego na formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="92e01-115">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 <span data-ttu-id="92e01-116">Pokazuje przy użyciu <xref:System.Windows.Forms.TableLayoutPanel> sterowania do formularza, który dobrze reagującego na kompilacji.</span><span class="sxs-lookup"><span data-stu-id="92e01-116">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to localization.</span></span>  
  
 [<span data-ttu-id="92e01-117">Porady: Tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych</span><span class="sxs-lookup"><span data-stu-id="92e01-117">How to: Create a Resizable Windows Form for Data Entry</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 <span data-ttu-id="92e01-118">Pokazuje przy użyciu <xref:System.Windows.Forms.TableLayoutPanel> formantu, aby utworzyć formularz, który odpowiada także zmiana rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="92e01-118">Demonstrates using a <xref:System.Windows.Forms.TableLayoutPanel> control to build a form that responds well to resizing.</span></span>  
  
1.  <span data-ttu-id="92e01-119">[Porady: wyrównywanie i rozciąganie formantu w formancie TableLayoutPanel](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="92e01-119">[How to: Align and Stretch a Control in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span></span>  
  
2.  <span data-ttu-id="92e01-120">[Porady: obejmowanie rzędów i kolumn w formancie TableLayoutPanel](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="92e01-120">[How to: Span Rows and Columns in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span></span>  
  
3.  <span data-ttu-id="92e01-121">[Porady: edytowanie rzędów i kolumn w formancie TableLayoutPanel](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="92e01-121">[How to: Edit Columns and Rows in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span></span>  
  
4.  <span data-ttu-id="92e01-122">[Wskazówki: Rozmieszczanie formantów na formularzach systemu Windows za pomocą TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="92e01-122">[Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span></span>  
  
## <a name="reference"></a><span data-ttu-id="92e01-123">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="92e01-123">Reference</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <span data-ttu-id="92e01-124">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="92e01-124">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 <span data-ttu-id="92e01-125">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.TableLayoutSettings> typu.</span><span class="sxs-lookup"><span data-stu-id="92e01-125">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutSettings> type.</span></span>  
  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <span data-ttu-id="92e01-126">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.FlowLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="92e01-126">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="92e01-127">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="92e01-127">Related Sections</span></span>  
 [<span data-ttu-id="92e01-128">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="92e01-128">Localization</span></span>](../../../../docs/standard/globalization-localization/localization.md)  
 <span data-ttu-id="92e01-129">Zawiera omówienie tematów dotyczących lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="92e01-129">Provides an overview of topics relating to localization.</span></span>  
  
 <span data-ttu-id="92e01-130">Zobacz też [lokalizowanie aplikacji](http://msdn.microsoft.com/library/z68135h5\(v=vs.110\)) lub [lokalizowanie aplikacji](http://msdn.microsoft.com/library/z68135h5\(v=vs.120\))</span><span class="sxs-lookup"><span data-stu-id="92e01-130">Also see [Localizing Applications](http://msdn.microsoft.com/library/z68135h5\(v=vs.110\)) or [Localizing Applications](http://msdn.microsoft.com/library/z68135h5\(v=vs.120\))</span></span>
