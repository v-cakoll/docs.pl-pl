---
title: "Konfigurowanie wartości limitów czasu w powiązaniu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 164b4e3bff3e327b82c78c403a0e65ec8db744ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-timeout-values-on-a-binding"></a>Konfigurowanie wartości limitów czasu w powiązaniu
Powiązania WCF ma dostępnych wiele ustawień limitu czasu. Ustawienie tych limitu czasu ustawienia poprawnie może zwiększyć nie tylko z usługą wydajności, ale również play rolę w zakresie użyteczności i zabezpieczeń usługi. Następujące limity czasu są dostępne na powiązań WCF:  
  
1.  openTimeout  
  
2.  closeTimeout  
  
3.  właściwości sendTimeout  
  
4.  receiveTimeout  
  
## <a name="wcf-binding-timeouts"></a>Limity czasu wiązania WCF  
 Wszystkie ustawienia omówione w tym temacie są dokonywane na powiązanie, albo w konfiguracji lub kodu. Poniższy kod przedstawia sposób programowane Ustawianie limitów czasu dla wiązania WCF w ramach samodzielnie hostowana usługa.  
  
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
  
### <a name="client-side-timeouts"></a>Limity czasu po stronie klienta  
 Po stronie klienta:  
  
1.  Właściwości SendTimeout — używaną do inicjalizacji OperationTimeout, rządzące całego procesu wysyłania wiadomości, w tym odbieranie komunikatu odpowiedzi dla operacji żądania/odpowiedzi usługi. Ten limit czasu ma również zastosowanie, podczas wysyłania wiadomości odpowiedzi z metody kontrakt wywołania zwrotnego.  
  
2.  OpenTimeout — używane podczas otwierania kanały, jeśli nie określono żadnej wartości limitu czasu jawne  
  
3.  CloseTimeout — używany podczas zamykania kanałów, jeśli nie określono żadnej wartości limitu czasu jawne  
  
4.  ReceiveTimeout — nie jest używany.  
  
### <a name="service-side-timeouts"></a>Limity czasu po stronie serwera  
 Na stronie usługi:  
  
1.  Właściwości SendTimeout, OpentTimeout, CloseTimeout są takie same, jak na komputerze klienckim  
  
2.  ReceiveTimeout — używane przez warstwę Framework usługi można zainicjować limit czasu bezczynności sesji, która kontroluje, jak długo sesji może być bezczynne przed przekroczeniem limitu czasu.
