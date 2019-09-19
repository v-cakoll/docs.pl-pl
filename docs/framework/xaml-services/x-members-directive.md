---
title: x:Members — dyrektywa
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: ca42079c1c40a8fb3b1ddfc8f4a6f742768fa9e1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053769"
---
# <a name="xmembers-directive"></a>x:Members — dyrektywa
Zawiera zestaw elementów członkowskich, które są zdefiniowane w znacznikach, które mają zastosowanie do x:Class elementu nadrzędnego.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`className`|Nazwa klasy zapasowej lub klasy częściowej dla produkcji XAML. Zobacz uwagi.|  
|`oneOrMoreMembers`|Co najmniej jeden element obiektu, który reprezentuje definicje elementów członkowskich. Zazwyczaj są to `x:Property` elementy obiektu. Zobacz uwagi.|  
  
## <a name="remarks"></a>Uwagi  
 W implementacji usług XAML .NET Framework nie istnieje Klasa zapasowa ani bazowa implementacja `x:Members`składowej. `x:Members`jest specjalnym elementem członkowskim XAML, który może istnieć jako element członkowski dowolnego typu. W strumieniu `x:Members` węzła XAML jest reprezentowany jako element członkowski o nazwie `Members`z przestrzeni nazw XAML języka XAML. Element członkowski `Members` zawiera ogólną `Member` listę obiektów tylko do odczytu. W typowym znaczniku poszczególne elementy członkowskie są `x:Property` określone jako elementy właściwości. `x:Property`jest bardziej precyzyjnym typem specyficznym dla właściwości typów i można ją przypisać do `x:Member`. Aby uzyskać więcej informacji, zobacz [X:Property dyrektywy](x-property-directive.md).  
  
 Aby obsłużyć praktyczne użycie `x:Members` jako środek do określenia definicji elementów członkowskich w znaczniku, elementy członkowskie muszą być skojarzone z klasą, która może być modyfikowana. Zamierzony model `x:Members` istnieje jako element członkowski typu, który `x:Class`określa. Jednak mechanizm kojarzenia typów i elementów członkowskich lub do tworzenia dynamicznych definicji elementów członkowskich nie jest obsługiwany na poziomie .NET Framework usług XAML. Jest to pozostało do pojedynczych platform, które mają modele aplikacji, które obsługują definicje elementów członkowskich z języka XAML. Zazwyczaj akcje kompilacji programu MSBUILD, które umożliwiają adiustację i kompilowanie kodu XAML, i integrowanie go z kodem związanym lub wytwarzaniem czystych zestawów z języka XAML, które są niezbędne do obsługi tej funkcji.  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>x:Members Windows Workflow Foundation  
 W przypadku Windows Workflow Foundation `x:Members` zawiera elementy członkowskie działania niestandardowego składające się całkowicie z języka XAML lub zdefiniowane w języku XAML dynamiczne elementy członkowskie dla projektanta działań z kodem. `x:Class`musi również być określony w elemencie głównym produkcji XAML. Nie jest to wymagane na poziomie .NET Framework usług XAML, ale jest wymagane, gdy produkcja XAML jest ładowana przez akcje kompilacji MSBUILD, które obsługują działania niestandardowe i Windows Workflow Foundation języka XAML. `x:Members`musi być pierwszym elementem podrzędnym w znacznikach elementu obiektu, który deklaruje `x:Class`.
