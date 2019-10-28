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
ms.openlocfilehash: 44b6ee3e4f74a523c1e902a4eb48a64b11eb3937
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/26/2019
ms.locfileid: "72960898"
---
# <a name="opengenericcercall-mda"></a>openGenericCERCall MDA

Asystent debugowania zarządzanego `openGenericCERCall` został aktywowany, aby ostrzec, że wykres ograniczonego regionu wykonania (CER) z zmiennymi typu ogólnego w metodzie głównej jest przetwarzany podczas kompilacji JIT lub czasu generowania obrazu natywnego, a co najmniej jeden typ ogólny zmienne to typ odwołania do obiektu.

## <a name="symptoms"></a>Symptomy

Kod CER nie jest uruchamiany, gdy wątek zostanie przerwany lub gdy domena aplikacji zostanie zwolniona.

## <a name="cause"></a>Przyczyna

W czasie kompilacji JIT proces tworzenia wystąpienia zawierającego typ odwołania do obiektu jest tylko reprezentatywny, ponieważ wynikowy kod jest współużytkowany, a Każda zmienna typu odwołania do obiektu może być dowolnym typem odwołania do obiektu. Może to uniemożliwić przygotowanie niektórych zasobów czasu wykonywania przed czasem.

W szczególności metody z zmiennymi typów ogólnych mogą opóźnieniem przydzielać zasoby w tle. Są one określane mianem zwykłych wpisów słownika. Na przykład dla instrukcji `List<T> list = new List<T>();`, gdzie `T` jest zmienną typu ogólnego, środowisko uruchomieniowe musi wyszukać i ewentualnie utworzyć dokładne wystąpienie w czasie wykonywania, na przykład `List<Object>, List<String>`i tak dalej. Może to się nie powieść z różnych powodów wykraczających poza kontrolę dewelopera, na przykład za mało pamięci.

To zdarzenie MDA powinno być aktywowane tylko w czasie kompilacji JIT, a nie w przypadku wystąpienia dokładnego.

Po aktywowaniu tego elementu MDA prawdopodobnie CERs nie działają w przypadku nieprawidłowych wystąpień. W rzeczywistości środowisko uruchomieniowe nie podjęło próby wdrożenia CER w warunkach, które spowodowały aktywowanie MDA. Tak więc jeśli deweloper korzysta z udostępnionego wystąpienia programu CER, błędy kompilacji JIT, błędy ładowania typów lub przerwania wątku w regionie zamierzonego CER nie są przechwytywane.

## <a name="resolution"></a>Rozwiązanie

Nie używaj typów ogólnych zmiennych, które są typu odwołania do obiektu dla metod, które mogą zawierać CER.

## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe

To zdarzenie MDA nie ma wpływu na środowisko CLR.

## <a name="output"></a>Dane wyjściowe

Poniżej znajduje się przykład danych wyjściowych z tego MDA:
  
 ```output
 Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.
 The caller must ensure this method is prepared explicitly at run time prior to execution. 
 method name="GenericMethodWithCer"
 declaringType name="OpenGenericCERCall"
 ```

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
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
