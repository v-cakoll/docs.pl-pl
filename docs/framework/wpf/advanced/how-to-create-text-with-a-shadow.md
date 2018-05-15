---
title: Jak utworzyć tekst z cieniem
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 1b7740284afcda6eab41fb68be3b4a2f032cc77d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="6fbec-102">Jak utworzyć tekst z cieniem</span><span class="sxs-lookup"><span data-stu-id="6fbec-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="6fbec-103">Przykłady w tej sekcji pokazano, jak utworzyć efekt cieniowania dla wyświetlanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="6fbec-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fbec-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6fbec-104">Example</span></span>  
 <span data-ttu-id="6fbec-105"><xref:System.Windows.Media.Effects.DropShadowEffect> Obiektu służy do tworzenia różnych spadku efektów cienia do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obiektów.</span><span class="sxs-lookup"><span data-stu-id="6fbec-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="6fbec-106">W poniższym przykładzie przedstawiono efektem cienia tekstu.</span><span class="sxs-lookup"><span data-stu-id="6fbec-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="6fbec-107">W takim przypadku cień jest cienia miękkie, co oznacza rozmywa kolor cienia.</span><span class="sxs-lookup"><span data-stu-id="6fbec-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 <span data-ttu-id="6fbec-108">![Cień tekstu z miękkości &#61; 0,25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")</span><span class="sxs-lookup"><span data-stu-id="6fbec-108">![Text shadow with Softness &#61; 0.25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")</span></span>  
<span data-ttu-id="6fbec-109">Przykład tekstu w tle elastyczne</span><span class="sxs-lookup"><span data-stu-id="6fbec-109">Example of text with a soft shadow</span></span>  
  
 <span data-ttu-id="6fbec-110">Szerokość cienia można kontrolować przez ustawienie <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6fbec-110">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="6fbec-111">Wartość `4.0` wskazuje na tle szerokości 4 pikseli.</span><span class="sxs-lookup"><span data-stu-id="6fbec-111">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="6fbec-112">Można kontrolować miękkość, lub rozmycia cienia modyfikując <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6fbec-112">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="6fbec-113">Wartość `0.0` wskazuje nie rozmycia.</span><span class="sxs-lookup"><span data-stu-id="6fbec-113">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="6fbec-114">Poniższy przykład kodu pokazuje, jak utworzyć nietrwałego cienia.</span><span class="sxs-lookup"><span data-stu-id="6fbec-114">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  <span data-ttu-id="6fbec-115">Te efekty cienia przechodzi przez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] potoku renderowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="6fbec-115">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="6fbec-116">W związku z tym ClearType jest wyłączona, korzystając z tych skutków.</span><span class="sxs-lookup"><span data-stu-id="6fbec-116">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="6fbec-117">W poniższym przykładzie przedstawiono twardych efektem cienia tekstu.</span><span class="sxs-lookup"><span data-stu-id="6fbec-117">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="6fbec-118">W takim przypadku nie zostało rozmyte cienia.</span><span class="sxs-lookup"><span data-stu-id="6fbec-118">In this case, the shadow is not blurred.</span></span>  
  
 <span data-ttu-id="6fbec-119">![Cień tekstu z miękkości &#61; 0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")</span><span class="sxs-lookup"><span data-stu-id="6fbec-119">![Text shadow with Softness &#61; 0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")</span></span>  
<span data-ttu-id="6fbec-120">Przykład tekstu w tle twardych</span><span class="sxs-lookup"><span data-stu-id="6fbec-120">Example of text with a hard shadow</span></span>  
  
 <span data-ttu-id="6fbec-121">Można utworzyć twardy cienia przez ustawienie <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> właściwości `0.0`, co oznacza, że nie rozmycia jest używana.</span><span class="sxs-lookup"><span data-stu-id="6fbec-121">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="6fbec-122">Można kontrolować kierunku cienia, modyfikując <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6fbec-122">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="6fbec-123">Ustaw kierunkową wartość tej właściwości w zakresie między `0` i `360`.</span><span class="sxs-lookup"><span data-stu-id="6fbec-123">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="6fbec-124">Na poniższej ilustracji przedstawiono wartości kierunkową <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> ustawienie właściwości.</span><span class="sxs-lookup"><span data-stu-id="6fbec-124">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 <span data-ttu-id="6fbec-125">![Ustawienie stopnia cień tle](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")</span><span class="sxs-lookup"><span data-stu-id="6fbec-125">![DropShadow degree setting of shadow](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")</span></span>  
<span data-ttu-id="6fbec-126">Diagram kierunek cień</span><span class="sxs-lookup"><span data-stu-id="6fbec-126">DropShadow Direction diagram</span></span>  
  
 <span data-ttu-id="6fbec-127">Poniższy przykład kodu pokazuje, jak utworzyć twardy cienia.</span><span class="sxs-lookup"><span data-stu-id="6fbec-127">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="6fbec-128">Za pomocą efektu rozmycia</span><span class="sxs-lookup"><span data-stu-id="6fbec-128">Using a Blur Effect</span></span>  
 <span data-ttu-id="6fbec-129">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> może służyć do tworzenia efektu przypominającej tle, który można umieścić za obiektu tekstu.</span><span class="sxs-lookup"><span data-stu-id="6fbec-129">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="6fbec-130">Efekt mapy bitowej rozmycia zastosowany do tekstu rozmywa tekst równomiernie we wszystkich kierunkach.</span><span class="sxs-lookup"><span data-stu-id="6fbec-130">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="6fbec-131">W poniższym przykładzie przedstawiono efekt rozmycia zastosowany do tekstu.</span><span class="sxs-lookup"><span data-stu-id="6fbec-131">The following example shows a blur effect applied to text.</span></span>  
  
 <span data-ttu-id="6fbec-132">![Cień tekstu przy użyciu BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")</span><span class="sxs-lookup"><span data-stu-id="6fbec-132">![Text shadow using a BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")</span></span>  
<span data-ttu-id="6fbec-133">Przykład tekstu z efektem rozmycia</span><span class="sxs-lookup"><span data-stu-id="6fbec-133">Example of text with a blur effect</span></span>  
  
 <span data-ttu-id="6fbec-134">Poniższy przykładowy kod przedstawia sposób tworzenia efektu rozmycia.</span><span class="sxs-lookup"><span data-stu-id="6fbec-134">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="6fbec-135">Przy użyciu translacji transformacji</span><span class="sxs-lookup"><span data-stu-id="6fbec-135">Using a Translate Transform</span></span>  
 <span data-ttu-id="6fbec-136">A <xref:System.Windows.Media.TranslateTransform> może służyć do tworzenia efektu przypominającej tle, który można umieścić za obiektu tekstu.</span><span class="sxs-lookup"><span data-stu-id="6fbec-136">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="6fbec-137">Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.TranslateTransform> do Przesunięcie tekstu.</span><span class="sxs-lookup"><span data-stu-id="6fbec-137">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="6fbec-138">W tym przykładzie nieco przesunięcia kopię tekstu poniżej tekst podstawowy tworzy efektem cienia.</span><span class="sxs-lookup"><span data-stu-id="6fbec-138">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 <span data-ttu-id="6fbec-139">![Cień tekstu przy użyciu TranslateTransform](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")</span><span class="sxs-lookup"><span data-stu-id="6fbec-139">![Text shadow using a TranslateTransform](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")</span></span>  
<span data-ttu-id="6fbec-140">Przykład przy użyciu transformacji dla efektu cienia tekstu</span><span class="sxs-lookup"><span data-stu-id="6fbec-140">Example of text using a transform for a shadow effect</span></span>  
  
 <span data-ttu-id="6fbec-141">Poniższy przykładowy kod przedstawia sposób tworzenia transformacji dla efektem cienia.</span><span class="sxs-lookup"><span data-stu-id="6fbec-141">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
