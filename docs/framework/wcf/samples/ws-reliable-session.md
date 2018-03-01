---
title: Sesja niezawodna WS
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c07130715b0416e7a8603b46a1c39c2f22dd7d2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ws-reliable-session"></a><span data-ttu-id="119e7-102">Sesja niezawodna WS</span><span class="sxs-lookup"><span data-stu-id="119e7-102">WS Reliable Session</span></span>
<span data-ttu-id="119e7-103">W przykładzie pokazano użycie niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="119e7-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="119e7-104">Niezawodne sesje zapewniają obsługę niezawodna obsługa komunikatów i sesje.</span><span class="sxs-lookup"><span data-stu-id="119e7-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="119e7-105">Niezawodna obsługa komunikatów ponowi próbę komunikacji w przypadku niepowodzenia i umożliwia gwarancje dostarczenia, należy określić, takich jak otrzymanie wiadomości w kolejności.</span><span class="sxs-lookup"><span data-stu-id="119e7-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="119e7-106">Sesje przechowywania stanu dla klientów między wywołaniami.</span><span class="sxs-lookup"><span data-stu-id="119e7-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="119e7-107">Próbka implementuje sesji do przechowywania stanu klienta i określa gwarancje dostarczenia w kolejności.</span><span class="sxs-lookup"><span data-stu-id="119e7-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="119e7-108">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="119e7-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="119e7-109">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="119e7-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="119e7-110">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="119e7-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="119e7-111">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="119e7-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="119e7-112">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="119e7-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="119e7-113">Funkcje niezawodnej sesji są włączone i skonfigurowane w plikach konfiguracji aplikacji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="119e7-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="119e7-114">W tym przykładzie usługa jest obsługiwana w Internet Information Services (IIS) i klient jest aplikacji konsoli (.exe).</span><span class="sxs-lookup"><span data-stu-id="119e7-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="119e7-115">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="119e7-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="119e7-116">W przykładzie użyto `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="119e7-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="119e7-117">Powiązanie jest określona w plikach konfiguracji klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="119e7-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="119e7-118">Typ powiązania jest określony w elemencie endpoint `binding` atrybutu, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="119e7-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="119e7-119">Zawiera punkt końcowy `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie "Binding1."</span><span class="sxs-lookup"><span data-stu-id="119e7-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="119e7-120">Konfiguracja powiązania umożliwia niezawodnej sesji przez ustawienie `enabled` atrybutu [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) do `true`.</span><span class="sxs-lookup"><span data-stu-id="119e7-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="119e7-121">Gwarancje dostarczenia uporządkowanej sesji są kontrolowane przez ustawienie atrybutu uporządkowane na `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="119e7-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="119e7-122">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="119e7-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="119e7-123">Implementuje klasy implementacji usługi <xref:System.ServiceModel.InstanceContextMode.PerSession> wystąpień do obsługi wystąpienia klasy osobne dla każdego klienta, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="119e7-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```  
  
 <span data-ttu-id="119e7-124">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="119e7-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="119e7-125">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="119e7-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="119e7-126">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="119e7-126">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="119e7-127">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="119e7-127">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="119e7-128">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="119e7-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="119e7-129">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="119e7-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="119e7-130">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="119e7-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="119e7-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="119e7-131">See Also</span></span>
