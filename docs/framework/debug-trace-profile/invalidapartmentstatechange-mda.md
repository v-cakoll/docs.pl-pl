---
title: invalidApartmentStateChange MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid apartment state
- managed debugging assistants (MDAs), invalid apartment state
- InvalidApartmentStateChange MDA
- invalid apartment state changes
- threading [.NET Framework], apartment states
- apartment states
- threading [.NET Framework], managed debugging assistants
- COM apartment states
ms.assetid: e56fb9df-5286-4be7-b313-540c4d876cd7
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 71634018e42ad66fdd2d03d0b0d496394cde801e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="invalidapartmentstatechange-mda"></a>invalidApartmentStateChange MDA
`invalidApartmentStateChange` Asystent debugowania zarządzanego (MDS) jest aktywowany przy użyciu jednej z dwóch problemów:  
  
-   Aby zmienić stan apartamentu COM wątku, który został już zainicjowany przez model COM do stanu apartamentu różnych podejmowana jest próba.  
  
-   Nieoczekiwana zmiana stanu apartamentu com. wątku.  
  
## <a name="symptoms"></a>Symptomy  
  
-   Stanem apartamentu COM wątku jest nie żądano. Może to spowodować, że serwery proxy do użycia dla składników COM, które ma inny niż bieżący model wątkowości. To z kolei może spowodować <xref:System.InvalidCastException> zostanie wygenerowany podczas wywoływania obiektu COM za pomocą interfejsów, które nie są skonfigurowane dla typu apartment między przekazywanie.  
  
-   Stanem apartamentu COM wątku jest inny niż oczekiwano. Może to spowodować <xref:System.Runtime.InteropServices.COMException> z HRESULT RPC_E_WRONG_THREAD, jak również <xref:System.InvalidCastException> podczas wprowadzania wywołuje w [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) (otoki RCW). Może to spowodować także niektóre jednowątkowe składniki COM można uzyskać dostęp przez wiele wątków jednocześnie, co może prowadzić do uszkodzenia lub utraty danych.  
  
## <a name="cause"></a>Przyczyna  
  
-   Wątek był poprzednio inicjowany do innego stanu apartamentu COM. Należy pamiętać, że można ustawić stanu apartamentu wątku jawnie lub niejawnie. Jawne operacji zalicza się <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> właściwości i <xref:System.Threading.Thread.SetApartmentState%2A> i <xref:System.Threading.Thread.TrySetApartmentState%2A> metody. Wątek, który został utworzony przy użyciu <xref:System.Threading.Thread.Start%2A> niejawnie ustawiono metodę <xref:System.Threading.ApartmentState.MTA> chyba że <xref:System.Threading.Thread.SetApartmentState%2A> jest wywoływana przed wątek jest uruchomiony. Można również niejawnie zainicjowano wątku głównego aplikacji <xref:System.Threading.ApartmentState.MTA> chyba że <xref:System.STAThreadAttribute> atrybut został określony dla metody main.  
  
-   `CoUninitialize` — Metoda (lub `CoInitializeEx` metody) z różnych współbieżności modelu jest wywoływana w wątku.  
  
## <a name="resolution"></a>Rozwiązanie  
 Ustawienie stanu apartamentu wątku, przed rozpoczęciem wykonywania lub zastosować jedną <xref:System.STAThreadAttribute> atrybutu lub <xref:System.MTAThreadAttribute> atrybut do metody głównej aplikacji.  
  
 Drugi Przyczyna najlepiej, jeśli kod, który odwołuje się `CoUninitialize` metody powinien zostać zmodyfikowany opóźnienia wywołanie, dopóki nie ma zakończenie wątku i nie ma żadnych RCWs i komponentów COM nadal używany przez wątek. Jednak jeśli nie jest możliwe zmodyfikować kod, który wywołuje `CoUninitialize` metody, a następnie RCWs nie powinien być używany z wątków, które są odinicjowany w ten sposób.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Stanem apartamentu COM bieżącego wątku i próbował wprowadzić kod stanu.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu pokazano sytuację, której można uaktywnić to zdarzenie MDA.  
  
```  
using System.Threading;  
namespace ApartmentStateMDA  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Thread.CurrentThread.SetApartmentState(ApartmentState.STA);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Przekazywanie międzyoperacyjne](../../../docs/framework/interop/interop-marshaling.md)
