---
title: "Zwracanie właściwości od dostawcy automatyzacji interfejsu użytkownika"
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
- providers, UI Automation, returning properties
- properties, returned by UI Automation providers
- UI Automation, providers returning properties
ms.assetid: 5eba950e-b9e1-48eb-ab8e-b69db76bf589
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: b0c340d809b0ea8a0a4b28cde3385e53dca7cfce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="return-properties-from-a-ui-automation-provider"></a><span data-ttu-id="a3ed7-102">Zwracanie właściwości od dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="a3ed7-102">Return Properties from a UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="a3ed7-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a3ed7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a3ed7-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="a3ed7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="a3ed7-105">Ten temat zawiera przykładowy kod, który pokazuje, jak dostawcy automatyzacji interfejsu użytkownika może zwracać element właściwości dla aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="a3ed7-105">This topic contains sample code that shows how a UI Automation provider can return properties of an element to client applications.</span></span>  
  
 <span data-ttu-id="a3ed7-106">Dla każdej właściwości, nie obsługuje jawnie dostawcy musi zwracać `null` (`Nothing` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a3ed7-106">For any property it does not explicitly support, the provider must return `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="a3ed7-107">Gwarantuje to, że [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] próbuje uzyskać właściwości z innego źródła, takiego jak dostawca okno hosta.</span><span class="sxs-lookup"><span data-stu-id="a3ed7-107">This ensures that [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] attempts to obtain the property from another source, such as the host window provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3ed7-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="a3ed7-108">Example</span></span>  
 [!code-csharp[UIAFragmentProvider_snip#117](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#117)]
 [!code-vb[UIAFragmentProvider_snip#117](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#117)]  
  
## <a name="see-also"></a><span data-ttu-id="a3ed7-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3ed7-109">See Also</span></span>  
 [<span data-ttu-id="a3ed7-110">Przegląd dostawców automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="a3ed7-110">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="a3ed7-111">Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="a3ed7-111">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
