---
title: memberInfoCacheCreation MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d82e77e2a47a9b0feb36ca054c0abcff2721940
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="memberinfocachecreation-mda"></a>memberInfoCacheCreation MDA
`memberInfoCacheCreation` Zarządzany Asystent debugowania (MDA) została aktywowana po <xref:System.Reflection.MemberInfo> pamięci podręcznej. To silne wskazanie program, który jest użycie funkcji odbicia zasobów.  
  
## <a name="symptoms"></a>Symptomy  
 Program roboczy zwiększa zestawu, ponieważ program jest za pomocą odbicia zasobów.  
  
## <a name="cause"></a>Przyczyna  
 Operacje odbicia, które obejmują <xref:System.Reflection.MemberInfo> obiekty są traktowane jako zasób kosztowne, ponieważ muszą one odczytu metadanych, które są przechowywane na stronach zimnych i ogólnie wskazują one program używa pewien typ scenariusza z późnym wiązaniem.  
  
## <a name="resolution"></a>Rozwiązanie  
 Można określić, gdzie odbicia jest używane w programie przez włączenie to zdarzenie MDA i ponownie uruchomić kodu w debugerze lub związane z debugera, po aktywowaniu MDA. W debugerze otrzymasz ślad stosu przedstawiający miejsce <xref:System.Reflection.MemberInfo> pamięci podręcznej został utworzony i z tego miejsca można określić, których program jest za pomocą odbicia.  
  
 Rozdzielczość jest zależny od celów kodu. To zdarzenie MDA alertów, czy program ma scenariusza z późnym wiązaniem. Można określić, czy można podstawić scenariusza z wczesnym wiązaniem też należy wziąć pod uwagę wydajności późne powiązania scenariusza.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA został aktywowany dla każdego <xref:System.Reflection.MemberInfo> pamięci podręcznej, która jest tworzona. Wpływ na wydajność jest niewielka.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA wyświetla komunikat informujący <xref:System.Reflection.MemberInfo> pamięci podręcznej został utworzony. Użyj debugera, aby uzyskać ślad stosu wyświetlane, gdy program jest za pomocą odbicia.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Ten przykładowy kod uaktywni `memberInfoCacheCreation` MDA.  
  
```  
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
 <xref:System.Reflection.MemberInfo>  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
