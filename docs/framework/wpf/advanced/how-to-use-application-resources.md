---
title: "Jak użyć zasobów aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bac1fa1576e684a4b10f00310c08e4e7101a5df0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-application-resources"></a><span data-ttu-id="a0bd2-102">Jak użyć zasobów aplikacji</span><span class="sxs-lookup"><span data-stu-id="a0bd2-102">How to: Use Application Resources</span></span>
<span data-ttu-id="a0bd2-103">Ten przykład przedstawia sposób użycia zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a0bd2-103">This example shows how to use application resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0bd2-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0bd2-104">Example</span></span>  
 <span data-ttu-id="a0bd2-105">W poniższym przykładzie przedstawiono plik definicji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a0bd2-105">The following example shows an application definition file.</span></span> <span data-ttu-id="a0bd2-106">Plik definicji aplikacji definiuje sekcji zasobów (wartość <xref:System.Windows.Application.Resources%2A> właściwości).</span><span class="sxs-lookup"><span data-stu-id="a0bd2-106">The application definition file defines a resource section (a value for the <xref:System.Windows.Application.Resources%2A> property).</span></span> <span data-ttu-id="a0bd2-107">Przez wszystkie strony, które są częścią aplikacji są dostępne zasoby zdefiniowane na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a0bd2-107">Resources defined at the application level can be accessed by all other pages that are part of the application.</span></span> <span data-ttu-id="a0bd2-108">W takim przypadku zasób jest zadeklarowane stylu.</span><span class="sxs-lookup"><span data-stu-id="a0bd2-108">In this case, the resource is a declared style.</span></span> <span data-ttu-id="a0bd2-109">Ponieważ pełną stylu, który zawiera szablon formantu może być długi, w tym przykładzie pomija kontroli szablonu, który jest definiowany w <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> metoda ustawiająca właściwości stylu.</span><span class="sxs-lookup"><span data-stu-id="a0bd2-109">Because a complete style that includes a control template can be lengthy, this example omits the control template that is defined within the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property setter of the style.</span></span>  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 <span data-ttu-id="a0bd2-110">W poniższym przykładzie przedstawiono [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony, który odwołuje się do zasobu poziomie aplikacji, zdefiniowanego w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a0bd2-110">The following example shows a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page that references the application-level resource that the previous example defined.</span></span> <span data-ttu-id="a0bd2-111">Zasób jest wywoływany przy użyciu [StaticResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) , który określa klucz unikatowy zasób do żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="a0bd2-111">The resource is referenced by using a     [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) that specifies the unique resource key for the requested resource.</span></span> <span data-ttu-id="a0bd2-112">Żaden zasób z kluczem "GelButton" znajduje się w bieżącej strony, dlatego zakres wyszukiwania zasobów dla żądanego zasobu nadal poza bieżącą stronę i do określonych zasobów na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a0bd2-112">No resource with key of "GelButton" is found in the current page, so the resource lookup scope for the requested resource continues beyond the current page and into the defined application-level resources.</span></span>  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a><span data-ttu-id="a0bd2-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0bd2-113">See Also</span></span>  
 [<span data-ttu-id="a0bd2-114">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="a0bd2-114">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="a0bd2-115">Zarządzanie aplikacjami — omówienie</span><span class="sxs-lookup"><span data-stu-id="a0bd2-115">Application Management Overview</span></span>](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [<span data-ttu-id="a0bd2-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="a0bd2-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
