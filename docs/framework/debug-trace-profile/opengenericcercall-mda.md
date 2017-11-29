---
title: openGenericCERCall MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- open generic CER calls
- constrained execution regions
- openGenericCERCall MDA
- CER calls
- managed debugging assistants (MDAs), CER calls
- generics [.NET Framework], open generic CER calls
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f82760eaeb051f2006a8baf11ac77c485d007758
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="opengenericcercall-mda"></a>openGenericCERCall MDA
`openGenericCERCall` Asystent debugowania zarządzanego został aktywowany do ostrzeżenie, że wykres region (CER) ograniczonego wykonania ze zmiennymi typu ogólnego w metodzie głównego jest przetwarzany w kompilacji JIT lub obrazu macierzystego czas generowania i co najmniej jeden z ogólnych zmienne typu jest typu odwołanie do obiektu.  
  
## <a name="symptoms"></a>Symptomy  
 CER kod nie zostanie uruchomiony, gdy wątek został przerwany lub domeny aplikacji jest zwolniony.  
  
## <a name="cause"></a>Przyczyna  
 W czasie kompilacji JIT podczas tworzenia wystąpienia typu odwołanie do obiektu zawierającego jest tylko przedstawiciel, ponieważ wynikowy kod jest udostępniony, a każdy z tych zmiennych typu odwołania mogą być dowolnego typu odwołanie do obiektu. Może to spowodować przygotowanie niektórych zasobów środowiska wykonawczego wcześniejsze.  
  
 W szczególności metody ze zmiennymi typu ogólnego opóźnieniem można przydzielić zasoby w tle. Te są określane jako wpisy słownika ogólnego. Na przykład dla instrukcji `List<T> list = new List<T>();` gdzie `T` jest zmienną typu ogólnego środowiska uruchomieniowego musi strzałki w górę i prawdopodobnie utworzyć wystąpienia dokładnie w czasie wykonywania, na przykład `List<Object>, List<String>`, itd. To może się nie powieść z różnych powodów pozostających poza kontrolą dewelopera, takich jak wyczerpaniu pamięci.  
  
 To zdarzenie MDA należy aktywować tylko w czasie kompilacji JIT nie po wystąpieniu dokładne.  
  
 Po uaktywnieniu to zdarzenie MDA objawy prawdopodobnie są CERs nie są funkcjonalności dla zły wystąpień. W rzeczywistości środowiska uruchomieniowego nie podjął próbę wykonania CER czynników, które spowodowały MDA do aktywacji. Dlatego projektanta używa udostępnionego podczas tworzenia wystąpienia CER, a następnie błędy kompilacji JIT, Ogólne wpisz błędy ładowania lub przerwanie wątku w regionie zamierzone CER nie są przechwytywane.  
  
## <a name="resolution"></a>Rozwiązanie  
 Nie należy używać zmiennych typu ogólnego typu odwołanie do obiektu dla metod, które mogą zawierać CER.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Poniżej przedstawiono przykładowe dane wyjściowe to zdarzenie MDA.  
  
 `Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.`  
  
 `The caller must ensure this method is prepared explicitly at run time prior to execution.`  
  
 `method name="GenericMethodWithCer"`  
  
 `declaringType name="OpenGenericCERCall"`  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <openGenericCERCall/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Kod CER nie została wykonana.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Runtime.CompilerServices;  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        CallGenericMethods();  
    }  
    static void CallGenericMethods()  
    {  
        // This call is correct. The instantiation of the method  
        // contains only nonreference types.  
        MyClass.GenericMethodWithCer<int>();  
  
        // This call is incorrect. A shared version of the method that  
        // cannot be completely analyzed will be JIT-compiled. The   
        // MDA will be activated at JIT-compile time, not at run time.  
        MyClass.GenericMethodWithCer<String>();  
    }  
}  
  
    class MyClass  
{  
    public static void GenericMethodWithCer<T>()  
    {  
        RuntimeHelpers.PrepareConstrainedRegions();  
        try  
        {  
  
        }  
        finally  
        {  
            // This is the start of the CER.  
            Console.WriteLine("In finally block.");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution>  
 [Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
