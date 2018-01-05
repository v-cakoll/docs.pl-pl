---
title: "x:Member — dyrektywa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ea04dfe5f3c371acbb388256b0854b0da8f45a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="xmember-directive"></a>x:Member — dyrektywa
Deklaruje element członkowski XAML w znaczników.  
  
## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML  
  
```  
<object x:Class="className">  
  <x:Members>  
    <x:Member Name="propertyName"/>  
    additionalMembers  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`className`|Nazwa klasy zapasowy lub częściowej klasy do produkcji XAML.|  
|`memberName`|Nazwa elementu członkowskiego jest zdefiniowana właściwość.|  
  
## <a name="remarks"></a>Uwagi  
 W implementacji usług .NET Framework XAML. `x:Member`nie ma typu bezpośrednie tworzenie kopii, ale jest obsługiwany przez <xref:System.Windows.Markup.MemberDefinition> klasy. W strumieniu węzłów XAML `x:Member` element jest reprezentowany jako element członkowski o nazwie `Member`, z przestrzeni nazw XAML języka XAML. Element członkowski `Member` przechowuje atrybuty zadeklarowanego znaczników.  
  
 Znaczenie `Name` i `Type` nie są przypisane na poziomie usług .NET Framework XAML. Są one przechowywane w początkowej strumień węzłów XAML jako wartości ciągu, należy interpretować później zgodnie z zasadami, które mogą zostać nałożone przez określonych platform. Znaczenie może być wyrównane do XAML nazwę i typ XAML, co oznacza lub może być tylko prawidłowe w systemie typ zapasowy, w zależności od implementacji.  
  
 Do obsługi praktyczne użycie `x:Members` jako środek do określania definicji elementu członkowskiego w znaczniku, elementy członkowskie muszą być skojarzone z klasy, który może być modyfikowany. Jest to zamierzone modelu, że `x:Members` istnieje jako element członkowski typu, który określa `x:Class`. Jednak mechanizm kojarzenia typy i składniki lub do produkcji definicje dynamicznego elementu członkowskiego nie jest obsługiwane na poziomie usług .NET Framework XAML. To pole pozostanie do poszczególnych platform, których modeli aplikacji, które obsługują definicji elementu członkowskiego XAML. Zwykle akcji kompilacji MSBUILD, które kompilacji znaczników XAML i albo zintegrować ją z kodem lub zestawy czyste z XAML produktu są wymagane do obsługi tej funkcji.  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>x: Property dla programu Windows Workflow Foundation  
 Dla programu Windows Workflow Foundation `x:Property` definiuje elementy niestandardowe działanie składające się wyłącznie w języku XAML lub XAML — definicja dynamicznych elementów członkowskich do projektanta działanie z kodem. `x:Class`należy określić również dla elementu głównego XAML produkcji. To nie jest wymagane na poziomie usługi XAML .NET Framework, ale staje się wymóg po załadowaniu przez akcje kompilacji MSBUILD obsługujące niestandardowych działań i Windows Workflow Foundation XAML ogólnie produkcji XAML. Windows Workflow Foundation nie używa czysty Nazwa typu XAML jako jego wartość docelowa dla `x:Property` `Type` atrybutu, a zamiast tego używa konwencji, który nie jest udokumentowany tutaj. Aby uzyskać więcej informacji, zobacz [dynamicznego tworzenia działania](http://msdn.microsoft.com/library/dd807392.aspx).
