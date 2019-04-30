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
ms.openlocfilehash: 62064286fecc4736f39ad790f0fd7f0e6d84b149
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754274"
---
# <a name="jitcompilationstart-mda"></a>jitCompilationStart MDA
`jitCompilationStart` Zarządzanego Asystenta debugowania (MDA) jest aktywowany do raportu, gdy kompilator just-in-time (JIT) zaczyna kompilować funkcję.  
  
## <a name="symptoms"></a>Symptomy  
 Zestaw roboczy zwiększania rozmiaru dla programu, który jest już w formacie obrazu natywnego, ponieważ mscorjit.dll jest ładowany do procesu.  
  
## <a name="cause"></a>Przyczyna  
 Nie wszystkie zestawy, których program jest zależny od zostały wygenerowane w formacie natywnym lub tych, które mają nie zostały poprawnie zarejestrowane.  
  
## <a name="resolution"></a>Rozwiązanie  
 Włączanie to zdarzenie MDA pozwala określić, która funkcja jest kompilowany dokładnie na czas. Ustalić, czy zestaw, który zawiera funkcję jest generowany w celu natywnego formatu oraz poprawnie zarejestrowany.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA rejestruje wiadomość, przed metodą jest kompilowany dokładnie na czas, dlatego włączenie to zdarzenie MDA ma znaczący wpływ na wydajność. Należy pamiętać, że jeśli metoda jest wbudowany, to zdarzenie MDA nie wygeneruje oddzielną wiadomość.  
  
## <a name="output"></a>Dane wyjściowe  
 Poniższy przykładowy kod przedstawia przykładowe dane wyjściowe. W tym przypadku pokazano w danych wyjściowych, które w zestawie testów metody "m" w klasie "ns2.CO" jest kompilowany dokładnie na czas.  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a>Konfiguracja  
 Następujący plik konfiguracji zawiera szereg filtry, które można zastosować, aby odfiltrować metody, które są zgłaszane, gdy są one najpierw kompilowanego dokładnie na czas. Można określić, że wszystkie metody należy podać, ustawiając wartość atrybutu nazwy \*.  
  
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
 Poniższy przykładowy kod jest przeznaczony do użycia z poprzedniego pliku konfiguracji.  
  
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
