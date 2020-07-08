---
title: memberInfoCacheCreation MDA
description: Informacje o programie memberInfoCacheCreation Managed Debug Assistant (MDA) w programie .NET, który jest uaktywniany podczas tworzenia pamięci podręcznej MemberInfo.
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
ms.openlocfilehash: c48be7ac8632b8072981be01e01997ee8c34b6b3
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051145"
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation MDA
`memberInfoCacheCreation`Asystent debugowania zarządzanego (MDA) jest uaktywniany po <xref:System.Reflection.MemberInfo> utworzeniu pamięci podręcznej. Jest to mocne wskazanie programu, który korzysta z funkcji odbicia kosztownych zasobów.  
  
## <a name="symptoms"></a>Objawy  
 Zestaw roboczy programu zostaje zwiększony, ponieważ program korzysta z bardziej kosztownego odbicia zasobów.  
  
## <a name="cause"></a>Przyczyna  
 Operacje odbicia obejmujące <xref:System.Reflection.MemberInfo> obiekty są uznawane za kosztowne, ponieważ muszą odczytywać metadane przechowywane na zimnych stronach i ogólnie wskazują, że program używa pewnego typu scenariusza z późnym wiązaniem.  
  
## <a name="resolution"></a>Rozwiązanie  
 Możesz określić, gdzie odbicie jest używane w programie, włączając ten MDA, a następnie uruchamiając kod w debugerze lub dołączając debuger, gdy zostanie uaktywnione zdarzenie MDA. W ramach debugera uzyskasz śledzenie stosu pokazujące miejsce <xref:System.Reflection.MemberInfo> utworzenia pamięci podręcznej, a następnie można określić, gdzie program używa odbicia.  
  
 Rozwiązanie zależy od celów kodu. To zdarzenie MDA ostrzega o tym, że program ma scenariusz z późnym wiązaniem. Warto określić, czy można zastąpić scenariusz wczesny, czy też wziąć pod uwagę wydajność scenariusza z późnym wiązaniem.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA jest aktywowane dla każdej <xref:System.Reflection.MemberInfo> tworzonej pamięci podręcznej. Wpływ na wydajność jest nieznaczny.  
  
## <a name="output"></a>Dane wyjściowe  
 Po utworzeniu pamięci podręcznej MDA zostanie wyświetlony komunikat wskazujący, że <xref:System.Reflection.MemberInfo> została utworzona. Użyj debugera, aby uzyskać ślad stosu pokazujący, gdzie program używa odbicia.  
  
## <a name="configuration"></a>Konfigurowanie  
  
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
