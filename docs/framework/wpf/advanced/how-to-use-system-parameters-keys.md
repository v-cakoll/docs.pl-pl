---
title: 'Instrukcje: Używanie kluczy parametrów systemowych'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: edacb4b98ab01f081f668dc3374f6588492210d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918368"
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="028a3-102">Instrukcje: Używanie kluczy parametrów systemowych</span><span class="sxs-lookup"><span data-stu-id="028a3-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="028a3-103">Zasoby systemowe uwidaczniają różne metryki systemu jako zasoby, które ułatwiają deweloperom tworzenie wizualizacji, które są spójne z ustawieniami systemowymi.</span><span class="sxs-lookup"><span data-stu-id="028a3-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="028a3-104"><xref:System.Windows.SystemParameters>to Klasa, która zawiera zarówno wartości parametru systemowego, jak i klucze zasobów powiązane z wartościami — na przykład <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> i <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="028a3-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="028a3-105">Metryki parametrów systemowych mogą służyć jako zasoby statyczne lub dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="028a3-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="028a3-106">Użyj zasobu dynamicznego, jeśli chcesz, aby Metryka parametru była aktualizowana automatycznie podczas uruchamiania aplikacji; w przeciwnym razie użyj zasobu statycznego.</span><span class="sxs-lookup"><span data-stu-id="028a3-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="028a3-107">Zasoby dynamiczne mają *klucz* słowa kluczowego, który jest dołączany do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="028a3-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="028a3-108">Poniższy przykład pokazuje, jak uzyskać dostęp do zasobów dynamicznych parametru systemu i używać ich do nadawania stylu lub dostosowywania przycisku.</span><span class="sxs-lookup"><span data-stu-id="028a3-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="028a3-109">Ten [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład zmienia rozmiar przycisku, przypisując <xref:System.Windows.SystemParameters> wartości do szerokości i wysokości przycisku.</span><span class="sxs-lookup"><span data-stu-id="028a3-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="028a3-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="028a3-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="028a3-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="028a3-111">See also</span></span>

- [<span data-ttu-id="028a3-112">Malowanie obszaru pędzlem systemowym</span><span class="sxs-lookup"><span data-stu-id="028a3-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="028a3-113">Używanie elementu SystemFonts</span><span class="sxs-lookup"><span data-stu-id="028a3-113">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
- [<span data-ttu-id="028a3-114">Używanie elementu SystemParameters</span><span class="sxs-lookup"><span data-stu-id="028a3-114">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
