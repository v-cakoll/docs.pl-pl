---
title: Jak użyć zasobów aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: e4114466fa8016f8e31100d7a37038b0abfdccca
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460270"
---
# <a name="how-to-use-application-resources"></a><span data-ttu-id="bf80a-102">Jak użyć zasobów aplikacji</span><span class="sxs-lookup"><span data-stu-id="bf80a-102">How to: Use Application Resources</span></span>
<span data-ttu-id="bf80a-103">Ten przykład pokazuje, jak używać zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf80a-103">This example shows how to use application resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf80a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="bf80a-104">Example</span></span>  
 <span data-ttu-id="bf80a-105">Poniższy przykład przedstawia plik definicji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf80a-105">The following example shows an application definition file.</span></span> <span data-ttu-id="bf80a-106">Plik definicji aplikacji definiuje sekcję zasobów (wartość właściwości <xref:System.Windows.Application.Resources%2A>).</span><span class="sxs-lookup"><span data-stu-id="bf80a-106">The application definition file defines a resource section (a value for the <xref:System.Windows.Application.Resources%2A> property).</span></span> <span data-ttu-id="bf80a-107">Do zasobów zdefiniowanych na poziomie aplikacji mogą być dostępne wszystkie inne strony, które są częścią aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf80a-107">Resources defined at the application level can be accessed by all other pages that are part of the application.</span></span> <span data-ttu-id="bf80a-108">W takim przypadku zasób jest zadeklarowanym stylem.</span><span class="sxs-lookup"><span data-stu-id="bf80a-108">In this case, the resource is a declared style.</span></span> <span data-ttu-id="bf80a-109">Ponieważ pełny styl, który zawiera szablon kontrolki może być długi, ten przykład pomija szablon formantu, który jest zdefiniowany w <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> właściwości setter stylu.</span><span class="sxs-lookup"><span data-stu-id="bf80a-109">Because a complete style that includes a control template can be lengthy, this example omits the control template that is defined within the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property setter of the style.</span></span>  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 <span data-ttu-id="bf80a-110">W poniższym przykładzie przedstawiono stronę [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], która odwołuje się do zasobu na poziomie aplikacji, który został zdefiniowany w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bf80a-110">The following example shows a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page that references the application-level resource that the previous example defined.</span></span> <span data-ttu-id="bf80a-111">Zasób jest przywoływany przy użyciu [rozszerzenia znacznika StaticResource](staticresource-markup-extension.md) , które określa unikatowy klucz zasobu dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="bf80a-111">The resource is referenced by using a     [StaticResource Markup Extension](staticresource-markup-extension.md) that specifies the unique resource key for the requested resource.</span></span> <span data-ttu-id="bf80a-112">Na bieżącej stronie nie znaleziono żadnego zasobu z kluczem "GelButton", więc zakres wyszukiwania zasobów dla żądanego zasobu będzie przekroczyć bieżącą stronę i zdefiniowane zasoby na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf80a-112">No resource with key of "GelButton" is found in the current page, so the resource lookup scope for the requested resource continues beyond the current page and into the defined application-level resources.</span></span>  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a><span data-ttu-id="bf80a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf80a-113">See also</span></span>

- [<span data-ttu-id="bf80a-114">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="bf80a-114">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="bf80a-115">Zarządzanie aplikacjami — omówienie</span><span class="sxs-lookup"><span data-stu-id="bf80a-115">Application Management Overview</span></span>](../app-development/application-management-overview.md)
- [<span data-ttu-id="bf80a-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="bf80a-116">How-to Topics</span></span>](resources-how-to-topics.md)
