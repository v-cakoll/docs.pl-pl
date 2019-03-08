---
title: Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text, highlighting
- finding text
- text, finding
- UI automation, highlighting text
- UI automation, finding text
- highlighting text
ms.assetid: b77693f5-87bb-4b29-a297-05ff882e2044
ms.openlocfilehash: a0df93b153f16dd09dfcc6da5d690dc69141435a
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57673707"
---
# <a name="find-and-highlight-text-using-ui-automation"></a><span data-ttu-id="f06da-102">Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="f06da-102">Find and Highlight Text Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="f06da-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f06da-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f06da-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="f06da-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="f06da-105">W tym temacie pokazano, jak sekwencyjnie wyszukiwania i zaznacz każde wystąpienie ciągu w zawartości przy użyciu kontrolki tekstu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f06da-105">This topic demonstrates how to sequentially search for and highlight each occurrence of a string within the content of a text control using [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="f06da-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="f06da-106">Example</span></span>  
 <span data-ttu-id="f06da-107">W poniższym przykładzie uzyskano <xref:System.Windows.Automation.TextPattern> obiekt w kontrolce tekst.</span><span class="sxs-lookup"><span data-stu-id="f06da-107">The following example obtains a <xref:System.Windows.Automation.TextPattern> object from a text control.</span></span> <span data-ttu-id="f06da-108">A <xref:System.Windows.Automation.Text.TextPatternRange> obiekt reprezentujący zawartości tekstowej całego dokumentu jest tworzony przy użyciu <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> właściwość to <xref:System.Windows.Automation.TextPattern>.</span><span class="sxs-lookup"><span data-stu-id="f06da-108">A <xref:System.Windows.Automation.Text.TextPatternRange> object, representing the textual content of the entire document, is then created using the <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> property of this <xref:System.Windows.Automation.TextPattern>.</span></span> <span data-ttu-id="f06da-109">Dwa dodatkowe <xref:System.Windows.Automation.Text.TextPatternRange> obiekty są tworzone dla kolejnych wyszukiwania i wyróżnić funkcji.</span><span class="sxs-lookup"><span data-stu-id="f06da-109">Two additional <xref:System.Windows.Automation.Text.TextPatternRange> objects are then created for the sequential search and highlight functionality.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#SearchTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#searchtarget)]
[!code-vb[FindText#SearchTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#searchtarget)]  
  
## <a name="see-also"></a><span data-ttu-id="f06da-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f06da-110">See also</span></span>
- [<span data-ttu-id="f06da-111">Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="f06da-111">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
