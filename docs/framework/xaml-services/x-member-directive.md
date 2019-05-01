---
title: x:Member — dyrektywa
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: 66d34ad6bc5b6bb98eba6219130035dc413b486f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61951219"
---
# <a name="xmember-directive"></a>x:Member — dyrektywa
Deklaruje element członkowski XAML, w znacznikach.  
  
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
|`className`|Nazwa klasy zapasowy lub częściowe klasy dla trybu produkcyjnego XAML.|  
|`memberName`|Nazwa elementu członkowskiego jest zdefiniowana właściwość.|  
  
## <a name="remarks"></a>Uwagi  
 W implementacji usług programu .NET Framework XAML. `x:Member` nie ma bezpośredniego typu kopii, ale jest obsługiwany przez <xref:System.Windows.Markup.MemberDefinition> klasy. W postaci strumienia węzłów XAML `x:Member` element jest reprezentowany jako składową o nazwie `Member`, z przestrzeni nazw XAML dla języka XAML. Element członkowski `Member` przechowuje atrybuty podaną przez znaczników.  
  
 Znaczenie `Name` i `Type` nie są przypisane na poziomie usług programu .NET Framework XAML. Są one przechowywane w początkowej strumień węzłów XAML jako wartości parametrów, należy interpretować później zgodnie z zasadami, które mogą zostać nałożone przez określonych platform. Znaczenie może być wyrównane do nazwy XAML i typu XAML, co oznacza, lub może być tylko prawidłowe w systemie typów zapasowy, w zależności od implementacji.  
  
 Do obsługi praktyczne wykorzystanie `x:Members` jako środek do określania definicje elementów członkowskich w znaczniku, elementy członkowskie muszą być skojarzone z klasy, który może być modyfikowany. Zamierzony modelu jest fakt, że `x:Members` istnieje jako element członkowski typu, który określa `x:Class`. Mechanizm kojarzenia typów i elementów członkowskich lub do tworzenia definicji dynamicznego elementu członkowskiego nie jest obsługiwane na poziomie usług programu .NET Framework XAML. To pole pozostanie do poszczególnych struktur, które mają modeli aplikacji, które obsługują definicje elementów członkowskich z XAML. Zwykle akcji kompilacji MSBUILD, które znaczników kompilacji XAML, a następnie zintegrować go z kodem lub zestawy czyste z XAML produktu są wymagane do obsługi tej funkcji.  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>x: Property dla programu Windows Workflow Foundation  
 Dla programu Windows Workflow Foundation `x:Property` definiuje elementy niestandardowe działanie składające się wyłącznie w XAML lub XAML — definicja dynamiczne elementy członkowskie w Projektancie działanie z kodem. `x:Class` musi być także określona w elemencie głównym produkcji XAML. To nie jest wymagane na poziomie usług programu .NET Framework XAML, ale staje się to wymagane, gdy produkcji XAML jest ładowany przez akcje kompilacji MSBUILD, które obsługują niestandardowych działań i Windows Workflow Foundation XAML ogólnie rzecz biorąc. Windows Workflow Foundation nie używa czystego Nazwa typu XAML jako jego wartość przeznaczone dla `x:Property` `Type` atrybutu i zamiast tego używa konwencji, który nie jest udokumentowany w tym miejscu. Aby uzyskać więcej informacji, zobacz [tworzenie działania DynamicActivity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).
