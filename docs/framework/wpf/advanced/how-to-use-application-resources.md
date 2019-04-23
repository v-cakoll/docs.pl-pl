---
title: 'Instrukcje: Używanie zasobów aplikacji'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: 70dff8089c4da70fdc61247a0c604cf7ee85d02b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088207"
---
# <a name="how-to-use-application-resources"></a><span data-ttu-id="e4d9d-102">Instrukcje: Używanie zasobów aplikacji</span><span class="sxs-lookup"><span data-stu-id="e4d9d-102">How to: Use Application Resources</span></span>
<span data-ttu-id="e4d9d-103">W tym przykładzie pokazano, jak korzystać z zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4d9d-103">This example shows how to use application resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4d9d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4d9d-104">Example</span></span>  
 <span data-ttu-id="e4d9d-105">Poniższy przykład pokazuje plik definicji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4d9d-105">The following example shows an application definition file.</span></span> <span data-ttu-id="e4d9d-106">Plik definicji aplikacji definiuje sekcję zasobów (wartość <xref:System.Windows.Application.Resources%2A> właściwości).</span><span class="sxs-lookup"><span data-stu-id="e4d9d-106">The application definition file defines a resource section (a value for the <xref:System.Windows.Application.Resources%2A> property).</span></span> <span data-ttu-id="e4d9d-107">Zasoby zdefiniowane na poziomie aplikacji jest możliwy przez wszystkich stron, które są częścią aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4d9d-107">Resources defined at the application level can be accessed by all other pages that are part of the application.</span></span> <span data-ttu-id="e4d9d-108">W tym przypadku zasób jest zadeklarowana stylu.</span><span class="sxs-lookup"><span data-stu-id="e4d9d-108">In this case, the resource is a declared style.</span></span> <span data-ttu-id="e4d9d-109">Ponieważ pełną stylu, który zawiera szablon kontrolki może być długi, w tym przykładzie pomija szablonu kontrolki, która jest zdefiniowana w <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> metoda ustawiająca właściwości stylu.</span><span class="sxs-lookup"><span data-stu-id="e4d9d-109">Because a complete style that includes a control template can be lengthy, this example omits the control template that is defined within the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property setter of the style.</span></span>  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 <span data-ttu-id="e4d9d-110">W poniższym przykładzie przedstawiono [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony, który odwołuje się do zasobu dodatku poziomu aplikacji, zdefiniowanego w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e4d9d-110">The following example shows a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page that references the application-level resource that the previous example defined.</span></span> <span data-ttu-id="e4d9d-111">Zasób jest wywoływany przy użyciu [staticresource — rozszerzenie znaczników](staticresource-markup-extension.md) , który określa klucz unikatowy zasób dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="e4d9d-111">The resource is referenced by using a     [StaticResource Markup Extension](staticresource-markup-extension.md) that specifies the unique resource key for the requested resource.</span></span> <span data-ttu-id="e4d9d-112">Żaden zasób z kluczem "GelButton" znajduje się na bieżącej stronie, aby zakres wyszukiwania zasobów dla żądanego zasobu kontynuuje poza bieżącą stronę i do określonych zasobów na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4d9d-112">No resource with key of "GelButton" is found in the current page, so the resource lookup scope for the requested resource continues beyond the current page and into the defined application-level resources.</span></span>  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a><span data-ttu-id="e4d9d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4d9d-113">See also</span></span>

- [<span data-ttu-id="e4d9d-114">Zasoby XAML</span><span class="sxs-lookup"><span data-stu-id="e4d9d-114">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="e4d9d-115">Zarządzanie aplikacjami — omówienie</span><span class="sxs-lookup"><span data-stu-id="e4d9d-115">Application Management Overview</span></span>](../app-development/application-management-overview.md)
- [<span data-ttu-id="e4d9d-116">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="e4d9d-116">How-to Topics</span></span>](resources-how-to-topics.md)
