---
title: 'Przewodniki: Tworzenie niestandardowego przycisku animowanego'
ms.date: 03/30/2017
helpviewer_keywords:
- custom animated buttons [WPF]
- buttons [WPF]
- animation [WPF], buttons [WPF]
ms.assetid: e9532c72-460f-4898-9332-613fa21d746a
ms.openlocfilehash: 3c601641a0eb1024722b4f449f0ab23e54fe93dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024472"
---
# <a name="walkthroughs-create-a-custom-animated-button"></a><span data-ttu-id="8d866-102">Przewodniki: Tworzenie niestandardowego przycisku animowanego</span><span class="sxs-lookup"><span data-stu-id="8d866-102">Walkthroughs: Create a Custom Animated Button</span></span>
<span data-ttu-id="8d866-103">Jak sugeruje nazwa, Windows Presentation Foundation (WPF) to idealne narzędzie do wprowadzania środowisk sformatowanego prezentacji dla klientów.</span><span class="sxs-lookup"><span data-stu-id="8d866-103">As its name suggests, Windows Presentation Foundation (WPF) is great for making rich presentation experiences for customers.</span></span> <span data-ttu-id="8d866-104">Te przewodniki pokazują, jak dostosować wygląd i zachowanie przycisku (w tym animacji).</span><span class="sxs-lookup"><span data-stu-id="8d866-104">These walkthroughs show you how to customize the look and behavior of a button (including animations).</span></span> <span data-ttu-id="8d866-105">To dostosowanie jest wykonywane przy użyciu stylów i szablonów, dzięki czemu można zastosować ten niestandardowy przycisk łatwo wszystkie przyciski w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8d866-105">This customization is done using a style and template so that you can apply this custom button easily to any buttons in your application.</span></span> <span data-ttu-id="8d866-106">Na poniższej ilustracji przedstawiono dostosowany przycisk tworzone.</span><span class="sxs-lookup"><span data-stu-id="8d866-106">The following illustration shows the customized button that you will create.</span></span>  
  
 <span data-ttu-id="8d866-107">![Dostosowany przycisk, który spowoduje utworzenie](./media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span><span class="sxs-lookup"><span data-stu-id="8d866-107">![The customized button that you will create](./media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span></span>  
  
 <span data-ttu-id="8d866-108">Grafika wektorowa, które tworzą wyglądu przycisku są tworzone za pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d866-108">The vector graphics that make up the appearance of the button are created by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <span data-ttu-id="8d866-109">jest podobny do formatu HTML, jednak jest bardziej wydajna i rozszerzalna.</span><span class="sxs-lookup"><span data-stu-id="8d866-109">is similar to HTML except it is more powerful and extensible.</span></span> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <span data-ttu-id="8d866-110">można wpisać w ręcznie przy użyciu programu Microsoft Visual Studio lub Notatnik lub można użyć narzędzia projektowania wizualnego, takiego jak Microsoft Expression Blend.</span><span class="sxs-lookup"><span data-stu-id="8d866-110">can be typed in manually using Microsoft Visual Studio or Notepad, or you can use a visual design tool such as Microsoft Expression Blend.</span></span> <span data-ttu-id="8d866-111">Expression Blend polega na tworzeniu podstawowych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kod, więc obie metody tworzenia tych samych grafiki.</span><span class="sxs-lookup"><span data-stu-id="8d866-111">Expression Blend works by creating underlying [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code, so both methods create the same graphics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8d866-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="8d866-112">In This Section</span></span>  
 [<span data-ttu-id="8d866-113">Tworzenie przycisku przy użyciu programu Microsoft Expression Blend</span><span class="sxs-lookup"><span data-stu-id="8d866-113">Create a Button by Using Microsoft Expression Blend</span></span>](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 <span data-ttu-id="8d866-114">Pokazuje, jak utworzyć przyciski niestandardowe zachowanie, korzystając z projektanta funkcji Expression Blend.</span><span class="sxs-lookup"><span data-stu-id="8d866-114">Demonstrates how to create buttons with custom behavior by using the designer features of Expression Blend.</span></span>  
  
 [<span data-ttu-id="8d866-115">Tworzenie przycisku przy użyciu XAML</span><span class="sxs-lookup"><span data-stu-id="8d866-115">Create a Button by Using XAML</span></span>](walkthrough-create-a-button-by-using-xaml.md)  
 <span data-ttu-id="8d866-116">Pokazuje, jak utworzyć przyciski niestandardowe zachowanie za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d866-116">Demonstrates how to create buttons with custom behavior by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and Visual Studio.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8d866-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="8d866-117">Related Sections</span></span>  
 [<span data-ttu-id="8d866-118">Tworzenie szablonów i stylów</span><span class="sxs-lookup"><span data-stu-id="8d866-118">Styling and Templating</span></span>](styling-and-templating.md)  
 <span data-ttu-id="8d866-119">W tym artykule opisano, jak style i szablony mogą służyć do określenia wyglądu i zachowania formantów.</span><span class="sxs-lookup"><span data-stu-id="8d866-119">Describes how styles and templates can be used to determine the appearance and behavior of controls.</span></span>  
  
 [<span data-ttu-id="8d866-120">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="8d866-120">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)  
 <span data-ttu-id="8d866-121">W tym artykule opisano, jak obiekty mogą być animowane przy użyciu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Animacja i system chronometrażu.</span><span class="sxs-lookup"><span data-stu-id="8d866-121">Describes how objects can be animated by using the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] animation and timing system.</span></span>  
  
 [<span data-ttu-id="8d866-122">Malowanie jednolitymi kolorami i gradientami — przegląd</span><span class="sxs-lookup"><span data-stu-id="8d866-122">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 <span data-ttu-id="8d866-123">W tym artykule opisano sposób wykorzystania obiektów pędzla do malowanie jednolitymi kolorami, użyciu gradientów liniowych i użyciu gradientów promieniowych.</span><span class="sxs-lookup"><span data-stu-id="8d866-123">Describes how to use brush objects to paint with solid colors, linear gradients, and radial gradients.</span></span>  
  
 [<span data-ttu-id="8d866-124">Efekty mapy bitowej — przegląd</span><span class="sxs-lookup"><span data-stu-id="8d866-124">Bitmap Effects Overview</span></span>](../graphics-multimedia/bitmap-effects-overview.md)  
 <span data-ttu-id="8d866-125">W tym artykule opisano efektów mapy bitowej, obsługiwane przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] i objaśnienie sposobu ich stosowania.</span><span class="sxs-lookup"><span data-stu-id="8d866-125">Describes the bitmap effects supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and explains how to apply them.</span></span>
