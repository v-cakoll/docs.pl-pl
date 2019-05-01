---
title: 'Instrukcje: Używanie elementu SystemParameters'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
ms.openlocfilehash: 344fb54b48bcbf188b36a29d8205c21deff713c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001458"
---
# <a name="how-to-use-systemparameters"></a><span data-ttu-id="8e3c4-102">Instrukcje: Używanie elementu SystemParameters</span><span class="sxs-lookup"><span data-stu-id="8e3c4-102">How to: Use SystemParameters</span></span>
<span data-ttu-id="8e3c4-103">W tym przykładzie pokazano, jak uzyskać dostęp do właściwości <xref:System.Windows.SystemParameters> do nadawania stylu lub dostosować przycisku.</span><span class="sxs-lookup"><span data-stu-id="8e3c4-103">This example shows how to access and use the properties of <xref:System.Windows.SystemParameters> in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e3c4-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e3c4-104">Example</span></span>  
 <span data-ttu-id="8e3c4-105">Zasoby systemowe uwidocznić kilka ustawień systemu na podstawie zasobów, aby ułatwić tworzenie wizualizacji, które są zgodne z ustawieniami systemu.</span><span class="sxs-lookup"><span data-stu-id="8e3c4-105">System resources expose several system based settings as resources in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="8e3c4-106"><xref:System.Windows.SystemParameters> jest klasą, który zawiera właściwości wartość parametru systemu i klucze zasobów, które wartości należy powiązać.</span><span class="sxs-lookup"><span data-stu-id="8e3c4-106"><xref:System.Windows.SystemParameters> is a class that contains both system parameter value properties, and resource keys that bind to the values.</span></span> <span data-ttu-id="8e3c4-107">Na przykład <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> jest <xref:System.Windows.SystemParameters> wartości właściwości i <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> jest odpowiedni klucz zasobu.</span><span class="sxs-lookup"><span data-stu-id="8e3c4-107">For example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> is a <xref:System.Windows.SystemParameters> property value and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> is the corresponding resource key.</span></span>  
  
 <span data-ttu-id="8e3c4-108">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można użyć elementów członkowskich <xref:System.Windows.SystemParameters> jako użycia właściwość statyczna lub odwołania do zasobu dynamicznego (wartością właściwości statycznej jako klucz).</span><span class="sxs-lookup"><span data-stu-id="8e3c4-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemParameters> as either a static property usage, or a dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="8e3c4-109">Użyj odwołania zasób dynamiczny, jeśli chcesz, aby wartość systemu opartego na automatyczne aktualizowanie podczas jej uruchomieniu; w przeciwnym razie użyj odwołania statycznego.</span><span class="sxs-lookup"><span data-stu-id="8e3c4-109">Use a dynamic resource reference if you want the system based value to update automatically while the application runs; otherwise, use a static reference.</span></span> <span data-ttu-id="8e3c4-110">Klucze zasobu mają ten sufiks `Key` dołączana do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="8e3c4-110">Resource keys have the suffix `Key` appended to the property name.</span></span>  
  
 <span data-ttu-id="8e3c4-111">Poniższy przykład pokazuje, jak uzyskać dostęp do wartości statycznej <xref:System.Windows.SystemParameters> do nadawania stylu i dostosowywania przycisku.</span><span class="sxs-lookup"><span data-stu-id="8e3c4-111">The following example shows how to access and use the static values of <xref:System.Windows.SystemParameters> to style or customize a button.</span></span> <span data-ttu-id="8e3c4-112">W tym przykładzie znaczników przycisku o rozmiarach, stosując <xref:System.Windows.SystemParameters> wartości do przycisku.</span><span class="sxs-lookup"><span data-stu-id="8e3c4-112">This markup example sizes a button by applying <xref:System.Windows.SystemParameters> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 <span data-ttu-id="8e3c4-113">Aby użyć wartości <xref:System.Windows.SystemParameters> w kodzie, nie trzeba używać odwołań statycznych lub dynamicznych zasobów odwołań.</span><span class="sxs-lookup"><span data-stu-id="8e3c4-113">To use the values of <xref:System.Windows.SystemParameters> in code, you do not have to use either static references or dynamic resource references.</span></span> <span data-ttu-id="8e3c4-114">Zamiast tego należy użyć wartości <xref:System.Windows.SystemParameters> klasy.</span><span class="sxs-lookup"><span data-stu-id="8e3c4-114">Instead, use the values of the <xref:System.Windows.SystemParameters> class.</span></span> <span data-ttu-id="8e3c4-115">Mimo że właściwości klucza najwyraźniej są definiowane jako właściwości statycznej, zachowanie środowiska uruchomieniowego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako hostowanej przez system spowoduje to ponowne ocenienie właściwości w czasie rzeczywistym i zostanie prawidłowo konto oparte na użytkownika zmiany wartości systemu.</span><span class="sxs-lookup"><span data-stu-id="8e3c4-115">Although the non-key properties are apparently defined as static properties, the runtime behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in realtime, and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="8e3c4-116">Poniższy przykład pokazuje, jak ustawić szerokość i wysokość przycisku przy użyciu <xref:System.Windows.SystemParameters> wartości.</span><span class="sxs-lookup"><span data-stu-id="8e3c4-116">The following example shows how to set the width and height of a button by using <xref:System.Windows.SystemParameters> values.</span></span>  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="8e3c4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e3c4-117">See also</span></span>

- <xref:System.Windows.SystemParameters>
- [<span data-ttu-id="8e3c4-118">Malowanie obszaru pędzlem systemowym</span><span class="sxs-lookup"><span data-stu-id="8e3c4-118">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="8e3c4-119">Używanie elementu SystemFonts</span><span class="sxs-lookup"><span data-stu-id="8e3c4-119">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
- [<span data-ttu-id="8e3c4-120">Używanie kluczy parametrów systemowych</span><span class="sxs-lookup"><span data-stu-id="8e3c4-120">Use System Parameters Keys</span></span>](how-to-use-system-parameters-keys.md)
- [<span data-ttu-id="8e3c4-121">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="8e3c4-121">How-to Topics</span></span>](resources-how-to-topics.md)
