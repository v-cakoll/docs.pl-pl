---
title: Dostawca WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 04fdbb7efcae6fdbb78f467352e6106ac5218799
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183190"
---
# <a name="wmi-provider"></a><span data-ttu-id="b0d04-102">Dostawca WMI</span><span class="sxs-lookup"><span data-stu-id="b0d04-102">WMI Provider</span></span>
<span data-ttu-id="b0d04-103">W tym przykładzie pokazano, jak zbierać dane z usług Windows Communication Foundation (WCF) w czasie wykonywania przy użyciu dostawcy instrumentacji zarządzania windows (WMI), który jest wbudowany w WCF.</span><span class="sxs-lookup"><span data-stu-id="b0d04-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="b0d04-104">Ponadto w tym przykładzie pokazano, jak dodać obiekt WMI zdefiniowane przez użytkownika do usługi.</span><span class="sxs-lookup"><span data-stu-id="b0d04-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="b0d04-105">Przykład aktywuje dostawcę usługi WMI dla [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i pokazuje, `ICalculator` jak zbierać dane z usługi w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b0d04-105">The sample activates the WMI provider for the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="b0d04-106">WMI jest wdrożenie microsoftu web-based Enterprise Management (WBEM) standard.</span><span class="sxs-lookup"><span data-stu-id="b0d04-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="b0d04-107">Aby uzyskać więcej informacji na temat zestawie WMI SDK, zobacz [Instrumentacja zarządzania windowsem](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="b0d04-107">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="b0d04-108">WBEM jest standardem branżowym w zakresie sposobu, w jaki aplikacje narażają instrumentację zarządzania na zewnętrzne narzędzia do zarządzania.</span><span class="sxs-lookup"><span data-stu-id="b0d04-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="b0d04-109">WCF implementuje dostawcę WMI, składnik, który udostępnia instrumentacji w czasie wykonywania za pośrednictwem interfejsu zgodnego z WBEM.</span><span class="sxs-lookup"><span data-stu-id="b0d04-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="b0d04-110">Narzędzia do zarządzania można połączyć się z usługami za pośrednictwem interfejsu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b0d04-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="b0d04-111">WCF udostępnia atrybuty usług, takich jak adresy, powiązania, zachowania i detektory.</span><span class="sxs-lookup"><span data-stu-id="b0d04-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="b0d04-112">Wbudowany dostawca WMI jest aktywowany w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b0d04-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="b0d04-113">Odbywa się to `wmiProviderEnabled` za pomocą atrybutu [ \<diagnostyki>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) w sekcji [ \<system.serviceModel>,](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) jak pokazano w poniższej konfiguracji przykładowej:</span><span class="sxs-lookup"><span data-stu-id="b0d04-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="b0d04-114">Ten wpis konfiguracji udostępnia interfejs WMI.</span><span class="sxs-lookup"><span data-stu-id="b0d04-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="b0d04-115">Aplikacje do zarządzania mogą teraz łączyć się za pośrednictwem tego interfejsu i uzyskiwać dostęp do instrumentacji zarządzania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b0d04-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="b0d04-116">Niestandardowy obiekt WMI</span><span class="sxs-lookup"><span data-stu-id="b0d04-116">Custom WMI Object</span></span>  
 <span data-ttu-id="b0d04-117">Dodanie obiektów WMI do usługi umożliwia ujawnienie informacji zdefiniowanych przez użytkownika wraz z wbudowanymi informacjami o dostawcy WMI.</span><span class="sxs-lookup"><span data-stu-id="b0d04-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="b0d04-118">Jest to realizowane przez opublikowanie schematu usługi do usługi WMI przy użyciu aplikacji Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="b0d04-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="b0d04-119">Instrukcje, aby to osiągnąć, wraz z więcej szczegółów można znaleźć w instrukcji konfiguracji na końcu tematu.</span><span class="sxs-lookup"><span data-stu-id="b0d04-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="b0d04-120">Uzyskiwanie dostępu do informacji w u obiektu WMI</span><span class="sxs-lookup"><span data-stu-id="b0d04-120">Accessing WMI Information</span></span>  

<span data-ttu-id="b0d04-121">Dostęp do danych usługi WMI można uzyskać na wiele różnych sposobów.</span><span class="sxs-lookup"><span data-stu-id="b0d04-121">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="b0d04-122">Firma Microsoft udostępnia interfejsy API usługi WMI dla skryptów, aplikacji Visual Basic, aplikacji W++ i programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b0d04-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="b0d04-123">Aby uzyskać więcej informacji, zobacz [Korzystanie z usługi WMI](/windows/desktop/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="b0d04-123">For more information, see [Using WMI](/windows/desktop/wmisdk/using-wmi).</span></span>
  
 <span data-ttu-id="b0d04-124">W tym przykładzie użyto dwóch skryptów Java: jednego do wyliczenia usług uruchomionych na komputerze wraz z niektórymi ich właściwościami, a drugi do wyświetlania zdefiniowanych przez użytkownika danych WMI.</span><span class="sxs-lookup"><span data-stu-id="b0d04-124">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="b0d04-125">Skrypt otwiera połączenie z dostawcą usługi WMI, analizuje dane i wyświetla zebrane dane.</span><span class="sxs-lookup"><span data-stu-id="b0d04-125">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="b0d04-126">Uruchom próbkę, aby utworzyć uruchomione wystąpienie usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="b0d04-126">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="b0d04-127">Gdy usługa jest uruchomiona, uruchom każdy skrypt Java przy użyciu następującego polecenia w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="b0d04-127">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```console  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="b0d04-128">Skrypt uzyskuje dostęp do instrumentacji zawartej w usłudze i generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="b0d04-128">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="b0d04-129">Następnie uruchom drugi skrypt Java, aby wyświetlić zdefiniowane przez użytkownika dane WMI:</span><span class="sxs-lookup"><span data-stu-id="b0d04-129">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="b0d04-130">Skrypt uzyskuje dostęp do instrumentacji zdefiniowanej przez użytkownika zawartej w usługach i generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="b0d04-130">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```console
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="b0d04-131">Dane wyjściowe pokazują, że na komputerze jest uruchomiona jedna usługa.</span><span class="sxs-lookup"><span data-stu-id="b0d04-131">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="b0d04-132">Usługa udostępnia jeden punkt końcowy, `ICalculator` który implementuje umowy.</span><span class="sxs-lookup"><span data-stu-id="b0d04-132">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="b0d04-133">Ustawienia zachowania i powiązania, które są implementowane przez punkt końcowy są wymienione jako suma poszczególnych elementów stosu obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b0d04-133">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="b0d04-134">WMI nie ogranicza się do narażania instrumentacji zarządzania infrastruktury WCF.</span><span class="sxs-lookup"><span data-stu-id="b0d04-134">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="b0d04-135">Aplikacja może udostępniać własne elementy danych specyficzne dla domeny za pośrednictwem tego samego mechanizmu.</span><span class="sxs-lookup"><span data-stu-id="b0d04-135">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="b0d04-136">Usługa WMI to ujednolicony mechanizm inspekcji i kontroli usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b0d04-136">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b0d04-137">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="b0d04-137">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b0d04-138">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b0d04-138">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b0d04-139">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b0d04-139">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b0d04-140">Opublikuj schemat usług w UMI, uruchamiając plik InstallUtil.exe (domyślne lokalizacje installUtil.exe to "%WINDIR%\Microsoft.NET\Framework\v4.30319") w pliku service.dll w katalogu hostingu.</span><span class="sxs-lookup"><span data-stu-id="b0d04-140">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="b0d04-141">Ten krok musi być wykonywany tylko po wprowadzeniu zmian w pliku service.dll.</span><span class="sxs-lookup"><span data-stu-id="b0d04-141">This step only needs to be executed when changes have been made to the service.dll file.</span></span>
  
4. <span data-ttu-id="b0d04-142">Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b0d04-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b0d04-143">Jeśli po zainstalowaniu WCF po zainstalowaniu ASP.NET, może być konieczne uruchomienie "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x, aby nadać kontu ASPNET uprawnienia do publikowania obiektów WMI.</span><span class="sxs-lookup"><span data-stu-id="b0d04-143">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5. <span data-ttu-id="b0d04-144">Wyświetlanie danych z próbki na powierzchni za pomocą `cscript EnumerateServices.js` usługi `cscript EnumerateCustomObjects.js`WMI za pomocą poleceń: lub .</span><span class="sxs-lookup"><span data-stu-id="b0d04-144">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b0d04-145">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b0d04-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b0d04-146">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="b0d04-146">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b0d04-147">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="b0d04-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b0d04-148">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b0d04-148">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="b0d04-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0d04-149">See also</span></span>

- <span data-ttu-id="b0d04-150">[Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b0d04-150">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
