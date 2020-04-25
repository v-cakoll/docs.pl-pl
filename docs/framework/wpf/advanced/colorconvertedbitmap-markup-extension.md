---
title: ColorConvertedBitmap — Rozszerzenie znaczników
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: a5b491723a036c1b1fd0bb61736e6f2ee53fbcd3
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141226"
---
# <a name="colorconvertedbitmap-markup-extension"></a><span data-ttu-id="f32ae-102">ColorConvertedBitmap — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="f32ae-102">ColorConvertedBitmap Markup Extension</span></span>
<span data-ttu-id="f32ae-103">Umożliwia określenie źródła mapy bitowej, które nie ma osadzonego profilu.</span><span class="sxs-lookup"><span data-stu-id="f32ae-103">Provides a way to specify a bitmap source that does not have an embedded profile.</span></span> <span data-ttu-id="f32ae-104">Konteksty koloru/profile są określane przez identyfikator URI, ponieważ jest to identyfikator URI źródła obrazu.</span><span class="sxs-lookup"><span data-stu-id="f32ae-104">Color contexts / profiles are specified by URI, as is the image source URI.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="f32ae-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="f32ae-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" ... />
```  
  
## <a name="xaml-values"></a><span data-ttu-id="f32ae-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="f32ae-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`imageSource`|<span data-ttu-id="f32ae-107">Identyfikator URI nieprofilowanej mapy bitowej.</span><span class="sxs-lookup"><span data-stu-id="f32ae-107">The URI of the nonprofiled bitmap.</span></span>|  
|`sourceIIC`|<span data-ttu-id="f32ae-108">Identyfikator URI konfiguracji profilu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="f32ae-108">The URI of the source profile configuration.</span></span>|  
|`destinationIIC`|<span data-ttu-id="f32ae-109">Identyfikator URI konfiguracji profilu docelowego</span><span class="sxs-lookup"><span data-stu-id="f32ae-109">The URI of the destination profile configuration</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f32ae-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f32ae-110">Remarks</span></span>  
 <span data-ttu-id="f32ae-111">To rozszerzenie znacznika służy do wypełnienia powiązanego zestawu wartości właściwości źródła obrazu, takich jak <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="f32ae-111">This markup extension is intended to fill a related set of image-source property values such as <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span></span>  
  
 <span data-ttu-id="f32ae-112">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="f32ae-112">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="f32ae-113">`ColorConvertedBitmap`(or `ColorConvertedBitmapExtension`) nie można użyć w składni elementu właściwości, ponieważ wartości można ustawić tylko jako wartości w konstruktorze początkowym, który jest ciągiem następującym po identyfikatorze rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="f32ae-113">`ColorConvertedBitmap` (or `ColorConvertedBitmapExtension`) cannot be used in property element syntax, because the values can only be set as values on the initial constructor, which is the string following the extension identifier.</span></span>  
  
 <span data-ttu-id="f32ae-114">`ColorConvertedBitmap`jest rozszerzeniem znaczników.</span><span class="sxs-lookup"><span data-stu-id="f32ae-114">`ColorConvertedBitmap` is a markup extension.</span></span> <span data-ttu-id="f32ae-115">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="f32ae-115">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="f32ae-116">Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używają znaków {i} w ich składni atrybutów, która jest konwencją, za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] której procesor rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut.</span><span class="sxs-lookup"><span data-stu-id="f32ae-116">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="f32ae-117">Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="f32ae-117">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f32ae-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f32ae-118">See also</span></span>

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [<span data-ttu-id="f32ae-119">Rozszerzenia znacznikowania i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="f32ae-119">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="f32ae-120">Przegląd Obrazowanie</span><span class="sxs-lookup"><span data-stu-id="f32ae-120">Imaging Overview</span></span>](../graphics-multimedia/imaging-overview.md)
