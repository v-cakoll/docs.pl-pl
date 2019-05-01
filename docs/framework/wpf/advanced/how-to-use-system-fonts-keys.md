---
title: 'Instrukcje: Używanie kluczy czcionek systemowych'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: e924f4c14d98380d9f4c0defe27d9f98c3293114
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001614"
---
# <a name="how-to-use-system-fonts-keys"></a><span data-ttu-id="393c9-102">Instrukcje: Używanie kluczy czcionek systemowych</span><span class="sxs-lookup"><span data-stu-id="393c9-102">How to: Use System Fonts Keys</span></span>
<span data-ttu-id="393c9-103">Zasoby systemowe ujawnić różne metryki systemu jako zasoby, które ułatwiają deweloperom tworzenie wizualizacji, które są zgodne z ustawieniami systemu.</span><span class="sxs-lookup"><span data-stu-id="393c9-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="393c9-104"><xref:System.Windows.SystemFonts> to klasa, która zawiera wartości czcionki systemowe i zasobów czcionek systemowych, które wartości należy powiązać — na przykład <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> i <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="393c9-104"><xref:System.Windows.SystemFonts> is a class that contains both system font values and system font resources that bind to the values—for example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.</span></span>  
  
 <span data-ttu-id="393c9-105">Metryki czcionki systemu może służyć jako zasoby statyczne lub dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="393c9-105">System font metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="393c9-106">Użyj dynamicznych zasobów, jeśli chcesz, aby metryki czcionki na automatyczne aktualizowanie podczas jej uruchomieniu; w przeciwnym razie użyj zasób statyczny.</span><span class="sxs-lookup"><span data-stu-id="393c9-106">Use a dynamic resource if you want the font metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="393c9-107">Dynamiczne zasoby mają słowa kluczowego *klucz* dołączana do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="393c9-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="393c9-108">Poniższy przykład pokazuje, jak uzyskać dostęp do zasobów dynamicznej czcionek systemowych do nadawania stylu i dostosowywania przycisku.</span><span class="sxs-lookup"><span data-stu-id="393c9-108">The following example shows how to access and use system font dynamic resources to style or customize a button.</span></span> <span data-ttu-id="393c9-109">To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład tworzy styl przycisku, który przypisuje <xref:System.Windows.SystemFonts> wartości do przycisku.</span><span class="sxs-lookup"><span data-stu-id="393c9-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example creates a button style that assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="393c9-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="393c9-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="393c9-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="393c9-111">See also</span></span>

- [<span data-ttu-id="393c9-112">Malowanie obszaru pędzlem systemowym</span><span class="sxs-lookup"><span data-stu-id="393c9-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="393c9-113">Używanie elementu SystemParameters</span><span class="sxs-lookup"><span data-stu-id="393c9-113">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="393c9-114">Używanie elementu SystemFonts</span><span class="sxs-lookup"><span data-stu-id="393c9-114">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
