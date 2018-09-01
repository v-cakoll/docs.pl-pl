---
title: Aktywacja TCP
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: c10cc1edfb06d55fc8a59a32bf905c95b20a19dc
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396106"
---
# <a name="tcp-activation"></a>Aktywacja TCP
Niniejszy przykład pokazuje usługi, który używa usługi aktywacji procesów Windows (WAS), aby aktywować usługę, która komunikuje się za pośrednictwem protokołu net.tcp hosta. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`  
  
 Przykład składa się z konsoli program kliencki (.exe) i usługi biblioteki (.dll), hostowana w procesie roboczym aktywowany przez WAS. Aktywność klienta jest widoczna w oknie konsoli.  
  
 Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź". Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (dodawania, odejmowania, mnożenia i dzielenia,) jak pokazano w poniższym przykładowym kodzie:  
  
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
  
 Implementacja usługi oblicza i zwraca odpowiedni wynik:  
  
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
  
 W przykładzie użyto wariant net.tcp, powiązanie z włączone udostępnianie portów TCP i zabezpieczeń wyłączona. Jeśli chcesz używać bezpiecznego powiązania protokołu TCP, Zmień tryb zabezpieczeń serwera na odpowiednie ustawienie i Svcutil.exe Uruchom ponownie na kliencie, aby wygenerować plik konfiguracji aktualizacji klienta.  
  
 Poniższy przykład pokazuje konfiguracji dla usługi:  
  
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
  
 Punkt końcowy klienta został skonfigurowany, jak pokazano w poniższym przykładowym kodzie:  
  
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
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że [!INCLUDE[iisver](../../../../includes/iisver-md.md)] jest zainstalowany. [!INCLUDE[iisver](../../../../includes/iisver-md.md)] jest wymagany do aktywacji WAS.  
  
2.  Pamiętaj, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
     Ponadto należy zainstalować składniki Aktywacja bez HTTP programu WCF:  
  
    1.  Z **Start** menu, wybierz **Panelu sterowania**.  
  
    2.  Wybierz **programy i funkcje**.  
  
    3.  Kliknij przycisk **włączyć składników Windows lub wyłączyć**.  
  
    4.  Rozwiń **Microsoft .NET Framework 3.0** węzła i wyboru **Aktywacja bez HTTP programu Windows Communication Foundation** funkcji.  
  
3.  Skonfiguruj WAS do obsługi aktywacji TCP.  
  
     Dla wygody następujące dwa kroki są implementowane w pliku wsadowym, o nazwie AddNetTcpSiteBinding.cmd znajduje się w katalogu próbki.  
  
    1.  Aby zapewnić obsługę aktywacji net.tcp, domyślna witryna sieci Web musi zostać powiązana portów net.tcp. Można to zrobić za pomocą Appcmd.exe, który jest instalowany z zestawem narzędzi zarządzania programu Internet Information Services 7.0 (IIS). Z wiersza polecenia z uprawnieniami administratora na poziomie uruchom następujące polecenie:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!TIP]
        >  To polecenie jest pojedynczy wiersz tekstu. To polecenie dodaje powiązanie witryny net.tcp, do domyślnej witryny sieci Web nasłuchiwanie na porcie TCP 808 przy użyciu dowolnej nazwy hosta.  
  
    2.  Mimo że wszystkie aplikacje w ramach lokacji mają wspólne powiązanie net.tcp, każdej aplikacji można włączyć obsługę net.tcp indywidualnie. Aby włączyć net.tcp aplikacji /servicemodelsamples, uruchom następujące polecenie z wiersza polecenia z uprawnieniami administratora na poziomie:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp  
        ```  
  
        > [!NOTE]
        >  To polecenie jest pojedynczy wiersz tekstu. To polecenie włącza aplikację /servicemodelsamples można uzyskać za pomocą zarówno http://localhost/servicemodelsamples i net.tcp://localhost/servicemodelsamples.  
  
4.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
     Usuń powiązanie witryny net.tcp, dodane dla tego przykładu.  
  
     Dla wygody następujące dwa kroki są implementowane w pliku wsadowym, o nazwie RemoveNetTcpSiteBinding.cmd znajduje się w katalogu próbki.  
  
    1.  Usuń z listy włączone protokoły net.tcp, uruchamiając następujące polecenie z wiersza polecenia z uprawnieniami administratora na poziomie:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  To polecenie muszą zostać wprowadzone jako pojedynczy wiersz tekstu.  
  
    2.  Usuń powiązanie witryny net.tcp, uruchamiając następujące polecenie z wiersza polecenia z uprawnieniami administratora na poziomie:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  To polecenie musi być wpisana w jako pojedynczy wiersz tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
