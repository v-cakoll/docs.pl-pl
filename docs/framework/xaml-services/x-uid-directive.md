---
title: x:Uid — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: 32cfd9ab0cf6037c731b619e81a7504ac92d5fb9
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837184"
---
# <a name="xuid-directive"></a>x:Uid — dyrektywa
Zapewnia unikatowy identyfikator dla elementów znaczników. W wielu scenariuszach Ten unikatowy identyfikator jest używany przez procesy i narzędzia lokalizacji XAML.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:Uid="identifier"... />  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`identifier`|Ręcznie utworzony lub generowany automatycznie ciąg, który powinien być unikatowy w pliku, gdy jest interpretowany przez konsumenta `x:Uid`.|  
  
## <a name="remarks"></a>Uwagi  
 W [MS-XAML], `x:Uid` jest zdefiniowany jako dyrektywa. Aby uzyskać więcej informacji, zobacz [sekcję\[MS-XAML\] sekcji 5.3.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
 `x:Uid` jest dyskretny od `x:Name` obu z powodu podanego scenariusza lokalizacji XAML i dlatego, że identyfikatory, które są używane dla lokalizacji, nie mają żadnych zależności od wpływu na model programowania `x:Name`. Ponadto `x:Name` podlega namescope języka XAML; Jednakże `x:Uid` nie podlega żadnym określonym w języku XAML pojęciem wymuszania unikatowości. Procesory XAML w szerokim sensie (procesory, które nie są częścią procesu lokalizacji) nie powinny wymuszać unikatowości wartości `x:Uid`. Ta odpowiedzialność jest koncepcyjnie zależna od nadawcy wartości. Oczekiwana jest unikatowość wartości `x:Uid` w ramach jednego źródła kodu XAML, które są odpowiednie dla konsumentów wartości, takich jak dedykowane procesy globalizacji lub narzędzia. Typowym modelem unikatowym jest to, że wartości `x:Uid` są unikatowe w ramach pliku zakodowanego w formacie XML, który reprezentuje kod XAML.  
  
 Narzędzia, które mają znaczącą wiedzę o określonym schemacie XAML, mogą zastosować `x:Uid` tylko dla ważnych lokalizowalnych ciągów, a nie dla wszystkich przypadków, w których napotkano wartość ciągu tekstowego w znaczniku.  
  
 Struktury mogą określać określoną właściwość w swoim modelu obiektów, aby była aliasem dla `x:Uid` przez zastosowanie atrybutu <xref:System.Windows.Markup.UidPropertyAttribute> do typu definiującego. Jeśli struktura określa określoną właściwość, nie jest ona prawidłowa do określenia zarówno `x:Uid`, jak i aliasu elementu członkowskiego tego samego obiektu. Jeśli określono zarówno `x:Uid`, jak i element członkowski z aliasem, .NET Framework interfejs API usług XAML zwykle zgłasza <xref:System.Xaml.XamlDuplicateMemberException> w tym przypadku.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 Aby uzyskać więcej informacji na temat roli `x:Uid` w procesie lokalizowania WPF i w formie BAML języka XAML, zobacz [globalizacja dla WPF](../wpf/advanced/globalization-for-wpf.md) lub <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [Globalizacja dla WPF](../wpf/advanced/globalization-for-wpf.md)
