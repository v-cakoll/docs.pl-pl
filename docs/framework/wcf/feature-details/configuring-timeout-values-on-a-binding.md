---
title: Konfigurowanie wartości limitów czasu w wiązaniu
description: Dowiedz się, jak zarządzać ustawieniami limitu czasu dla powiązań programu WCF w celu zwiększenia wydajności, użyteczności i zabezpieczeń usługi.
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: c41824a242d9b42290183cd70b9acf5b8ee59e6b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245118"
---
# <a name="configuring-timeout-values-on-a-binding"></a>Konfigurowanie wartości limitów czasu w wiązaniu
W powiązaniach WCF dostępne są wiele ustawień limitu czasu. Poprawne ustawienie tych ustawień limitu czasu może poprawić nie tylko wydajność usługi, ale również odgrywać rolę w zakresie użyteczności i bezpieczeństwa usługi. W powiązaniach WCF są dostępne następujące limity czasu:  
  
1. OpenTimeout  
  
2. CloseTimeout  
  
3. Właściwości SendTimeout  
  
4. ReceiveTimeout  
  
## <a name="wcf-binding-timeouts"></a>Limity czasu powiązania WCF  
 Wszystkie ustawienia omówione w tym temacie są wykonywane w ramach powiązania w kodzie lub konfiguracji. Poniższy kod pokazuje, jak programowo ustawiać limity czasu dla powiązania WCF w kontekście usługi samodzielnej.  
  
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
  
 Poniższy przykład pokazuje, jak skonfigurować limity czasu dla powiązania w pliku konfiguracji.  
  
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
  
 Więcej informacji o tych ustawieniach można znaleźć w dokumentacji <xref:System.ServiceModel.Channels.Binding> klasy.  
  
### <a name="client-side-timeouts"></a>Limity czasu po stronie klienta  
 Po stronie klienta:  
  
1. Właściwości SendTimeout — służy do inicjowania OperationTimeout, który reguluje cały proces wysyłania komunikatu, w tym otrzymywanie komunikatu odpowiedzi dla operacji usługi żądania/odpowiedzi. Ten limit czasu obowiązuje również podczas wysyłania komunikatów odpowiedzi z metody kontraktu wywołania zwrotnego.  
  
2. OpenTimeout — używane podczas otwierania kanałów, gdy nie określono jawnej wartości limitu czasu.  
  
3. CloseTimeout — używany podczas zamykania kanałów, gdy nie określono jawnej wartości limitu czasu.  
  
4. ReceiveTimeout — nie jest używany.  
  
### <a name="service-side-timeouts"></a>Limity czasu po stronie usługi  
 Po stronie usługi:  
  
1. Właściwości SendTimeout, OpenTimeout, CloseTimeout są takie same jak na kliencie.  
  
2. ReceiveTimeout — używana przez warstwę struktury usługi do inicjowania limitu czasu bezczynności sesji, która określa, jak długo sesja może być bezczynna przed upływem limitu czasu.
