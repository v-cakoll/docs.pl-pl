---
title: Konfigurowanie wartości limitów czasu w wiązaniu
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: f323dfff338f8a3ba24caab6df3b3916d3ae0d13
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773249"
---
# <a name="configuring-timeout-values-on-a-binding"></a>Konfigurowanie wartości limitów czasu w wiązaniu
Istnieje kilka ustawień limitu czasu są dostępne w powiązaniach WCF. Ustawienia te timeout ustawienia poprawnie ulepszyć nie tylko z usługą wydajność, ale również odtwarzania roli w użyteczność i zabezpieczeń usługi. Następujące limity czasu są dostępne na powiązaniami WCF:  
  
1. OpenTimeout  
  
2. closeTimeout  
  
3. SendTimeout  
  
4. ReceiveTimeout  
  
## <a name="wcf-binding-timeouts"></a>Powiązania WCF przekroczeń limitu czasu  
 Wszystkie ustawienia omówione w tym temacie są dokonywane na powiązanie, albo w kodzie lub konfiguracji. Poniższy kod pokazuje, jak programowo ustawić limity czasu w powiązaniu usługi WCF w kontekście samodzielnie hostowanej usługi.  
  
```csharp  
public static void Main()
{
    Uri baseAddress = new Uri("http://localhost/MyServer/MyService");
    
    try
    {
        ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService));
        
        WSHttpBinding binding = new WSHttpBinding();
        binding.OpenTimeout = new TimeSpan(0, 10, 0);
        binding.CloseTimeout = new TimeSpan(0, 10, 0);
        binding.SendTimeout = new TimeSpan(0, 10, 0);
        binding.ReceiveTimeout = new TimeSpan(0, 10, 0);
        
        serviceHost.AddServiceEndpoint("ICalculator", binding, baseAddress);
        serviceHost.Open();
        
        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();
    }
    catch (CommunicationException ex)
    {
        // Handle exception ...
    }
}
```  
  
 Poniższy przykład pokazuje, jak skonfigurować limity czasu w powiązaniu w pliku konfiguracji.  
  
```xml  
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding openTimeout="00:10:00" 
                 closeTimeout="00:10:00" 
                 sendTimeout="00:10:00" 
                 receiveTimeout="00:10:00">
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
 Więcej informacji na temat tych ustawień można znaleźć w dokumentacji dotyczącej <xref:System.ServiceModel.Channels.Binding> klasy.  
  
### <a name="client-side-timeouts"></a>Przekroczenia limitu czasu po stronie klienta  
 Po stronie klienta:  
  
1. Właściwości SendTimeout — używane do zainicjowania OperationTimeout, rządzące całego procesu wysyłania wiadomości, w tym odebranie komunikatu odpowiedzi dla operacji usługowej żądanie/nietypizowana odpowiedź. Tego limitu czasu ma również zastosowanie, podczas wysyłania komunikatów odpowiedzi z metodą kontrakt wywołania zwrotnego.  
  
2. OpenTimeout — które są używane podczas otwierania kanały, gdy określona jest wartość nie jawnego limitu czasu.  
  
3. CloseTimeout — używany podczas zamykania kanałów, gdy określona jest wartość limitu czasu jawne nie.  
  
4. ReceiveTimeout — nie jest używana.  
  
### <a name="service-side-timeouts"></a>Przekroczenia limitu czasu po stronie usługi  
 Na stronie usługi:  
  
1. Właściwości SendTimeout, OpenTimeout, CloseTimeout są takie same, jak na komputerze klienckim.  
  
2. ReceiveTimeout — używane przez warstwę Framework usługi do zainicjowania czasu bezczynności sesji, określający, jak długo sesja może być bezczynne przed przekroczeniem limitu czasu.
