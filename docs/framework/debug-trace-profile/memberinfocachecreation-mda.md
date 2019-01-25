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
ms.openlocfilehash: 028ff1048813ccbc845d5ad3e7f522b492348f87
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651035"
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation MDA
`memberInfoCacheCreation` Zarządzanego Asystenta debugowania (MDA) jest aktywowany po <xref:System.Reflection.MemberInfo> utworzeniu pamięci podręcznej. To silne wskazanie program, który wykonuje korzystania z funkcji odbicia drogich zasobów.  
  
## <a name="symptoms"></a>Symptomy  
 Program użytkownika działa zestaw rośnie, ponieważ program używa odbicia drogich zasobów.  
  
## <a name="cause"></a>Przyczyna  
 Operacje odbicia, obejmujące <xref:System.Reflection.MemberInfo> obiekty są traktowane jako zasób kosztowne, ponieważ będzie musi odczytać metadane, które są przechowywane na stronach zimnych i ogólnie rzecz biorąc wskazują program używa jakiegoś rodzaju scenariusza z późnym wiązaniem.  
  
## <a name="resolution"></a>Rozwiązanie  
 Można określić, gdy odbicie jest używany w programie przez włączenie to zdarzenie MDA i ponownie uruchomić usługi kodu w debugerze lub dołączania za pomocą debugera, gdy zdarzenie MDA jest aktywowane. W debugerze, zostanie wyświetlony ślad stosu, przedstawiający miejsce <xref:System.Reflection.MemberInfo> pamięci podręcznej został utworzony, a w tym miejscu możesz określić, gdzie program używa odbicia.  
  
 Rozwiązanie jest zależna od celów kodu. To zdarzenie MDA alertów, czy program ma scenariusza z późnym wiązaniem. Możesz chcieć ustalenia, czy należy zastąpić scenariusza z wczesnym wiązaniem lub należy wziąć pod uwagę wydajność pod koniec scenariusza związanego.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA jest aktywowane dla każdego <xref:System.Reflection.MemberInfo> pamięci podręcznej, który jest tworzony. Wpływ na wydajność jest niewielki.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA wyświetla komunikat informujący o <xref:System.Reflection.MemberInfo> pamięć podręczna została utworzona. Należy użyć debugera, aby uzyskać ślad stosu przedstawiający, gdzie program używa odbicia.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Ten przykładowy kod będą aktywowane `memberInfoCacheCreation` MDA.  
  
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
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
