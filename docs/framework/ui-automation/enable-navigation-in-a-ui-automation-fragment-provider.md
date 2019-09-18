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
ms.openlocfilehash: 729d8c117599ca6d9aa011de6b3cf0e9a86cbea3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043820"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a><span data-ttu-id="922e3-102">Włączanie nawigacji w dostawcy fragmentu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="922e3-102">Enable Navigation in a UI Automation Fragment Provider</span></span>
> [!NOTE]
> <span data-ttu-id="922e3-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="922e3-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="922e3-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="922e3-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="922e3-105">Ten temat zawiera przykładowy kod, który pokazuje, jak włączyć nawigację w dostawcy automatyzacji interfejsu użytkownika dla elementu znajdującego się w fragmencie.</span><span class="sxs-lookup"><span data-stu-id="922e3-105">This topic contains example code that shows how to enable navigation in a UI Automation provider for an element that is within a fragment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="922e3-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="922e3-106">Example</span></span>  
 <span data-ttu-id="922e3-107">Poniższy przykładowy kod implementuje <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> dla elementu listy znajdującego się na liście.</span><span class="sxs-lookup"><span data-stu-id="922e3-107">The following example code implements <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> for a list item within a list.</span></span> <span data-ttu-id="922e3-108">Element nadrzędny jest elementem pola listy, a elementy równorzędne są innymi elementami w kolekcji list.</span><span class="sxs-lookup"><span data-stu-id="922e3-108">The parent element is the list box element, and the sibling elements are other items in the list collection.</span></span> <span data-ttu-id="922e3-109">Metoda zwraca `null` (`Nothing` w Visual Basic) dla wskazówek, które są nieprawidłowe; w tym przypadku, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> i <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, ponieważ element nie ma elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="922e3-109">The method returns `null` (`Nothing` in Visual Basic) for directions that are not valid; in this case, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> and <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, because the element has no children.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="922e3-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="922e3-110">See also</span></span>

- [<span data-ttu-id="922e3-111">Przegląd dostawców automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="922e3-111">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="922e3-112">Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="922e3-112">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
