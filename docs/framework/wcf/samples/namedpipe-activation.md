---
title: Aktywowanie elementu NamedPipe
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2d7c722078947e86e677f57c67d87ba69a0f524
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="namedpipe-activation"></a>Aktywowanie elementu NamedPipe
W przykładzie pokazano obsługującego usługę korzystającą z usługi aktywacji procesów systemu Windows (WAS) można aktywować usługi, która komunikuje się za pośrednictwem potoków nazwy. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i wymaga [!INCLUDE[wv](../../../../includes/wv-md.md)] do uruchomienia.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Próbki składa się z konsoli programu klienckiego (.exe) i usługi biblioteki (.dll), hostowana w procesie roboczym aktywowany przez usługi aktywacji procesów systemu Windows (WAS). Aktywność klienta jest widoczna w oknie konsoli.  
  
 Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź. Kontrakt jest definiowana za pomocą `ICalculator` interfejsu, który udostępnia operacji matematycznych (Dodawanie, odjąć mnożenia i dzielenia), jak pokazano w poniższym kodzie próbki.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 Klient wysyła żądań synchronicznych operacji matematycznych danego i implementacji usługi jest obliczana i zwraca odpowiedni wynik.  
  
```  
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 W przykładzie użyto zmodyfikowanych `netNamedPipeBinding` powiązania z żadnych zabezpieczeń. Powiązanie jest określona w plikach konfiguracji dla klienta i usługi. Typ powiązania dla usługi jest określony w elemencie endpoint `binding` atrybutu, jak pokazano w poniższych Przykładowa konfiguracja.  
  
 Jeśli chcesz użyć wiązania zabezpieczonych nazwany potok, Zmień tryb zabezpieczeń serwera z ustawieniem wymaganymi i ponownie uruchom svcutil.exe na kliencie, aby uzyskać zaktualizowanego klienta z pliku konfiguracji.  
  
```xml  
<system.serviceModel>  
        <services>  
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
  
        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->  
        <endpoint address=""   
                  binding="netNamedPipeBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is explosed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexNamedPipeBinding"  
                  contract="IMetadataExchange" />  
      </service>  
        </services>      
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="Binding1" >  
                    <security mode = "None">  
                    </security>  
                </binding >  
            </netNamedPipeBinding>  
        </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 Informacje o punkcie końcowym klienta jest skonfigurowane, jak pokazano na następujący przykładowy kod.  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <endpoint name=""  
                          address="net.pipe://localhost/servicemodelsamples/service.svc"   
                          binding="netNamedPipeBinding"   
                          bindingConfiguration="Binding1"   
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
    <bindings>  
  
      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.  
            Each property is configured with the default value.   -->  
  
      <netNamedPipeBinding>  
        <binding name="Binding1"   
                         maxBufferSize="65536"  
                         maxConnections="10">  
          <security mode = "None">  
          </security>  
        </binding >  
  
      </netNamedPipeBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że [!INCLUDE[iisver](../../../../includes/iisver-md.md)] jest zainstalowany. [!INCLUDE[iisver](../../../../includes/iisver-md.md)]jest wymagany dla aktywacji WAS.  
  
2.  Upewnij się, można zlecić [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
     Ponadto należy zainstalować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składniki Aktywacja bez HTTP:  
  
    1.  Z **Start** menu, wybierz **Panelu sterowania**.  
  
    2.  Wybierz **programy i funkcje**.  
  
    3.  Kliknij przycisk **Włącz składniki systemu Windows lub wyłącz**.  
  
    4.  Rozwiń węzeł **Microsoft .NET Framework 3.0** węzeł i wyboru **Aktywacja bez HTTP programu systemu Windows Communication Foundation** funkcji.  
  
3.  Skonfiguruj Windows Process Activation Service (WAS) do obsługi aktywacji nazwanego potoku.  
  
     Dla wygody następujące dwa kroki są implementowane w pliku wsadowym o nazwie AddNetPipeSiteBinding.cmd znajduje się w katalogu próbki.  
  
    1.  Aby zapewnić obsługę aktywacji usługi net.pipe, domyślnej witryny sieci Web musi zostać powiązana protokołu usługi net.pipe. Można to zrobić przy użyciu appcmd.exe, który jest instalowany z zestawu narzędzi zarządzania usług IIS 7.0. Z wiersza polecenia z podniesionymi uprawnieniami (administrator) uruchom następujące polecenie.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  To polecenie jest pojedynczy wiersz tekstu.  
  
         To polecenie dodaje powiązania witryny usługi net.pipe do domyślnej witryny sieci Web.  
  
    2.  Mimo że wszystkie aplikacje w obrębie lokacji korzystają wspólnej powiązania usługi net.pipe, każdej aplikacji można włączyć obsługę usługi net.pipe pojedynczo. Aby włączyć usługi net.pipe aplikacji /servicemodelsamples, uruchom następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe  
        ```  
  
        > [!NOTE]
        >  To polecenie jest pojedynczy wiersz tekstu.  
  
         To polecenie włącza /servicemodelsamples aplikacji można uzyskać dostęp, używając http://localhost/servicemodelsamples i net.tcp://localhost/servicemodelsamples.  
  
4.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Usuń powiązanie witryny usługi net.pipe, dodane dla tego przykładu.  
  
     Dla wygody następujące dwa kroki są wykonywane w pliku wsadowym o nazwie RemoveNetPipeSiteBinding.cmd znajduje się w katalogu próbki:  
  
    1.  Usuń net.tcp z listy włączonych protokołów, uruchamiając następujące polecenie z wiersza polecenia o podniesionych uprawnieniach.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  To polecenie należy wprowadzić jako pojedynczy wiersz tekstu.  
  
    2.  Usuń powiązanie witryny net.tcp, uruchamiając następujące polecenie z wiersza polecenia o podniesionych uprawnieniach.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  To polecenie należy wpisać w jako pojedynczy wiersz tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
