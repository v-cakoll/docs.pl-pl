---
title: openGenericCERCall MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- open generic CER calls
- constrained execution regions
- openGenericCERCall MDA
- CER calls
- managed debugging assistants (MDAs), CER calls
- generics [.NET Framework], open generic CER calls
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92528a2cf2227520327b9be2dca70be4c238ff61
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564685"
---
# <a name="opengenericcercall-mda"></a>openGenericCERCall MDA
`openGenericCERCall` Zarządzany Asystent debugowania jest aktywowana Aby ostrzeżenie, że wykres ograniczonego wykonania region (CER) za pomocą zmiennych typu rodzajowego w metodzie głównej jest przetwarzany na kompilację JIT lub obrazu macierzystego czas generowania i co najmniej jeden z ogólnych zmienne typu jest typu odwołanie do obiektu.  
  
## <a name="symptoms"></a>Symptomy  
 CER kodu nie jest uruchamiany, gdy wątek został przerwany lub domena aplikacji jest zwalniana.  
  
## <a name="cause"></a>Przyczyna  
 W czasie kompilacji JIT podczas tworzenia wystąpienia typu odwołanie do obiektu zawierającego to tylko ponieważ wynikowy kod jest współużytkowany, a każda z tych zmiennych typu odwołania może być dowolnego typu odwołanie do obiektu. Może to spowodować przygotowania niektóre zasoby środowiska wykonawczego wcześniej.  
  
 W szczególności metody ze zmiennymi typu ogólnego, opóźnieniem można przydzielić zasoby w tle. Są one określane jako wpisy generyczny słownik. Na przykład dla instrukcji `List<T> list = new List<T>();` gdzie `T` jest zmienną typu rodzajowego, środowisko wykonawcze musi strzałki w górę i ewentualnie utworzyć związanej dokładna w czasie wykonywania, na przykład `List<Object>, List<String>`, i tak dalej. To może się nie powieść z różnych powodów będące poza kontrolą dewelopera, takie jak uruchamianie za mało pamięci.  
  
 To zdarzenie MDA można uaktywniać tylko w czasie kompilacji JIT, nie po dokładnie egzemplarz.  
  
 To zdarzenie MDA jest aktywowane, prawdopodobnie objawów są czy CERs nie działają dla zły wystąpień. W rzeczywistości środowisko wykonawcze nie próbował zaimplementować CER w sytuacjach, które spowodowały MDA zostanie uaktywniony. Dlatego jeśli programistka używa udostępnionego podczas tworzenia wystąpienia CER, a następnie błędy kompilacji JIT, ogólne typu błędy ładowania lub Wątek przerywa w obrębie regionu zamierzony CER nie zostały wyłapane.  
  
## <a name="resolution"></a>Rozwiązanie  
 Nie należy używać zmiennych typu ogólnego, które są typu odwołanie do obiektu dla metod, które mogą zawierać CER.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Poniżej przedstawiono przykładowe dane wyjściowe z tego MDA.  
  
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
 Kod CER nie jest wykonywany.  
  
```csharp
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
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
