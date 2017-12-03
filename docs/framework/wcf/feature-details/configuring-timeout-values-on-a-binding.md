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
ms.openlocfilehash: cd6206d3b9445b321230bf5968891773abcac9c5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="fe8a5-102">Konfigurowanie wartości limitów czasu w powiązaniu</span><span class="sxs-lookup"><span data-stu-id="fe8a5-102">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="fe8a5-103">Powiązania WCF ma dostępnych wiele ustawień limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="fe8a5-103">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="fe8a5-104">Ustawienie tych limitu czasu ustawienia poprawnie może zwiększyć nie tylko z usługą wydajności, ale również play rolę w zakresie użyteczności i zabezpieczeń usługi.</span><span class="sxs-lookup"><span data-stu-id="fe8a5-104">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="fe8a5-105">Następujące limity czasu są dostępne na powiązań WCF:</span><span class="sxs-lookup"><span data-stu-id="fe8a5-105">The following timeouts are available on WCF bindings:</span></span>  
  
1.  <span data-ttu-id="fe8a5-106">openTimeout</span><span class="sxs-lookup"><span data-stu-id="fe8a5-106">OpenTimeout</span></span>  
  
2.  <span data-ttu-id="fe8a5-107">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="fe8a5-107">CloseTimeout</span></span>  
  
3.  <span data-ttu-id="fe8a5-108">właściwości sendTimeout</span><span class="sxs-lookup"><span data-stu-id="fe8a5-108">SendTimeout</span></span>  
  
4.  <span data-ttu-id="fe8a5-109">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="fe8a5-109">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="fe8a5-110">Limity czasu wiązania WCF</span><span class="sxs-lookup"><span data-stu-id="fe8a5-110">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="fe8a5-111">Wszystkie ustawienia omówione w tym temacie są dokonywane na powiązanie, albo w konfiguracji lub kodu.</span><span class="sxs-lookup"><span data-stu-id="fe8a5-111">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="fe8a5-112">Poniższy kod przedstawia sposób programowane Ustawianie limitów czasu dla wiązania WCF w ramach samodzielnie hostowana usługa.</span><span class="sxs-lookup"><span data-stu-id="fe8a5-112">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
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
  
 <span data-ttu-id="fe8a5-113">Poniższy przykład pokazuje, jak skonfigurować limity czasu w powiązaniu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fe8a5-113">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="fe8a5-114">Więcej informacji na temat tych ustawień można znaleźć w dokumentacji dotyczącej <xref:System.ServiceModel.Channels.Binding> klasy.</span><span class="sxs-lookup"><span data-stu-id="fe8a5-114">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="fe8a5-115">Limity czasu po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="fe8a5-115">Client-side Timeouts</span></span>  
 <span data-ttu-id="fe8a5-116">Po stronie klienta:</span><span class="sxs-lookup"><span data-stu-id="fe8a5-116">On the client side:</span></span>  
  
1.  <span data-ttu-id="fe8a5-117">Właściwości SendTimeout — używaną do inicjalizacji OperationTimeout, rządzące całego procesu wysyłania wiadomości, w tym odbieranie komunikatu odpowiedzi dla operacji żądania/odpowiedzi usługi.</span><span class="sxs-lookup"><span data-stu-id="fe8a5-117">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="fe8a5-118">Ten limit czasu ma również zastosowanie, podczas wysyłania wiadomości odpowiedzi z metody kontrakt wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="fe8a5-118">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2.  <span data-ttu-id="fe8a5-119">OpenTimeout — używane podczas otwierania kanały, jeśli nie określono żadnej wartości limitu czasu jawne</span><span class="sxs-lookup"><span data-stu-id="fe8a5-119">OpenTimeout – used when opening channels when no explicit timeout value is specified</span></span>  
  
3.  <span data-ttu-id="fe8a5-120">CloseTimeout — używany podczas zamykania kanałów, jeśli nie określono żadnej wartości limitu czasu jawne</span><span class="sxs-lookup"><span data-stu-id="fe8a5-120">CloseTimeout – used when closing channels when no explicit timeout value is specified</span></span>  
  
4.  <span data-ttu-id="fe8a5-121">ReceiveTimeout — nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="fe8a5-121">ReceiveTimeout – is not used</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="fe8a5-122">Limity czasu po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="fe8a5-122">Service-side Timeouts</span></span>  
 <span data-ttu-id="fe8a5-123">Na stronie usługi:</span><span class="sxs-lookup"><span data-stu-id="fe8a5-123">On the service side:</span></span>  
  
1.  <span data-ttu-id="fe8a5-124">Właściwości SendTimeout, OpentTimeout, CloseTimeout są takie same, jak na komputerze klienckim</span><span class="sxs-lookup"><span data-stu-id="fe8a5-124">SendTimeout, OpentTimeout, CloseTimeout are the same as on the client</span></span>  
  
2.  <span data-ttu-id="fe8a5-125">ReceiveTimeout — używane przez warstwę Framework usługi można zainicjować limit czasu bezczynności sesji, która kontroluje, jak długo sesji może być bezczynne przed przekroczeniem limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="fe8a5-125">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
