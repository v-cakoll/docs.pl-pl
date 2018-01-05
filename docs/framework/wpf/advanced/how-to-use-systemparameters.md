---
title: 'Porady: korzystanie z SystemParameters'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ec333fbc30374ff6f8e2e7674ab332644ff7aad0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-systemparameters"></a><span data-ttu-id="d5778-102">Porady: korzystanie z SystemParameters</span><span class="sxs-lookup"><span data-stu-id="d5778-102">How to: Use SystemParameters</span></span>
<span data-ttu-id="d5778-103">W tym przykładzie pokazano, jak uzyskać dostęp i użyj właściwości <xref:System.Windows.SystemParameters> do nadawania stylu lub dostosowywanie przycisku.</span><span class="sxs-lookup"><span data-stu-id="d5778-103">This example shows how to access and use the properties of <xref:System.Windows.SystemParameters> in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5778-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5778-104">Example</span></span>  
 <span data-ttu-id="d5778-105">Zasoby systemowe ujawnia niektóre ustawienia systemu zasobów, aby pomóc tworzyć elementy wizualne, które są zgodne z ustawieniami systemu.</span><span class="sxs-lookup"><span data-stu-id="d5778-105">System resources expose several system based settings as resources in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="d5778-106"><xref:System.Windows.SystemParameters>jest klasa, która zawiera właściwości wartość parametru systemu i klucze zasobów, które powiązać wartości.</span><span class="sxs-lookup"><span data-stu-id="d5778-106"><xref:System.Windows.SystemParameters> is a class that contains both system parameter value properties, and resource keys that bind to the values.</span></span> <span data-ttu-id="d5778-107">Na przykład <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> jest <xref:System.Windows.SystemParameters> wartość właściwości i <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> jest odpowiedni klucz zasobów.</span><span class="sxs-lookup"><span data-stu-id="d5778-107">For example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> is a <xref:System.Windows.SystemParameters> property value and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> is the corresponding resource key.</span></span>  
  
 <span data-ttu-id="d5778-108">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można użyć elementów członkowskich <xref:System.Windows.SystemParameters> jako użycie statycznej właściwości lub odwołania do zasobów dynamicznych (o wartości właściwości statycznej jako klucz).</span><span class="sxs-lookup"><span data-stu-id="d5778-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemParameters> as either a static property usage, or a dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="d5778-109">Użyj odwołania zasobu dynamicznego, jeśli wartość system na podstawie automatycznie aktualizowane podczas aplikacji działa; w przeciwnym razie użyj odwołanie statyczne.</span><span class="sxs-lookup"><span data-stu-id="d5778-109">Use a dynamic resource reference if you want the system based value to update automatically while the application runs; otherwise, use a static reference.</span></span> <span data-ttu-id="d5778-110">Klucze zasobów przedrostkiem `Key` dołączonym do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="d5778-110">Resource keys have the suffix `Key` appended to the property name.</span></span>  
  
 <span data-ttu-id="d5778-111">Poniższy przykład przedstawia sposób dostępu i statyczne wartości można używać <xref:System.Windows.SystemParameters> stylu lub dostosowanie przycisku.</span><span class="sxs-lookup"><span data-stu-id="d5778-111">The following example shows how to access and use the static values of <xref:System.Windows.SystemParameters> to style or customize a button.</span></span> <span data-ttu-id="d5778-112">W tym przykładzie znaczników rozmiar przycisku przez zastosowanie <xref:System.Windows.SystemParameters> wartości do przycisku.</span><span class="sxs-lookup"><span data-stu-id="d5778-112">This markup example sizes a button by applying <xref:System.Windows.SystemParameters> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 <span data-ttu-id="d5778-113">Aby użyć wartości <xref:System.Windows.SystemParameters> w kodzie, nie masz do użycia statycznego odwołania lub odwołania do zasobów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="d5778-113">To use the values of <xref:System.Windows.SystemParameters> in code, you do not have to use either static references or dynamic resource references.</span></span> <span data-ttu-id="d5778-114">Użyj wartości <xref:System.Windows.SystemParameters> klasy.</span><span class="sxs-lookup"><span data-stu-id="d5778-114">Instead, use the values of the <xref:System.Windows.SystemParameters> class.</span></span> <span data-ttu-id="d5778-115">Mimo że właściwości niekluczowe pozornie są zdefiniowane jako właściwości statyczne, zachowanie środowiska uruchomieniowego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako hostowanej przez system będzie obliczyć ponownie właściwości w czasie rzeczywistym, a zostanie prawidłowo konta użytkownika driven zmiany wartości systemu.</span><span class="sxs-lookup"><span data-stu-id="d5778-115">Although the non-key properties are apparently defined as static properties, the runtime behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in realtime, and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="d5778-116">Poniższy przykład przedstawia sposób ustawić szerokość i wysokość przycisku przy użyciu <xref:System.Windows.SystemParameters> wartości.</span><span class="sxs-lookup"><span data-stu-id="d5778-116">The following example shows how to set the width and height of a button by using <xref:System.Windows.SystemParameters> values.</span></span>  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="d5778-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5778-117">See Also</span></span>  
 <xref:System.Windows.SystemParameters>  
 [<span data-ttu-id="d5778-118">Malowanie obszaru pędzlem systemowym</span><span class="sxs-lookup"><span data-stu-id="d5778-118">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="d5778-119">Używanie elementu SystemFonts</span><span class="sxs-lookup"><span data-stu-id="d5778-119">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [<span data-ttu-id="d5778-120">Używanie kluczy parametrów systemowych</span><span class="sxs-lookup"><span data-stu-id="d5778-120">Use System Parameters Keys</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)  
 [<span data-ttu-id="d5778-121">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="d5778-121">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
