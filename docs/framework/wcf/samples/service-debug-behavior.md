---
title: Zachowanie debugowania usług
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: b87911426b6d4edf8a6f9b0172f4872fac7b9b6f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43465554"
---
# <a name="service-debug-behavior"></a><span data-ttu-id="f683a-102">Zachowanie debugowania usług</span><span class="sxs-lookup"><span data-stu-id="f683a-102">Service Debug Behavior</span></span>
<span data-ttu-id="f683a-103">Niniejszy przykład pokazuje, jak można skonfigurować ustawienia zachowanie debugowania usług.</span><span class="sxs-lookup"><span data-stu-id="f683a-103">This sample demonstrates how service debug behavior settings can be configured.</span></span> <span data-ttu-id="f683a-104">Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="f683a-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="f683a-105">W tym przykładzie jawnie definiuje zachowanie debugowania usług w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f683a-105">This sample explicitly defines service debug behavior in the configuration file.</span></span> <span data-ttu-id="f683a-106">Ponadto możesz obowiązkowo w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f683a-106">It can also be done imperatively in code.</span></span>  
  
 <span data-ttu-id="f683a-107">W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="f683a-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f683a-108">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="f683a-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f683a-109">Plik Web.config dla serwera definiuje zachowanie debugowania usług, aby włączyć stronę pomocy i obsługi wyjątków, jak pokazano w następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f683a-109">The Web.config file for the server defines the service debug behavior to enable the help page and exception handling as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="f683a-110">[\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) jest elementem konfiguracji, który umożliwia zmianę właściwości zachowanie debugowania usług.</span><span class="sxs-lookup"><span data-stu-id="f683a-110">[\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) is the configuration element that allows changing the service debug behavior properties.</span></span> <span data-ttu-id="f683a-111">Użytkownik może modyfikować tego zachowania do osiągnięcia następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="f683a-111">The user can modify this behavior to achieve the following:</span></span>  
  
-   <span data-ttu-id="f683a-112">Dzięki temu zwracanej każdy wyjątek, który jest zgłaszany przez kod aplikacji, nawet jeśli wyjątek nie jest zadeklarowany za pomocą usługi <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f683a-112">This allows the service to return any exception that is thrown by the application code even if the exception is not declared using the <xref:System.ServiceModel.FaultContractAttribute>.</span></span> <span data-ttu-id="f683a-113">Odbywa się przez ustawienie `includeExceptionDetailInFaults` do `true`.</span><span class="sxs-lookup"><span data-stu-id="f683a-113">It is done by setting `includeExceptionDetailInFaults` to `true`.</span></span> <span data-ttu-id="f683a-114">To ustawienie jest przydatne podczas debugowania przypadków, gdy serwer jest zgłaszanie nieoczekiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f683a-114">This setting is useful when debugging cases where the server is throwing an unexpected exception.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f683a-115">Nie jest bezpieczne, aby włączyć to ustawienie w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="f683a-115">It is not secure to turn this setting on in a production environment.</span></span> <span data-ttu-id="f683a-116">Serwer nieoczekiwany wyjątek może mieć pewne informacje, które nie są przeznaczone dla klienta i dlatego ustawienie `includeExceptionDetailsInFaults` do `true` może prowadzić do przecieków informacji.</span><span class="sxs-lookup"><span data-stu-id="f683a-116">An unexpected server exception may have some information that is not intended for the client and so setting `includeExceptionDetailsInFaults` to `true` might result in an information leak.</span></span>  
  
-   <span data-ttu-id="f683a-117">[ \<ServiceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) również pozwala użytkownikowi na włączanie lub wyłączanie strony pomocy.</span><span class="sxs-lookup"><span data-stu-id="f683a-117">The [\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) also allows a user to enable or disable the help page.</span></span> <span data-ttu-id="f683a-118">Każda usługa Opcjonalnie można ujawnić stronę pomocy, który zawiera informacje dotyczące usługi, w tym punkt końcowy, aby uzyskać WSDL usługi.</span><span class="sxs-lookup"><span data-stu-id="f683a-118">Each service can optionally expose a help page that contains information about the service including the endpoint to get WSDL for the service.</span></span> <span data-ttu-id="f683a-119">To może być włączona `httpHelpPageEnabled` do `true`.</span><span class="sxs-lookup"><span data-stu-id="f683a-119">This can be enabled by setting `httpHelpPageEnabled` to `true`.</span></span> <span data-ttu-id="f683a-120">Dzięki temu strony pomocy do zwrócenia na żądanie GET do podstawowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="f683a-120">This enables the help page to be returned to a GET request to the base address of the service.</span></span> <span data-ttu-id="f683a-121">Ten adres można zmienić przez ustawienie innego atrybutu `httpHelpPageUrl`.</span><span class="sxs-lookup"><span data-stu-id="f683a-121">You can change this address by setting another attribute `httpHelpPageUrl`.</span></span> <span data-ttu-id="f683a-122">Umożliwia to bezpieczne przy użyciu protokołu HTTPS zamiast protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f683a-122">You can make this secure by using HTTPS instead of HTTP.</span></span> <span data-ttu-id="f683a-123">Można to zrobić, ustawiając `httpsHelpPageEnabled` i `httpsHelpPageUrl`.</span><span class="sxs-lookup"><span data-stu-id="f683a-123">This can be done by setting `httpsHelpPageEnabled` and `httpsHelpPageUrl`.</span></span>  
  
 <span data-ttu-id="f683a-124">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="f683a-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f683a-125">Pierwsze trzy operacje (dodawania, odejmowania i mnożenia) musi zakończyć się sukcesem.</span><span class="sxs-lookup"><span data-stu-id="f683a-125">The first three operations (Add, Subtract and Multiply) must succeed.</span></span> <span data-ttu-id="f683a-126">Ostatnia operacja ("dzielenie") kończy się niepowodzeniem z dzielenia przez zero wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f683a-126">The last operation ("divide") fails with a division by zero exception.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f683a-127">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="f683a-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f683a-128">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f683a-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f683a-129">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f683a-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="f683a-130">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f683a-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f683a-131">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f683a-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f683a-132">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="f683a-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f683a-133">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="f683a-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f683a-134">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f683a-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
  
## <a name="see-also"></a><span data-ttu-id="f683a-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f683a-135">See Also</span></span>
