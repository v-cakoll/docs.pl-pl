---
title: "x:Uid — dyrektywa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
caps.latest.revision: "12"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 4d49e9630b481b2daf103feabd225dd5ef0c8ca2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xuid-directive"></a>x:Uid — dyrektywa
Zawiera unikatowy identyfikator dla elementów kodu znaczników. W wielu scenariuszach ten unikatowy identyfikator jest używany przez XAML lokalizacja procesów i narzędzi.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:Uid="identifier"... />  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`identifier`|Utworzony ręcznie lub automatycznie wygenerowany ciąg, który powinien być unikatowy w pliku podczas jest interpretowany przez `x:Uid` konsumenta.|  
  
## <a name="remarks"></a>Uwagi  
 W [MS-XAML] `x:Uid` jest zdefiniowany dyrektywą. Aby uzyskać więcej informacji, zobacz [ \[MS XAML\] sekcji 5.3.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
 `x:Uid`jest odrębny z `x:Name` zarówno z powodu podane scenariusz lokalizacja XAML i tak, aby identyfikatorów, które są używane do lokalizacji nie ma żadnych zależności na skutki modelu programowania `x:Name`. Ponadto `x:Name` podlega XAML namescope; jednak `x:Uid` nie podlega żadnych koncepcji zdefiniowane języka XAML wymuszania unikatowości. Aby wymusić unikatowość nie powinny procesorów XAML szeroko (procesorów, które nie są częścią procesu lokalizacja) `x:Uid` wartości. Odpowiedzialność jest koncepcyjnie na inicjatorem wartości. Oczekuje unikatowość `x:Uid` wartości w ramach jednego źródła XAML jest uzasadnione dla konsumentów wartości, takich jak globalizacja dedykowanych procesów lub narzędzia. Model typowe unikatowości jest to, że `x:Uid` wartości są unikatowe w obrębie pliku kodowany w formacie XML, reprezentujący XAML.  
  
 Narzędzia, które posiadają znaczne wiedzę na temat określonego schematu XAML mogą być stosowane `x:Uid` tylko w przypadku true Lokalizowalny ciągi, a nie we wszystkich przypadkach, gdy napotkano wartości ciągu tekstowego w znaczniku.  
  
 Struktury można określić określonej właściwości w modelu obiektów, ich jako alias dla `x:Uid` przez zastosowanie atrybutu <xref:System.Windows.Markup.UidPropertyAttribute> typowi definiującego. Jeśli platforma określa określonej właściwości, nie jest prawidłową określić ich obu `x:Uid` i element członkowski aliasem w tym samym obiekcie. Jeśli oba `x:Uid` i podano elementu członkowskiego aliasu, interfejsu API programu .NET Framework XAML Services zwykle zgłasza <xref:System.Xaml.XamlDuplicateMemberException> dla tej sprawy.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 Aby uzyskać więcej informacji o roli `x:Uid` w procesie lokalizacji WPF i w postaci BAML XAML, zobacz [globalizacji dla WPF](../../../docs/framework/wpf/advanced/globalization-for-wpf.md) lub<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
 <xref:Microsoft.Build.Tasks.Windows.UidManager>  
 [Globalizacja dla WPF](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
