---
title: Uzyskiwanie atrybutów tekstu przy użyciu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting, text attributes
- UI Automation, getting text attributes
- text attributes, getting
ms.assetid: fdefc6c3-b836-4cfe-8dec-1484bfdc5551
ms.openlocfilehash: d4cb9d12e4e2d5a28744e3a238884616a6db8f68
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214900"
---
# <a name="obtain-text-attributes-using-ui-automation"></a><span data-ttu-id="92f38-102">Uzyskiwanie atrybutów tekstu przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="92f38-102">Obtain Text Attributes Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="92f38-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="92f38-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="92f38-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="92f38-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="92f38-105">W tym temacie pokazano, jak używać [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] na uzyskiwanie atrybutów tekstu z zakresu tekstu.</span><span class="sxs-lookup"><span data-stu-id="92f38-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attributes from a text range.</span></span> <span data-ttu-id="92f38-106">Zakres tekstu może odpowiadać w bieżącej lokalizacji karetki (lub zdegenerowanym zaznaczenia) w dokumencie, wyboru ciągłego, tekstu, zbiór zaznaczenia tekstu rozłączne lub całej zawartości tekstowej dokumentu.</span><span class="sxs-lookup"><span data-stu-id="92f38-106">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92f38-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="92f38-107">Example</span></span>  
 <span data-ttu-id="92f38-108">Poniższy przykład kodu demonstruje sposób uzyskiwania <xref:System.Windows.Automation.TextPattern.FontNameAttribute> z zakresu tekstu.</span><span class="sxs-lookup"><span data-stu-id="92f38-108">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 <span data-ttu-id="92f38-109"><xref:System.Windows.Automation.TextPattern> — Wzorzec kontrolki, w połączeniu z sekcją <xref:System.Windows.Automation.Text.TextPatternRange> klasy, obsługuje podstawowe atrybuty, właściwości i metody.</span><span class="sxs-lookup"><span data-stu-id="92f38-109">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="92f38-110">Dla funkcji specyficznej dla kontroli, która nie jest obsługiwana przez <xref:System.Windows.Automation.TextPattern> lub <xref:System.Windows.Automation.Text.TextPatternRange> <xref:System.Windows.Automation.AutomationElement>, klasa dostarcza metody dla klientów automatyzacji interfejsu użytkownika dostępu odpowiedni model obiektów natywnych.</span><span class="sxs-lookup"><span data-stu-id="92f38-110">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange> the <xref:System.Windows.Automation.AutomationElement>, class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f38-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92f38-111">See also</span></span>

- [<span data-ttu-id="92f38-112">Przegląd automatyzacji interfejsu użytkownika — TextPattern</span><span class="sxs-lookup"><span data-stu-id="92f38-112">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [<span data-ttu-id="92f38-113">Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="92f38-113">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="92f38-114">Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="92f38-114">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="92f38-115">Wzorce formantów automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="92f38-115">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="92f38-116">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="92f38-116">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="92f38-117">Uzyskiwanie szczegółów atrybutów tekstu mieszanego przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="92f38-117">Obtain Mixed Text Attribute Details Using UI Automation</span></span>](../../../docs/framework/ui-automation/obtain-mixed-text-attribute-details-using-ui-automation.md)
