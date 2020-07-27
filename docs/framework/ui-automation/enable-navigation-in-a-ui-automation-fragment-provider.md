---
title: Włączanie nawigacji w dostawcy fragmentu automatyzacji interfejsu użytkownika
description: Przeczytaj przykład, który pokazuje, jak włączyć nawigację w dostawcy automatyzacji interfejsu użytkownika dla elementu, który znajduje się w fragmencie.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: bf9e43e9d70b9191fba93e5efa4eae544196c735
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168490"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a><span data-ttu-id="77c2c-103">Włączanie nawigacji w dostawcy fragmentu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="77c2c-103">Enable Navigation in a UI Automation Fragment Provider</span></span>
> [!NOTE]
> <span data-ttu-id="77c2c-104">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="77c2c-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="77c2c-105">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="77c2c-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="77c2c-106">Ten temat zawiera przykładowy kod, który pokazuje, jak włączyć nawigację w dostawcy automatyzacji interfejsu użytkownika dla elementu znajdującego się w fragmencie.</span><span class="sxs-lookup"><span data-stu-id="77c2c-106">This topic contains example code that shows how to enable navigation in a UI Automation provider for an element that is within a fragment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77c2c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="77c2c-107">Example</span></span>  
 <span data-ttu-id="77c2c-108">Poniższy przykładowy kod implementuje <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> dla elementu listy znajdującego się na liście.</span><span class="sxs-lookup"><span data-stu-id="77c2c-108">The following example code implements <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> for a list item within a list.</span></span> <span data-ttu-id="77c2c-109">Element nadrzędny jest elementem pola listy, a elementy równorzędne są innymi elementami w kolekcji list.</span><span class="sxs-lookup"><span data-stu-id="77c2c-109">The parent element is the list box element, and the sibling elements are other items in the list collection.</span></span> <span data-ttu-id="77c2c-110">Metoda zwraca `null` ( `Nothing` w Visual Basic) dla wskazówek, które są nieprawidłowe; w tym przypadku, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> i <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild> , ponieważ element nie ma elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="77c2c-110">The method returns `null` (`Nothing` in Visual Basic) for directions that are not valid; in this case, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> and <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, because the element has no children.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="77c2c-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77c2c-111">See also</span></span>

- [<span data-ttu-id="77c2c-112">Przegląd dostawców automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="77c2c-112">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="77c2c-113">Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="77c2c-113">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
