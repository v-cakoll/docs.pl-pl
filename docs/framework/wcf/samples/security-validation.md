---
title: "Walidacja zabezpieczeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
caps.latest.revision: "35"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 86a10a4117a5bbeb48e9d1d15b1ce8da9d7c7751
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="security-validation"></a>Walidacja zabezpieczeń
W tym przykładzie przedstawiono sposób użycia niestandardowego zachowania do sprawdzania poprawności usług na komputerze, aby upewnić się, że spełniają określone kryteria. W tym przykładzie usług są weryfikowane przez niestandardowe działanie przez skanowanie za pomocą każdego punktu końcowego w usłudze i sprawdzanie, czy zawierają one elementy bezpiecznego powiązania. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="endpoint-validation-custom-behavior"></a>Niestandardowe zachowanie weryfikacji punktu końcowego  
 Dodając kod użytkownika do `Validate` metody zawarte w <xref:System.ServiceModel.Description.IServiceBehavior> interfejsu, niestandardowe zachowanie można przydzielić do usługi lub punkt końcowy do wykonania akcji zdefiniowane przez użytkownika. Poniższy kod służy do pętli każdego punktu końcowego objętych usługą, które wyszukiwania za pomocą ich kolekcji powiązanie dla bezpiecznego powiązania.  
  
```  
public void Validate(ServiceDescription serviceDescription,   
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually gathering their    
       binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =   
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any   
        // secure binding elements. Transport, Asymmetric, and Symmetric      
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 Dodawanie następujący kod do pliku Web.config dodaje `serviceValidate` rozszerzenia zachowania usługi do rozpoznania.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 Po dodaniu rozszerzenia zachowania do usługi jest teraz można dodać `endpointValidate` zachowania do listy zachowania w pliku Web.config i w związku z tym do usługi.  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 Zachowania i ich rozszerzeń, które są dodawane do pliku Web.config dotyczą zachowania poszczególnych usług, podczas gdy dodany do pliku Machine.config zastosować zachowanie do każdej usługi, które są aktywne na komputerze.  
  
> [!NOTE]
>  Podczas dodawania zachowania do wszystkich usług, zalecane jest aby utworzyć kopię zapasową pliku Machine.config przed wprowadzeniem zmian.  
  
 Teraz z klientem w katalogu client\bin tego przykładu. Wyjątek ma występuje następujący komunikat o błędzie: "żądanej usługi nie można aktywować"http://localhost/servicemodelsamples/service.svc"." Oczekuje się, ponieważ przyjęto, że punkt końcowy jest niebezpieczne przez punkt końcowy, sprawdzanie poprawności zachowania i uniemożliwia uruchomienie usługi. Zachowanie również zgłasza wyjątek wewnętrzny, który opisano, który punkt końcowy jest niebezpieczne i zapisuje komunikat do systemu Podglądu zdarzeń w źródle "System.ServiceModel 4.0.0.0" oraz kategorii "WebHost". Użytkownik może również włączyć śledzenie usługi, w tym przykładzie. Dzięki temu użytkownikowi na wyświetlanie wyjątki wyrzucane przez działanie sprawdzania poprawności punktu końcowego, otwierając wynikowy ślady usługi za pomocą narzędzia podglądu śledzenia usługi.  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>Aby wyświetlić nie powiodło się komunikaty o wyjątku weryfikacji punktu końcowego w Podglądzie zdarzeń  
  
1.  Kliknij przycisk **Start** menu i wybierz **Uruchom...** .  
  
2.  Typ `eventvwr` i kliknij przycisk **OK**.  
  
3.  W oknie Podgląd zdarzeń, kliknij przycisk **aplikacji**.  
  
4.  Kliknij dwukrotnie zdarzenie ostatnio dodane "System.ServiceModel 4.0.0.0" w kategorii "WebHost" w **aplikacji** okna, aby wyświetlić komunikaty niezabezpieczonych punktu końcowego.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
