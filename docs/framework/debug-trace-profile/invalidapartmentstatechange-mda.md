---
title: invalidApartmentStateChange MDA
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c201ab51c1af8a86fc1c2c4f80738007152b3bd9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122853"
---
# <a name="invalidapartmentstatechange-mda"></a>invalidApartmentStateChange MDA
`invalidApartmentStateChange` Zarządzanego Asystenta debugowania (MDS) została aktywowana przy użyciu jednej z dwa problemy:  
  
-   Aby zmienić stan apartamentu COM wątku, który został już zainicjowany przez model COM do stanu różnych apartamentu zostanie podjęta próba.  
  
-   Stan apartamentu COM wątek nieoczekiwanie ulega zmianie.  
  
## <a name="symptoms"></a>Symptomy  
  
-   Stan apartamentu COM wątku jest nie żądano. Może to spowodować, że serwery proxy ma być używany dla składników modelu COM, które mają inny niż bieżący model wątkowości. To z kolei może spowodować, że <xref:System.InvalidCastException> zostanie wygenerowany podczas wywoływania obiektu COM za pomocą interfejsów, które nie są skonfigurowane do szeregowanie między apartamentu.  
  
-   Stan apartamentu COM wątku jest inny niż oczekiwano. Może to spowodować <xref:System.Runtime.InteropServices.COMException> z HRESULT RPC_E_WRONG_THREAD, a także <xref:System.InvalidCastException> podczas wprowadzania wzywa [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW). Może to również spowodować niektóre jednowątkowe składniki COM można uzyskać dostęp przez wiele wątków, w tym samym czasie, co może prowadzić do uszkodzenia lub utraty danych.  
  
## <a name="cause"></a>Przyczyna  
  
-   Wątek był poprzednio inicjowany do innego stanu apartamentu COM. Należy pamiętać, że stan apartamentu wątku można ustawić jawnie lub niejawnie. Jawne operacje obejmują <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> właściwości i <xref:System.Threading.Thread.SetApartmentState%2A> i <xref:System.Threading.Thread.TrySetApartmentState%2A> metody. Wątek utworzone za pomocą <xref:System.Threading.Thread.Start%2A> niejawnie ustawiono metodę <xref:System.Threading.ApartmentState.MTA> chyba że <xref:System.Threading.Thread.SetApartmentState%2A> jest wywoływana przed wątek jest uruchomiony. Dodatkowo niejawnie zainicjowaniu wątku głównego aplikacji <xref:System.Threading.ApartmentState.MTA> chyba że <xref:System.STAThreadAttribute> atrybut jest określony w metodzie głównej.  
  
-   `CoUninitialize` — Metoda (lub `CoInitializeEx` metoda) ze współbieżnością inny model jest wywoływana w wątku.  
  
## <a name="resolution"></a>Rozwiązanie  
 Ustaw stan apartamentu wątku, przed rozpoczęciem, wykonania lub zastosować jedną <xref:System.STAThreadAttribute> atrybutu lub <xref:System.MTAThreadAttribute> atrybutu do metody głównej aplikacji.  
  
 Drugi przyczynę najlepiej, jeśli kod wywołująca `CoUninitialize` metody należy zmodyfikować, aby opóźnić wywołanie, aż wątek się zakończyć i nie ma żadnych RCW i komponentów COM nadal używany przez wątek. Jednakże jeśli nie jest możliwe zmodyfikować kod, który wywołuje `CoUninitialize` metody, a następnie RCW nie powinny być używane z wątków, które są niezainicjowana w ten sposób.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Stan apartamentu COM bieżącego wątku, a stan, który próbowano zastosować kodu.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu pokazano sytuację, która może aktywować to zdarzenie MDA.  
  
```csharp
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Organizowanie międzyoperacyjne](../../../docs/framework/interop/interop-marshaling.md)
