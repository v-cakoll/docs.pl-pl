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
ms.openlocfilehash: ed4933ae59223c0674d2e36428894cbc3a07933f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052663"
---
# <a name="invalidapartmentstatechange-mda"></a>invalidApartmentStateChange MDA
Asystent `invalidApartmentStateChange` debugowania zarządzanego (MDS) jest uaktywniany z jednego z dwóch problemów:  
  
- Podjęto próbę zmiany stanu apartamentu COM wątku, który został już zainicjowany przez COM do innego stanu apartamentu.  
  
- Stan apartamentu COM wątku zmienia się nieoczekiwanie.  
  
## <a name="symptoms"></a>Symptomy  
  
- Stan apartamentu COM wątku nie jest żądaniem. Może to spowodować, że serwery proxy mają być używane dla składników COM, które mają model wątkowości inny niż bieżący. To z kolei może spowodować, <xref:System.InvalidCastException> że w przypadku wywoływania obiektu com za pomocą interfejsów, które nie są skonfigurowane do organizowania między różnymi komórkami.  
  
- Stan apartamentu COM wątku jest inny niż oczekiwano. Może to spowodować <xref:System.Runtime.InteropServices.COMException> wynik HRESULT of RPC_E_WRONG_THREAD, a także <xref:System.InvalidCastException> podczas wykonywania wywołań dla otoki (RCW) [środowiska uruchomieniowego](../../standard/native-interop/runtime-callable-wrapper.md) . Może to spowodować, że pewne składniki COM jednowątkowego są dostępne jednocześnie przez wiele wątków, co może prowadzić do uszkodzenia lub utraty danych.  
  
## <a name="cause"></a>Przyczyna  
  
- Wątek został wcześniej zainicjowany do innego stanu apartamentu COM. Należy zauważyć, że stan Apartment wątku może być ustawiony jawnie lub niejawnie. Operacje jawne obejmują <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> Właściwość <xref:System.Threading.Thread.SetApartmentState%2A> oraz metody i <xref:System.Threading.Thread.TrySetApartmentState%2A> . Wątek utworzony przy użyciu <xref:System.Threading.Thread.Start%2A> metody jest niejawnie ustawiony na <xref:System.Threading.ApartmentState.MTA> , chyba że <xref:System.Threading.Thread.SetApartmentState%2A> jest wywoływana przed uruchomieniem wątku. Główny wątek aplikacji jest również niejawnie zainicjowany <xref:System.Threading.ApartmentState.MTA> , <xref:System.STAThreadAttribute> chyba że atrybut jest określony w metodzie Main.  
  
- `CoUninitialize` Metoda (`CoInitializeEx` lub metoda) z innym modelem współbieżności jest wywoływana w wątku.  
  
## <a name="resolution"></a>Rozwiązanie  
 Ustaw stan apartamentu wątku przed rozpoczęciem jego wykonywania lub Zastosuj <xref:System.STAThreadAttribute> atrybut <xref:System.MTAThreadAttribute> lub atrybut do metody Main aplikacji.  
  
 Dla drugiej przyczyny, najlepiej, kod wywołujący `CoUninitialize` metodę należy zmodyfikować tak, aby opóźnić wywołanie do momentu zakończenia wątku, i nie RCW i ich bazowe składniki com nadal są używane przez wątek. Jednakże jeśli nie można zmodyfikować kodu wywołującego `CoUninitialize` metodę, nie należy używać RCW z wątków, które nie zostały zainicjowane w ten sposób.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Stan apartamentu modelu COM bieżącego wątku oraz stan, który próbuje zastosować kod.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sytuację, w której można aktywować to MDA.  
  
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
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
