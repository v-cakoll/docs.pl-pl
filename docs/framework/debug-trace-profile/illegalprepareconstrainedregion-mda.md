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
ms.openlocfilehash: 23a36d1709f03583ce39af0e7c80bb1ecd7cf809
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754391"
---
# <a name="illegalprepareconstrainedregion-mda"></a>illegalPrepareConstrainedRegion MDA
`illegalPrepareConstrainedRegion` Zarządzanego Asystenta debugowania (MDA) jest aktywowany po <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> wywołanie metody nie bezpośrednio poprzedzać `try` instrukcji obsługi wyjątków. To ograniczenie jest w MSIL poziomu, więc jest dozwolone do generowania kodu źródło między wywołanie i `try`, takich jak komentarze.  
  
## <a name="symptoms"></a>Symptomy  
 Region ograniczonego wykonania (CER), która nigdy nie jest traktowana jako takie, ale jako prosty bloku obsługi wyjątków (`finally` lub `catch`). W konsekwencji regionie nie działa w przypadku warunku braku pamięci lub przerwanie wątku.  
  
## <a name="cause"></a>Przyczyna  
 Wzorzec przygotowania CER nie jest prawidłowo zakończony.  To zdarzenie błędu. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Wywołania metody, używany do oznaczania obsługi wyjątków jako wprowadzenie do CER w ich `catch` / `finally` / `fault` / `filter` bloków musi używać bezpośrednio przed `try` instrukcji.  
  
## <a name="resolution"></a>Rozwiązanie  
 Upewnij się, że wywołanie <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> ma miejsce bezpośrednio przed `try` instrukcji.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA Wyświetla nazwę wywołanie metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> metodę, przesunięcie MSIL i komunikat informujący o wywołaniu nie bezpośrednio poprzedzać początku bloku try.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje wzorzec, który powoduje, że to zdarzenie MDA zostanie uaktywniony.  
  
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
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
