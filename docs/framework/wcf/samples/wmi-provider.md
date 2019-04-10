---
title: Dostawca WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 519f63f8dfc558a83a98ca44f74e926beb81c190
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59327233"
---
# <a name="wmi-provider"></a><span data-ttu-id="05f13-102">Dostawca WMI</span><span class="sxs-lookup"><span data-stu-id="05f13-102">WMI Provider</span></span>
<span data-ttu-id="05f13-103">W tym przykładzie pokazano, jak zbieranie danych z usługi Windows Communication Foundation (WCF) w czasie wykonywania przy użyciu dostawcy Instrumentacji zarządzania Windows (WMI), która jest wbudowana w usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="05f13-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="05f13-104">Ponadto w tym przykładzie przedstawiono sposób dodawania obiektu WMI zdefiniowanych przez użytkownika do usługi.</span><span class="sxs-lookup"><span data-stu-id="05f13-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="05f13-105">Przykładowe aktywuje dostawcy WMI o [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i pokazuje, jak zbierać dane z `ICalculator` usługi w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="05f13-105">The sample activates the WMI provider for the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="05f13-106">WMI jest implementacja firmy Microsoft opartego na sieci Web Enterprise Management (WBEM) standardowa.</span><span class="sxs-lookup"><span data-stu-id="05f13-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="05f13-107">Aby uzyskać więcej informacji na temat zestawu SDK usługi WMI, zobacz [Instrumentacji zarządzania Windows](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="05f13-107">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="05f13-108">Technologia WBEM jest branżowy standard jak aplikacje uwidocznić Instrumentacji zarządzania do narzędzi zarządzania zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="05f13-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="05f13-109">Usługi WCF implementuje dostawcę WMI składnika, który udostępnia Instrumentacji w czasie wykonywania za pomocą interfejsu WBEM zgodne.</span><span class="sxs-lookup"><span data-stu-id="05f13-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="05f13-110">Narzędzia do zarządzania może nawiązać połączenia usług za pośrednictwem interfejsu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="05f13-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="05f13-111">Usługa WCF umożliwia atrybuty usługi, takie jak adresy, powiązania, zachowań i odbiorników.</span><span class="sxs-lookup"><span data-stu-id="05f13-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="05f13-112">Wbudowany dostawca usługi WMI jest ono aktywowane w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="05f13-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="05f13-113">Jest to realizowane `wmiProviderEnabled` atrybutu [ \<Diagnostyka >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) w [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) sekcji, jak pokazano w następującym przykładzie Konfiguracja:</span><span class="sxs-lookup"><span data-stu-id="05f13-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="05f13-114">Ten wpis konfiguracji udostępnia interfejs usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="05f13-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="05f13-115">Aplikacje do zarządzania można teraz nawiązać połączenie za pośrednictwem tego interfejsu i uzyskać dostęp z Instrumentacją zarządzania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="05f13-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="05f13-116">Obiektu WMI niestandardowe</span><span class="sxs-lookup"><span data-stu-id="05f13-116">Custom WMI Object</span></span>  
 <span data-ttu-id="05f13-117">Dodawanie obiektów WMI do usługi umożliwia do ujawnienia informacji użytkownika wraz z wbudowaną informacji o dostawcy WMI.</span><span class="sxs-lookup"><span data-stu-id="05f13-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="05f13-118">Jest to realizowane przez opublikowanie schemat usługi WMI za pomocą aplikacji Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="05f13-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="05f13-119">Instrukcje, aby to osiągnąć, podając więcej szczegółów można znaleźć w instrukcjach instalacji na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="05f13-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="05f13-120">Uzyskiwanie dostępu do informacji usługi WMI</span><span class="sxs-lookup"><span data-stu-id="05f13-120">Accessing WMI Information</span></span>  
 <span data-ttu-id="05f13-121">Dane usługi WMI są dostępne wiele różnych sposobów.</span><span class="sxs-lookup"><span data-stu-id="05f13-121">WMI data can be accessed many different ways.</span></span> <span data-ttu-id="05f13-122">Firma Microsoft udostępnia interfejsy API usługi WMI dla skryptów, aplikacji Visual Basic, aplikacji w języku C++ i [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (https://docs.microsoft.com/windows/desktop/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="05f13-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (https://docs.microsoft.com/windows/desktop/wmisdk/using-wmi).</span></span>  
  
 <span data-ttu-id="05f13-123">W tym przykładzie użyto dwóch skryptów języka Java: jeden wyliczyć usługi uruchomione na komputerze oraz niektóre z ich właściwości, a druga do wyświetlania danych WMI zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="05f13-123">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="05f13-124">Skrypt otwiera połączenie z dostawcą WMI, analizuje dane i wyświetla dane zebrane.</span><span class="sxs-lookup"><span data-stu-id="05f13-124">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="05f13-125">Uruchom przykład, aby utworzyć uruchomionego wystąpienia usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="05f13-125">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="05f13-126">Gdy usługa jest uruchomiona, uruchom każdego skryptu języka Java przy użyciu następującego polecenia w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="05f13-126">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="05f13-127">Skrypt uzyskuje dostęp do Instrumentacji znajdujących się w usłudze, a także generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="05f13-127">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="05f13-128">Następnie uruchom drugi skryptu Java, aby wyświetlić dane WMI zdefiniowanych przez użytkownika:</span><span class="sxs-lookup"><span data-stu-id="05f13-128">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="05f13-129">Skrypt uzyskuje dostęp do Instrumentacji zdefiniowanych przez użytkownika, zawartych w usługach i generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="05f13-129">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="05f13-130">Dane wyjściowe pokazują, że istnieje jednej usługi uruchomione na komputerze.</span><span class="sxs-lookup"><span data-stu-id="05f13-130">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="05f13-131">Usługa udostępnia jeden punkt końcowy, który implementuje `ICalculator` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="05f13-131">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="05f13-132">Ustawienia zachowania i powiązanie, które są implementowane przez punkt końcowy jest wyświetlany tekst sumę poszczególne elementy stosem obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="05f13-132">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="05f13-133">Usługa WMI nie jest ograniczona do uwidaczniania Instrumentacji zarządzania infrastrukturą usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="05f13-133">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="05f13-134">Aplikacja może uwidocznić własne elementy danych specyficznych dla domeny przez ten sam mechanizm.</span><span class="sxs-lookup"><span data-stu-id="05f13-134">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="05f13-135">Usługa WMI jest mechanizmem ujednoliconego inspekcji i kontroli usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="05f13-135">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="05f13-136">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="05f13-136">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="05f13-137">Upewnij się, kiedy została wykonana [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="05f13-137">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="05f13-138">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="05f13-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="05f13-139">Opublikuj schemat usługi WMI, uruchamiając InstallUtil.exe (domyślne lokalizacje programu InstallUtil.exe jest "% WINDIR%\Microsoft.NET\Framework\v4.0.30319") w pliku service.dll w katalogu macierzystym.</span><span class="sxs-lookup"><span data-stu-id="05f13-139">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="05f13-140">Ten krok wymaga tylko do wykonania, gdy wprowadzono zmiany w pliku service.dll.</span><span class="sxs-lookup"><span data-stu-id="05f13-140">This step only needs to be executed when changes have been made to the service.dll file.</span></span>
  
4. <span data-ttu-id="05f13-141">Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="05f13-141">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="05f13-142">Po zainstalowaniu programu WCF po zainstalowaniu programu ASP.NET, może być konieczne uruchomienie "%WINDIR%\ Foundation\servicemodelreg.exe komunikacji Microsoft.Net\Framework\v3.0\Windows "- r - x, aby udzielić uprawnień konto ASPNET, aby opublikować obiektów WMI.</span><span class="sxs-lookup"><span data-stu-id="05f13-142">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5. <span data-ttu-id="05f13-143">Wyświetlanie danych z przykładu udostępniane za pośrednictwem usługi WMI za pomocą poleceń: `cscript EnumerateServices.js` lub `cscript EnumerateCustomObjects.js`.</span><span class="sxs-lookup"><span data-stu-id="05f13-143">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="05f13-144">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="05f13-144">The samples may already be installed on your computer.</span></span> <span data-ttu-id="05f13-145">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="05f13-145">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="05f13-146">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="05f13-146">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="05f13-147">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="05f13-147">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="05f13-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05f13-148">See also</span></span>

- [<span data-ttu-id="05f13-149">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="05f13-149">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
