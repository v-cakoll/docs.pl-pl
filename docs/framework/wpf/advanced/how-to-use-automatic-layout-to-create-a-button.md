---
title: "Jak użyć automatycznego układu to utworzenia przycisku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c642e6491722e9bfe35337d066e3870f5a70f38c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a><span data-ttu-id="2a5a0-102">Jak użyć automatycznego układu to utworzenia przycisku</span><span class="sxs-lookup"><span data-stu-id="2a5a0-102">How to: Use Automatic Layout to Create a Button</span></span>
<span data-ttu-id="2a5a0-103">W tym przykładzie przedstawiono sposób użyć metody automatycznego układu, aby utworzyć element button w aplikacji lokalizowalny.</span><span class="sxs-lookup"><span data-stu-id="2a5a0-103">This example describes how to use the automatic layout approach to create a button in a localizable application.</span></span>  
  
 <span data-ttu-id="2a5a0-104">Lokalizacja [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] może być czasochłonne procesu.</span><span class="sxs-lookup"><span data-stu-id="2a5a0-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="2a5a0-105">Często wiadomość dla lokalizatorów konieczne rozmiar i położenie elementów oprócz tłumaczenie tekstu.</span><span class="sxs-lookup"><span data-stu-id="2a5a0-105">Often localizers need to resize and reposition elements in addition to translating text.</span></span> <span data-ttu-id="2a5a0-106">W przeszłości każdego języka, który [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] została dostosowana wymaganych dostosowań.</span><span class="sxs-lookup"><span data-stu-id="2a5a0-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="2a5a0-107">Teraz z funkcjami [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] można zaprojektować elementów pozwalających ograniczyć potrzebę dostosowania.</span><span class="sxs-lookup"><span data-stu-id="2a5a0-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="2a5a0-108">Podejście do pisania aplikacji, które mogą być łatwo po zmianie rozmiaru i zmienionym jest nazywany `automatic layout`.</span><span class="sxs-lookup"><span data-stu-id="2a5a0-108">The approach to writing applications that can be more easily resized and repositioned is called `automatic layout`.</span></span>  
  
 <span data-ttu-id="2a5a0-109">Następujące dwa [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykłady tworzenia aplikacji, które wystąpienia przycisk; jeden z tekstu w języku angielskim i jeden z tekstu w języku hiszpańskim.</span><span class="sxs-lookup"><span data-stu-id="2a5a0-109">The following two [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples create applications that instantiate a button; one with English text and one with Spanish text.</span></span> <span data-ttu-id="2a5a0-110">Zwróć uwagę, że kod jest taki sam, z wyjątkiem tekstu. Ten przycisk jest dopasowywany tekst.</span><span class="sxs-lookup"><span data-stu-id="2a5a0-110">Notice that the code is the same except for the text; the button adjusts to fit the text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a5a0-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a5a0-111">Example</span></span>  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="2a5a0-112">Na poniższym rysunku przedstawiono dane wyjściowe przykładów kodu.</span><span class="sxs-lookup"><span data-stu-id="2a5a0-112">The following graphic shows the output of the code samples.</span></span>  
  
 <span data-ttu-id="2a5a0-113">![Ten sam przycisk z tekstem w różnych językach](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span><span class="sxs-lookup"><span data-stu-id="2a5a0-113">![The same button with text in different languages](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span></span>  
<span data-ttu-id="2a5a0-114">Przycisk o zmiennym rozmiarze automatycznie</span><span class="sxs-lookup"><span data-stu-id="2a5a0-114">Auto Resizable Button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a5a0-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a5a0-115">See Also</span></span>  
 [<span data-ttu-id="2a5a0-116">Przegląd używania automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="2a5a0-116">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [<span data-ttu-id="2a5a0-117">Używanie siatki do automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="2a5a0-117">Use a Grid for Automatic Layout</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
