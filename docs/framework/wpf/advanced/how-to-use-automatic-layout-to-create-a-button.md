---
title: 'Instrukcje: Użyj automatycznego układu to utworzenia przycisku'
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 501341f0e71e6e5a224c51e4ae01c68ce6b845cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543490"
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a><span data-ttu-id="e25be-102">Instrukcje: Użyj automatycznego układu to utworzenia przycisku</span><span class="sxs-lookup"><span data-stu-id="e25be-102">How to: Use Automatic Layout to Create a Button</span></span>
<span data-ttu-id="e25be-103">W tym przykładzie opisano sposób używania metody automatycznego układu to utworzenia przycisku w aplikacji możliwych do zlokalizowania.</span><span class="sxs-lookup"><span data-stu-id="e25be-103">This example describes how to use the automatic layout approach to create a button in a localizable application.</span></span>  
  
 <span data-ttu-id="e25be-104">Lokalizacja [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] może być procesem dużo czasu.</span><span class="sxs-lookup"><span data-stu-id="e25be-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="e25be-105">Często lokalizatorzy konieczne zmiany rozmiaru i położenia elementów oprócz tłumaczenie tekstu.</span><span class="sxs-lookup"><span data-stu-id="e25be-105">Often localizers need to resize and reposition elements in addition to translating text.</span></span> <span data-ttu-id="e25be-106">W przeszłości każdego z języków, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] została dostosowana wymaganych dostosowań.</span><span class="sxs-lookup"><span data-stu-id="e25be-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="e25be-107">Teraz z możliwościami [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] można zaprojektować elementy, które zmniejszyć zapotrzebowanie na dostosowanie.</span><span class="sxs-lookup"><span data-stu-id="e25be-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="e25be-108">Nosi nazwę podejścia do pisania aplikacji, które można łatwiej o zmienionym rozmiarze i zmienionym `automatic layout`.</span><span class="sxs-lookup"><span data-stu-id="e25be-108">The approach to writing applications that can be more easily resized and repositioned is called `automatic layout`.</span></span>  
  
 <span data-ttu-id="e25be-109">Następujące dwa [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykłady tworzenia aplikacji do tworzenia wystąpienia przycisku; jeden z tekstu w języku angielskim i jeden z tekstu w języku hiszpańskim.</span><span class="sxs-lookup"><span data-stu-id="e25be-109">The following two [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples create applications that instantiate a button; one with English text and one with Spanish text.</span></span> <span data-ttu-id="e25be-110">Należy zauważyć, że kod jest taki sam, z wyjątkiem tekstu. Ten przycisk jest dopasowywany tekstu.</span><span class="sxs-lookup"><span data-stu-id="e25be-110">Notice that the code is the same except for the text; the button adjusts to fit the text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e25be-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="e25be-111">Example</span></span>  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="e25be-112">Na poniższym rysunku przedstawiono dane wyjściowe z przykładów kodu.</span><span class="sxs-lookup"><span data-stu-id="e25be-112">The following graphic shows the output of the code samples.</span></span>  
  
 <span data-ttu-id="e25be-113">![Ten sam przycisk z tekstem w różnych językach](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span><span class="sxs-lookup"><span data-stu-id="e25be-113">![The same button with text in different languages](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span></span>  
<span data-ttu-id="e25be-114">Zmienny rozmiar przycisku automatycznie</span><span class="sxs-lookup"><span data-stu-id="e25be-114">Auto Resizable Button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e25be-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e25be-115">See also</span></span>
- [<span data-ttu-id="e25be-116">Przegląd używania automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="e25be-116">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)
- [<span data-ttu-id="e25be-117">Używanie siatki do automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="e25be-117">Use a Grid for Automatic Layout</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
