---
title: "Jak usunąć atrament na niestandardowej kontrolce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], erasing ink on
- ink [WPF], erasing on custom control
ms.assetid: d88c50f9-b4d8-4962-a28b-67d6a15a5fe0
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e05163bcbafd360e0929fe784ff1111bd0663ef3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-erase-ink-on-a-custom-control"></a><span data-ttu-id="08212-102">Jak usunąć atrament na niestandardowej kontrolce</span><span class="sxs-lookup"><span data-stu-id="08212-102">How to: Erase Ink on a Custom Control</span></span>
<span data-ttu-id="08212-103"><xref:System.Windows.Ink.IncrementalStrokeHitTester> Określa, czy obecnie narysowanego obrysu przecina obrysu innego.</span><span class="sxs-lookup"><span data-stu-id="08212-103">The <xref:System.Windows.Ink.IncrementalStrokeHitTester> determines whether the currently drawn stroke intersects another stroke.</span></span>  <span data-ttu-id="08212-104">Jest to przydatne do tworzenia formantu, który umożliwia użytkownikowi wymazać części pociągnięcia, sposób użytkownik może na <xref:System.Windows.Controls.InkCanvas> podczas <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> ma ustawioną wartość <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.</span><span class="sxs-lookup"><span data-stu-id="08212-104">This is useful for creating a control that enables a user to erase parts of a stroke, the way a user can on an <xref:System.Windows.Controls.InkCanvas> when the <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> is set to <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08212-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="08212-105">Example</span></span>  
 <span data-ttu-id="08212-106">Poniższy przykład tworzy kontrolkę niestandardową, który umożliwia użytkownikowi na usunięcie części pociągnięć.</span><span class="sxs-lookup"><span data-stu-id="08212-106">The following example creates a custom control that enables the user to erase parts of strokes.</span></span>  <span data-ttu-id="08212-107">W tym przykładzie tworzy kontrolkę, która zawiera odręczne po zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="08212-107">This example creates a control that contains ink when it is initialized.</span></span>  <span data-ttu-id="08212-108">Aby utworzyć formant, który zbiera pismo odręczne, zobacz [Tworzenie formantu danych wejściowych odręcznego](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span><span class="sxs-lookup"><span data-stu-id="08212-108">To create a control that collects ink, see [Creating an Ink Input Control](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span></span>  
  
 [!code-csharp[HowToEraseInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
