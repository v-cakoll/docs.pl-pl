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
ms.openlocfilehash: 7492a4c0547680a6ace85a5f7c98567770f5575a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181783"
---
# <a name="opengenericcercall-mda"></a>openGenericCERCall MDA

Zarządzany `openGenericCERCall` asystent debugowania jest aktywowany, aby ostrzec, że wykres regionu ograniczonego wykonywania (CER) z ogólnymi zmiennymi typu w metodzie głównej jest przetwarzany w czasie generowania kompilacji JIT lub obrazu natywnego, a co najmniej jedna ze zmiennych typu ogólnego jest typem odwołania do obiektu.

## <a name="symptoms"></a>Objawy

Kod CER nie jest uruchamiany, gdy wątek zostanie przerwany lub gdy domena aplikacji zostanie zwolniona.

## <a name="cause"></a>Przyczyna

W czasie kompilacji JIT wystąpienia zawierającego typ odwołania do obiektu jest tylko reprezentatywne, ponieważ wynikowy kod jest współużytkowany, a każda ze zmiennych typu odwołania do obiektu może być dowolnym typem odwołania do obiektu. Może to uniemożliwić przygotowanie niektórych zasobów w czasie wykonywania z wyprzedzeniem.

W szczególności metody ze zmiennymi typu ogólnego można leniwie przydzielać zasoby w tle. Są one określane jako ogólne wpisy słownika. Na przykład dla `List<T> list = new List<T>();` instrukcji, gdzie `T` jest zmienną typu ogólnego środowisko wykonawcze musi wyszukać i `List<Object>, List<String>`ewentualnie utworzyć dokładne wystąpienie w czasie wykonywania, na przykład i tak dalej. To może zakończyć się niepowodzeniem z różnych powodów poza kontrolą dewelopera, takich jak wyczerpanie pamięci.

To MDA powinny być aktywowane tylko w czasie kompilacji JIT, a nie wtedy, gdy istnieje dokładne wystąpienie.

Po aktywacji tego MDA, prawdopodobne objawy są, że CEPTR nie są funkcjonalne dla złych wystąpień. W rzeczywistości środowisko wykonawcze nie próbował zaimplementować CER w okolicznościach, które spowodowały MDA do aktywacji. Więc jeśli deweloper używa udostępnionego wystąpienia CER, a następnie błędy kompilacji JIT, błędy ładowania typu generics lub przerywanie wątku w regionie zamierzonego CER nie są przechwytywane.

## <a name="resolution"></a>Rozwiązanie

Nie należy używać zmiennych typu ogólnego, które są typu odwołania do obiektu dla metod, które mogą zawierać CER.

## <a name="effect-on-the-runtime"></a>Wpływ na czas działania

To MDA nie ma wpływu na CLR.

## <a name="output"></a>Dane wyjściowe

Poniżej przedstawiono przykład danych wyjściowych z tego MDA:
  
 ```output
 Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.
 The caller must ensure this method is prepared explicitly at run time prior to execution.
 method name="GenericMethodWithCer"
 declaringType name="OpenGenericCERCall"
 ```

## <a name="configuration"></a>Konfigurowanie

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

## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
