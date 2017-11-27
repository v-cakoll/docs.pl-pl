---
title: "Porady: projektowanie układu formularzy systemu Windows dobrze reagującego na lokalizację"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3584b1a5751257c558d5e000135478966605f9c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="6efc7-102">Porady: projektowanie układu formularzy systemu Windows dobrze reagującego na lokalizację</span><span class="sxs-lookup"><span data-stu-id="6efc7-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="6efc7-103">Tworzenie formularzy, które są gotowe do przeniesienia znacznie zlokalizowane szybkości rozwoju na rynkach międzynarodowych.</span><span class="sxs-lookup"><span data-stu-id="6efc7-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="6efc7-104">Można użyć <xref:System.Windows.Forms.TableLayoutPanel> formantu do zaimplementowania układów reagujące bezpiecznie zgodnie z powodu zmian w zmiana rozmiaru formantów ich <xref:System.Windows.Forms.Control.Text%2A> wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="6efc7-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6efc7-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="6efc7-105">Example</span></span>  
 <span data-ttu-id="6efc7-106">Ten formularz pokazuje, jak utworzyć układ proporcjonalnie dopasowuje podczas translacji wartości ciągu wyświetlanego w innych językach.</span><span class="sxs-lookup"><span data-stu-id="6efc7-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="6efc7-107">Po wywołaniu tego procesu tłumaczenia *lokalizacja*.</span><span class="sxs-lookup"><span data-stu-id="6efc7-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="6efc7-108">Aby uzyskać więcej informacji, zobacz [lokalizacja](../../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="6efc7-108">For more information, see [Localization](../../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="6efc7-109">Brak kompleksową obsługę tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6efc7-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="6efc7-110">Zobacz też [wskazówki: tworzenia układu, który dostosowuje część lokalizacji](http://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="6efc7-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](http://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
1.  <span data-ttu-id="6efc7-111">[Porady: wyrównywanie i rozciąganie formantu w formancie TableLayoutPanel](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6efc7-111">[How to: Align and Stretch a Control in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span></span>  
  
2.  <span data-ttu-id="6efc7-112">[Wskazówki: Rozmieszczanie formantów na formularzach systemu Windows za pomocą FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6efc7-112">[Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))</span></span>  
  
3.  <span data-ttu-id="6efc7-113">[Porady: obejmowanie rzędów i kolumn w formancie TableLayoutPanel](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6efc7-113">[How to: Span Rows and Columns in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span></span>  
  
4.  <span data-ttu-id="6efc7-114">[Porady: edytowanie rzędów i kolumn w formancie TableLayoutPanel](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6efc7-114">[How to: Edit Columns and Rows in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span></span>  
  
5.  <span data-ttu-id="6efc7-115">[Wskazówki: Przeprowadzanie typowych zadań z tagami inteligentnymi na Windows formantów formularzy](http://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6efc7-115">[Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](http://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))</span></span>  
  
6.  <span data-ttu-id="6efc7-116">[Wskazówki: Rozmieszczanie formantów na formularzach systemu Windows za pomocą TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6efc7-116">[Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span></span>  
  
7.  <span data-ttu-id="6efc7-117">[Wskazówki: Tworzenie Windows formantów formularzy dopełnienie, marginesami oraz właściwościami AutoSize właściwość](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6efc7-117">[Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))</span></span>  
  
8.  <span data-ttu-id="6efc7-118">[Porady: Obsługa lokalizacji w formularzach systemu Windows za pomocą AutoSize i TableLayoutPanel — formant](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6efc7-118">[How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))</span></span>  
  
9. <span data-ttu-id="6efc7-119">[Wskazówki: Tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych](http://msdn.microsoft.com/library/991eahec\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6efc7-119">[Walkthrough: Creating a Resizable Windows Form for Data Entry](http://msdn.microsoft.com/library/991eahec\(v=vs.110\))</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6efc7-120">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6efc7-120">Compiling the Code</span></span>  
 <span data-ttu-id="6efc7-121">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="6efc7-121">This example requires:</span></span>  
  
-   <span data-ttu-id="6efc7-122">Odwołania do zestawów systemu, dane systemowe, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6efc7-122">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6efc7-123">Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6efc7-123">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6efc7-124">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="6efc7-124">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="6efc7-125">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="6efc7-125">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6efc7-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6efc7-126">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [<span data-ttu-id="6efc7-127">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="6efc7-127">Localization</span></span>](../../../../docs/standard/globalization-localization/localization.md)
