---
title: BasicBinding
ms.date: 03/30/2017
ms.assetid: 86fbeb87-4d89-4b61-9577-867e0ac12945
ms.openlocfilehash: e98b1254710ebac2305fd7dd5d39a146d749ff44
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990135"
---
# <a name="basicbinding"></a>BasicBinding

Ten przykład ilustruje użycie `basicHttpBinding` usługi, która zapewnia komunikację HTTP i maksymalną współdziałanie z usługami sieci Web pierwszej i drugiej generacji.

> [!NOTE]
> Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\Http`

## <a name="sample-details"></a>Przykładowe szczegóły

Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora.

Aby użyć podstawowego powiązania z zachowaniem domyślnym, wymagana jest tylko nazwa sekcji powiązania. Jeśli chcesz skonfigurować powiązanie podstawowe i zmienić niektóre z jego ustawień, musisz zdefiniować konfigurację powiązania. Punkt końcowy musi odwoływać się do konfiguracji powiązania przez nazwę przy `bindingConfiguration` użyciu atrybutu > <`endpoint`elementu, jak pokazano w poniższym przykładowym kodzie.

```xml
<services>
    <service
        type="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
       <endpoint address=""
             binding="basicHttpBinding"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
</services>
```

W tym przykładzie Konfiguracja powiązania ma nazwę `"Binding1"` i jest zdefiniowana, jak pokazano w poniższym przykładzie kodu.

```xml
<bindings>
   <basicHttpBinding>
      <binding name="Binding1"
               hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true" >
         <security mode="None" />
      </binding>
   </basicHttpBinding>
</bindings>
```

Element Binding zawiera atrybuty służące do ustawiania trybu porównywania nazw hostów, maksymalny rozmiar komunikatu, opcje serwera proxy, limity czasu, kodowanie wiadomości i inne opcje.

Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

3. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).
