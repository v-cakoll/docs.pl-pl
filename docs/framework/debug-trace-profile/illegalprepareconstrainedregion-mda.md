---
title: illegalPrepareConstrainedRegion MDA
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 623aff91eb801b4b32fc180bd97ed3822ad7f163
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052678"
---
# <a name="illegalprepareconstrainedregion-mda"></a>illegalPrepareConstrainedRegion MDA
Asystent `illegalPrepareConstrainedRegion` debugowania zarządzanego (MDA) jest uaktywniany, <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> gdy wywołanie metody nie poprzedza `try` bezpośrednio instrukcji programu obsługi wyjątków. To ograniczenie jest na poziomie MSIL, dlatego można mieć źródło `try`, które nie umożliwia generowania kodu między wywołaniem i, takimi jak komentarze.  
  
## <a name="symptoms"></a>Symptomy  
 Ograniczony region wykonywania (CER), który nigdy nie jest traktowany jak taki, ale jako prosty blok obsługi wyjątków (`finally` lub `catch`). W związku z tym region nie jest uruchamiany w przypadku warunku braku pamięci lub przerwania wątku.  
  
## <a name="cause"></a>Przyczyna  
 Wzorzec przygotowania dla programu CER nie działa poprawnie.  Jest to zdarzenie błędu. / / `catch` `filter` `finally` / `fault` Wywołanie metody używane do oznaczania procedur obsługi wyjątków, które wprowadza CER w swoich blokach, musi być używane bezpośrednio przed <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> `try` instrukcja.  
  
## <a name="resolution"></a>Rozwiązanie  
 Upewnij się, że wywołanie <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> jest wykonywane bezpośrednio `try` przed instrukcją.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA Wyświetla nazwę metody wywołującej <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> metodę, przesunięcie MSIL i komunikat wskazujący, że wywołanie nie następuje bezpośrednio przed początkiem bloku try.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje wzorzec, który powoduje aktywowanie tego MDA.  
  
```csharp
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
