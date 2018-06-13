---
title: Włączanie nawigacji w dostawcy fragmentu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 1f4dea321ba4a4242af0766a367731222368372e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401030"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a><span data-ttu-id="a9cd1-102">Włączanie nawigacji w dostawcy fragmentu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="a9cd1-102">Enable Navigation in a UI Automation Fragment Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="a9cd1-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a9cd1-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a9cd1-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="a9cd1-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="a9cd1-105">Ten temat zawiera przykładowy kod, który pokazuje, jak włączanie nawigacji w dostawcy automatyzacji interfejsu użytkownika dla elementu w obrębie fragmentu.</span><span class="sxs-lookup"><span data-stu-id="a9cd1-105">This topic contains example code that shows how to enable navigation in a UI Automation provider for an element that is within a fragment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9cd1-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9cd1-106">Example</span></span>  
 <span data-ttu-id="a9cd1-107">Poniższy przykładowy kod implementuje <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> dla elementu listy, na liście.</span><span class="sxs-lookup"><span data-stu-id="a9cd1-107">The following example code implements <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> for a list item within a list.</span></span> <span data-ttu-id="a9cd1-108">Element nadrzędny jest element pola listy, a elementów równorzędnych są innych elementów w kolekcji list.</span><span class="sxs-lookup"><span data-stu-id="a9cd1-108">The parent element is the list box element, and the sibling elements are other items in the list collection.</span></span> <span data-ttu-id="a9cd1-109">Metoda zwraca `null` (`Nothing` w języku Visual Basic) dla wskazówki, które nie są prawidłowe; w takim przypadku <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> i <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, ponieważ element nie ma elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a9cd1-109">The method returns `null` (`Nothing` in Visual Basic) for directions that are not valid; in this case, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> and <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, because the element has no children.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="a9cd1-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9cd1-110">See Also</span></span>  
 [<span data-ttu-id="a9cd1-111">Przegląd dostawców automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="a9cd1-111">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="a9cd1-112">Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="a9cd1-112">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
