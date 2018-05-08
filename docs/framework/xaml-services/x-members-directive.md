---
title: x:Members — dyrektywa
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: 2c273fce1f15d9a5af72bc3f5a530d3c26dfc77e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xmembers-directive"></a>x:Members — dyrektywa
Zawiera zestaw elementów członkowskich, które są zdefiniowane w znaczniku, które dotyczą x: Class elementu nadrzędnego.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`className`|Nazwa klasy zapasowy lub częściowej klasy do produkcji XAML. Zobacz uwagi.|  
|`oneOrMoreMembers`|Jeden lub więcej elementów obiektu, które reprezentują definicji elementu członkowskiego. Zazwyczaj są to `x:Property` obiekt elementów. Zobacz uwagi.|  
  
## <a name="remarks"></a>Uwagi  
 W implementacji usług .NET Framework XAML nie istnieje klasa zapasowy lub implementacja elementu członkowskiego dla `x:Members`. `x:Members` to specjalne Członkowskiego XAML, który może istnieć jako elementu członkowskiego dla dowolnego typu. W strumieniu węzłów XAML `x:Members` jest reprezentowany jako element członkowski o nazwie `Members`, z przestrzeni nazw XAML języka XAML. Element członkowski `Members` zawiera tylko do odczytu ogólnego listę `Member` obiektów. W typowej znaczników poszczególne elementy są określane jako `x:Property` elementów właściwości. `x:Property` jest typem dokładniejsze specjalnie z myślą o właściwości typów i można przypisać do `x:Member`. Aby uzyskać więcej informacji, zobacz [dyrektywy x: Property](../../../docs/framework/xaml-services/x-property-directive.md).  
  
 Do obsługi praktyczne użycie `x:Members` jako środek do określania definicji elementu członkowskiego w znaczniku, elementy członkowskie muszą być skojarzone z klasy, który może być modyfikowany. Jest to zamierzone modelu, że `x:Members` istnieje jako element członkowski typu, który określa `x:Class`. Jednak mechanizm kojarzenia typy i składniki lub do produkcji definicje dynamicznego elementu członkowskiego nie jest obsługiwane na poziomie usług .NET Framework XAML. To pole pozostanie do poszczególnych platform, których modeli aplikacji, które obsługują definicji elementu członkowskiego XAML. Zwykle akcji kompilacji MSBUILD, które kompilacji znaczników XAML i albo zintegrować ją z kodem lub zestawy czyste z XAML produktu są wymagane do obsługi tej funkcji.  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>x: Members dla programu Windows Workflow Foundation  
 Dla programu Windows Workflow Foundation `x:Members` zawiera członków niestandardowe działanie składające się wyłącznie w języku XAML lub XAML — definicja dynamicznych elementów członkowskich do projektanta działanie z kodem. `x:Class` należy określić również dla elementu głównego XAML produkcji. To nie jest wymagane na poziomie usługi XAML .NET Framework, ale staje się wymóg po załadowaniu przez akcje kompilacji MSBUILD obsługujące niestandardowych działań i Windows Workflow Foundation XAML ogólnie produkcji XAML. `x:Members` musi być pierwszym elementem podrzędnym w znaczniku elementu obiektu, który deklaruje `x:Class`.
