---
title: illegalPrepareConstrainedRegion MDA
description: Zapoznaj się z asystentem debugowania zarządzanego przez illegalPrepareConstrainedRegion, który jest wywoływany, gdy wywołanie PrepareConstrainedRegions nie poprzedza instrukcji try.
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
ms.openlocfilehash: d6a0d1d95840ebd735806c5547730ae9e0b2aace
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051288"
---
# <a name="illegalprepareconstrainedregion-mda"></a>illegalPrepareConstrainedRegion MDA
`illegalPrepareConstrainedRegion`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> wywołanie metody nie poprzedza bezpośrednio instrukcji programu `try` obsługi wyjątków. To ograniczenie jest na poziomie MSIL, dlatego można mieć źródło, które nie umożliwia generowania kodu między wywołaniem i `try` , takimi jak komentarze.  
  
## <a name="symptoms"></a>Objawy  
 Ograniczony region wykonywania (CER), który nigdy nie jest traktowany jak taki, ale jako prosty blok obsługi wyjątków ( `finally` lub `catch` ). W związku z tym region nie jest uruchamiany w przypadku warunku braku pamięci lub przerwania wątku.  
  
## <a name="cause"></a>Przyczyna  
 Wzorzec przygotowania dla programu CER nie działa poprawnie.  Jest to zdarzenie błędu. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>Wywołanie metody używane do oznaczania procedur obsługi wyjątków, które wprowadza CER w swoich `catch` / `finally` / `fault` / `filter` blokach, musi być używane bezpośrednio przed `try` instrukcją.  
  
## <a name="resolution"></a>Rozwiązanie  
 Upewnij się, że wywołanie jest <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> wykonywane bezpośrednio przed `try` instrukcją.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA Wyświetla nazwę metody wywołującej <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> metodę, przesunięcie MSIL i komunikat wskazujący, że wywołanie nie następuje bezpośrednio przed początkiem bloku try.  
  
## <a name="configuration"></a>Konfigurowanie  
  
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
- [Organizowanie międzyoperacyjne](../interop/interop-marshaling.md)
