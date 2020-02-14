---
title: memberInfoCacheCreation MDA
ms.date: 03/30/2017
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
ms.openlocfilehash: e5dbc769bd634afae06582ee614addafd611fad9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217313"
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation MDA
`memberInfoCacheCreation` Asystent debugowania zarządzanego (MDA) jest uaktywniany podczas tworzenia <xref:System.Reflection.MemberInfo> pamięci podręcznej. Jest to mocne wskazanie programu, który korzysta z funkcji odbicia kosztownych zasobów.  
  
## <a name="symptoms"></a>Objawy  
 Zestaw roboczy programu zostaje zwiększony, ponieważ program korzysta z bardziej kosztownego odbicia zasobów.  
  
## <a name="cause"></a>Przyczyna  
 Operacje odbicia, które obejmują <xref:System.Reflection.MemberInfo> obiektów, są uznawane za zasoby kosztowne, ponieważ muszą odczytywać metadane przechowywane na zimnych stronach i ogólnie wskazują, że program używa pewnego typu scenariusza z późnym wiązaniem.  
  
## <a name="resolution"></a>Rozwiązanie  
 Możesz określić, gdzie odbicie jest używane w programie, włączając ten MDA, a następnie uruchamiając kod w debugerze lub dołączając debuger, gdy zostanie uaktywnione zdarzenie MDA. W ramach debugera zostanie wyświetlony ślad stosu przedstawiający miejsce utworzenia pamięci podręcznej <xref:System.Reflection.MemberInfo>, a w tym miejscu można określić, gdzie program używa odbicia.  
  
 Rozwiązanie zależy od celów kodu. To zdarzenie MDA ostrzega o tym, że program ma scenariusz z późnym wiązaniem. Warto określić, czy można zastąpić scenariusz wczesny, czy też wziąć pod uwagę wydajność scenariusza z późnym wiązaniem.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA jest aktywowane dla każdej tworzonej pamięci podręcznej <xref:System.Reflection.MemberInfo>. Wpływ na wydajność jest nieznaczny.  
  
## <a name="output"></a>Dane wyjściowe  
 W wyniku tego zostanie wyświetlony komunikat z informacją o utworzeniu pamięci podręcznej <xref:System.Reflection.MemberInfo>. Użyj debugera, aby uzyskać ślad stosu pokazujący, gdzie program używa odbicia.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Ten przykładowy kod aktywuje `memberInfoCacheCreation` MDA.  
  
```csharp
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection.MemberInfo>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
