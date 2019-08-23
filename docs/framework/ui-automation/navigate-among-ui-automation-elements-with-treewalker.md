---
title: Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, TreeWalker
- TreeWalker class
- elements, navigating among
- UI Automation, navigating among elements
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
ms.openlocfilehash: 506cc4db3fcf255d270f72470a1f0d68e9cca7ce
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966420"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a><span data-ttu-id="41f46-102">Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker</span><span class="sxs-lookup"><span data-stu-id="41f46-102">Navigate Among UI Automation Elements with TreeWalker</span></span>
> [!NOTE]
> <span data-ttu-id="41f46-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="41f46-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="41f46-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="41f46-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="41f46-105">Ten temat zawiera przykładowy kod, który pokazuje, jak przechodzić między [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elementami <xref:System.Windows.Automation.TreeWalker> przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="41f46-105">This topic contains example code that shows how to navigate among [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements by using the <xref:System.Windows.Automation.TreeWalker> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41f46-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="41f46-106">Example</span></span>  
 <span data-ttu-id="41f46-107">Poniższy przykład używa <xref:System.Windows.Automation.TreeWalker.GetParent%2A> do [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] przeszukiwania drzewa do momentu znalezienia elementu głównego lub pulpitu.</span><span class="sxs-lookup"><span data-stu-id="41f46-107">The following example uses <xref:System.Windows.Automation.TreeWalker.GetParent%2A> to walk up the [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tree until it finds the root element, or desktop.</span></span> <span data-ttu-id="41f46-108">Element poniżej, który jest oknem nadrzędnym określonego elementu.</span><span class="sxs-lookup"><span data-stu-id="41f46-108">The element just below that is the parent window of the specified element.</span></span>  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a><span data-ttu-id="41f46-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="41f46-109">Example</span></span>  
 <span data-ttu-id="41f46-110">Poniższy przykład używa <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> i <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> do tworzenia <xref:System.Windows.Forms.TreeView> , który pokazuje Całe poddrzewo [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elementów znajdujących się w widoku kontrolki, które są włączone.</span><span class="sxs-lookup"><span data-stu-id="41f46-110">The following example uses <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> and <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> to create a <xref:System.Windows.Forms.TreeView> that shows an entire subtree of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements that are in the control view and that are enabled.</span></span>  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a><span data-ttu-id="41f46-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41f46-111">See also</span></span>

- [<span data-ttu-id="41f46-112">Uzyskiwanie elementów automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="41f46-112">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
