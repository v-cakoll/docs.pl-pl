---
title: "x:Members — dyrektywa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e76f539e713f3d21751de18c86cc2dcebf99f570
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="xmembers-directive"></a><span data-ttu-id="1004d-102">x:Members — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="1004d-102">x:Members Directive</span></span>
<span data-ttu-id="1004d-103">Zawiera zestaw elementów członkowskich, które są zdefiniowane w znaczniku, które dotyczą x: Class elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="1004d-103">Holds a set of members that are defined in markup, which apply to the x:Class of the parent element.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="1004d-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="1004d-104">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="1004d-105">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="1004d-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`className`|<span data-ttu-id="1004d-106">Nazwa klasy zapasowy lub częściowej klasy do produkcji XAML.</span><span class="sxs-lookup"><span data-stu-id="1004d-106">Name of the backing class or partial class for the XAML production.</span></span> <span data-ttu-id="1004d-107">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="1004d-107">See Remarks.</span></span>|  
|`oneOrMoreMembers`|<span data-ttu-id="1004d-108">Jeden lub więcej elementów obiektu, które reprezentują definicji elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1004d-108">One or more object elements that represent member definitions.</span></span> <span data-ttu-id="1004d-109">Zazwyczaj są to `x:Property` obiekt elementów.</span><span class="sxs-lookup"><span data-stu-id="1004d-109">Typically, these are `x:Property` object elements.</span></span> <span data-ttu-id="1004d-110">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="1004d-110">See Remarks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1004d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1004d-111">Remarks</span></span>  
 <span data-ttu-id="1004d-112">W implementacji usług .NET Framework XAML nie istnieje klasa zapasowy lub implementacja elementu członkowskiego dla `x:Members`.</span><span class="sxs-lookup"><span data-stu-id="1004d-112">In the .NET Framework XAML Services implementation, there is no backing class or underlying member implementation for `x:Members`.</span></span> <span data-ttu-id="1004d-113">`x:Members`to specjalne Członkowskiego XAML, który może istnieć jako elementu członkowskiego dla dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="1004d-113">`x:Members` is a special XAML member that can exist as a member on any type.</span></span> <span data-ttu-id="1004d-114">W strumieniu węzłów XAML `x:Members` jest reprezentowany jako element członkowski o nazwie `Members`, z przestrzeni nazw XAML języka XAML.</span><span class="sxs-lookup"><span data-stu-id="1004d-114">In a XAML node stream, `x:Members` is represented as a member named `Members`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="1004d-115">Element członkowski `Members` zawiera tylko do odczytu ogólnego listę `Member` obiektów.</span><span class="sxs-lookup"><span data-stu-id="1004d-115">The member `Members` contains a read-only generic list of `Member` objects.</span></span> <span data-ttu-id="1004d-116">W typowej znaczników poszczególne elementy są określane jako `x:Property` elementów właściwości.</span><span class="sxs-lookup"><span data-stu-id="1004d-116">In typical markup the individual members are specified as `x:Property` property elements.</span></span> <span data-ttu-id="1004d-117">`x:Property`jest typem dokładniejsze specjalnie z myślą o właściwości typów i można przypisać do `x:Member`.</span><span class="sxs-lookup"><span data-stu-id="1004d-117">`x:Property` is a more precise type specifically for properties of types and is assignable to `x:Member`.</span></span> <span data-ttu-id="1004d-118">Aby uzyskać więcej informacji, zobacz [dyrektywy x: Property](../../../docs/framework/xaml-services/x-property-directive.md).</span><span class="sxs-lookup"><span data-stu-id="1004d-118">For more information, see [x:Property Directive](../../../docs/framework/xaml-services/x-property-directive.md).</span></span>  
  
 <span data-ttu-id="1004d-119">Do obsługi praktyczne użycie `x:Members` jako środek do określania definicji elementu członkowskiego w znaczniku, elementy członkowskie muszą być skojarzone z klasy, który może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="1004d-119">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="1004d-120">Jest to zamierzone modelu, że `x:Members` istnieje jako element członkowski typu, który określa `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="1004d-120">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="1004d-121">Jednak mechanizm kojarzenia typy i składniki lub do produkcji definicje dynamicznego elementu członkowskiego nie jest obsługiwane na poziomie usług .NET Framework XAML.</span><span class="sxs-lookup"><span data-stu-id="1004d-121">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at the .NET Framework XAML Services level.</span></span> <span data-ttu-id="1004d-122">To pole pozostanie do poszczególnych platform, których modeli aplikacji, które obsługują definicji elementu członkowskiego XAML.</span><span class="sxs-lookup"><span data-stu-id="1004d-122">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="1004d-123">Zwykle akcji kompilacji MSBUILD, które kompilacji znaczników XAML i albo zintegrować ją z kodem lub zestawy czyste z XAML produktu są wymagane do obsługi tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="1004d-123">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>  
  
## <a name="xmembers-for-windows-workflow-foundation"></a><span data-ttu-id="1004d-124">x: Members dla programu Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="1004d-124">x:Members for Windows Workflow Foundation</span></span>  
 <span data-ttu-id="1004d-125">Dla programu Windows Workflow Foundation `x:Members` zawiera członków niestandardowe działanie składające się wyłącznie w języku XAML lub XAML — definicja dynamicznych elementów członkowskich do projektanta działanie z kodem.</span><span class="sxs-lookup"><span data-stu-id="1004d-125">For Windows Workflow Foundation, `x:Members` contains the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="1004d-126">`x:Class`należy określić również dla elementu głównego XAML produkcji.</span><span class="sxs-lookup"><span data-stu-id="1004d-126">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="1004d-127">To nie jest wymagane na poziomie usługi XAML .NET Framework, ale staje się wymóg po załadowaniu przez akcje kompilacji MSBUILD obsługujące niestandardowych działań i Windows Workflow Foundation XAML ogólnie produkcji XAML.</span><span class="sxs-lookup"><span data-stu-id="1004d-127">This is not a requirement at the .NET Framework XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="1004d-128">`x:Members`musi być pierwszym elementem podrzędnym w znaczniku elementu obiektu, który deklaruje `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="1004d-128">`x:Members` must be the first child element in markup of the object element that declares the `x:Class`.</span></span>
