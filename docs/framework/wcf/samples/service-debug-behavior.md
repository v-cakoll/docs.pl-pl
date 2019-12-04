---
title: Zachowanie debugowania usług
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 6a0a1c5d9f9741da978c633d35ea1e39664bed5b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716305"
---
# <a name="service-debug-behavior"></a><span data-ttu-id="a2bb2-102">Zachowanie debugowania usług</span><span class="sxs-lookup"><span data-stu-id="a2bb2-102">Service Debug Behavior</span></span>

<span data-ttu-id="a2bb2-103">Ten przykład pokazuje, jak można skonfigurować ustawienia zachowania debugowania usługi.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-103">This sample demonstrates how service debug behavior settings can be configured.</span></span> <span data-ttu-id="a2bb2-104">Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje kontrakt usługi `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="a2bb2-105">Ten przykład jawnie definiuje zachowanie debugowania usługi w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-105">This sample explicitly defines service debug behavior in the configuration file.</span></span> <span data-ttu-id="a2bb2-106">Można go również wykonać bezwzględnie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-106">It can also be done imperatively in code.</span></span>

<span data-ttu-id="a2bb2-107">W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="a2bb2-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="a2bb2-108">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="a2bb2-109">Plik Web. config dla serwera definiuje zachowanie debugowania usługi, aby włączyć stronę pomocy i obsługę wyjątków, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-109">The Web.config file for the server defines the service debug behavior to enable the help page and exception handling as shown in the following sample.</span></span>

```xml
<behaviors>
     <serviceBehaviors>
         <behavior name="CalculatorServiceBehavior">
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->
         <!-- Please set this to false when deploying -->
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>
         </behavior>
     </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="a2bb2-110">[\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) to element konfiguracji, który umożliwia zmianę właściwości zachowania debugowania usługi.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-110">[\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) is the configuration element that allows changing the service debug behavior properties.</span></span> <span data-ttu-id="a2bb2-111">Użytkownik może zmodyfikować to zachowanie, aby osiągnąć następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="a2bb2-111">The user can modify this behavior to achieve the following:</span></span>

- <span data-ttu-id="a2bb2-112">Dzięki temu usługa zwróci wyjątek, który jest generowany przez kod aplikacji, nawet jeśli wyjątek nie został zadeklarowany przy użyciu <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-112">This allows the service to return any exception that is thrown by the application code even if the exception is not declared using the <xref:System.ServiceModel.FaultContractAttribute>.</span></span> <span data-ttu-id="a2bb2-113">Jest to wykonywane przez ustawienie `includeExceptionDetailInFaults` `true`.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-113">It is done by setting `includeExceptionDetailInFaults` to `true`.</span></span> <span data-ttu-id="a2bb2-114">To ustawienie jest przydatne w przypadku debugowania, gdy serwer zgłasza nieoczekiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-114">This setting is useful when debugging cases where the server is throwing an unexpected exception.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="a2bb2-115">Włączenie tego ustawienia w środowisku produkcyjnym nie jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-115">It is not secure to turn this setting on in a production environment.</span></span> <span data-ttu-id="a2bb2-116">Nieoczekiwany wyjątek serwera może mieć pewne informacje, które nie są przeznaczone dla klienta i dlatego ustawienie `includeExceptionDetailsInFaults` do `true` może spowodować przeciek informacji.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-116">An unexpected server exception may have some information that is not intended for the client and so setting `includeExceptionDetailsInFaults` to `true` might result in an information leak.</span></span>

- <span data-ttu-id="a2bb2-117">[\<serviceDebug](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) umożliwia użytkownikowi włączenie lub wyłączenie strony pomocy.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-117">The [\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) also allows a user to enable or disable the help page.</span></span> <span data-ttu-id="a2bb2-118">Każda usługa może opcjonalnie uwidocznić stronę pomocy, która zawiera informacje o usłudze, w tym punkt końcowy do pobrania WSDL dla usługi.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-118">Each service can optionally expose a help page that contains information about the service including the endpoint to get WSDL for the service.</span></span> <span data-ttu-id="a2bb2-119">Można to włączyć, ustawiając `httpHelpPageEnabled` `true`.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-119">This can be enabled by setting `httpHelpPageEnabled` to `true`.</span></span> <span data-ttu-id="a2bb2-120">Dzięki temu strona pomocy ma zostać zwrócona do żądania GET na adres podstawowy usługi.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-120">This enables the help page to be returned to a GET request to the base address of the service.</span></span> <span data-ttu-id="a2bb2-121">Możesz zmienić ten adres, ustawiając inny `httpHelpPageUrl`atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-121">You can change this address by setting another attribute `httpHelpPageUrl`.</span></span> <span data-ttu-id="a2bb2-122">Można to zabezpieczyć przy użyciu protokołu HTTPS zamiast protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-122">You can make this secure by using HTTPS instead of HTTP.</span></span> <span data-ttu-id="a2bb2-123">Można to zrobić, ustawiając `httpsHelpPageEnabled` i `httpsHelpPageUrl`.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-123">This can be done by setting `httpsHelpPageEnabled` and `httpsHelpPageUrl`.</span></span>

<span data-ttu-id="a2bb2-124">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a2bb2-125">Pierwsze trzy operacje (Dodaj, Odejmij i pomnóż) muszą się powieść.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-125">The first three operations (Add, Subtract and Multiply) must succeed.</span></span> <span data-ttu-id="a2bb2-126">Ostatnia operacja ("dzielenie") kończy się niepowodzeniem z wyjątkiem dzielenia przez zero.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-126">The last operation ("divide") fails with a division by zero exception.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a2bb2-127">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="a2bb2-127">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="a2bb2-128">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a2bb2-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="a2bb2-129">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a2bb2-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="a2bb2-130">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a2bb2-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a2bb2-131">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a2bb2-132">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="a2bb2-132">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="a2bb2-133">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a2bb2-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a2bb2-134">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a2bb2-134">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`
