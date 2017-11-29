---
title: "Jak użyć zasobów w zlokalizowanych aplikacjach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d803989292e2fc6b0945c397df5ce32d318147fc
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-resources-in-localizable-applications"></a><span data-ttu-id="04d53-102">Jak użyć zasobów w zlokalizowanych aplikacjach</span><span class="sxs-lookup"><span data-stu-id="04d53-102">How to: Use Resources in Localizable Applications</span></span>
<span data-ttu-id="04d53-103">Lokalizowanie oznacza dostosowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do innych kultur.</span><span class="sxs-lookup"><span data-stu-id="04d53-103">Localization means to adapt a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to different cultures.</span></span> <span data-ttu-id="04d53-104">W tym celu tekstu na przykład tytułów, podpisów, elementy listy i tak dalej ma ma zostać poddany translacji.</span><span class="sxs-lookup"><span data-stu-id="04d53-104">To do this, text such as titles, captions, list box items and so forth have to be translated.</span></span> <span data-ttu-id="04d53-105">Aby ułatwić tłumaczenia elementów, które ma zostać poddany translacji są zbierane w pliki zasobów.</span><span class="sxs-lookup"><span data-stu-id="04d53-105">To make translation easier the items to be translated are collected into resource files.</span></span> <span data-ttu-id="04d53-106">Zobacz [lokalizowanie aplikacji](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md) informacji na temat sposobu tworzenia pliku zasobu do lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="04d53-106">See [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md) for information on how to create a resource file for localization.</span></span> <span data-ttu-id="04d53-107">Aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji Lokalizowalny deweloperzy potrzebne do tworzenia zlokalizowania zasobów w ramach zestawu zasobów.</span><span class="sxs-lookup"><span data-stu-id="04d53-107">To make a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="04d53-108">Zestaw zasobów jest zlokalizowane w różnych językach, a kodem używa zarządzanie zasobami [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] do załadowania.</span><span class="sxs-lookup"><span data-stu-id="04d53-108">The resource assembly is localized into different languages, and the code-behind uses resource management [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] to load.</span></span> <span data-ttu-id="04d53-109">Jeden z plików wymaganych do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji jest plikiem projektu (.proj).</span><span class="sxs-lookup"><span data-stu-id="04d53-109">One of the files required for a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application is a project file (.proj).</span></span> <span data-ttu-id="04d53-110">W pliku projektu powinien znajdować się wszystkie zasoby, które są używane w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="04d53-110">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="04d53-111">Poniższy przykład kodu pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="04d53-111">The following code example shows this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04d53-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="04d53-112">Example</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 <span data-ttu-id="04d53-113">Aby użyć zasób w aplikacji, można utworzyć wystąpienia <xref:System.Resources.ResourceManager> i załadować zasobu, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="04d53-113">To use a resource in your application, you instantiate <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="04d53-114">Poniżej pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="04d53-114">The following demonstrates how to do this.</span></span>  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
