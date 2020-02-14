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
ms.openlocfilehash: 8acafcc2fba9a7d30cc77f25f06adaca7c79db32
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217417"
---
# <a name="invalidapartmentstatechange-mda"></a>invalidApartmentStateChange MDA
Asystent debugowania zarządzanego `invalidApartmentStateChange` (MDS) jest uaktywniany z jednego z dwóch problemów:  
  
- Podjęto próbę zmiany stanu apartamentu COM wątku, który został już zainicjowany przez COM do innego stanu apartamentu.  
  
- Stan apartamentu COM wątku zmienia się nieoczekiwanie.  
  
## <a name="symptoms"></a>Objawy  
  
- Stan apartamentu COM wątku nie jest żądaniem. Może to spowodować, że serwery proxy mają być używane dla składników COM, które mają model wątkowości inny niż bieżący. To z kolei może spowodować, że <xref:System.InvalidCastException> być zgłaszane podczas wywoływania obiektu COM za pomocą interfejsów, które nie są skonfigurowane do organizowania między komórkami.  
  
- Stan apartamentu COM wątku jest inny niż oczekiwano. Może to spowodować <xref:System.Runtime.InteropServices.COMException> z wartością HRESULT RPC_E_WRONG_THREAD, a także <xref:System.InvalidCastException> podczas wykonywania wywołań dla otoki wywołującej (otoka) [środowiska uruchomieniowego](../../standard/native-interop/runtime-callable-wrapper.md) . Może to spowodować, że pewne składniki COM jednowątkowego są dostępne jednocześnie przez wiele wątków, co może prowadzić do uszkodzenia lub utraty danych.  
  
## <a name="cause"></a>Przyczyna  
  
- Wątek został wcześniej zainicjowany do innego stanu apartamentu COM. Należy zauważyć, że stan Apartment wątku może być ustawiony jawnie lub niejawnie. Operacje jawne obejmują Właściwość <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> i metody <xref:System.Threading.Thread.SetApartmentState%2A> i <xref:System.Threading.Thread.TrySetApartmentState%2A>. Wątek utworzony przy użyciu metody <xref:System.Threading.Thread.Start%2A> jest niejawnie ustawiany na <xref:System.Threading.ApartmentState.MTA>, chyba że <xref:System.Threading.Thread.SetApartmentState%2A> jest wywoływana przed uruchomieniem wątku. Główny wątek aplikacji jest również niejawnie zainicjowany do <xref:System.Threading.ApartmentState.MTA>, chyba że atrybut <xref:System.STAThreadAttribute> jest określony w metodzie Main.  
  
- Metoda `CoUninitialize` (lub metoda `CoInitializeEx`) z innym modelem współbieżności jest wywoływana w wątku.  
  
## <a name="resolution"></a>Rozwiązanie  
 Ustaw stan apartamentu wątku przed rozpoczęciem jego wykonywania lub zastosuj atrybut <xref:System.STAThreadAttribute> lub atrybut <xref:System.MTAThreadAttribute> do głównej metody aplikacji.  
  
 W przypadku drugiej przyczyny, najlepiej, kod wywołujący metodę `CoUninitialize` należy zmodyfikować, aby opóźnić wywołanie do momentu zakończenia wątku i nie RCW i ich bazowe składniki COM nadal są używane przez wątek. Jednakże jeśli nie można zmodyfikować kodu wywołującego metodę `CoUninitialize`, nie należy używać RCW z wątków, które nie zostały zainicjowane w ten sposób.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
