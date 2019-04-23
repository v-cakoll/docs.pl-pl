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
ms.openlocfilehash: aed8c624a75364dcc97c73ae7ebd6331275ceff4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182874"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a>Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera przykładowy kod, który pokazuje, jak do nawigowania między [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elementy przy użyciu <xref:System.Windows.Automation.TreeWalker> klasy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Automation.TreeWalker.GetParent%2A> Aby krokowo [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] drzewa do momentu znalezienia elementu głównego lub pulpitu. Element tuż poniżej, jest okna nadrzędnego określonego elementu.  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> i <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> utworzyć <xref:System.Windows.Forms.TreeView> pokazujący całego poddrzewie [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elementy, które znajdują się w widoku formantu i są włączone.  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie elementów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
