---
title: Dostawca WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: dd24a6d270a0bd9012bbda2a53913167c9697bc5
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424513"
---
# <a name="wmi-provider"></a><span data-ttu-id="19df6-102">Dostawca WMI</span><span class="sxs-lookup"><span data-stu-id="19df6-102">WMI Provider</span></span>
<span data-ttu-id="19df6-103">Ten przykład pokazuje, jak zbierać dane z usług Windows Communication Foundation (WCF) w środowisku uruchomieniowym przy użyciu dostawcy Instrumentacja zarządzania Windows (WMI) wbudowanego w funkcję WCF.</span><span class="sxs-lookup"><span data-stu-id="19df6-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="19df6-104">Ponadto w tym przykładzie pokazano, jak dodać obiekt usługi WMI zdefiniowany przez użytkownika do usługi.</span><span class="sxs-lookup"><span data-stu-id="19df6-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="19df6-105">Przykład aktywuje dostawcę WMI dla [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i pokazuje, jak zbierać dane z usługi `ICalculator` w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="19df6-105">The sample activates the WMI provider for the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="19df6-106">Usługa WMI to implementacja standardu opartego na sieci Web (WBEM) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="19df6-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="19df6-107">Aby uzyskać więcej informacji na temat zestawu WMI SDK, zobacz [Instrumentacja zarządzania Windows](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="19df6-107">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="19df6-108">WBEM to standardowy branża, w której aplikacje uwidaczniają Instrumentację zarządzania w zewnętrznych narzędziach do zarządzania.</span><span class="sxs-lookup"><span data-stu-id="19df6-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="19df6-109">Funkcja WCF implementuje dostawcę WMI, składnik, który udostępnia instrumentację w czasie wykonywania za pomocą interfejsu zgodnego z pakietem WBEM.</span><span class="sxs-lookup"><span data-stu-id="19df6-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="19df6-110">Narzędzia do zarządzania programu mogą łączyć się z usługami za pomocą interfejsu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="19df6-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="19df6-111">Funkcja WCF udostępnia atrybuty usług, takie jak adresy, powiązania, zachowania i odbiorniki.</span><span class="sxs-lookup"><span data-stu-id="19df6-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="19df6-112">Wbudowany Dostawca usługi WMI jest aktywowany w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="19df6-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="19df6-113">Odbywa się to za pomocą atrybutu `wmiProviderEnabled` [diagnostyki\<](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) w sekcji [\<system. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , jak pokazano w poniższej konfiguracji przykładowej:</span><span class="sxs-lookup"><span data-stu-id="19df6-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="19df6-114">Ten wpis konfiguracji uwidacznia interfejs WMI.</span><span class="sxs-lookup"><span data-stu-id="19df6-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="19df6-115">Aplikacje zarządzania mogą teraz łączyć się za pomocą tego interfejsu i uzyskiwać dostęp do Instrumentacji zarządzania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="19df6-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="19df6-116">Niestandardowy obiekt WMI</span><span class="sxs-lookup"><span data-stu-id="19df6-116">Custom WMI Object</span></span>  
 <span data-ttu-id="19df6-117">Dodanie obiektów usługi WMI do usługi umożliwia ujawnienie informacji zdefiniowanych przez użytkownika oraz wbudowanych informacji o dostawcach WMI.</span><span class="sxs-lookup"><span data-stu-id="19df6-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="19df6-118">Jest to realizowane przez opublikowanie schematu usługi w usłudze WMI przy użyciu aplikacji Installutil. exe.</span><span class="sxs-lookup"><span data-stu-id="19df6-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="19df6-119">Instrukcje do osiągnięcia tego, a także więcej szczegółów można znaleźć w instrukcjach instalacji na końcu tematu.</span><span class="sxs-lookup"><span data-stu-id="19df6-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="19df6-120">Uzyskiwanie dostępu do informacji WMI</span><span class="sxs-lookup"><span data-stu-id="19df6-120">Accessing WMI Information</span></span>  
 <span data-ttu-id="19df6-121">Dostęp do danych usługi WMI można uzyskać na wiele różnych sposobów.</span><span class="sxs-lookup"><span data-stu-id="19df6-121">WMI data can be accessed many different ways.</span></span> <span data-ttu-id="19df6-122">Firma Microsoft udostępnia interfejsy API usługi WMI dla skryptów, C++ aplikacji Visual Basic, aplikacji i .NET Framework (https://docs.microsoft.com/windows/desktop/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="19df6-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework (https://docs.microsoft.com/windows/desktop/wmisdk/using-wmi).</span></span>  
  
 <span data-ttu-id="19df6-123">W tym przykładzie zastosowano dwa skrypty Java: jeden do wyliczania usług działających na komputerze wraz z niektórymi właściwościami, a drugą, aby wyświetlić dane usługi WMI zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="19df6-123">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="19df6-124">Skrypt otwiera połączenie z dostawcą WMI, analizuje dane i wyświetla zebrane dane.</span><span class="sxs-lookup"><span data-stu-id="19df6-124">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="19df6-125">Rozpocznij przykład, aby utworzyć uruchomione wystąpienie usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="19df6-125">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="19df6-126">Gdy usługa jest uruchomiona, uruchom każdy skrypt Java za pomocą następującego polecenia w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="19df6-126">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```console  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="19df6-127">Skrypt uzyskuje dostęp do Instrumentacji zawartej w usłudze i tworzy następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="19df6-127">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
```console  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 <span data-ttu-id="19df6-128">Następnie Uruchom drugi skrypt języka Java, aby wyświetlić dane zdefiniowane przez użytkownika usługi WMI:</span><span class="sxs-lookup"><span data-stu-id="19df6-128">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="19df6-129">Skrypt uzyskuje dostęp do zdefiniowanej przez użytkownika Instrumentacji zawartej w usługach i tworzy następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="19df6-129">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```console 
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="19df6-130">Dane wyjściowe pokazują, że na komputerze jest uruchomiona jedna usługa.</span><span class="sxs-lookup"><span data-stu-id="19df6-130">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="19df6-131">Usługa udostępnia jeden punkt końcowy, który implementuje kontrakt `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="19df6-131">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="19df6-132">Ustawienia zachowania i powiązania, które są implementowane przez punkt końcowy, są wyświetlane jako suma poszczególnych elementów stosu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="19df6-132">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="19df6-133">Usługa WMI nie jest ograniczona do uwidaczniania Instrumentacji zarządzania infrastruktury WCF.</span><span class="sxs-lookup"><span data-stu-id="19df6-133">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="19df6-134">Aplikacja może uwidaczniać własne specyficzne dla domeny elementy danych za pomocą tego samego mechanizmu.</span><span class="sxs-lookup"><span data-stu-id="19df6-134">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="19df6-135">Usługa WMI to ujednolicony mechanizm kontroli i kontroli nad usługą sieci Web.</span><span class="sxs-lookup"><span data-stu-id="19df6-135">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="19df6-136">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="19df6-136">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="19df6-137">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="19df6-137">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="19df6-138">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="19df6-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="19df6-139">Opublikuj schemat usług w usłudze WMI, uruchamiając InstallUtil. exe (domyślne lokalizacje dla InstallUtil. exe to "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") w pliku Service. dll w katalogu hostingu.</span><span class="sxs-lookup"><span data-stu-id="19df6-139">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="19df6-140">Ten krok należy wykonać tylko po wprowadzeniu zmian w pliku. dll usługi.</span><span class="sxs-lookup"><span data-stu-id="19df6-140">This step only needs to be executed when changes have been made to the service.dll file.</span></span>
  
4. <span data-ttu-id="19df6-141">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="19df6-141">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="19df6-142">W przypadku zainstalowania programu WCF po zainstalowaniu ASP.NET może być konieczne uruchomienie "% WINDIR% \ Microsoft. Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe "-r-x", aby nadać kontu ASPNET uprawnienie do publikowania obiektów usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="19df6-142">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5. <span data-ttu-id="19df6-143">Dane z przykładu są wyświetlane za pośrednictwem usługi WMI przy użyciu poleceń: `cscript EnumerateServices.js` lub `cscript EnumerateCustomObjects.js`.</span><span class="sxs-lookup"><span data-stu-id="19df6-143">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="19df6-144">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="19df6-144">The samples may already be installed on your computer.</span></span> <span data-ttu-id="19df6-145">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="19df6-145">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="19df6-146">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="19df6-146">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="19df6-147">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="19df6-147">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="19df6-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19df6-148">See also</span></span>

- [<span data-ttu-id="19df6-149">Przykłady monitorowania oprogramowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="19df6-149">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
