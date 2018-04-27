---
title: Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3df15e80a550857adbfbf30ebf8b6ef902426a1a
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="44221-102">Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki</span><span class="sxs-lookup"><span data-stu-id="44221-102">Using Windows Management Instrumentation for Diagnostics</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="44221-103"> udostępnia dane inspekcji usługi w czasie wykonywania za pośrednictwem [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] dostawcy Instrumentacji zarządzania Windows (WMI).</span><span class="sxs-lookup"><span data-stu-id="44221-103"> exposes inspection data of a service at runtime through a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="44221-104">Włączanie usługi WMI</span><span class="sxs-lookup"><span data-stu-id="44221-104">Enabling WMI</span></span>  
 <span data-ttu-id="44221-105">Usługa WMI stanowi implementację firmy Microsoft w sieci Web-Based Enterprise Management (WBEM) standardowa.</span><span class="sxs-lookup"><span data-stu-id="44221-105">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="44221-106"> zestaw SDK usługi WMI, zobacz [Instrumentacji zarządzania Windows](https://msdn.microsoft.com/library/aa394582.aspx).</span><span class="sxs-lookup"><span data-stu-id="44221-106"> the WMI SDK, see [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx).</span></span> <span data-ttu-id="44221-107">Technologia WBEM jest branżowy standard jak aplikacje ujawnia Instrumentacji zarządzania do narzędzia do zarządzania zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="44221-107">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="44221-108">Dostawca WMI jest składnik, który ujawnia Instrumentacji w czasie wykonywania za pośrednictwem interfejsu zgodnego WBEM.</span><span class="sxs-lookup"><span data-stu-id="44221-108">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="44221-109">Zawiera zestaw obiektów WMI, które mają pary atrybut/wartość.</span><span class="sxs-lookup"><span data-stu-id="44221-109">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="44221-110">Pary może mieć wiele typów prostych.</span><span class="sxs-lookup"><span data-stu-id="44221-110">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="44221-111">Narzędzia do zarządzania mogą łączyć się usługi za pomocą interfejsu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="44221-111">Management tools can connect to the services through the interface at runtime.</span></span> [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="44221-112"> udostępnia Atrybuty usług, takich jak adresy, powiązania zachowania i odbiorników.</span><span class="sxs-lookup"><span data-stu-id="44221-112"> exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="44221-113">W pliku konfiguracyjnym aplikacji można aktywować wbudowanego dostawcy WMI.</span><span class="sxs-lookup"><span data-stu-id="44221-113">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="44221-114">Jest to zrobić za pomocą `wmiProviderEnabled` atrybutu [ \<diagnostyki >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) w [ \<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) sekcji, jak pokazano w następującym przykładowym Konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="44221-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="44221-115">Ten wpis konfiguracji uwidacznia interfejs WMI.</span><span class="sxs-lookup"><span data-stu-id="44221-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="44221-116">Aplikacje do zarządzania można teraz łączenie się za pośrednictwem tego interfejsu i uzyskać dostęp z Instrumentacją zarządzania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="44221-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="44221-117">Uzyskiwanie dostępu do danych usługi WMI</span><span class="sxs-lookup"><span data-stu-id="44221-117">Accessing WMI Data</span></span>  
 <span data-ttu-id="44221-118">Wiele różnych sposobów można uzyskać dostępu do danych usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="44221-118">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="44221-119">Firma Microsoft udostępnia interfejsy API usługi WMI dla skryptów aplikacji Visual Basic, aplikacji C++ i [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="44221-119">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="44221-120">Aby uzyskać więcej informacji, zobacz [za pomocą usługi WMI](http://go.microsoft.com/fwlink/?LinkId=95183).</span><span class="sxs-lookup"><span data-stu-id="44221-120">For more information, see [Using WMI](http://go.microsoft.com/fwlink/?LinkId=95183).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="44221-121">Jeśli używasz metody podane w programie .NET Framework do uzyskania programowego dostępu do danych usługi WMI, należy zwrócić uwagę, takich metod może zgłaszać wyjątki po nawiązaniu połączenia.</span><span class="sxs-lookup"><span data-stu-id="44221-121">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="44221-122">Połączenie nie zostanie nawiązane podczas budowy <xref:System.Management.ManagementObject> wystąpienia, ale pierwszego żądania obejmujące rzeczywiste dane programu exchange.</span><span class="sxs-lookup"><span data-stu-id="44221-122">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="44221-123">W związku z tym należy używać `try..catch` bloku catch możliwych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="44221-123">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="44221-124">Można zmienić śledzenia i poziom rejestrowania komunikatów, a także opcje rejestrowania komunikatów dla `System.ServiceModel` źródła śledzenia w usłudze WMI.</span><span class="sxs-lookup"><span data-stu-id="44221-124">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="44221-125">Można to zrobić po zalogowaniu się do [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) wystąpienia, która udostępnia te właściwości, wartość logiczna: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, i `TraceLevel`.</span><span class="sxs-lookup"><span data-stu-id="44221-125">This can be done by accessing the [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="44221-126">W związku z tym jeśli skonfiguruj odbiornik śledzenia dla rejestrowanie komunikatów, ale ustawiona korzystać z tych opcji do `false` w konfiguracji można później zmienić ich `true` gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="44221-126">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="44221-127">Umożliwi to efektywne rejestrowanie komunikatów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="44221-127">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="44221-128">Podobnie po włączeniu rejestrowania w pliku konfiguracyjnym komunikatów, można ją wyłączyć w czasie wykonywania za pomocą usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="44221-128">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="44221-129">Należy zwrócić uwagę że jeśli nie rejestrowanie komunikatów śledzenia odbiorników dla rejestrowanie komunikatów lub nie `System.ServiceModel` obiektów nasłuchujących śledzenia śledzenia są określone w pliku konfiguracji, żadne zmiany są brane pod efekt, mimo że zmiany są akceptowane przez usługę WMI.</span><span class="sxs-lookup"><span data-stu-id="44221-129">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="44221-130">Aby uzyskać więcej informacji na temat prawidłowo konfigurowania odpowiednich odbiorników, zobacz [Konfigurowanie rejestrowania komunikatów](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) i [Konfigurowanie śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="44221-130">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) and [Configuring Tracing](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="44221-131">Poziom śledzenia wszystkich innych źródeł śledzenia określony w konfiguracji jest skuteczne, podczas uruchamiania aplikacji i nie można zmienić.</span><span class="sxs-lookup"><span data-stu-id="44221-131">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="44221-132"> przedstawia `GetOperationCounterInstanceName` metod dla skryptów.</span><span class="sxs-lookup"><span data-stu-id="44221-132"> exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="44221-133">Ta metoda zwraca nazwę wystąpienia licznika wydajności w przypadku udostępnienia operacji o nazwie.</span><span class="sxs-lookup"><span data-stu-id="44221-133">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="44221-134">Dane wejściowe nie są jednak zweryfikować.</span><span class="sxs-lookup"><span data-stu-id="44221-134">However, it does not validate your input.</span></span> <span data-ttu-id="44221-135">W związku z tym Jeśli podasz nazwę operacji niepoprawne, zwracana jest nazwa niepoprawny licznik.</span><span class="sxs-lookup"><span data-stu-id="44221-135">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="44221-136">`OutgoingChannel` Właściwość `Service` wystąpienia nie będą uwzględniane kanały otwarte przez usługę, aby połączyć się z inną usługą, w przypadku [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] klienta usługi docelowej nie jest tworzony w `Service` metody.</span><span class="sxs-lookup"><span data-stu-id="44221-136">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="44221-137">**Uwaga** obsługuje tylko WMI <xref:System.TimeSpan> wartość 3 miejsc dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="44221-137">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="44221-138">Na przykład, jeśli Usługa ustawia jedną z jej właściwości na <xref:System.TimeSpan.MaxValue>, jego wartość zostanie obcięta po 3 miejsc dziesiętnych, podczas wyświetlania za pomocą usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="44221-138">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="44221-139">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="44221-139">Security</span></span>  
 <span data-ttu-id="44221-140">Ponieważ [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] dostawcy WMI umożliwia odnajdywanie usług w środowisku, należy zachować wyjątkową ostrożność za udzielanie dostępu do niego.</span><span class="sxs-lookup"><span data-stu-id="44221-140">Because the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="44221-141">Jeśli zmniejszą domyślnego dostępu tylko do administratora, może zezwolić stron zaufanych mniej dostęp do poufnych danych w danym środowisku.</span><span class="sxs-lookup"><span data-stu-id="44221-141">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="44221-142">W szczególności jeśli Poluzuj uprawnienia na zdalny dostęp do usługi WMI, zalewania ataków mogą wystąpić.</span><span class="sxs-lookup"><span data-stu-id="44221-142">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="44221-143">Jeśli proces jest wypełniony nadmiernego żądania usługi WMI, jego wydajność może znacznie mniej wydajna.</span><span class="sxs-lookup"><span data-stu-id="44221-143">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="44221-144">Ponadto jeśli zmniejszą uprawnienia dostępu do pliku MOF, Zaufane mniej strony można manipulować zachowanie usługi WMI i alter obiektów, które są ładowane w schemacie WMI.</span><span class="sxs-lookup"><span data-stu-id="44221-144">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="44221-145">Na przykład pola można usunąć danych o kluczowym znaczeniu jest ukrywane przez administratora lub pola, które nie wypełnić lub spowodować wyjątki są dodawane do pliku.</span><span class="sxs-lookup"><span data-stu-id="44221-145">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="44221-146">Domyślnie [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] dostawcy WMI przyznaje "Wykonaj metodę", "zapis dostawcy" i "Włącz konto" uprawnień administratora, a "Włącz konto" uprawnień dla platformy ASP.NET, Usługa lokalna i Usługa sieciowa.</span><span class="sxs-lookup"><span data-stu-id="44221-146">By default, the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="44221-147">W szczególności na inną niż[!INCLUDE[wv](../../../../../includes/wv-md.md)] platform, konto ASP.NET ma dostęp do odczytu przestrzeni nazw usługi WMI ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="44221-147">In particular, on non-[!INCLUDE[wv](../../../../../includes/wv-md.md)] platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="44221-148">Jeśli nie chcesz przyznać odpowiednie uprawnienia do określonej grupy użytkowników, należy albo Dezaktywuj dostawcy usługi WMI (on jest domyślnie wyłączona) lub wyłączyć dostęp do określonej grupy użytkowników.</span><span class="sxs-lookup"><span data-stu-id="44221-148">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="44221-149">Ponadto podczas próby włączenia usługi WMI za pomocą konfiguracji usługi WMI może nie być włączone z powodu niewystarczających użytkownika uprawnień.</span><span class="sxs-lookup"><span data-stu-id="44221-149">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="44221-150">Jednak brak zdarzenia są zapisywane w dzienniku zdarzeń, aby zarejestrować ten błąd.</span><span class="sxs-lookup"><span data-stu-id="44221-150">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="44221-151">Aby zmodyfikować poziomy uprawnień użytkownika, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="44221-151">To modify user privilege levels, use the following steps.</span></span>  
  
1.  <span data-ttu-id="44221-152">Kliknij przycisk Start, a następnie uruchom i wpisz **compmgmt.msc**.</span><span class="sxs-lookup"><span data-stu-id="44221-152">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2.  <span data-ttu-id="44221-153">Kliknij prawym przyciskiem myszy **usług i aplikacji/WMI formanty** wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="44221-153">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3.  <span data-ttu-id="44221-154">Wybierz **zabezpieczeń** kartę, a następnie przejdź do **główny/ServiceModel** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="44221-154">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="44221-155">Kliknij przycisk **zabezpieczeń** przycisku.</span><span class="sxs-lookup"><span data-stu-id="44221-155">Click the **Security** button.</span></span>  
  
4.  <span data-ttu-id="44221-156">Wybierz określonej grupy lub użytkownika, który ma zostać kontroli dostępu i użycia **Zezwalaj** lub **Odmów** pole wyboru, aby skonfigurować uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="44221-156">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="44221-157">Udzielanie uprawnień rejestracji WCF WMI dodatkowym użytkownikom</span><span class="sxs-lookup"><span data-stu-id="44221-157">Granting WCF WMI Registration Permissions to Additional Users</span></span>  
 <span data-ttu-id="44221-158">Usługa WCF umożliwia dane zarządzania z usługą WMI.</span><span class="sxs-lookup"><span data-stu-id="44221-158">WCF exposes management data to WMI.</span></span> <span data-ttu-id="44221-159">Robi to przez hosting w trakcie dostawcy WMI, czasem nazywany "odłączonego dostawcy".</span><span class="sxs-lookup"><span data-stu-id="44221-159">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="44221-160">Dla danych zarządzania, które mają być uwidaczniane konto, które rejestruje ten dostawca musi mieć odpowiednie uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="44221-160">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="44221-161">W systemie Windows mały zestaw kont uprzywilejowanych można zarejestrować dostawcy rozdzielonymi domyślnie.</span><span class="sxs-lookup"><span data-stu-id="44221-161">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="44221-162">Jest to problem, ponieważ użytkownicy często mają być udostępnianie danych usługi WMI z poziomu usługi WCF uruchomiony na koncie, który nie znajduje się w domyślnym zestawem.</span><span class="sxs-lookup"><span data-stu-id="44221-162">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="44221-163">Aby zapewnić dostęp, administrator musi Przyznaj następujące uprawnienia do dodatkowe konta w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="44221-163">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1.  <span data-ttu-id="44221-164">Uprawnienia dostępu do usługi WCF Namespace WMI.</span><span class="sxs-lookup"><span data-stu-id="44221-164">Permission to access to the WCF WMI Namespace.</span></span>  
  
2.  <span data-ttu-id="44221-165">Uprawnienia do rejestrowania dostawcy instrumentacji WMI programu WCF odłączona.</span><span class="sxs-lookup"><span data-stu-id="44221-165">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="44221-166">Aby udzielić uprawnień dostępu do przestrzeni nazw usługi WMI</span><span class="sxs-lookup"><span data-stu-id="44221-166">To grant WMI namespace access permission</span></span>  
  
1.  <span data-ttu-id="44221-167">Uruchom następujący skrypt programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44221-167">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting Access to root/servicemodel WMI namespace to built in users group"  
    write-host ""  
  
    # Create the binary representation of the permissions to grant in SDDL  
    $newPermissions = "O:BAG:BAD:P(A;CI;CCDCLCSWRPWPRCWD;;;BA)(A;CI;CC;;;NS)(A;CI;CC;;;LS)(A;CI;CC;;;BU)"  
    $converter = new-object system.management.ManagementClass Win32_SecurityDescriptorHelper  
    $binarySD = $converter.SDDLToBinarySD($newPermissions)  
    $convertedPermissions = ,$binarySD.BinarySD  
  
    # Get the object used to set the permissions  
    $security = gwmi -namespace root/servicemodel -class __SystemSecurity  
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "Previous ACL: "$outsddl.SDDL  
  
    # Change the Access Control List (ACL) using SDDL  
    $result = $security.PsBase.InvokeMethod("SetSD",$convertedPermissions)   
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "New ACL:      "$outsddl.SDDL  
    write-host ""  
    ```  
  
     <span data-ttu-id="44221-168">Ten skrypt programu PowerShell używa definicji języka SDDL (Security Descriptor), aby udzielić dostępu grupy wbudowane użytkowników do obszaru nazw WMI "główny/servicemodel".</span><span class="sxs-lookup"><span data-stu-id="44221-168">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="44221-169">Określa on następujące listy ACL:</span><span class="sxs-lookup"><span data-stu-id="44221-169">It specifies the following ACLs:</span></span>  
  
    -   <span data-ttu-id="44221-170">Wbudowanego konta administratora (BA) — już dostępu.</span><span class="sxs-lookup"><span data-stu-id="44221-170">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    -   <span data-ttu-id="44221-171">Usługa nazw (NS) - sieciowa ma już dostępu.</span><span class="sxs-lookup"><span data-stu-id="44221-171">Network Service (NS) - Already Had Access.</span></span>  
  
    -   <span data-ttu-id="44221-172">System lokalny (LS) - ma już dostępu.</span><span class="sxs-lookup"><span data-stu-id="44221-172">Local System (LS) - Already Had Access.</span></span>  
  
    -   <span data-ttu-id="44221-173">Wbudowanych użytkownicy — grupa, aby udzielić dostępu do.</span><span class="sxs-lookup"><span data-stu-id="44221-173">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="44221-174">Aby przyznać dostawcy dostęp do rejestracji</span><span class="sxs-lookup"><span data-stu-id="44221-174">To grant provider registration access</span></span>  
  
1.  <span data-ttu-id="44221-175">Uruchom następujący skrypt programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44221-175">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting WCF provider registration access to built in users group"  
    write-host ""  
    # Set security on ServiceModel provider  
    $provider = get-WmiObject -namespace "root\servicemodel" __Win32Provider  
  
    write-host "Previous ACL: "$provider.SecurityDescriptor  
    $result = $provider.SecurityDescriptor = "O:BUG:BUD:(A;;0x1;;;BA)(A;;0x1;;;NS)(A;;0x1;;;LS)(A;;0x1;;;BU)"  
  
    # Commit the changes and display it to the console  
    $result = $provider.Put()  
    write-host "New ACL:      "$provider.SecurityDescriptor  
    write-host ""  
    ```  
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="44221-176">Udzielanie dostępu do dowolnych użytkowników lub grup</span><span class="sxs-lookup"><span data-stu-id="44221-176">Granting Access to Arbitrary Users or Groups</span></span>  
 <span data-ttu-id="44221-177">Przykład w tej sekcji przyznaje uprawnienia rejestracji dostawcy WMI do wszystkich użytkowników lokalnych.</span><span class="sxs-lookup"><span data-stu-id="44221-177">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="44221-178">Jeśli chcesz udzielić dostępu do użytkownika lub grupę, która nie korzysta z wbudowanej w, następnie należy uzyskać tego użytkownika lub grupy identyfikator zabezpieczeń (SID).</span><span class="sxs-lookup"><span data-stu-id="44221-178">If you want to grant access to a user or group that is not built in, then you must obtain that user or group’s Security Identifier (SID).</span></span> <span data-ttu-id="44221-179">Nie istnieje prosty sposób można pobrać identyfikatora SID dla dowolnego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="44221-179">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="44221-180">Jedna z metod jest Zaloguj się jako odpowiedniego użytkownika, a następnie wystawiania następujące polecenia powłoki.</span><span class="sxs-lookup"><span data-stu-id="44221-180">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```  
Whoami /user  
```  
  
 <span data-ttu-id="44221-181">Zapewnia to identyfikator SID bieżącego użytkownika, ale nie można użyć tej metody można pobrać identyfikatora SID dla dowolnego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="44221-181">This provides the SID of the current user, but this method cannot be used to get the SID on any arbitrary user.</span></span> <span data-ttu-id="44221-182">Innej metody, aby uzyskać identyfikator SID jest użycie [getsid.exe](http://go.microsoft.com/fwlink/?LinkId=186467) narzędzia z [narzędzi systemu Windows 2000 Resource Kit dla zadań administracyjnych](http://go.microsoft.com/fwlink/?LinkId=178660).</span><span class="sxs-lookup"><span data-stu-id="44221-182">Another method to get the SID is to use the [getsid.exe](http://go.microsoft.com/fwlink/?LinkId=186467) tool from the [Windows 2000 Resource Kit Tools for administrative tasks](http://go.microsoft.com/fwlink/?LinkId=178660).</span></span> <span data-ttu-id="44221-183">To narzędzie porównuje SID dwóch użytkowników (lokalnego lub domeny), a po stronie efekt drukuje dwa identyfikatory SID do wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="44221-183">This tool compares the SID of two users (local or domain), and as a side effect prints the two SIDs to the command line.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="44221-184"> [Dobrze znane identyfikatory SID](http://go.microsoft.com/fwlink/?LinkId=186468).</span><span class="sxs-lookup"><span data-stu-id="44221-184"> [Well Known SIDs](http://go.microsoft.com/fwlink/?LinkId=186468).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="44221-185">Uzyskiwanie dostępu do wystąpienia obiektu zdalną usługę WMI</span><span class="sxs-lookup"><span data-stu-id="44221-185">Accessing Remote WMI Object Instances</span></span>  
 <span data-ttu-id="44221-186">Jeśli chcesz uzyskać dostęp do [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] wystąpienia usługi WMI na komputerze zdalnym, należy włączyć prywatność pakietów narzędzia używane dla dostępu.</span><span class="sxs-lookup"><span data-stu-id="44221-186">If you need to access [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="44221-187">W poniższej sekcji opisano jak to osiągnąć przy użyciu usługi WMI CIM Studio, Tester oprzyrządowania Instrumentacji zarządzania Windows, jak również .NET SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="44221-187">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="44221-188">WMI CIM Studio</span><span class="sxs-lookup"><span data-stu-id="44221-188">WMI CIM Studio</span></span>  
 <span data-ttu-id="44221-189">Jeśli zainstalowano [narzędzia administracyjne WMI](http://go.microsoft.com/fwlink/?LinkId=95185), można użyć WMI CIM Studio do wystąpień WMI dostępu.</span><span class="sxs-lookup"><span data-stu-id="44221-189">If you have installed [WMI Administrative Tools](http://go.microsoft.com/fwlink/?LinkId=95185), you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="44221-190">Narzędzia znajdują się w folderze</span><span class="sxs-lookup"><span data-stu-id="44221-190">The tools are in the following folder</span></span>  
  
 <span data-ttu-id="44221-191">**Narzędzia Files\WMI %Windir%\Program\\**</span><span class="sxs-lookup"><span data-stu-id="44221-191">**%windir%\Program Files\WMI Tools\\**</span></span>  
  
1.  <span data-ttu-id="44221-192">W **Połącz z przestrzeni nazw:** wpisz **root\ServiceModel** i kliknij przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="44221-192">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2.  <span data-ttu-id="44221-193">W **WMI CIM Studio logowania** okna, kliknij przycisk **Opcje >>** przycisk, aby rozwinąć okna.</span><span class="sxs-lookup"><span data-stu-id="44221-193">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="44221-194">Wybierz **prywatność pakietów** dla **poziom uwierzytelniania**i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="44221-194">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="44221-195">Tester oprzyrządowania Instrumentacji zarządzania Windows</span><span class="sxs-lookup"><span data-stu-id="44221-195">Windows Management Instrumentation Tester</span></span>  
 <span data-ttu-id="44221-196">To narzędzie jest instalowane przez system Windows.</span><span class="sxs-lookup"><span data-stu-id="44221-196">This tool is installed by Windows.</span></span> <span data-ttu-id="44221-197">Aby go uruchomić, należy uruchomić konsoli poleceń, wpisując **cmd.exe** w **Start/Uruchom** okno dialogowe i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="44221-197">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="44221-198">Następnie wpisz **wbemtest.exe** w oknie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="44221-198">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="44221-199">Następnie zostanie uruchomione Narzędzie Tester oprzyrządowania Instrumentacji zarządzania Windows.</span><span class="sxs-lookup"><span data-stu-id="44221-199">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1.  <span data-ttu-id="44221-200">Kliknij przycisk **Connect** przycisk w prawym górnym rogu okna.</span><span class="sxs-lookup"><span data-stu-id="44221-200">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2.  <span data-ttu-id="44221-201">W nowym oknie, wprowadź **root\ServiceModel** dla **Namespace** pola i wybierz pozycję **prywatność pakietów** dla **poziom uwierzytelniania**.</span><span class="sxs-lookup"><span data-stu-id="44221-201">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="44221-202">Kliknij przycisk **Połącz**.</span><span class="sxs-lookup"><span data-stu-id="44221-202">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="44221-203">Za pomocą kodu zarządzanego</span><span class="sxs-lookup"><span data-stu-id="44221-203">Using Managed Code</span></span>  
 <span data-ttu-id="44221-204">Można również przejść zdalnego wystąpień WMI programowo przy użyciu klasy podał <xref:System.Management> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="44221-204">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="44221-205">Poniższy przykład kodu pokazuje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="44221-205">The following code sample demonstrates how to do this.</span></span>  
  
```  
String wcfNamespace = String.Format(@"\\{0}\Root\ServiceModel",      
   this.serviceMachineName);  
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
