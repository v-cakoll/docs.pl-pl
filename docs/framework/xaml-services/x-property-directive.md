---
title: "x:Property — dyrektywa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
caps.latest.revision: "6"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a59eb23ab3ed6ee6adbbebab0859caffd293b24f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="xproperty-directive"></a><span data-ttu-id="d68df-102">x:Property — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="d68df-102">x:Property Directive</span></span>
<span data-ttu-id="d68df-103">Deklaruje właściwością XAML w znaczniku.</span><span class="sxs-lookup"><span data-stu-id="d68df-103">Declares a XAML property in markup.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="d68df-104">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="d68df-104">XAML Object Element Usage</span></span>  
  
```  
<object x:Class="className">  
  <x:Members>  
    <x:Property Name="propertyName" Type="propertyType/>  
    additionalProperties  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="d68df-105">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="d68df-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`className`|<span data-ttu-id="d68df-106">Nazwa klasy zapasowy lub częściowej klasy do produkcji XAML.</span><span class="sxs-lookup"><span data-stu-id="d68df-106">Name of the backing class or partial class for the XAML production.</span></span>|  
|`propertyName`|<span data-ttu-id="d68df-107">Nazwa elementu członkowskiego jest zdefiniowana właściwość.</span><span class="sxs-lookup"><span data-stu-id="d68df-107">Member name of the property being defined.</span></span>|  
|`propertyType`|<span data-ttu-id="d68df-108">Wpisz nazwę (lub inne formy ciąg określonej struktury), który określa typ tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="d68df-108">Type name (or other string form, framework-specific) that specifies the type of this property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d68df-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d68df-109">Remarks</span></span>  
 <span data-ttu-id="d68df-110">W implementacji usług .NET Framework XAML.</span><span class="sxs-lookup"><span data-stu-id="d68df-110">In the .NET Framework XAML Services implementation, .</span></span> <span data-ttu-id="d68df-111">`x:Property`nie ma typu bezpośrednie tworzenie kopii, ale jest obsługiwany przez <xref:System.Windows.Markup.PropertyDefinition> klasy.</span><span class="sxs-lookup"><span data-stu-id="d68df-111">`x:Property` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.PropertyDefinition> class.</span></span> <span data-ttu-id="d68df-112">W strumieniu węzłów XAML `x:Property` element jest reprezentowany jako element członkowski o nazwie `Property`, z przestrzeni nazw XAML języka XAML.</span><span class="sxs-lookup"><span data-stu-id="d68df-112">In a XAML node stream, an `x:Property` element is represented as a member named `Property`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="d68df-113">Element członkowski `Property` przechowywania atrybuty zadeklarowanego znaczników.</span><span class="sxs-lookup"><span data-stu-id="d68df-113">The member `Property` hold attributes as declared by markup.</span></span>  
  
 <span data-ttu-id="d68df-114">Znaczenie `Name` i `Type` nie są przypisane na poziomie usług .NET Framework XAML.</span><span class="sxs-lookup"><span data-stu-id="d68df-114">The meaning of `Name` and `Type` are not assigned at the .NET Framework XAML Services level.</span></span> <span data-ttu-id="d68df-115">Są one przechowywane w początkowej strumień węzłów XAML jako wartości ciągu, należy interpretować później zgodnie z zasadami, które mogą zostać nałożone przez określonych platform.</span><span class="sxs-lookup"><span data-stu-id="d68df-115">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="d68df-116">Znaczenie może być wyrównane do XAML nazwę i typ XAML, co oznacza lub może być tylko prawidłowe w systemie typ zapasowy, w zależności od implementacji.</span><span class="sxs-lookup"><span data-stu-id="d68df-116">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>  
  
 <span data-ttu-id="d68df-117">Do obsługi praktyczne użycie `x:Members` jako środek do określania definicji elementu członkowskiego w znaczniku, elementy członkowskie muszą być skojarzone z klasy, który może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="d68df-117">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="d68df-118">Jest to zamierzone modelu, że `x:Members` istnieje jako element członkowski typu, który określa `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="d68df-118">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="d68df-119">Jednak mechanizm kojarzenia typy i składniki lub do produkcji definicje dynamicznego elementu członkowskiego nie jest obsługiwane na poziomie usług .NET Framework XAML.</span><span class="sxs-lookup"><span data-stu-id="d68df-119">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at the .NET Framework XAML Services level.</span></span> <span data-ttu-id="d68df-120">To pole pozostanie do poszczególnych platform, których modeli aplikacji, które obsługują definicji elementu członkowskiego XAML.</span><span class="sxs-lookup"><span data-stu-id="d68df-120">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="d68df-121">Zwykle akcji kompilacji MSBUILD, które kompilacji znaczników XAML i albo zintegrować ją z kodem lub zestawy czyste z XAML produktu są wymagane do obsługi tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d68df-121">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>  
  
## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="d68df-122">x: Property dla programu Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="d68df-122">x:Property for Windows Workflow Foundation</span></span>  
 <span data-ttu-id="d68df-123">Dla programu Windows Workflow Foundation `x:Property` definiuje elementy niestandardowe działanie składające się wyłącznie w języku XAML lub XAML — definicja dynamicznych elementów członkowskich do projektanta działanie z kodem.</span><span class="sxs-lookup"><span data-stu-id="d68df-123">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="d68df-124">`x:Class`należy określić również dla elementu głównego XAML produkcji.</span><span class="sxs-lookup"><span data-stu-id="d68df-124">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="d68df-125">To nie jest wymagane na poziomie usługi XAML .NET Framework, ale staje się wymóg po załadowaniu przez akcje kompilacji MSBUILD obsługujące niestandardowych działań i Windows Workflow Foundation XAML ogólnie produkcji XAML.</span><span class="sxs-lookup"><span data-stu-id="d68df-125">This is not a requirement at the .NET Framework XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="d68df-126">Windows Workflow Foundation nie używa czysty Nazwa typu XAML jako jego wartość docelowa dla `x:Property` `Type` atrybutu, a zamiast tego używa konwencji, który nie jest udokumentowany tutaj.</span><span class="sxs-lookup"><span data-stu-id="d68df-126">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="d68df-127">Aby uzyskać więcej informacji, zobacz [dynamicznego tworzenia działania](http://msdn.microsoft.com/library/dd807392.aspx).</span><span class="sxs-lookup"><span data-stu-id="d68df-127">For more information, see [Dynamic Activity Creation](http://msdn.microsoft.com/library/dd807392.aspx).</span></span>
