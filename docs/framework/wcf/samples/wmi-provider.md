---
title: Dostawca WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: d135466c402fa21b6a1b11f208ca900f58748bdb
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807309"
---
# <a name="wmi-provider"></a><span data-ttu-id="b05ac-102">Dostawca WMI</span><span class="sxs-lookup"><span data-stu-id="b05ac-102">WMI Provider</span></span>
<span data-ttu-id="b05ac-103">W tym przykładzie pokazano, jak można zebrać danych z usługi Windows Communication Foundation (WCF) w czasie wykonywania za pomocą dostawcy Instrumentacji zarządzania Windows (WMI), który jest wbudowany w usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="b05ac-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="b05ac-104">Ponadto w przykładzie pokazano sposób dodawania obiektu WMI zdefiniowane przez użytkownika do usługi.</span><span class="sxs-lookup"><span data-stu-id="b05ac-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="b05ac-105">Przykład aktywuje dostawcy WMI o [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i pokazuje, jak zbierać dane z `ICalculator` usługi w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b05ac-105">The sample activates the WMI provider for the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="b05ac-106">Usługa WMI stanowi implementację firmy Microsoft w sieci Web-Based Enterprise Management (WBEM) standardowa.</span><span class="sxs-lookup"><span data-stu-id="b05ac-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="b05ac-107">Aby uzyskać więcej informacji o zestawie SDK usługi WMI, zobacz [Instrumentacji zarządzania Windows](https://msdn.microsoft.com/library/aa394582.aspx).</span><span class="sxs-lookup"><span data-stu-id="b05ac-107">For more information about the WMI SDK, see [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx).</span></span> <span data-ttu-id="b05ac-108">Technologia WBEM jest branżowy standard jak aplikacje ujawnia Instrumentacji zarządzania do narzędzia do zarządzania zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="b05ac-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="b05ac-109">Usługi WCF implementuje dostawcę WMI składnik, który ujawnia Instrumentacji w czasie wykonywania za pośrednictwem interfejsu zgodnego WBEM.</span><span class="sxs-lookup"><span data-stu-id="b05ac-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="b05ac-110">Narzędzia do zarządzania mogą łączyć się usługi za pomocą interfejsu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b05ac-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="b05ac-111">Usługa WCF umożliwia atrybuty usług, takich jak adresy, powiązania zachowania i odbiorników.</span><span class="sxs-lookup"><span data-stu-id="b05ac-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="b05ac-112">Wbudowane dostawcy WMI jest aktywowana w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b05ac-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="b05ac-113">Jest to zrobić za pomocą `wmiProviderEnabled` atrybutu [ \<diagnostyki >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) w [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) sekcji, jak pokazano w następującym przykładowym Konfiguracja:</span><span class="sxs-lookup"><span data-stu-id="b05ac-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="b05ac-114">Ten wpis konfiguracji uwidacznia interfejs WMI.</span><span class="sxs-lookup"><span data-stu-id="b05ac-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="b05ac-115">Aplikacje do zarządzania można teraz łączenie się za pośrednictwem tego interfejsu i uzyskać dostęp z Instrumentacją zarządzania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b05ac-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="b05ac-116">Obiekt WMI niestandardowych</span><span class="sxs-lookup"><span data-stu-id="b05ac-116">Custom WMI Object</span></span>  
 <span data-ttu-id="b05ac-117">Dodawanie obiektów WMI z usługą umożliwia ujawnić informacje zdefiniowane przez użytkownika wraz z wbudowanych informacji o dostawcy WMI.</span><span class="sxs-lookup"><span data-stu-id="b05ac-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="b05ac-118">Jest to osiągane przez publikowanie schemat usługi WMI za pomocą aplikacji Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="b05ac-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="b05ac-119">Instrukcje w tym celu, wraz z bardziej szczegółowe informacje można znaleźć w instrukcjach instalacji na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b05ac-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="b05ac-120">Uzyskiwanie dostępu do informacji usługi WMI</span><span class="sxs-lookup"><span data-stu-id="b05ac-120">Accessing WMI Information</span></span>  
 <span data-ttu-id="b05ac-121">Dane usługi WMI są dostępne wiele różnych sposobów.</span><span class="sxs-lookup"><span data-stu-id="b05ac-121">WMI data can be accessed many different ways.</span></span> <span data-ttu-id="b05ac-122">Firma Microsoft udostępnia interfejsy API usługi WMI dla skryptów aplikacji Visual Basic, aplikacji C++ i [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).</span><span class="sxs-lookup"><span data-stu-id="b05ac-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).</span></span>  
  
 <span data-ttu-id="b05ac-123">W przykładzie użyto dwóch skryptów Java: jeden wyliczyć usługi uruchomione na komputerze wraz z niektórych właściwości i drugiego do wyświetlania danych usługi WMI zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b05ac-123">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="b05ac-124">Skrypt otwiera połączenie z dostawcą WMI, analizuje dane i wyświetla zbieranych danych.</span><span class="sxs-lookup"><span data-stu-id="b05ac-124">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="b05ac-125">Uruchom przykład, aby utworzyć działającego wystąpienia usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="b05ac-125">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="b05ac-126">Gdy usługa jest uruchomiona, uruchom każdego skryptu języka Java przy użyciu następującego polecenia w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="b05ac-126">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="b05ac-127">Skrypt uzyskuje dostęp do zawartych w usłudze Instrumentacja i następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="b05ac-127">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
```  
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
  
 <span data-ttu-id="b05ac-128">Następnie uruchom skrypt Java drugi do wyświetlania danych usługi WMI zdefiniowane przez użytkownika:</span><span class="sxs-lookup"><span data-stu-id="b05ac-128">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="b05ac-129">Skrypt uzyskuje dostęp do zawartych w usługach Instrumentacja zdefiniowane przez użytkownika i następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="b05ac-129">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="b05ac-130">Dane wyjściowe wskazuje, że istnieje pojedynczą usługę uruchomionej na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b05ac-130">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="b05ac-131">Usługa udostępnia jeden punkt końcowy, który implementuje `ICalculator` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="b05ac-131">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="b05ac-132">Ustawienia zachowania i powiązania, które są implementowane przez punkt końcowy są wyświetlane jako sumę poszczególne elementy stosem obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b05ac-132">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="b05ac-133">Usługa WMI nie jest ograniczone do udostępnianie Instrumentacji zarządzania infrastrukturą usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="b05ac-133">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="b05ac-134">Aplikacja może narazić elementy dane specyficzne dla domeny przez ten sam mechanizm.</span><span class="sxs-lookup"><span data-stu-id="b05ac-134">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="b05ac-135">Usługa WMI stanowi mechanizm ujednoliconego inspekcji i kontroli usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b05ac-135">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b05ac-136">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="b05ac-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b05ac-137">Upewnij się, można zlecić [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b05ac-137">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b05ac-138">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b05ac-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b05ac-139">Opublikuj schemat usługi WMI, uruchamiając InstallUtil.exe (domyślne lokalizacje InstallUtil.exe jest "% WINDIR%\Microsoft.NET\Framework\v4.0.30319") w pliku service.dll w katalogu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="b05ac-139">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="b05ac-140">Ten krok tylko musi być wykonywana w przypadku zmiany zostały wprowadzone w pliku service.dll.</span><span class="sxs-lookup"><span data-stu-id="b05ac-140">This step only needs to be executed when changes have been made to the service.dll file.</span></span> <span data-ttu-id="b05ac-141">Aby uzyskać więcej informacji, zobacz dostarczanie informacji dotyczących zarządzania przez aplikacje Instrumentacji w: http://msdn2.microsoft.com/library/ms186147.aspx w sekcji "Jak do: publikowanie schematu do usługi WMI dla Instrumentacji aplikacji".</span><span class="sxs-lookup"><span data-stu-id="b05ac-141">For more information, see Providing Management Information by Instrumenting Applications at: http://msdn2.microsoft.com/library/ms186147.aspx in the "How To: Publish the Scheme to WMI for an Instrumented Application" section.</span></span>  
  
4.  <span data-ttu-id="b05ac-142">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b05ac-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b05ac-143">Jeśli WCF jest zainstalowany po zainstalowaniu programu ASP.NET, może być konieczne uruchomienie "%WINDIR%\ Foundation\servicemodelreg.exe komunikacji Microsoft.Net\Framework\v3.0\Windows "- r - x, aby udzielić ASPNET uprawnienia konta do publikowania obiektów WMI.</span><span class="sxs-lookup"><span data-stu-id="b05ac-143">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5.  <span data-ttu-id="b05ac-144">Wyświetl dane przykładowe udostępniane za pośrednictwem usługi WMI za pomocą poleceń: `cscript EnumerateServices.js` lub `cscript EnumerateCustomObjects.js`.</span><span class="sxs-lookup"><span data-stu-id="b05ac-144">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b05ac-145">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b05ac-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b05ac-146">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b05ac-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b05ac-147">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="b05ac-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b05ac-148">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b05ac-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="b05ac-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b05ac-149">See Also</span></span>  
 [<span data-ttu-id="b05ac-150">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="b05ac-150">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
