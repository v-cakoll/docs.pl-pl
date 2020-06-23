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
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="40918-103">Konfigurowanie wartości limitów czasu w wiązaniu</span><span class="sxs-lookup"><span data-stu-id="40918-103">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="40918-104">W powiązaniach WCF dostępne są wiele ustawień limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="40918-104">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="40918-105">Poprawne ustawienie tych ustawień limitu czasu może poprawić nie tylko wydajność usługi, ale również odgrywać rolę w zakresie użyteczności i bezpieczeństwa usługi.</span><span class="sxs-lookup"><span data-stu-id="40918-105">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="40918-106">W powiązaniach WCF są dostępne następujące limity czasu:</span><span class="sxs-lookup"><span data-stu-id="40918-106">The following timeouts are available on WCF bindings:</span></span>  
  
1. <span data-ttu-id="40918-107">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="40918-107">OpenTimeout</span></span>  
  
2. <span data-ttu-id="40918-108">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="40918-108">CloseTimeout</span></span>  
  
3. <span data-ttu-id="40918-109">Właściwości SendTimeout</span><span class="sxs-lookup"><span data-stu-id="40918-109">SendTimeout</span></span>  
  
4. <span data-ttu-id="40918-110">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="40918-110">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="40918-111">Limity czasu powiązania WCF</span><span class="sxs-lookup"><span data-stu-id="40918-111">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="40918-112">Wszystkie ustawienia omówione w tym temacie są wykonywane w ramach powiązania w kodzie lub konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="40918-112">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="40918-113">Poniższy kod pokazuje, jak programowo ustawiać limity czasu dla powiązania WCF w kontekście usługi samodzielnej.</span><span class="sxs-lookup"><span data-stu-id="40918-113">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
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
  
 <span data-ttu-id="40918-114">Poniższy przykład pokazuje, jak skonfigurować limity czasu dla powiązania w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="40918-114">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="40918-115">Więcej informacji o tych ustawieniach można znaleźć w dokumentacji <xref:System.ServiceModel.Channels.Binding> klasy.</span><span class="sxs-lookup"><span data-stu-id="40918-115">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="40918-116">Limity czasu po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="40918-116">Client-side Timeouts</span></span>  
 <span data-ttu-id="40918-117">Po stronie klienta:</span><span class="sxs-lookup"><span data-stu-id="40918-117">On the client side:</span></span>  
  
1. <span data-ttu-id="40918-118">Właściwości SendTimeout — służy do inicjowania OperationTimeout, który reguluje cały proces wysyłania komunikatu, w tym otrzymywanie komunikatu odpowiedzi dla operacji usługi żądania/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="40918-118">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="40918-119">Ten limit czasu obowiązuje również podczas wysyłania komunikatów odpowiedzi z metody kontraktu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="40918-119">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2. <span data-ttu-id="40918-120">OpenTimeout — używane podczas otwierania kanałów, gdy nie określono jawnej wartości limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="40918-120">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3. <span data-ttu-id="40918-121">CloseTimeout — używany podczas zamykania kanałów, gdy nie określono jawnej wartości limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="40918-121">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4. <span data-ttu-id="40918-122">ReceiveTimeout — nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="40918-122">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="40918-123">Limity czasu po stronie usługi</span><span class="sxs-lookup"><span data-stu-id="40918-123">Service-side Timeouts</span></span>  
 <span data-ttu-id="40918-124">Po stronie usługi:</span><span class="sxs-lookup"><span data-stu-id="40918-124">On the service side:</span></span>  
  
1. <span data-ttu-id="40918-125">Właściwości SendTimeout, OpenTimeout, CloseTimeout są takie same jak na kliencie.</span><span class="sxs-lookup"><span data-stu-id="40918-125">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2. <span data-ttu-id="40918-126">ReceiveTimeout — używana przez warstwę struktury usługi do inicjowania limitu czasu bezczynności sesji, która określa, jak długo sesja może być bezczynna przed upływem limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="40918-126">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
