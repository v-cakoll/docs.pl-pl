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
ms.openlocfilehash: 559f0ee3bf1da1b33ff73b116c67ed2849cbe782
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966397"
---
# <a name="obtain-text-attributes-using-ui-automation"></a><span data-ttu-id="159d3-102">Uzyskiwanie atrybutów tekstu przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="159d3-102">Obtain Text Attributes Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="159d3-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="159d3-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="159d3-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="159d3-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="159d3-105">W tym temacie pokazano, jak [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] używać programu do uzyskiwania atrybutów tekstu z zakresu tekstu.</span><span class="sxs-lookup"><span data-stu-id="159d3-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attributes from a text range.</span></span> <span data-ttu-id="159d3-106">Zakres tekstu może odpowiadać bieżącej lokalizacji karetki (lub wygenerowania zaznaczenia) w dokumencie, ciągłym wyborze tekstu, kolekcji rozłączonych opcji tekstowych lub całej zawartości tekstowej dokumentu.</span><span class="sxs-lookup"><span data-stu-id="159d3-106">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="159d3-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="159d3-107">Example</span></span>  
 <span data-ttu-id="159d3-108">Poniższy przykład kodu demonstruje, <xref:System.Windows.Automation.TextPattern.FontNameAttribute> jak uzyskać z zakresu tekstu.</span><span class="sxs-lookup"><span data-stu-id="159d3-108">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 <span data-ttu-id="159d3-109">Wzorzec kontrolki, w połączeniu <xref:System.Windows.Automation.Text.TextPatternRange> z klasą, obsługuje podstawowe atrybuty tekstu, właściwości i metody. <xref:System.Windows.Automation.TextPattern></span><span class="sxs-lookup"><span data-stu-id="159d3-109">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="159d3-110">W przypadku funkcji specyficznych dla kontroli, które nie <xref:System.Windows.Automation.TextPattern> są <xref:System.Windows.Automation.Text.TextPatternRange> obsługiwane <xref:System.Windows.Automation.AutomationElement>przez program lub, Klasa dostarcza metody dla klienta automatyzacji interfejsu użytkownika w celu uzyskania dostępu do odpowiedniego modelu obiektów macierzystych.</span><span class="sxs-lookup"><span data-stu-id="159d3-110">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange> the <xref:System.Windows.Automation.AutomationElement>, class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="159d3-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="159d3-111">See also</span></span>

- [<span data-ttu-id="159d3-112">Przegląd automatyzacji interfejsu użytkownika — TextPattern</span><span class="sxs-lookup"><span data-stu-id="159d3-112">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [<span data-ttu-id="159d3-113">Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="159d3-113">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="159d3-114">Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="159d3-114">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="159d3-115">Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="159d3-115">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="159d3-116">Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="159d3-116">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="159d3-117">Uzyskiwanie szczegółów atrybutów tekstu mieszanego przy użyciu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="159d3-117">Obtain Mixed Text Attribute Details Using UI Automation</span></span>](../../../docs/framework/ui-automation/obtain-mixed-text-attribute-details-using-ui-automation.md)
