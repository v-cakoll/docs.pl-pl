---
title: Jak używać kluczy czcionek systemowych
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: c68f197daebd7423aa4ad2e7fdfb6e7f89c74ed0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544430"
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="16fe3-102">Jak używać kluczy czcionek systemowych</span><span class="sxs-lookup"><span data-stu-id="16fe3-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="16fe3-103">Zasoby systemowe ujawnia szereg metryki systemu jako zasoby, aby pomóc deweloperom tworzenie elementów wizualnych, które są zgodne z ustawieniami systemu.</span><span class="sxs-lookup"><span data-stu-id="16fe3-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="16fe3-104"><xref:System.Windows.SystemFonts> jest klasa, która zawiera wartości czcionki systemu i zasobów systemowych czcionek powiązać wartości — na przykład <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> i <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="16fe3-104"><xref:System.Windows.SystemFonts> is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="16fe3-105">Mierniki czcionki systemu może służyć jako zasoby statyczne lub dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="16fe3-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="16fe3-106">Użyć zasobu dynamicznego, jeśli Metryka czcionki automatycznej aktualizacji podczas aplikacji działa; w przeciwnym razie użyj statycznych zasobu.</span><span class="sxs-lookup"><span data-stu-id="16fe3-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16fe3-107">Dynamiczne zasobów mieć słowa kluczowego *klucza* dołączonym do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="16fe3-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="16fe3-108">Poniższy przykład pokazuje, jak dostępu i korzystać z zasobów dynamicznej czcionki systemu do nadawania stylu lub dostosowywanie przycisku.</span><span class="sxs-lookup"><span data-stu-id="16fe3-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="16fe3-109">To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład tworzy styl przycisku, który przypisuje <xref:System.Windows.SystemFonts> wartości do przycisku.</span><span class="sxs-lookup"><span data-stu-id="16fe3-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16fe3-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="16fe3-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="16fe3-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16fe3-111">See Also</span></span>  
 [<span data-ttu-id="16fe3-112">Malowanie obszaru pędzlem systemowym</span><span class="sxs-lookup"><span data-stu-id="16fe3-112">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="16fe3-113">Używanie elementu SystemParameters</span><span class="sxs-lookup"><span data-stu-id="16fe3-113">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [<span data-ttu-id="16fe3-114">Używanie elementu SystemFonts</span><span class="sxs-lookup"><span data-stu-id="16fe3-114">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
