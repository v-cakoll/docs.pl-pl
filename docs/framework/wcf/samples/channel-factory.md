---
title: "Fabryka kanałów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6962cbbdd632ac9fa15253939ba2dad09eaf00de
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="channel-factory"></a>Fabryka kanałów
W tym przykładzie pokazano, jak utworzyć aplikację kliencką kanału o <xref:System.ServiceModel.ChannelFactory> klasy zamiast wygenerowanego klienta. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W przykładzie użyto <xref:System.ServiceModel.ChannelFactory%601> klasy w celu utworzenia kanału dla punktu końcowego. Zazwyczaj próba utworzenia kanału dla punktu końcowego generowania typ klienta z [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) i utworzyć wystąpienia typu wygenerowany. Można również utworzyć kanał za pomocą <xref:System.ServiceModel.ChannelFactory%601> klasy, jak pokazano w przykładzie. Usługa utworzony przez następujący przykładowy kod jest taki sam jak usługi w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
```  
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
WSHttpBinding binding = new WSHttpBinding();  
ChannelFactory<ICalculator> factory = new   
                    ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = factory.CreateChannel();  
```  
  
> [!IMPORTANT]
>  Jeśli korzystasz z tego przykładu w scenariuszu między komputerami, musisz zastąpić "localhost" w poprzednim kodzie pełną nazwę komputera, na którym jest uruchomiona usługa. W tym przykładzie nie korzysta z konfiguracji, aby ustawić adres punktu końcowego, tak aby to zrobić w kodzie.  
  
 Po utworzeniu kanału można wywołać operacji usługi, tak jak w przypadku wygenerowanego klienta.  
  
```  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
 Aby zamknąć kanał, jego musi najpierw można rzutować na <xref:System.ServiceModel.IClientChannel> interfejsu. Jest to spowodowane zadeklarowano kanału wygenerowane w aplikacji klienta przy użyciu `ICalculator` interfejs, który ma metody takie jak `Add` i `Subtract` , ale nie `Close`. `Close` Metody pochodzi z <xref:System.ServiceModel.ICommunicationObject> interfejsu.  
  
```  
// Close the channel.  
 ((IClientChannel)client).Close();  
```  
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć aplikacji klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Należy pamiętać, że w tym przykładzie umożliwiają publikowanie metadanych. Należy najpierw włączyć publikowanie metadanych dla tego przykładu, można ponownie wygenerować typu klienta.  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-cross-machine"></a>Aby uruchomić przykład cross maszyny  
  
1.  Zastąp wartość "localhost" w poniższym kodzie pełną nazwę komputera, na którym jest uruchomiona usługa.  
  
    ```  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  
  
## <a name="see-also"></a>Zobacz też
