---
title: "Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
caps.latest.revision: "13"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0acd6510e6349917b38e33e487123a118c2e653c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="d54e7-102">Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="d54e7-102">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="d54e7-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d54e7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d54e7-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="d54e7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="d54e7-105">Ten temat zawiera przykładowy kod, który demonstruje sposób użycia [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Wstawianie tekstu w polu tekstowym jeden wiersz.</span><span class="sxs-lookup"><span data-stu-id="d54e7-105">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="d54e7-106">Alternatywna metoda podano wiele wierszy i sformatowanego tekstu formantów gdzie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nie ma zastosowania.</span><span class="sxs-lookup"><span data-stu-id="d54e7-106">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="d54e7-107">Dla porównania w przykładzie pokazano sposób użycia metody Win32 na takie same wyniki.</span><span class="sxs-lookup"><span data-stu-id="d54e7-107">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d54e7-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="d54e7-108">Example</span></span>  
 <span data-ttu-id="d54e7-109">Następujące przykładowe kroki przez sekwencję tekstu formantów w aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="d54e7-109">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="d54e7-110">Każdej kontrolki tekstu jest testowany, aby sprawdzić, czy <xref:System.Windows.Automation.ValuePattern> obiektu można uzyskać za pomocą <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d54e7-110">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="d54e7-111">Jeśli formant tekstu obsługuje <xref:System.Windows.Automation.ValuePattern>, <xref:System.Windows.Automation.ValuePattern.SetValue%2A> metoda służy do wstawiania ciągu zdefiniowane przez użytkownika w formancie tekstu.</span><span class="sxs-lookup"><span data-stu-id="d54e7-111">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="d54e7-112">W przeciwnym razie <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> metoda jest używana.</span><span class="sxs-lookup"><span data-stu-id="d54e7-112">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="d54e7-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d54e7-113">See Also</span></span>  
 [<span data-ttu-id="d54e7-114">Wstaw TextPattern przykładowy tekst</span><span class="sxs-lookup"><span data-stu-id="d54e7-114">TextPattern Insert Text Sample</span></span>](http://msdn.microsoft.com/en-us/67353f93-7ee2-42f2-ab76-5c078cf6ca16)
