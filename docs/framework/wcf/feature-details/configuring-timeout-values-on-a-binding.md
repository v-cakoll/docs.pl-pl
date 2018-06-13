---
title: Konfigurowanie wartości limitów czasu w powiązaniu
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: 21d99ad2ce092db738469f93e80c39380acabd00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489612"
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="7b5ad-102">Konfigurowanie wartości limitów czasu w powiązaniu</span><span class="sxs-lookup"><span data-stu-id="7b5ad-102">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="7b5ad-103">Powiązania WCF ma dostępnych wiele ustawień limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="7b5ad-103">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="7b5ad-104">Ustawienie tych limitu czasu ustawienia poprawnie może zwiększyć nie tylko z usługą wydajności, ale również play rolę w zakresie użyteczności i zabezpieczeń usługi.</span><span class="sxs-lookup"><span data-stu-id="7b5ad-104">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="7b5ad-105">Następujące limity czasu są dostępne na powiązań WCF:</span><span class="sxs-lookup"><span data-stu-id="7b5ad-105">The following timeouts are available on WCF bindings:</span></span>  
  
1.  <span data-ttu-id="7b5ad-106">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="7b5ad-106">OpenTimeout</span></span>  
  
2.  <span data-ttu-id="7b5ad-107">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="7b5ad-107">CloseTimeout</span></span>  
  
3.  <span data-ttu-id="7b5ad-108">właściwości sendTimeout</span><span class="sxs-lookup"><span data-stu-id="7b5ad-108">SendTimeout</span></span>  
  
4.  <span data-ttu-id="7b5ad-109">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="7b5ad-109">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="7b5ad-110">Limity czasu wiązania WCF</span><span class="sxs-lookup"><span data-stu-id="7b5ad-110">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="7b5ad-111">Wszystkie ustawienia omówione w tym temacie są dokonywane na powiązanie, albo w konfiguracji lub kodu.</span><span class="sxs-lookup"><span data-stu-id="7b5ad-111">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="7b5ad-112">Poniższy kod przedstawia sposób programowane Ustawianie limitów czasu dla wiązania WCF w ramach samodzielnie hostowana usługa.</span><span class="sxs-lookup"><span data-stu-id="7b5ad-112">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
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
  
 <span data-ttu-id="7b5ad-113">Poniższy przykład pokazuje, jak skonfigurować limity czasu w powiązaniu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7b5ad-113">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="7b5ad-114">Więcej informacji na temat tych ustawień można znaleźć w dokumentacji dotyczącej <xref:System.ServiceModel.Channels.Binding> klasy.</span><span class="sxs-lookup"><span data-stu-id="7b5ad-114">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="7b5ad-115">Limity czasu po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="7b5ad-115">Client-side Timeouts</span></span>  
 <span data-ttu-id="7b5ad-116">Po stronie klienta:</span><span class="sxs-lookup"><span data-stu-id="7b5ad-116">On the client side:</span></span>  
  
1.  <span data-ttu-id="7b5ad-117">Właściwości SendTimeout — używaną do inicjalizacji OperationTimeout, rządzące całego procesu wysyłania wiadomości, w tym odbieranie komunikatu odpowiedzi dla operacji żądania/odpowiedzi usługi.</span><span class="sxs-lookup"><span data-stu-id="7b5ad-117">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="7b5ad-118">Ten limit czasu ma również zastosowanie, podczas wysyłania wiadomości odpowiedzi z metody kontrakt wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="7b5ad-118">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2.  <span data-ttu-id="7b5ad-119">OpenTimeout — używane podczas otwierania kanały, jeśli nie określono żadnej wartości jawne limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="7b5ad-119">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3.  <span data-ttu-id="7b5ad-120">CloseTimeout — używany podczas zamykania kanałów, jeśli nie określono żadnej wartości jawne limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="7b5ad-120">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4.  <span data-ttu-id="7b5ad-121">ReceiveTimeout — nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="7b5ad-121">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="7b5ad-122">Limity czasu po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="7b5ad-122">Service-side Timeouts</span></span>  
 <span data-ttu-id="7b5ad-123">Na stronie usługi:</span><span class="sxs-lookup"><span data-stu-id="7b5ad-123">On the service side:</span></span>  
  
1.  <span data-ttu-id="7b5ad-124">Właściwości SendTimeout, OpenTimeout, CloseTimeout są takie same, jak na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="7b5ad-124">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2.  <span data-ttu-id="7b5ad-125">ReceiveTimeout — używane przez warstwę Framework usługi można zainicjować limit czasu bezczynności sesji, która kontroluje, jak długo sesji może być bezczynne przed przekroczeniem limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="7b5ad-125">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
