---
title: 'Instrukcje: Użyj kluczy parametrów systemowych'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: a71551c5d539d7009fb9a052c81928a009fc4c35
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357199"
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="07bf4-102">Instrukcje: Użyj kluczy parametrów systemowych</span><span class="sxs-lookup"><span data-stu-id="07bf4-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="07bf4-103">Zasoby systemowe ujawnić różne metryki systemu jako zasoby, które ułatwiają deweloperom tworzenie wizualizacji, które są zgodne z ustawieniami systemu.</span><span class="sxs-lookup"><span data-stu-id="07bf4-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="07bf4-104"><xref:System.Windows.SystemParameters> to klasa, która zawiera wartości parametrów systemu i klucze zasobów, które wartości należy powiązać — na przykład <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> i <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="07bf4-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="07bf4-105">Metryki parametru systemu może służyć jako zasoby statyczne lub dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="07bf4-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="07bf4-106">Użyj dynamicznych zasobów, jeśli chcesz, aby metryki parametru na automatyczne aktualizowanie podczas jej uruchomieniu; w przeciwnym razie użyj zasób statyczny.</span><span class="sxs-lookup"><span data-stu-id="07bf4-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07bf4-107">Dynamiczne zasoby mają słowa kluczowego *klucz* dołączana do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="07bf4-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="07bf4-108">Poniższy przykład pokazuje, jak uzyskać dostęp do zasobów dynamiczny parametr systemu do określania stylu i dostosowywania przycisku.</span><span class="sxs-lookup"><span data-stu-id="07bf4-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="07bf4-109">To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład przycisku o rozmiarach, przypisując <xref:System.Windows.SystemParameters> wartości szerokości i wysokości przycisku.</span><span class="sxs-lookup"><span data-stu-id="07bf4-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07bf4-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="07bf4-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="07bf4-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07bf4-111">See also</span></span>
- [<span data-ttu-id="07bf4-112">Malowanie obszaru pędzlem systemowym</span><span class="sxs-lookup"><span data-stu-id="07bf4-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="07bf4-113">Używanie elementu SystemFonts</span><span class="sxs-lookup"><span data-stu-id="07bf4-113">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
- [<span data-ttu-id="07bf4-114">Używanie elementu SystemParameters</span><span class="sxs-lookup"><span data-stu-id="07bf4-114">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
