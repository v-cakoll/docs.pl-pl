---
title: 'Instrukcje: Używanie kluczy czcionek systemowych'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: 7283e4225b75909322fa312583e9f1a0679762e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918389"
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="81c7b-102">Instrukcje: Używanie kluczy czcionek systemowych</span><span class="sxs-lookup"><span data-stu-id="81c7b-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="81c7b-103">Zasoby systemowe uwidaczniają różne metryki systemu jako zasoby, które ułatwiają deweloperom tworzenie wizualizacji, które są spójne z ustawieniami systemowymi.</span><span class="sxs-lookup"><span data-stu-id="81c7b-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="81c7b-104"><xref:System.Windows.SystemFonts>to Klasa, która zawiera zarówno wartości czcionki systemowej, jak i zasoby czcionki systemowej, które są powiązane z <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> wartościami <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>— na przykład i.</span><span class="sxs-lookup"><span data-stu-id="81c7b-104"><xref:System.Windows.SystemFonts> is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="81c7b-105">Metryki czcionek systemowych mogą służyć jako zasoby statyczne lub dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="81c7b-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="81c7b-106">Użyj zasobu dynamicznego, jeśli chcesz, aby Metryka czcionki była aktualizowana automatycznie podczas uruchamiania aplikacji; w przeciwnym razie użyj zasobu statycznego.</span><span class="sxs-lookup"><span data-stu-id="81c7b-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81c7b-107">Zasoby dynamiczne mają *klucz* słowa kluczowego, który jest dołączany do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="81c7b-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="81c7b-108">Poniższy przykład pokazuje, jak uzyskać dostęp do zasobów dynamicznych czcionki systemu i używać ich do nadawania stylu lub dostosowywania przycisku.</span><span class="sxs-lookup"><span data-stu-id="81c7b-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="81c7b-109">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tym przykładzie tworzony jest styl przycisku przypisujący <xref:System.Windows.SystemFonts> wartości do przycisku.</span><span class="sxs-lookup"><span data-stu-id="81c7b-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81c7b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="81c7b-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="81c7b-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81c7b-111">See also</span></span>

- [<span data-ttu-id="81c7b-112">Malowanie obszaru pędzlem systemowym</span><span class="sxs-lookup"><span data-stu-id="81c7b-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="81c7b-113">Używanie elementu SystemParameters</span><span class="sxs-lookup"><span data-stu-id="81c7b-113">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="81c7b-114">Używanie elementu SystemFonts</span><span class="sxs-lookup"><span data-stu-id="81c7b-114">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
