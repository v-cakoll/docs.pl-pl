---
title: Jak utworzyć tekst z cieniem
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: c3e8135372ce4a092552c812cd971cb70bc49bf3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186850"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="22f7d-102">Jak utworzyć tekst z cieniem</span><span class="sxs-lookup"><span data-stu-id="22f7d-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="22f7d-103">Przykłady w tej sekcji pokazują, jak utworzyć efekt cienia dla wyświetlanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="22f7d-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22f7d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="22f7d-104">Example</span></span>  
 <span data-ttu-id="22f7d-105">Obiekt <xref:System.Windows.Media.Effects.DropShadowEffect> umożliwia tworzenie różnych efektów cienia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dla obiektów.</span><span class="sxs-lookup"><span data-stu-id="22f7d-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="22f7d-106">W poniższym przykładzie przedstawiono efekt cienia zastosowany do tekstu.</span><span class="sxs-lookup"><span data-stu-id="22f7d-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="22f7d-107">W tym przypadku cień jest miękkim cieniem, co oznacza, że kolor cienia się zaciera.</span><span class="sxs-lookup"><span data-stu-id="22f7d-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 ![Cień tekstu z miękkością &#61; 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg)
  
 <span data-ttu-id="22f7d-109">Szerokość cienia można kontrolować, ustawiając <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="22f7d-109">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="22f7d-110">Wartość `4.0` wskazuje szerokość cienia 4 pikseli.</span><span class="sxs-lookup"><span data-stu-id="22f7d-110">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="22f7d-111">Miękkość lub rozmycie cienia można kontrolować, <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> modyfikując właściwość.</span><span class="sxs-lookup"><span data-stu-id="22f7d-111">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="22f7d-112">Wartość wskazuje, `0.0` że nie rozmycie.</span><span class="sxs-lookup"><span data-stu-id="22f7d-112">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="22f7d-113">W poniższym przykładzie kodu pokazano, jak utworzyć cień miękki.</span><span class="sxs-lookup"><span data-stu-id="22f7d-113">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> <span data-ttu-id="22f7d-114">Te efekty cienia nie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] przechodzą przez potok renderowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="22f7d-114">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="22f7d-115">W rezultacie ClearType jest wyłączona podczas korzystania z tych efektów.</span><span class="sxs-lookup"><span data-stu-id="22f7d-115">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="22f7d-116">W poniższym przykładzie przedstawiono efekt twardego cienia zastosowany do tekstu.</span><span class="sxs-lookup"><span data-stu-id="22f7d-116">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="22f7d-117">W takim przypadku cień nie jest rozmyty.</span><span class="sxs-lookup"><span data-stu-id="22f7d-117">In this case, the shadow is not blurred.</span></span>  
  
 ![Cień tekstu z miękkością &#61; 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg)
  
 <span data-ttu-id="22f7d-119">Twardy cień można utworzyć, <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> ustawiając `0.0`właściwość na , co oznacza, że nie jest używane rozmycie.</span><span class="sxs-lookup"><span data-stu-id="22f7d-119">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="22f7d-120">Można kontrolować kierunek cienia, modyfikując <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="22f7d-120">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="22f7d-121">Ustaw wartość kierunkową tej właściwości na `0` `360`stopień między .</span><span class="sxs-lookup"><span data-stu-id="22f7d-121">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="22f7d-122">Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> wartości kierunkowe ustawienia właściwości.</span><span class="sxs-lookup"><span data-stu-id="22f7d-122">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 ![Ustawienie stopnia DropShadow cienia](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 <span data-ttu-id="22f7d-124">W poniższym przykładzie kodu pokazano, jak utworzyć twardy cień.</span><span class="sxs-lookup"><span data-stu-id="22f7d-124">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="22f7d-125">Korzystanie z efektu rozmycia</span><span class="sxs-lookup"><span data-stu-id="22f7d-125">Using a Blur Effect</span></span>  
 <span data-ttu-id="22f7d-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> może służyć do tworzenia efektu podobnego do cienia, który można umieścić za obiektem tekstowym.</span><span class="sxs-lookup"><span data-stu-id="22f7d-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="22f7d-127">Efekt rozmycia bitmapy zastosowanej do tekstu rozmywa tekst równomiernie we wszystkich kierunkach.</span><span class="sxs-lookup"><span data-stu-id="22f7d-127">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="22f7d-128">W poniższym przykładzie przedstawiono efekt rozmycia zastosowany do tekstu.</span><span class="sxs-lookup"><span data-stu-id="22f7d-128">The following example shows a blur effect applied to text.</span></span>  
  
 ![Cień tekstu przy użyciu efektu BlurBitmapEffect](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 <span data-ttu-id="22f7d-130">W poniższym przykładzie kodu pokazano, jak utworzyć efekt rozmycia.</span><span class="sxs-lookup"><span data-stu-id="22f7d-130">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="22f7d-131">Korzystanie z transformacji tłumaczenia</span><span class="sxs-lookup"><span data-stu-id="22f7d-131">Using a Translate Transform</span></span>  
 <span data-ttu-id="22f7d-132">A <xref:System.Windows.Media.TranslateTransform> może służyć do tworzenia efektu podobnego do cienia, który można umieścić za obiektem tekstowym.</span><span class="sxs-lookup"><span data-stu-id="22f7d-132">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="22f7d-133">Poniższy przykład kodu <xref:System.Windows.Media.TranslateTransform> używa do przesunięcia tekstu.</span><span class="sxs-lookup"><span data-stu-id="22f7d-133">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="22f7d-134">W tym przykładzie nieznacznie odsunięta kopia tekstu poniżej tekstu podstawowego tworzy efekt cienia.</span><span class="sxs-lookup"><span data-stu-id="22f7d-134">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 ![Cień tekstu przy użyciu translatetransform](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)
  
 <span data-ttu-id="22f7d-136">Poniższy przykład kodu pokazuje, jak utworzyć transformację dla efektu cienia.</span><span class="sxs-lookup"><span data-stu-id="22f7d-136">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
