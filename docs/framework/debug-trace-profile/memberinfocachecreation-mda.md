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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3b65ecc226c1caf7b53d746f0583e1f57c7d8c1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052471"
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation MDA
Asystent debugowania <xref:System.Reflection.MemberInfo> zarządzanego (MDA) jest uaktywniany po utworzeniu pamięci podręcznej. `memberInfoCacheCreation` Jest to mocne wskazanie programu, który korzysta z funkcji odbicia kosztownych zasobów.  
  
## <a name="symptoms"></a>Symptomy  
 Zestaw roboczy programu zostaje zwiększony, ponieważ program korzysta z bardziej kosztownego odbicia zasobów.  
  
## <a name="cause"></a>Przyczyna  
 Operacje odbicia obejmujące <xref:System.Reflection.MemberInfo> obiekty są uznawane za kosztowne, ponieważ muszą odczytywać metadane przechowywane na zimnych stronach i ogólnie wskazują, że program używa pewnego typu scenariusza z późnym wiązaniem.  
  
## <a name="resolution"></a>Rozwiązanie  
 Możesz określić, gdzie odbicie jest używane w programie, włączając ten MDA, a następnie uruchamiając kod w debugerze lub dołączając debuger, gdy zostanie uaktywnione zdarzenie MDA. W ramach debugera uzyskasz śledzenie stosu pokazujące miejsce <xref:System.Reflection.MemberInfo> utworzenia pamięci podręcznej, a następnie można określić, gdzie program używa odbicia.  
  
 Rozwiązanie zależy od celów kodu. To zdarzenie MDA ostrzega o tym, że program ma scenariusz z późnym wiązaniem. Warto określić, czy można zastąpić scenariusz wczesny, czy też wziąć pod uwagę wydajność scenariusza z późnym wiązaniem.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA jest aktywowane dla <xref:System.Reflection.MemberInfo> każdej tworzonej pamięci podręcznej. Wpływ na wydajność jest nieznaczny.  
  
## <a name="output"></a>Dane wyjściowe  
 Po utworzeniu pamięci podręcznej MDA <xref:System.Reflection.MemberInfo> zostanie wyświetlony komunikat wskazujący, że została utworzona. Użyj debugera, aby uzyskać ślad stosu pokazujący, gdzie program używa odbicia.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Ten przykładowy kod spowoduje aktywowanie `memberInfoCacheCreation` MDA.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.MemberInfo>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
