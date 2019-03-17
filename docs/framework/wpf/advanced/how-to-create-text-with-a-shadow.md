---
title: 'Instrukcje: Utwórz tekst z cieniem'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: a2225e297dbc0b5f9d49799cb34eb5539746e62e
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125788"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="4d13d-102">Instrukcje: Utwórz tekst z cieniem</span><span class="sxs-lookup"><span data-stu-id="4d13d-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="4d13d-103">Przykłady w tej sekcji pokazano, jak utworzyć efekt dla tekstu wyświetlanego w tle.</span><span class="sxs-lookup"><span data-stu-id="4d13d-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d13d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d13d-104">Example</span></span>  
 <span data-ttu-id="4d13d-105"><xref:System.Windows.Media.Effects.DropShadowEffect> Obiektu służy do tworzenia różnych upuszczania efekty dla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obiektów.</span><span class="sxs-lookup"><span data-stu-id="4d13d-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="4d13d-106">Poniższy przykład pokazuje efektem cienia tekstu.</span><span class="sxs-lookup"><span data-stu-id="4d13d-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="4d13d-107">W tym przypadku cień jest elastyczne w tle, co oznacza rozmywa kolor cienia.</span><span class="sxs-lookup"><span data-stu-id="4d13d-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 ![Cień tekstu z miękkości &#61; 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg) 
  
 <span data-ttu-id="4d13d-109">Szerokość w tle można kontrolować przez ustawienie <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4d13d-109">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="4d13d-110">Wartość `4.0` wskazuje 4 pikseli szerokości w tle.</span><span class="sxs-lookup"><span data-stu-id="4d13d-110">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="4d13d-111">Można kontrolować miękkość, lub Rozmycie cienia, modyfikując <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4d13d-111">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="4d13d-112">Wartość `0.0` wskazuje nie Rozmycie.</span><span class="sxs-lookup"><span data-stu-id="4d13d-112">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="4d13d-113">Poniższy przykład kodu pokazuje sposób tworzenia nietrwałego w tle.</span><span class="sxs-lookup"><span data-stu-id="4d13d-113">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  <span data-ttu-id="4d13d-114">Efekty cieniowania te nie odbywają się za pośrednictwem [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] potoku renderowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="4d13d-114">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="4d13d-115">W rezultacie ClearType jest wyłączona, korzystając z tych skutków.</span><span class="sxs-lookup"><span data-stu-id="4d13d-115">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="4d13d-116">Poniższy przykład pokazuje twardych efektem cienia tekstu.</span><span class="sxs-lookup"><span data-stu-id="4d13d-116">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="4d13d-117">W tym przypadku nie zostało rozmyte cienia.</span><span class="sxs-lookup"><span data-stu-id="4d13d-117">In this case, the shadow is not blurred.</span></span>  
  
 ![Cień tekstu z miękkości &#61; 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg) 
  
 <span data-ttu-id="4d13d-119">Utworzyć twardy w tle, ustawiając <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> właściwości `0.0`, co oznacza, że Rozmycie nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="4d13d-119">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="4d13d-120">Możesz kontrolować kierunku cienia, modyfikując <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4d13d-120">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="4d13d-121">Ustaw kierunkowe wartość tej właściwości w zakresie między `0` i `360`.</span><span class="sxs-lookup"><span data-stu-id="4d13d-121">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="4d13d-122">Na poniższej ilustracji przedstawiono wartości kierunkowe <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> ustawienie właściwości.</span><span class="sxs-lookup"><span data-stu-id="4d13d-122">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 ![Ustawienie stopnia DropShadow w tle](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 <span data-ttu-id="4d13d-124">Poniższy przykład kodu pokazuje, jak utworzyć twardy w tle.</span><span class="sxs-lookup"><span data-stu-id="4d13d-124">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="4d13d-125">Przy użyciu efektu rozmycia</span><span class="sxs-lookup"><span data-stu-id="4d13d-125">Using a Blur Effect</span></span>  
 <span data-ttu-id="4d13d-126">Element <xref:System.Windows.Media.Effects.BlurBitmapEffect> może służyć do tworzenia efekt podobne w tle, który można umieścić za obiektem tekstu.</span><span class="sxs-lookup"><span data-stu-id="4d13d-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="4d13d-127">Efekt mapy bitowej Rozmycie tekstu rozmywa tekst równomiernie we wszystkich kierunkach.</span><span class="sxs-lookup"><span data-stu-id="4d13d-127">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="4d13d-128">Poniższy przykład przedstawia efekt rozmycia tekstu.</span><span class="sxs-lookup"><span data-stu-id="4d13d-128">The following example shows a blur effect applied to text.</span></span>  
  
 ![Cień tekstu przy użyciu BlurBitmapEffect](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 <span data-ttu-id="4d13d-130">W poniższym przykładzie kodu pokazano, jak utworzyć efekt Rozmycie.</span><span class="sxs-lookup"><span data-stu-id="4d13d-130">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="4d13d-131">Za pomocą przekład — przekształcenie</span><span class="sxs-lookup"><span data-stu-id="4d13d-131">Using a Translate Transform</span></span>  
 <span data-ttu-id="4d13d-132">Element <xref:System.Windows.Media.TranslateTransform> może służyć do tworzenia efekt podobne w tle, który można umieścić za obiektem tekstu.</span><span class="sxs-lookup"><span data-stu-id="4d13d-132">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="4d13d-133">Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.TranslateTransform> na przesunięcie tekstu.</span><span class="sxs-lookup"><span data-stu-id="4d13d-133">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="4d13d-134">W tym przykładzie nieco przesunięcia kopię tekstu poniżej tekst podstawowy tworzy efekt w tle.</span><span class="sxs-lookup"><span data-stu-id="4d13d-134">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 ![Cień tekstu przy użyciu TranslateTransform](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)    
  
 <span data-ttu-id="4d13d-136">Poniższy przykład kodu pokazuje sposób tworzenia transformacji dla efektu w tle.</span><span class="sxs-lookup"><span data-stu-id="4d13d-136">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
