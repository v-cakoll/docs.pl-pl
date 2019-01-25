---
title: ColorConvertedBitmap — Rozszerzenie znaczników
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: 4f71b90fa00d1aaee0ec5ad43e5a19be03c79c50
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647650"
---
# <a name="colorconvertedbitmap-markup-extension"></a><span data-ttu-id="a934a-102">ColorConvertedBitmap — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="a934a-102">ColorConvertedBitmap Markup Extension</span></span>
<span data-ttu-id="a934a-103">Zapewnia sposób określania źródła mapy bitowej, który nie ma profilu osadzonego.</span><span class="sxs-lookup"><span data-stu-id="a934a-103">Provides a way to specify a bitmap source that does not have an embedded profile.</span></span> <span data-ttu-id="a934a-104">Kolor kontekstów / profile są określone przez [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], ponieważ jest źródło obrazu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a934a-104">Color contexts / profiles are specified by [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], as is the image source [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="a934a-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="a934a-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="a934a-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="a934a-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`imageSource`|<span data-ttu-id="a934a-107">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Dla nieprofilowanych mapy bitowej.</span><span class="sxs-lookup"><span data-stu-id="a934a-107">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the nonprofiled bitmap.</span></span>|  
|`sourceIIC`|<span data-ttu-id="a934a-108">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Źródła konfiguracji profilu.</span><span class="sxs-lookup"><span data-stu-id="a934a-108">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the source profile configuration.</span></span>|  
|`destinationIIC`|<span data-ttu-id="a934a-109">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Konfiguracji profil docelowy</span><span class="sxs-lookup"><span data-stu-id="a934a-109">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the destination profile configuration</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a934a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a934a-110">Remarks</span></span>  
 <span data-ttu-id="a934a-111">Tego rozszerzenia znacznika jest przeznaczona do wypełnienia powiązany zestaw wartości właściwości źródło obrazu, takich jak <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="a934a-111">This markup extension is intended to fill a related set of image-source property values such as <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span></span>  
  
 <span data-ttu-id="a934a-112">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="a934a-112">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="a934a-113">`ColorConvertedBitmap` (lub `ColorConvertedBitmapExtension`) nie można używać w składni elementu właściwości, ponieważ wartość można ustawić tylko jako wartości na początkowej konstruktora, który jest ciągiem następujące identyfikator rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="a934a-113">`ColorConvertedBitmap` (or `ColorConvertedBitmapExtension`) cannot be used in property element syntax, because the values can only be set as values on the initial constructor, which is the string following the extension identifier.</span></span>  
  
 <span data-ttu-id="a934a-114">`ColorConvertedBitmap` jest rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="a934a-114">`ColorConvertedBitmap` is a markup extension.</span></span> <span data-ttu-id="a934a-115">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="a934a-115">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="a934a-116">Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Użyj {i} znaków w składni swoich atrybutów, które jest do Konwencja, za pomocą którego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora rozpoznaje, że rozszerzenie znacznika musi wykonać przetwarzanie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a934a-116">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="a934a-117">Aby uzyskać więcej informacji, zobacz [rozszerzenia znacznikowania i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="a934a-117">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a934a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a934a-118">See also</span></span>
- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [<span data-ttu-id="a934a-119">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="a934a-119">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="a934a-120">Obrazowanie — przegląd</span><span class="sxs-lookup"><span data-stu-id="a934a-120">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
