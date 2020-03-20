---
title: Weryfikacja zabezpieczeń
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: 17e6e250c6b345477f7c9b377eb8e16ff4331ca7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183381"
---
# <a name="security-validation"></a>Weryfikacja zabezpieczeń
W tym przykładzie pokazano, jak używać zachowania niestandardowego do sprawdzania poprawności usług na komputerze, aby upewnić się, że spełniają określone kryteria. W tym przykładzie usługi są sprawdzane przez zachowanie niestandardowe przez skanowanie za pośrednictwem każdego punktu końcowego w usłudze i sprawdzanie, czy zawierają one bezpieczne elementy wiązania. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="endpoint-validation-custom-behavior"></a>Zachowanie niestandardowe sprawdzania poprawności punktu końcowego  
 Dodając kod użytkownika `Validate` do metody zawartej w interfejsie, <xref:System.ServiceModel.Description.IServiceBehavior> zachowanie niestandardowe można nadawać do usługi lub punktu końcowego do wykonywania akcji zdefiniowanych przez użytkownika. Poniższy kod jest używany do pętli przez każdy punkt końcowy zawarty w usłudze, która przeszukuje ich kolekcje powiązania dla bezpiecznych powiązań.  
  
```csharp
public void Validate(ServiceDescription serviceDescription,
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually, gathering their
    // binding elements.  
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
  
 Dodanie następującego kodu do pliku Web.config dodaje rozszerzenie `serviceValidate` zachowania dla usługi do rozpoznania.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 Po dodaniu rozszerzenia zachowania do usługi można teraz `endpointValidate` dodać zachowanie do listy zachowań w pliku Web.config, a tym samym do usługi.  
  
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
  
 Zachowania i ich rozszerzenia, które są dodawane do pliku Web.config, stosują zachowanie do poszczególnych usług, podczas gdy po dodaniu do pliku Machine.config stosuje się zachowanie do każdej usługi aktywnej na komputerze.  
  
> [!NOTE]
> Podczas dodawania zachowania do wszystkich usług, zaleca się, aby wykonać kopię zapasową pliku Machine.config przed wprowadzeniem jakichkolwiek zmian.  
  
 Teraz uruchom klienta podanego w katalogu client\bin tego przykładu. Wyjątek występuje z następującym komunikatem: "Żądana usługa ' 'http://localhost/servicemodelsamples/service.svcnie można aktywować." Jest to oczekiwane, ponieważ punkt końcowy jest uważany za niebezpieczny przez zachowanie sprawdzania poprawności punktu końcowego i uniemożliwia uruchamianie usługi. Zachowanie zgłasza również wewnętrzny wyjątek, który opisuje, który punkt końcowy jest niebezpieczny i zapisuje komunikat do podglądu zdarzeń systemu w obszarze "System.ServiceModel 4.0.0.0" źródło i "WebHost" kategorii. Istnieje również możliwość włączenia śledzenia w usłudze w tym przykładzie. Dzięki temu użytkownik może wyświetlić wyjątki zgłaszane przez zachowanie sprawdzania poprawności punktu końcowego, otwierając wynikowe ślady usługi za pomocą narzędzia Podgląd śledzenia usług.  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>Aby wyświetlić komunikaty wyjątków sprawdzania poprawności nie powiodło się w Podglądzie zdarzeń  
  
1. Kliknij menu **Start** i wybierz polecenie **Uruchom...**.  
  
2. Wpisz `eventvwr` i kliknij przycisk **OK**.  
  
3. W oknie Podgląd zdarzeń kliknij pozycję **Aplikacja**.  
  
4. Kliknij dwukrotnie niedawno dodane zdarzenie "System.ServiceModel 4.0.0.0" w kategorii "WebHost" w oknie **Aplikacji,** aby wyświetlić niezabezpieczone komunikaty punktu końcowego.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>Zobacz też

- [Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
