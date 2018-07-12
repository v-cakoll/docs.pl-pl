---
title: Aktywacja TCP
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: 9f08864c1d5139160ac25e0733ddcfc1c8557ad9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807413"
---
# <a name="tcp-activation"></a>Aktywacja TCP
W przykładzie pokazano obsługującego usługę korzystającą z usługi aktywacji procesów systemu Windows (WAS) można aktywować usługi, która komunikuje się za pomocą protokołu net.tcp. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`  
  
 Próbki składa się z konsoli programu klienckiego (.exe) i usługi biblioteki (.dll), hostowana w procesie roboczym aktywowany przez usługę WAS. Aktywność klienta jest widoczna w oknie konsoli.  
  
 Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź. Kontrakt jest definiowana za pomocą `ICalculator` interfejsu, który udostępnia operacji matematycznych (Dodawanie, odjąć mnożenia i dzielenia), jak pokazano w poniższym kodzie próbki:  
  
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
  
 Implementacja usługi oblicza i zwraca wynik w odpowiednich:  
  
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
  
 W przykładzie użyto wariant net.tcp powiązanie o włączone udostępnianie portów TCP i zabezpieczeń wyłączone. Jeśli chcesz użyć zabezpieczonych powiązanie TCP, Zmień tryb zabezpieczeń serwera na odpowiednie ustawienie i uruchom ponownie Svcutil.exe na kliencie, aby wygenerować plik konfiguracji aktualizacji klienta.  
  
 Poniższy przykład przedstawia konfigurację usługi:  
  
```xml  
<system.serviceModel>  
  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->  
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is explosed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexTcpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="PortSharingBinding" portSharingEnabled="true">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
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
  
 Punkt końcowy klienta jest skonfigurowane, jak pokazano na następujący kod:  
  
```xml  
<system.serviceModel>  
    <bindings>  
        <netTcpBinding>  
          <binding name="NetTcpBinding_ICalculator">  
            <security mode="None"/>  
          </binding>  
        </netTcpBinding>  
    </bindings>  
    <client>  
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"  
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />  
    </client>  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że [!INCLUDE[iisver](../../../../includes/iisver-md.md)] jest zainstalowany. [!INCLUDE[iisver](../../../../includes/iisver-md.md)] jest wymagany dla aktywacji WAS.  
  
2.  Pamiętaj, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
     Ponadto należy zainstalować składniki Aktywacja bez HTTP usług WCF:  
  
    1.  Z **Start** menu, wybierz **Panelu sterowania**.  
  
    2.  Wybierz **programy i funkcje**.  
  
    3.  Kliknij przycisk **Włącz składniki systemu Windows lub wyłącz**.  
  
    4.  Rozwiń węzeł **Microsoft .NET Framework 3.0** węzeł i wyboru **Aktywacja bez HTTP programu systemu Windows Communication Foundation** funkcji.  
  
3.  Skonfiguruj WAS do obsługi aktywacji TCP.  
  
     Dla wygody następujące dwa kroki są implementowane w pliku wsadowym o nazwie AddNetTcpSiteBinding.cmd znajduje się w katalogu próbki.  
  
    1.  Aby zapewnić obsługę aktywacji net.tcp, domyślnej witryny sieci Web musi zostać powiązana do portów net.tcp. Można to zrobić przy użyciu Appcmd.exe, który jest instalowany z zestawu narzędzi zarządzania usługi Internet Information Services 7.0 (IIS). Z wiersza polecenia z uprawnieniami administratora na poziomie uruchom następujące polecenie:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!TIP]
        >  To polecenie jest pojedynczy wiersz tekstu. To polecenie dodaje powiązania witryny net.tcp, do domyślnej witryny sieci Web nasłuchiwanie na porcie TCP 808 z dowolnej nazwy hosta.  
  
    2.  Mimo że wszystkie aplikacje w obrębie lokacji korzystają wspólnej powiązanie net.tcp, każdej aplikacji można włączyć obsługę net.tcp pojedynczo. Aby włączyć net.tcp dla aplikacji /servicemodelsamples, uruchom następujące polecenie z wiersza polecenia z uprawnieniami administratora na poziomie:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp  
        ```  
  
        > [!NOTE]
        >  To polecenie jest pojedynczy wiersz tekstu. To polecenie umożliwia aplikacji /servicemodelsamples uzyskać dostęp za pomocą obu http://localhost/servicemodelsamples i net.tcp://localhost/servicemodelsamples.  
  
4.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
     Usuń powiązanie witryny net.tcp, dodane dla tego przykładu.  
  
     Dla wygody następujące dwa kroki są implementowane w pliku wsadowym o nazwie RemoveNetTcpSiteBinding.cmd znajduje się w katalogu próbki.  
  
    1.  Usuń net.tcp z listy włączonych protokołów, uruchamiając następujące polecenie z wiersza polecenia z uprawnieniami administratora na poziomie:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  To polecenie należy wprowadzić jako pojedynczy wiersz tekstu.  
  
    2.  Usuń powiązanie witryny net.tcp, uruchamiając następujące polecenie z wiersza polecenia z uprawnieniami administratora na poziomie:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  To polecenie należy wpisać w jako pojedynczy wiersz tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
