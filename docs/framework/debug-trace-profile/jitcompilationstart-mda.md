---
title: jitCompilationStart MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 67c80fce223d8f212fa485a8105862bcf24e161b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="jitcompilationstart-mda"></a>jitCompilationStart MDA
`jitCompilationStart` Zarządzany Asystent debugowania (MDA) został aktywowany do raportu podczas uruchamiania kompilatora just-in-time (JIT) skompilować funkcję.  
  
## <a name="symptoms"></a>Symptomy  
 Zestaw roboczy zwiększania rozmiaru dla programu, który jest już w formacie obrazu macierzystego, ponieważ mscorjit.dll jest ładowany do procesu.  
  
## <a name="cause"></a>Przyczyna  
 Nie wszystkie zestawy, których program jest zależny od zostały wygenerowane do formatu macierzystego lub te, które mają nie zostały poprawnie zarejestrowane.  
  
## <a name="resolution"></a>Rozwiązanie  
 Włączanie to zdarzenie MDA pozwala określić, funkcji, które są kompilowane JIT. Określ, czy zestaw zawierający funkcję jest generowane w celu formatu macierzystego i poprawnie zarejestrowany.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA rejestruje komunikat tuż przed metodą jest kompilacji JIT, dlatego włączenie tego MDA ma znaczący wpływ na wydajność. Należy pamiętać, że jeśli metoda jest wbudowany, to zdarzenie MDA nie wygeneruje osobnej wiadomości.  
  
## <a name="output"></a>Dane wyjściowe  
 Poniższy przykład kodu pokazuje przykładowe dane wyjściowe. W takim przypadku pokazuje dane wyjściowe, które w zestawie testów metody "m" w klasie "ns2.CO" został skompilowany JIT.  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a>Konfiguracja  
 Następujący plik konfiguracji zawiera szereg filtry, które można zastosować do odfiltrowywania które metody są zgłaszane, gdy są one najpierw kompilacji JIT. Można określić, że wszystkie metody zgłoszone przez ustawienie wartości atrybutu nazwy *.  
  
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
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Przekazywanie międzyoperacyjne](../../../docs/framework/interop/interop-marshaling.md)
