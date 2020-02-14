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
ms.openlocfilehash: b80d6160876834b22e8d9d1eb7112b8b67c15fcc
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216461"
---
# <a name="illegalprepareconstrainedregion-mda"></a>illegalPrepareConstrainedRegion MDA
Asystent debugowania zarządzanego `illegalPrepareConstrainedRegion` (MDA) jest uaktywniany, gdy wywołanie metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> nie poprzedza bezpośrednio instrukcji `try` programu obsługi wyjątków. To ograniczenie jest na poziomie MSIL, dlatego można mieć źródło, które nie umożliwia generowania kodu między wywołaniem i `try`, takie jak komentarze.  
  
## <a name="symptoms"></a>Objawy  
 Ograniczony region wykonywania (CER), który nigdy nie jest traktowany jak taki, ale jako prosty blok obsługi wyjątków (`finally` lub `catch`). W związku z tym region nie jest uruchamiany w przypadku warunku braku pamięci lub przerwania wątku.  
  
## <a name="cause"></a>Przyczyna  
 Wzorzec przygotowania dla programu CER nie działa poprawnie.  Jest to zdarzenie błędu. Wywołanie metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> używane do oznaczania procedur obsługi wyjątków jako przedstawiające CER w ich `catch`/`finally`/`fault`/`filter` bloków należy używać bezpośrednio przed instrukcją `try`.  
  
## <a name="resolution"></a>Rozwiązanie  
 Upewnij się, że wywołanie <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> następuje bezpośrednio przed instrukcją `try`.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA Wyświetla nazwę metody wywołującej metodę <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>, przesunięcie MSIL i komunikat wskazujący, że wywołanie nie następuje bezpośrednio przed początkiem bloku try.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
