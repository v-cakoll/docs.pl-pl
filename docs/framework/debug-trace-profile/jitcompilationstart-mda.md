---
title: jitCompilationStart MDA
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 80473e01581a372c193c4b816a37166b73d57824
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854146"
---
# <a name="jitcompilationstart-mda"></a>jitCompilationStart MDA
Asystent `jitCompilationStart` debugowania zarządzanego (MDA) jest aktywowany do raportowania, gdy kompilator just in Time (JIT) rozpocznie Kompilowanie funkcji.  
  
## <a name="symptoms"></a>Symptomy  
 Rozmiar zestawu roboczego rośnie dla programu, który jest już w formacie obrazu natywnego, ponieważ MSCORJIT. dll jest ładowany do procesu.  
  
## <a name="cause"></a>Przyczyna  
 Nie wszystkie zestawy, od których zależy program, zostały wygenerowane w formacie natywnym lub te, które nie zostały poprawnie zarejestrowane.  
  
## <a name="resolution"></a>Rozwiązanie  
 Włączenie tego MDA pozwala określić, która funkcja jest skompilowana w trybie JIT. Ustal, czy zestaw, który zawiera funkcję, jest generowany w formacie natywnym i poprawnie zarejestrowany.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie jest rejestrowane tuż przed użyciem metody z kompilacją JIT, dlatego włączenie tego elementu MDA ma znaczny wpływ na wydajność. Należy pamiętać, że jeśli metoda jest wbudowana, to MDA nie będzie generować osobnego komunikatu.  
  
## <a name="output"></a>Dane wyjściowe  
 Poniższy przykład kodu pokazuje przykładowe dane wyjściowe. W takim przypadku dane wyjściowe pokazują, że w teście zestawu Metoda "m" w klasie "ns2.CO" została skompilowana JIT.  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a>Konfiguracja  
 Poniższy plik konfiguracji przedstawia różne filtry, które mogą być stosowane do filtrowania metod zgłaszanych podczas pierwszego kompilowania JIT. Możesz określić, że wszystkie metody mają być zgłaszane przez ustawienie wartości atrybutu Name na \*.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <jitCompilationStart>  
      <methods>  
        <match name="C0::m" />  
        <match name="MyMethod" />  
        <match name="C2::*" />  
        <match name="ns0::*" />  
        <match name="ns1.C0::*" />  
        <match name="ns2.C0::m" />  
        <match name="ns2.C0+N0::m" />  
      </methods>  
    </jitCompilationStart >  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu jest przeznaczony do użycia w poprzednim pliku konfiguracyjnym.  
  
```csharp
using System;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public static void Main(string[] args)  
    {  
        C0.m();  
        C1.MyMethod();  
        C2.m();  
  
        ns0.C0.m();  
        ns0.C0.N0.m();  
        ns0.C1.m();  
  
        ns1.C0.m();  
        ns1.C0.N0.m();  
  
        ns2.C0.m();  
        ns2.C0.N0.m();  
    }  
}  
  
public class C0  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
public class C1  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void MyMethod() { }  
}  
  
public class C2  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
namespace ns0  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
  
    public class C1  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
    }  
}  
  
namespace ns1  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
  
namespace ns2  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
