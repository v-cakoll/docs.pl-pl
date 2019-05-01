---
title: x:Members — dyrektywa
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: d23e6b459af932e0a6f69309f26a1cce70a9d256
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938895"
---
# <a name="xmembers-directive"></a>x:Members — dyrektywa
Zawiera zestaw elementów członkowskich, które są zdefiniowane w znaczniku, które stosuje się do x: Class elementu nadrzędnego.  
  
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
|`className`|Nazwa klasy zapasowy lub częściowe klasy dla trybu produkcyjnego XAML. Zobacz uwagi.|  
|`oneOrMoreMembers`|Co najmniej jeden element obiektu, które reprezentują definicje elementów członkowskich. Zazwyczaj są to `x:Property` obiektu elementów. Zobacz uwagi.|  
  
## <a name="remarks"></a>Uwagi  
 W implementacji .NET Framework XAML Services nie ma klasy zapasowy lub podstawowej implementacji elementu członkowskiego dla `x:Members`. `x:Members` jest specjalnych elementów członkowskich XAML, która może istnieć jako członka z każdym typem. W postaci strumienia węzłów XAML `x:Members` jest reprezentowany jako składową o nazwie `Members`, z przestrzeni nazw XAML dla języka XAML. Element członkowski `Members` zawiera tylko do odczytu ogólne listę `Member` obiektów. W typowym znaczników poszczególne elementy członkowskie są określane jako `x:Property` elementów właściwości. `x:Property` jest bardziej precyzyjne typ specjalnie dla właściwości typów i można przypisać do `x:Member`. Aby uzyskać więcej informacji, zobacz [dyrektywy x: Property](x-property-directive.md).  
  
 Do obsługi praktyczne wykorzystanie `x:Members` jako środek do określania definicje elementów członkowskich w znaczniku, elementy członkowskie muszą być skojarzone z klasy, który może być modyfikowany. Zamierzony modelu jest fakt, że `x:Members` istnieje jako element członkowski typu, który określa `x:Class`. Mechanizm kojarzenia typów i elementów członkowskich lub do tworzenia definicji dynamicznego elementu członkowskiego nie jest obsługiwane na poziomie usług programu .NET Framework XAML. To pole pozostanie do poszczególnych struktur, które mają modeli aplikacji, które obsługują definicje elementów członkowskich z XAML. Zwykle akcji kompilacji MSBUILD, które znaczników kompilacji XAML, a następnie zintegrować go z kodem lub zestawy czyste z XAML produktu są wymagane do obsługi tej funkcji.  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>x: Members dla programu Windows Workflow Foundation  
 Dla programu Windows Workflow Foundation `x:Members` zawiera elementy członkowskie niestandardowe działanie składające się wyłącznie w XAML lub XAML — definicja dynamiczne elementy członkowskie w Projektancie działanie z kodem. `x:Class` musi być także określona w elemencie głównym produkcji XAML. To nie jest wymagane na poziomie usług programu .NET Framework XAML, ale staje się to wymagane, gdy produkcji XAML jest ładowany przez akcje kompilacji MSBUILD, które obsługują niestandardowych działań i Windows Workflow Foundation XAML ogólnie rzecz biorąc. `x:Members` musi być pierwszy element podrzędny w znaczniku elementu obiekt, który deklaruje `x:Class`.
