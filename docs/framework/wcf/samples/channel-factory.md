---
title: Fabryka kanałów
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: 6bf0668c6b846671db12dc20465ee70137d70b35
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43442762"
---
# <a name="channel-factory"></a>Fabryka kanałów
Niniejszy przykład pokazuje, jak utworzyć aplikację kliencką kanału o <xref:System.ServiceModel.ChannelFactory> klasy zamiast wygenerowanego klienta. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 W tym przykładzie użyto <xref:System.ServiceModel.ChannelFactory%601> klasy w celu utworzenia kanału do punktu końcowego usługi. Zazwyczaj próba utworzenia kanału do punktu końcowego usługi generowania typ klienta, za pomocą [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) i utworzyć wystąpienie typu wygenerowany. Można również utworzyć kanał za pomocą <xref:System.ServiceModel.ChannelFactory%601> klasy, jak pokazano w tym przykładzie. Usługi utworzone przez następujący przykładowy kod jest identyczny z usługą w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
```csharp  
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
WSHttpBinding binding = new WSHttpBinding();  
ChannelFactory<ICalculator> factory = new   
                    ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = factory.CreateChannel();  
```  
  
> [!IMPORTANT]
>  Jeśli korzystasz z tego przykładu w scenariuszu między komputerami, musisz zastąpić "localhost" w poprzednim kodzie za pomocą w pełni kwalifikowana nazwa maszyny, na którym jest uruchomiona usługa. W tym przykładzie nie używa konfiguracji można ustawić adresu punktu końcowego, więc jest to niezbędne w kodzie.  
  
 Po utworzeniu kanału operacji usługi może być wywoływany podobnie jak w przypadku wygenerowanego klienta.  
  
```csharp  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
 Aby zamknąć okno kanał, jego musi najpierw można rzutować <xref:System.ServiceModel.IClientChannel> interfejsu. Jest to spowodowane kanału, w miarę generowania jest zadeklarowana w aplikacji klienta przy użyciu `ICalculator` interfejs, który posiada metody takie jak `Add` i `Subtract` , ale nie `Close`. `Close` Metody pochodzi z <xref:System.ServiceModel.ICommunicationObject> interfejsu.  
  
```csharp  
// Close the channel.  
 ((IClientChannel)client).Close();  
```  
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta do zamykania aplikacji klienckiej.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Należy pamiętać, że w tym przykładzie umożliwiają publikowanie metadanych. Należy najpierw włączyć publikowanie metadanych dla tego przykładu ponownie wygenerować typu klienta.  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-cross-machine"></a>Aby uruchomić przykład krzyżowe maszyny  
  
1.  Zastąp "localhost", w poniższym kodzie w pełni kwalifikowana nazwa maszyny, na którym jest uruchomiona usługa.  
  
    ```csharp  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  
  
## <a name="see-also"></a>Zobacz też
