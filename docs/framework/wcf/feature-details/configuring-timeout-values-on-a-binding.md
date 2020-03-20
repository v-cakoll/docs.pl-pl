---
title: Konfigurowanie wartości limitów czasu w wiązaniu
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: 968e80bbd4b50d72d089a325f8e3fe498de2eac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185288"
---
# <a name="configuring-timeout-values-on-a-binding"></a>Konfigurowanie wartości limitów czasu w wiązaniu
Istnieje wiele ustawień limitu czasu dostępnych w WCF powiązania. Prawidłowe ustawienie tych ustawień limitu czasu może poprawić nie tylko wydajność usługi, ale także odgrywać rolę w użyteczności i bezpieczeństwie usługi. Następujące limity czasu są dostępne w powiązaniach WCF:  
  
1. Czas otwarcia  
  
2. Limit czasu zamknięcia  
  
3. Limit czasu wysyłania  
  
4. Receivetimeout  
  
## <a name="wcf-binding-timeouts"></a>Limity czasu wiązania WCF  
 Każde z ustawień omówionych w tym temacie są dokonywane na samo powiązanie, w kodzie lub konfiguracji. Poniższy kod pokazuje, jak programowo ustawić limity czasu na WCF powiązania w kontekście usługi hostowane samodzielnie.  
  
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
  
 W poniższym przykładzie pokazano, jak skonfigurować limity czasu na powiązanie w pliku konfiguracji.  
  
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
  
 Więcej informacji na temat tych ustawień można <xref:System.ServiceModel.Channels.Binding> znaleźć w dokumentacji dla klasy.  
  
### <a name="client-side-timeouts"></a>Limity czasu po stronie klienta  
 Po stronie klienta:  
  
1. SendTimeout — służy do inicjowania OperationTimeout, który reguluje cały proces wysyłania wiadomości, w tym odbieranie wiadomości odpowiedzi dla operacji usługi żądania/odpowiedzi. Ten limit czasu ma również zastosowanie podczas wysyłania wiadomości odpowiedzi z metody umowy wywołania zwrotnego.  
  
2. OpenTimeout — używany podczas otwierania kanałów, gdy nie określono jawnego limitu czasu.  
  
3. CloseTimeout — używane podczas zamykania kanałów, gdy nie określono jawnego limitu czasu.  
  
4. ReceiveTimeout – nie jest używany.  
  
### <a name="service-side-timeouts"></a>Limity czasu po stronie usługi  
 Po stronie serwisowej:  
  
1. SendTimeout, OpenTimeout, CloseTimeout są takie same jak na kliencie.  
  
2. ReceiveTimeout — używane przez warstwę Service Framework do inicjowania limitu czasu bezczynności sesji, który kontroluje, jak długo sesja może być bezczynny przed limit czasu.
