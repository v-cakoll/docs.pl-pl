---
title: 'Instrukcje: Używanie zasobów w lokalizowalnych aplikacjach'
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: 3634bb72cbacfb02b0a1230a47a1664cb8ce5009
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238459"
---
# <a name="how-to-use-resources-in-localizable-applications"></a><span data-ttu-id="8819e-102">Instrukcje: Używanie zasobów w lokalizowalnych aplikacjach</span><span class="sxs-lookup"><span data-stu-id="8819e-102">How to: Use Resources in Localizable Applications</span></span>
<span data-ttu-id="8819e-103">Lokalizowanie oznacza dostosowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do różnych kultur.</span><span class="sxs-lookup"><span data-stu-id="8819e-103">Localization means to adapt a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to different cultures.</span></span> <span data-ttu-id="8819e-104">Aby to zrobić, tekstu, takie jak tytuły, napisy, elementów pola listy i tak dalej mieć ma zostać poddany translacji.</span><span class="sxs-lookup"><span data-stu-id="8819e-104">To do this, text such as titles, captions, list box items and so forth have to be translated.</span></span> <span data-ttu-id="8819e-105">Aby ułatwić tłumaczenia elementów, które ma zostać poddany translacji są zbierane w plików zasobów.</span><span class="sxs-lookup"><span data-stu-id="8819e-105">To make translation easier the items to be translated are collected into resource files.</span></span> <span data-ttu-id="8819e-106">Zobacz [Lokalizuj aplikację](how-to-localize-an-application.md) informacji na temat tworzenia pliku zasobów dla lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="8819e-106">See [Localize an Application](how-to-localize-an-application.md) for information on how to create a resource file for localization.</span></span> <span data-ttu-id="8819e-107">Zapewnienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji możliwych do zlokalizowania, umożliwiające tworzenie lokalizowalne zasoby w ramach zestawu zasobów.</span><span class="sxs-lookup"><span data-stu-id="8819e-107">To make a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="8819e-108">Zestaw zasobów jest zlokalizowany w różnych językach i związane z kodem wykorzystuje interfejs API zarządzania zasobami można załadować.</span><span class="sxs-lookup"><span data-stu-id="8819e-108">The resource assembly is localized into different languages, and the code-behind uses resource management API to load.</span></span> <span data-ttu-id="8819e-109">Jeden z plików wymaganych do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji to plik projektu (plików Proj).</span><span class="sxs-lookup"><span data-stu-id="8819e-109">One of the files required for a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application is a project file (.proj).</span></span> <span data-ttu-id="8819e-110">Wszystkie zasoby, których używasz w aplikacji powinny być objęte w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="8819e-110">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="8819e-111">Poniższy przykład kodu pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="8819e-111">The following code example shows this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8819e-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="8819e-112">Example</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 <span data-ttu-id="8819e-113">Aby korzystać z zasobów w aplikacji, wystąpienia <xref:System.Resources.ResourceManager> i załaduj zasób, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="8819e-113">To use a resource in your application, you instantiate <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="8819e-114">Poniżej pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="8819e-114">The following demonstrates how to do this.</span></span>  
  
 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
