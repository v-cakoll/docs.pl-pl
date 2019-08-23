---
title: 'Instrukcje: Tworzenie tekstu z cieniem'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 0fe64e4e9e7aadbd30a38743647251f9fa49ba95
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960444"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="aac1c-102">Instrukcje: Tworzenie tekstu z cieniem</span><span class="sxs-lookup"><span data-stu-id="aac1c-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="aac1c-103">W przykładach w tej sekcji pokazano, jak utworzyć efekt cieniowania wyświetlanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="aac1c-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aac1c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="aac1c-104">Example</span></span>  
 <span data-ttu-id="aac1c-105">Obiekt umożliwia tworzenie różnorodnych efektów cienia dla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obiektów. <xref:System.Windows.Media.Effects.DropShadowEffect></span><span class="sxs-lookup"><span data-stu-id="aac1c-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="aac1c-106">W poniższym przykładzie pokazano efekt cieniowania stosowany do tekstu.</span><span class="sxs-lookup"><span data-stu-id="aac1c-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="aac1c-107">W tym przypadku cień jest miękką cienią, co oznacza, że kolor cienia jest zamazany.</span><span class="sxs-lookup"><span data-stu-id="aac1c-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 ![Cień tekstu z miękką &#61; 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg) 
  
 <span data-ttu-id="aac1c-109">Szerokość cienia można kontrolować przez ustawienie <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="aac1c-109">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="aac1c-110">Wartość `4.0` wskazuje szerokość cienia wynoszącą 4 piksele.</span><span class="sxs-lookup"><span data-stu-id="aac1c-110">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="aac1c-111">Możesz kontrolować miękkość lub rozmycie cienia, modyfikując <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="aac1c-111">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="aac1c-112">Wartość nie wskazuje `0.0` na rozmyte.</span><span class="sxs-lookup"><span data-stu-id="aac1c-112">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="aac1c-113">Poniższy przykład kodu pokazuje, jak utworzyć miękki cień.</span><span class="sxs-lookup"><span data-stu-id="aac1c-113">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> <span data-ttu-id="aac1c-114">Te efekty cienia nie przechodzą przez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] potok renderowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="aac1c-114">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="aac1c-115">W związku z tym technologia ClearType jest wyłączona podczas korzystania z tych efektów.</span><span class="sxs-lookup"><span data-stu-id="aac1c-115">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="aac1c-116">Poniższy przykład pokazuje efekt trwałego cienia zastosowany do tekstu.</span><span class="sxs-lookup"><span data-stu-id="aac1c-116">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="aac1c-117">W takim przypadku cień nie jest rozmyty.</span><span class="sxs-lookup"><span data-stu-id="aac1c-117">In this case, the shadow is not blurred.</span></span>  
  
 ![Cień tekstu z niemiękką &#61; wartością 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg) 
  
 <span data-ttu-id="aac1c-119">Można utworzyć twardą cień przez ustawienie <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> właściwości na `0.0`, która wskazuje, że nie jest używane rozmycie.</span><span class="sxs-lookup"><span data-stu-id="aac1c-119">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="aac1c-120">Kierunek cienia można kontrolować, modyfikując <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="aac1c-120">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="aac1c-121">Ustaw wartość kierunkową tej właściwości na poziom między `0` i. `360`</span><span class="sxs-lookup"><span data-stu-id="aac1c-121">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="aac1c-122">Na poniższej ilustracji przedstawiono wartości <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> kierunkowe ustawienia właściwości.</span><span class="sxs-lookup"><span data-stu-id="aac1c-122">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 ![Ustawienie stopnia DropShadow cienia](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 <span data-ttu-id="aac1c-124">Poniższy przykład kodu pokazuje, jak utworzyć cień twardy.</span><span class="sxs-lookup"><span data-stu-id="aac1c-124">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="aac1c-125">Używanie efektu rozmycia</span><span class="sxs-lookup"><span data-stu-id="aac1c-125">Using a Blur Effect</span></span>  
 <span data-ttu-id="aac1c-126"><xref:System.Windows.Media.Effects.BlurBitmapEffect> Można użyć do utworzenia efektu przypominającego cień, który może być umieszczony za obiektem tekstowym.</span><span class="sxs-lookup"><span data-stu-id="aac1c-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="aac1c-127">Efekt mapy bitowej rozmywania stosowany do tekstu rozmywa tekst równomiernie we wszystkich kierunkach.</span><span class="sxs-lookup"><span data-stu-id="aac1c-127">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="aac1c-128">W poniższym przykładzie pokazano efekt rozmycia stosowany do tekstu.</span><span class="sxs-lookup"><span data-stu-id="aac1c-128">The following example shows a blur effect applied to text.</span></span>  
  
 ![Cień tekstu przy użyciu BlurBitmapEffect](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 <span data-ttu-id="aac1c-130">Poniższy przykład kodu pokazuje, jak utworzyć efekt rozmycia.</span><span class="sxs-lookup"><span data-stu-id="aac1c-130">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="aac1c-131">Używanie transformacji tłumaczenia</span><span class="sxs-lookup"><span data-stu-id="aac1c-131">Using a Translate Transform</span></span>  
 <span data-ttu-id="aac1c-132"><xref:System.Windows.Media.TranslateTransform> Można użyć do utworzenia efektu przypominającego cień, który może być umieszczony za obiektem tekstowym.</span><span class="sxs-lookup"><span data-stu-id="aac1c-132">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="aac1c-133">Poniższy przykład kodu używa <xref:System.Windows.Media.TranslateTransform> do przesunięcia tekstu.</span><span class="sxs-lookup"><span data-stu-id="aac1c-133">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="aac1c-134">W tym przykładzie nieznacznie przesunięta kopia tekstu poniżej podstawowego tekstu tworzy efekt cienia.</span><span class="sxs-lookup"><span data-stu-id="aac1c-134">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 ![Cień tekstu przy użyciu TranslateTransform](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)    
  
 <span data-ttu-id="aac1c-136">Poniższy przykład kodu pokazuje, jak utworzyć transformację dla efektu cienia.</span><span class="sxs-lookup"><span data-stu-id="aac1c-136">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
