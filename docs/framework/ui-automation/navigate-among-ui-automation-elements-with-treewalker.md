---
title: "Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker"
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
- classes, TreeWalker
- TreeWalker class
- elements, navigating among
- UI Automation, navigating among elements
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
caps.latest.revision: "8"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 3f237184cb4364b90d8a16cd078faeaec62bb693
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a><span data-ttu-id="01634-102">Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker</span><span class="sxs-lookup"><span data-stu-id="01634-102">Navigate Among UI Automation Elements with TreeWalker</span></span>
> [!NOTE]
>  <span data-ttu-id="01634-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="01634-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="01634-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="01634-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="01634-105">Ten temat zawiera przykładowy kod, pokazujący sposób poruszania się między [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elementów przy użyciu <xref:System.Windows.Automation.TreeWalker> klasy.</span><span class="sxs-lookup"><span data-stu-id="01634-105">This topic contains example code that shows how to navigate among [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements by using the <xref:System.Windows.Automation.TreeWalker> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01634-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="01634-106">Example</span></span>  
 <span data-ttu-id="01634-107">W poniższym przykładzie użyto <xref:System.Windows.Automation.TreeWalker.GetParent%2A> do podejść [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] drzewa aż do znalezienia elementu głównego lub pulpitu.</span><span class="sxs-lookup"><span data-stu-id="01634-107">The following example uses <xref:System.Windows.Automation.TreeWalker.GetParent%2A> to walk up the [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tree until it finds the root element, or desktop.</span></span> <span data-ttu-id="01634-108">Element pod który jest okna nadrzędnego określonego elementu.</span><span class="sxs-lookup"><span data-stu-id="01634-108">The element just below that is the parent window of the specified element.</span></span>  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a><span data-ttu-id="01634-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="01634-109">Example</span></span>  
 <span data-ttu-id="01634-110">W poniższym przykładzie użyto <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> i <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> utworzyć <xref:System.Windows.Forms.TreeView> który pokazuje całą poddrzewa [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elementów, które znajdują się w widoku kontrolki i są włączone.</span><span class="sxs-lookup"><span data-stu-id="01634-110">The following example uses <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> and <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> to create a <xref:System.Windows.Forms.TreeView> that shows an entire subtree of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements that are in the control view and that are enabled.</span></span>  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a><span data-ttu-id="01634-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01634-111">See Also</span></span>  
 [<span data-ttu-id="01634-112">Uzyskiwanie elementów automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="01634-112">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
