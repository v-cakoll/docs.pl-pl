---
title: x:Property — dyrektywa
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: 7624014e0cd9ddd47cc84ee9686a6f11c27d1843
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053924"
---
# <a name="xproperty-directive"></a>x:Property — dyrektywa
Deklaruje Właściwość XAML w znaczniku.  
  
## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML  
  
```xaml  
<object x:Class="className">  
  <x:Members>  
    <x:Property Name="propertyName" Type="propertyType"/>  
    additionalProperties  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`className`|Nazwa klasy zapasowej lub klasy częściowej dla produkcji XAML.|  
|`propertyName`|Nazwa elementu członkowskiego zdefiniowanej właściwości.|  
|`propertyType`|Nazwa typu (lub inny formularz ciągu, specyficzny dla platformy), który określa typ tej właściwości.|  
  
## <a name="remarks"></a>Uwagi  
 W .NET Framework implementacji usług XAML. `x:Property`nie ma bezpośredniego typu zapasowego, ale jest obsługiwany przez <xref:System.Windows.Markup.PropertyDefinition> klasę. W strumieniu `x:Property` węzła XAML element jest reprezentowany jako element członkowski o nazwie `Property`, z przestrzeni nazw XAML języka XAML. Składowa `Property` zawiera atrybuty zadeklarowane przez znacznik.  
  
 Znaczenie `Name` i`Type` nie są przypisane na poziomie .NET Framework usług XAML. Są one przechowywane w początkowym strumieniu węzła XAML jako wartości ciągów, które mają być interpretowane później w ramach reguł, które mogą zostać nałożone przez określone struktury. Znaczenie może być wyrównane do nazwy XAML i typu XAML lub może być prawidłowe tylko w systemie typu zapasowego, w zależności od implementacji.  
  
 Aby obsłużyć praktyczne użycie `x:Members` jako środek do określenia definicji elementów członkowskich w znaczniku, elementy członkowskie muszą być skojarzone z klasą, która może być modyfikowana. Zamierzony model `x:Members` istnieje jako element członkowski typu, który `x:Class`określa. Jednak mechanizm kojarzenia typów i elementów członkowskich lub do tworzenia dynamicznych definicji elementów członkowskich nie jest obsługiwany na poziomie .NET Framework usług XAML. Jest to pozostało do pojedynczych platform, które mają modele aplikacji, które obsługują definicje elementów członkowskich z języka XAML. Zazwyczaj akcje kompilacji programu MSBUILD, które umożliwiają adiustację i kompilowanie kodu XAML, i integrowanie go z kodem związanym lub wytwarzaniem czystych zestawów z języka XAML, które są niezbędne do obsługi tej funkcji.  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>x:Property Windows Workflow Foundation  
 W przypadku Windows Workflow Foundation `x:Property` definiuje elementy członkowskie działania niestandardowego składające się całkowicie z języka XAML lub zdefiniowane w języku XAML dynamiczne elementy członkowskie dla projektanta działań z kodem. `x:Class`musi również być określony w elemencie głównym produkcji XAML. Nie jest to wymagane na poziomie .NET Framework usług XAML, ale jest wymagane, gdy produkcja XAML jest ładowana przez akcje kompilacji MSBUILD, które obsługują działania niestandardowe i Windows Workflow Foundation języka XAML. Windows Workflow Foundation nie używa czystej nazwy typu XAML jako zamierzonej wartości `x:Property` `Type` atrybutu, a zamiast tego używa konwencji, która nie jest udokumentowana w tym miejscu. Aby uzyskać więcej informacji, zobacz [dynamiczne tworzenie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).
