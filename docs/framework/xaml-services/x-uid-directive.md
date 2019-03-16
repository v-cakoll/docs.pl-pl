---
title: x:Uid — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: 6e946c63227a06b2032ce27e61899c1b8f05ec9f
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58042973"
---
# <a name="xuid-directive"></a>x:Uid — dyrektywa
Zawiera unikatowy identyfikator dla elementów kodu znaczników. W wielu scenariuszach ten unikatowy identyfikator jest używany przez XAML lokalizacji procesów i narzędzi.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:Uid="identifier"... />  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`identifier`|Utworzony ręcznie lub automatycznie wygenerowany ciąg powinien być unikatowy w pliku, gdy jest on interpretowany przez `x:Uid` konsumenta.|  
  
## <a name="remarks"></a>Uwagi  
 W [MS-XAML] `x:Uid` jest zdefiniowany jako dyrektywy. Aby uzyskać więcej informacji, zobacz [ \[MS-XAML\] sekcji 5.3.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
 `x:Uid` jest odrębny z `x:Name` zarówno z powodu określonego scenariusza lokalizacji XAML i tak, aby identyfikatory, które są używane dla lokalizacji ma żadnych zależności w konsekwencji modelu programowania `x:Name`. Ponadto `x:Name` podlega XAML namescope; jednak `x:Uid` nie podlega XAML dowolnego języka zdefiniowanego koncepcji wymuszania unikatowości. Procesory XAML szeroko (procesorów, które nie są częścią proces lokalizacji) najprawdopodobniej nie wymusza unikatowości `x:Uid` wartości. Czy odpowiedzialność jest koncepcyjnie na inicjatorem wartości. Oczekuje unikatowość `x:Uid` wartości w jednym źródle XAML jest uzasadnione dla konsumentów wartości, takich jak procesy globalizacji dedykowanych lub narzędzia. Modelu unikatowości typowy jest fakt, że `x:Uid` wartości są unikatowe w obrębie plik zakodowane w formacie XML, który reprezentuje XAML.  
  
 Narzędzia, które dysponują wiedzą na temat znaczące określonego schematu XAML można zdecydowali się zastosować `x:Uid` tylko w przypadku wartości true możliwych do zlokalizowania ciągi zamiast we wszystkich przypadkach, w którym występuje wartości ciągu tekstowego w znacznikach.  
  
 Struktury, można określić określonej właściwości w modelu obiektu jako alias dla `x:Uid` , stosując atrybut <xref:System.Windows.Markup.UidPropertyAttribute> do definiowania typu. Jeśli platforma określa danej właściwości, nie jest prawidłową podać obydwie wartości `x:Uid` i elementów członkowskich alias dla tego samego obiektu. Jeśli oba `x:Uid` i podano składowej aliasu, interfejs API programu .NET Framework XAML usług zwykle zgłasza <xref:System.Xaml.XamlDuplicateMemberException> dla tej sprawy.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użytkowania WPF  
 Aby uzyskać więcej informacji o roli `x:Uid` w procesie lokalizacji WPF i formularz BAML XAML, zobacz [globalizacja dla WPF](../wpf/advanced/globalization-for-wpf.md) lub <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [Globalizacja dla WPF](../wpf/advanced/globalization-for-wpf.md)
