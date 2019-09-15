---
title: Fabryka kanałów
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: 9b754531059e367a8102a96cfb50b6147da84978
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990093"
---
# <a name="channel-factory"></a>Fabryka kanałów

Ten przykład pokazuje, <xref:System.ServiceModel.ChannelFactory> jak aplikacja kliencka może utworzyć kanał z klasą zamiast wygenerowanego klienta. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

Ten przykład używa <xref:System.ServiceModel.ChannelFactory%601> klasy w celu utworzenia kanału do punktu końcowego usługi. Zazwyczaj w celu utworzenia kanału w punkcie końcowym usługi wygenerowany typ klienta za pomocą narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) i Utwórz wystąpienie wygenerowanego typu. Kanał można również utworzyć za pomocą <xref:System.ServiceModel.ChannelFactory%601> klasy, jak pokazano w tym przykładzie. Usługa utworzona przez następujący przykładowy kod jest taka sama jak usługa w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).

```csharp
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
WSHttpBinding binding = new WSHttpBinding();
ChannelFactory<ICalculator> factory = new
                    ChannelFactory<ICalculator>(binding, address);
ICalculator channel = factory.CreateChannel();
```

> [!IMPORTANT]
> Jeśli używasz tego przykładu w scenariuszu między maszynami, musisz zastąpić "localhost" w powyższym kodzie za pomocą w pełni kwalifikowanej nazwy komputera, na którym działa usługa. Ten przykład nie używa konfiguracji do ustawienia adresu punktu końcowego, dlatego należy to zrobić w kodzie.

Po utworzeniu kanału operacje usługi mogą być wywoływane tak samo jak z wygenerowanym klientem.

```csharp
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = channel.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

Aby zamknąć kanał, najpierw należy go rzutować do <xref:System.ServiceModel.IClientChannel> interfejsu. Wynika to z faktu, że kanał jako wygenerowany jest zadeklarowany w aplikacji `ICalculator` klienckiej przy użyciu interfejsu, `Add` który ma metody `Close`takie jak i, `Subtract` ale nie. `Close` Metoda pochodzi<xref:System.ServiceModel.ICommunicationObject> z interfejsu.

```csharp
// Close the channel.
 ((IClientChannel)client).Close();
```

Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć aplikację kliencką.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Należy zauważyć, że ten przykład nie umożliwia publikowania metadanych. Najpierw należy włączyć Publikowanie metadanych dla tego przykładu w celu ponownego wygenerowania typu klienta.

3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-cross-machine"></a>Aby uruchomić przykładową maszynę

1. Zastąp wartość "localhost" w następującym kodzie z w pełni kwalifikowaną nazwą komputera, na którym działa usługa.

    ```csharp
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
    ```

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`
