---
title: "Jak używać kluczy parametrów systemowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b2a7352540456b459428dd87f6c60be0b8bc08b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="16163-102">Jak używać kluczy parametrów systemowych</span><span class="sxs-lookup"><span data-stu-id="16163-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="16163-103">Zasoby systemowe ujawnia szereg metryki systemu jako zasoby, aby pomóc deweloperom tworzenie elementów wizualnych, które są zgodne z ustawieniami systemu.</span><span class="sxs-lookup"><span data-stu-id="16163-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="16163-104"><xref:System.Windows.SystemParameters>jest klasa, która zawiera klucze zasobów, które powiązać wartości i wartości parametrów systemu — na przykład <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> i <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="16163-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="16163-105">Metryki parametru systemu może służyć jako zasoby statyczne lub dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="16163-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="16163-106">Użyć zasobu dynamicznego, jeśli parametr metryki automatycznej aktualizacji podczas aplikacji działa; w przeciwnym razie użyj statycznych zasobu.</span><span class="sxs-lookup"><span data-stu-id="16163-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16163-107">Dynamiczne zasobów mieć słowa kluczowego *klucza* dołączonym do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="16163-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="16163-108">Poniższy przykład pokazuje, jak dostępu i korzystać z zasobów dynamicznej parametru systemu do nadawania stylu lub dostosowywanie przycisku.</span><span class="sxs-lookup"><span data-stu-id="16163-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="16163-109">To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład rozmiar przycisku przez przypisanie <xref:System.Windows.SystemParameters> wartości szerokości i wysokości przycisku.</span><span class="sxs-lookup"><span data-stu-id="16163-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16163-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="16163-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="16163-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16163-111">See Also</span></span>  
 [<span data-ttu-id="16163-112">Malowanie obszaru pędzlem systemowym</span><span class="sxs-lookup"><span data-stu-id="16163-112">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="16163-113">Używanie elementu SystemFonts</span><span class="sxs-lookup"><span data-stu-id="16163-113">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [<span data-ttu-id="16163-114">Używanie elementu SystemParameters</span><span class="sxs-lookup"><span data-stu-id="16163-114">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
