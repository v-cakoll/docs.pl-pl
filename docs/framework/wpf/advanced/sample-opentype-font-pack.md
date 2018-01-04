---
title: "Przykład pakietu czcionek OpenType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7390c8c84caa17b984d5a16b7ac6b9704b8f3c6e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sample-opentype-font-pack"></a><span data-ttu-id="a3dcb-102">Przykład pakietu czcionek OpenType</span><span class="sxs-lookup"><span data-stu-id="a3dcb-102">Sample OpenType Font Pack</span></span>
<span data-ttu-id="a3dcb-103">Ten temat zawiera omówienie przykładowej [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionek, które są dystrybuowane wraz z [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a3dcb-103">This topic provides an overview of the sample [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts that are distributed with the [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)].</span></span> <span data-ttu-id="a3dcb-104">Obsługa czcionek próbki rozszerzony [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] funkcje, które mogą być używane przez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3dcb-104">The sample fonts support extended [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] features that can be used by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications.</span></span>  
  
  
<a name="overview"></a>   
## <a name="fonts-in-the-opentype-font-pack"></a><span data-ttu-id="a3dcb-105">Czcionki w pakiecie czcionek OpenType</span><span class="sxs-lookup"><span data-stu-id="a3dcb-105">Fonts in the OpenType Font Pack</span></span>  
 <span data-ttu-id="a3dcb-106">[!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] Zawiera zestaw próbki [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki używane podczas tworzenia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3dcb-106">The [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] provides a set of sample [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts that you can use in creating [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="a3dcb-107">Czcionki próbki są dostarczane w ramach licencji Wydłużenie górne Corporation.</span><span class="sxs-lookup"><span data-stu-id="a3dcb-107">The sample fonts are supplied under license from Ascender Corporation.</span></span> <span data-ttu-id="a3dcb-108">Tylko podzbiór całkowitej funkcje zdefiniowane przez wdrożenie tych czcionek [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] format.</span><span class="sxs-lookup"><span data-stu-id="a3dcb-108">These fonts implement only a subset of the total features defined by the [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] format.</span></span> <span data-ttu-id="a3dcb-109">W poniższej tabeli wymieniono nazwy próbki [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki.</span><span class="sxs-lookup"><span data-stu-id="a3dcb-109">The following table lists the names of the sample [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts.</span></span>  
  
|<span data-ttu-id="a3dcb-110">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="a3dcb-110">**Name**</span></span>|<span data-ttu-id="a3dcb-111">**Plik**</span><span class="sxs-lookup"><span data-stu-id="a3dcb-111">**File**</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="a3dcb-112">Kootenay</span><span class="sxs-lookup"><span data-stu-id="a3dcb-112">Kootenay</span></span>|<span data-ttu-id="a3dcb-113">Kooten.ttf</span><span class="sxs-lookup"><span data-stu-id="a3dcb-113">Kooten.ttf</span></span>|  
|<span data-ttu-id="a3dcb-114">Lindsey</span><span class="sxs-lookup"><span data-stu-id="a3dcb-114">Lindsey</span></span>|<span data-ttu-id="a3dcb-115">Linds.ttf</span><span class="sxs-lookup"><span data-stu-id="a3dcb-115">Linds.ttf</span></span>|  
|<span data-ttu-id="a3dcb-116">Miramonte</span><span class="sxs-lookup"><span data-stu-id="a3dcb-116">Miramonte</span></span>|<span data-ttu-id="a3dcb-117">Miramo.ttf</span><span class="sxs-lookup"><span data-stu-id="a3dcb-117">Miramo.ttf</span></span>|  
|<span data-ttu-id="a3dcb-118">Miramonte Bold</span><span class="sxs-lookup"><span data-stu-id="a3dcb-118">Miramonte Bold</span></span>|<span data-ttu-id="a3dcb-119">Miramob.ttf</span><span class="sxs-lookup"><span data-stu-id="a3dcb-119">Miramob.ttf</span></span>|  
|<span data-ttu-id="a3dcb-120">Perykles</span><span class="sxs-lookup"><span data-stu-id="a3dcb-120">Pericles</span></span>|<span data-ttu-id="a3dcb-121">Peric.ttf</span><span class="sxs-lookup"><span data-stu-id="a3dcb-121">Peric.ttf</span></span>|  
|<span data-ttu-id="a3dcb-122">Jasny Perykles</span><span class="sxs-lookup"><span data-stu-id="a3dcb-122">Pericles Light</span></span>|<span data-ttu-id="a3dcb-123">Pericl.ttf</span><span class="sxs-lookup"><span data-stu-id="a3dcb-123">Pericl.ttf</span></span>|  
|<span data-ttu-id="a3dcb-124">Pescadero</span><span class="sxs-lookup"><span data-stu-id="a3dcb-124">Pescadero</span></span>|<span data-ttu-id="a3dcb-125">Pesca.ttf</span><span class="sxs-lookup"><span data-stu-id="a3dcb-125">Pesca.ttf</span></span>|  
|<span data-ttu-id="a3dcb-126">Pescadero Bold</span><span class="sxs-lookup"><span data-stu-id="a3dcb-126">Pescadero Bold</span></span>|<span data-ttu-id="a3dcb-127">Pescab.ttf</span><span class="sxs-lookup"><span data-stu-id="a3dcb-127">Pescab.ttf</span></span>|  
  
 <span data-ttu-id="a3dcb-128">Na poniższej ilustracji przedstawiono przykładu [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] wyglądać czcionki.</span><span class="sxs-lookup"><span data-stu-id="a3dcb-128">The following illustration shows what the sample [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts look like.</span></span>  
  
 <span data-ttu-id="a3dcb-129">![Lista nazw czcionek w przykładowym pakiecie czcionek](../../../../docs/framework/wpf/advanced/media/samplefontpack01.gif "samplefontpack01")</span><span class="sxs-lookup"><span data-stu-id="a3dcb-129">![List of font names in sample font pack](../../../../docs/framework/wpf/advanced/media/samplefontpack01.gif "samplefontpack01")</span></span>  
<span data-ttu-id="a3dcb-130">Czcionki w pakiecie czcionek OpenType</span><span class="sxs-lookup"><span data-stu-id="a3dcb-130">Fonts in the OpenType Font Pack</span></span>  
  
 <span data-ttu-id="a3dcb-131">Czcionki próbki są dostarczane w ramach licencji Wydłużenie górne Corporation.</span><span class="sxs-lookup"><span data-stu-id="a3dcb-131">The sample fonts are supplied under license from Ascender Corporation.</span></span> <span data-ttu-id="a3dcb-132">Wydłużenie górne jest dostawcą produktów zaawansowane czcionki.</span><span class="sxs-lookup"><span data-stu-id="a3dcb-132">Ascender is a provider of advanced font products.</span></span> <span data-ttu-id="a3dcb-133">Aby licencji czcionki próbki w wersji rozszerzonej lub niestandardowych, zobacz [witryny sieci Web Corporation Wydłużenie górne](http://go.microsoft.com/fwlink/?LinkId=182627).</span><span class="sxs-lookup"><span data-stu-id="a3dcb-133">To license extended or custom versions of the sample fonts, see [Ascender Corporation's Web site](http://go.microsoft.com/fwlink/?LinkId=182627).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3dcb-134">Projektant jest obowiązek upewnij się, że masz wymagane prawa dla żadnej czcionki osadzić w aplikacji lub w przeciwnym razie ponownie rozesłać.</span><span class="sxs-lookup"><span data-stu-id="a3dcb-134">As a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  
  
<a name="installing_the_fonts"></a>   
## <a name="installing-the-fonts"></a><span data-ttu-id="a3dcb-135">Instalowanie czcionek</span><span class="sxs-lookup"><span data-stu-id="a3dcb-135">Installing the Fonts</span></span>  
 <span data-ttu-id="a3dcb-136">Istnieje możliwość zainstalowania przykładowej [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki domyślne [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] katalogu czcionki **\WINDOWS\Fonts**.</span><span class="sxs-lookup"><span data-stu-id="a3dcb-136">You have the option of installing the sample [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts to the default [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Fonts directory, **\WINDOWS\Fonts**.</span></span> <span data-ttu-id="a3dcb-137">Należy zainstalować czcionek czcionki w Panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="a3dcb-137">Use the Fonts control panel to install the fonts.</span></span> <span data-ttu-id="a3dcb-138">Po te czcionki na komputerze, są dostępne dla wszystkich aplikacji, które odwołują się do domyślnego [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] czcionki.</span><span class="sxs-lookup"><span data-stu-id="a3dcb-138">Once these fonts are on your computer, they are accessible to all applications that reference default [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] fonts.</span></span> <span data-ttu-id="a3dcb-139">Reprezentatywny zestaw znaków w kilku rozmiary czcionek można wyświetlić, klikając podwojenie — plik czcionki.</span><span class="sxs-lookup"><span data-stu-id="a3dcb-139">You can display a representative set of characters in several font sizes by doubling-clicking the font file.</span></span> <span data-ttu-id="a3dcb-140">Poniższy zrzut ekranu przedstawia plik czcionki Lindsey Linds.ttf.</span><span class="sxs-lookup"><span data-stu-id="a3dcb-140">The following screenshot shows the Lindsey font file, Linds.ttf.</span></span>  
  
 <span data-ttu-id="a3dcb-141">![Czcionka Lindsey &#40; OpenType &#41; ] (../../../../docs/framework/wpf/advanced/media/typographyinwpf-04.png "TypographyInWPF_04")</span><span class="sxs-lookup"><span data-stu-id="a3dcb-141">![Lindsey font &#40;OpenType&#41;](../../../../docs/framework/wpf/advanced/media/typographyinwpf-04.png "TypographyInWPF_04")</span></span>  
<span data-ttu-id="a3dcb-142">Wyświetlanie czcionki Lindsey</span><span class="sxs-lookup"><span data-stu-id="a3dcb-142">Displaying the Lindsey font</span></span>  
  
<a name="using_the_fonts"></a>   
## <a name="using-the-fonts"></a><span data-ttu-id="a3dcb-143">Używanie czcionek</span><span class="sxs-lookup"><span data-stu-id="a3dcb-143">Using the Fonts</span></span>  
 <span data-ttu-id="a3dcb-144">Istnieją dwa sposoby, w której można czcionek w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3dcb-144">There are two ways that you can use fonts in your application.</span></span> <span data-ttu-id="a3dcb-145">Czcionki można dodać do aplikacji projektu elementy zawartości, które nie są osadzone jako zasoby w zestawie.</span><span class="sxs-lookup"><span data-stu-id="a3dcb-145">You can add fonts to your application as project content items that are not embedded as resources within an assembly.</span></span> <span data-ttu-id="a3dcb-146">Alternatywnie można dodać czcionek w aplikacji jako elementy zasobów projektu, które są osadzone w aplikacji zestawu plików.</span><span class="sxs-lookup"><span data-stu-id="a3dcb-146">Alternatively, you can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="a3dcb-147">Aby uzyskać więcej informacji, zobacz [czcionki tworzenia pakietów z aplikacjami](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md).</span><span class="sxs-lookup"><span data-stu-id="a3dcb-147">For more information, see [Packaging Fonts with Applications](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3dcb-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3dcb-148">See Also</span></span>  
 <xref:System.Windows.Documents.Typography>  
 [<span data-ttu-id="a3dcb-149">Funkcje czcionki OpenType</span><span class="sxs-lookup"><span data-stu-id="a3dcb-149">OpenType Font Features</span></span>](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [<span data-ttu-id="a3dcb-150">Pakowanie czcionek z aplikacjami</span><span class="sxs-lookup"><span data-stu-id="a3dcb-150">Packaging Fonts with Applications</span></span>](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)
