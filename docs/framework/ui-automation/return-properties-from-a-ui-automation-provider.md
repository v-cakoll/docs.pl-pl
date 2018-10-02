---
title: Zwracanie właściwości od dostawcy automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- providers, UI Automation, returning properties
- properties, returned by UI Automation providers
- UI Automation, providers returning properties
ms.assetid: 5eba950e-b9e1-48eb-ab8e-b69db76bf589
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: ac5d539f99fe4f7a20d9030986120318840801bb
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "47862948"
---
# <a name="return-properties-from-a-ui-automation-provider"></a><span data-ttu-id="9d5b0-102">Zwracanie właściwości od dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="9d5b0-102">Return Properties from a UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="9d5b0-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9d5b0-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9d5b0-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="9d5b0-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="9d5b0-105">Ten temat zawiera przykładowy kod, który pokazuje, jak dostawcy automatyzacji interfejsu użytkownika mogą zwracać właściwości elementu dla aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="9d5b0-105">This topic contains sample code that shows how a UI Automation provider can return properties of an element to client applications.</span></span>  
  
 <span data-ttu-id="9d5b0-106">Dla dowolnej właściwości, jawnie nie obsługuje dostawca musi zwracać `null` (`Nothing` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="9d5b0-106">For any property it does not explicitly support, the provider must return `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="9d5b0-107">Gwarantuje to, że [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] próbuje uzyskać właściwości z innego źródła, takiego jak dostawca okna hosta.</span><span class="sxs-lookup"><span data-stu-id="9d5b0-107">This ensures that [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] attempts to obtain the property from another source, such as the host window provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d5b0-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d5b0-108">Example</span></span>  
 [!code-csharp[UIAFragmentProvider_snip#117](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#117)]
 [!code-vb[UIAFragmentProvider_snip#117](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#117)]  
  
## <a name="see-also"></a><span data-ttu-id="9d5b0-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d5b0-109">See Also</span></span>  
 [<span data-ttu-id="9d5b0-110">Przegląd dostawców automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="9d5b0-110">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="9d5b0-111">Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="9d5b0-111">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
