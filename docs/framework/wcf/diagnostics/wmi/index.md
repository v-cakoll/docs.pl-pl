---
title: Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: 0c803e3988f7a63980d991190db87c263c992b80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185673"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="8f40d-102">Używanie Instrumentacji zarządzania Windows na potrzeby diagnostyki</span><span class="sxs-lookup"><span data-stu-id="8f40d-102">Using Windows Management Instrumentation for Diagnostics</span></span>
<span data-ttu-id="8f40d-103">Windows Communication Foundation (WCF) udostępnia dane inspekcji usługi w czasie wykonywania za pośrednictwem dostawcy WCF Windows Instrumentation (WMI) dostawcy.</span><span class="sxs-lookup"><span data-stu-id="8f40d-103">Windows Communication Foundation (WCF) exposes inspection data of a service at runtime through a WCF Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="8f40d-104">Włączanie funkcji WMI</span><span class="sxs-lookup"><span data-stu-id="8f40d-104">Enabling WMI</span></span>  
 <span data-ttu-id="8f40d-105">WMI jest wdrożenie microsoftu web-based Enterprise Management (WBEM) standard.</span><span class="sxs-lookup"><span data-stu-id="8f40d-105">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="8f40d-106">Aby uzyskać więcej informacji na temat zestawie WMI SDK, zobacz [Instrumentacja zarządzania windowsem](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="8f40d-106">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="8f40d-107">WBEM jest standardem branżowym w zakresie sposobu, w jaki aplikacje narażają instrumentację zarządzania na zewnętrzne narzędzia do zarządzania.</span><span class="sxs-lookup"><span data-stu-id="8f40d-107">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="8f40d-108">Dostawca WMI jest składnikiem, który udostępnia instrumentacji w czasie wykonywania za pośrednictwem interfejsu zgodnego z WBEM.</span><span class="sxs-lookup"><span data-stu-id="8f40d-108">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="8f40d-109">Składa się z zestawu obiektów WMI, które mają pary atrybutów/wartości.</span><span class="sxs-lookup"><span data-stu-id="8f40d-109">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="8f40d-110">Pary mogą być wielu prostych typów.</span><span class="sxs-lookup"><span data-stu-id="8f40d-110">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="8f40d-111">Narzędzia do zarządzania można połączyć się z usługami za pośrednictwem interfejsu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8f40d-111">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="8f40d-112">WCF udostępnia atrybuty usług, takich jak adresy, powiązania, zachowania i detektory.</span><span class="sxs-lookup"><span data-stu-id="8f40d-112">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="8f40d-113">Wbudowany dostawca WMI można aktywować w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8f40d-113">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="8f40d-114">Odbywa się to `wmiProviderEnabled` za pomocą atrybutu [ \<diagnostyki>](../../../configure-apps/file-schema/wcf/diagnostics.md) w [ \<sekcji system.serviceModel>,](../../../configure-apps/file-schema/wcf/system-servicemodel.md) jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="8f40d-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="8f40d-115">Ten wpis konfiguracji udostępnia interfejs WMI.</span><span class="sxs-lookup"><span data-stu-id="8f40d-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="8f40d-116">Aplikacje do zarządzania mogą teraz łączyć się za pośrednictwem tego interfejsu i uzyskiwać dostęp do instrumentacji zarządzania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8f40d-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="8f40d-117">Uzyskiwanie dostępu do danych usługi WMI</span><span class="sxs-lookup"><span data-stu-id="8f40d-117">Accessing WMI Data</span></span>  
 <span data-ttu-id="8f40d-118">Dostęp do danych usługi WMI można uzyskać na wiele różnych sposobów.</span><span class="sxs-lookup"><span data-stu-id="8f40d-118">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="8f40d-119">Firma Microsoft udostępnia interfejsy API usługi WMI dla skryptów, aplikacji Visual Basic, aplikacji W++ i programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8f40d-119">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="8f40d-120">Aby uzyskać więcej informacji, zobacz [Korzystanie z usługi WMI](/windows/win32/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="8f40d-120">For more information, see [Using WMI](/windows/win32/wmisdk/using-wmi).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="8f40d-121">Jeśli używasz .NET Framework pod warunkiem metody programowego dostępu do danych WMI, należy pamiętać, że takie metody mogą zgłaszać wyjątki po nawiązaniu połączenia.</span><span class="sxs-lookup"><span data-stu-id="8f40d-121">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="8f40d-122">Połączenie nie jest ustanawiane podczas <xref:System.Management.ManagementObject> budowy wystąpienia, ale na pierwsze żądanie obejmujące rzeczywistą wymianę danych.</span><span class="sxs-lookup"><span data-stu-id="8f40d-122">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="8f40d-123">W związku z tym `try..catch` należy użyć bloku, aby złapać możliwe wyjątki.</span><span class="sxs-lookup"><span data-stu-id="8f40d-123">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="8f40d-124">Można zmienić poziom śledzenia i rejestrowania wiadomości, a także `System.ServiceModel` opcje rejestrowania wiadomości dla źródła śledzenia w UMI.</span><span class="sxs-lookup"><span data-stu-id="8f40d-124">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="8f40d-125">Można to zrobić, uzyskując dostęp do wystąpienia [AppDomainInfo,](appdomaininfo.md) które `LogMessagesAtServiceLevel` `LogMessagesAtTransportLevel`udostępnia `LogMalformedMessages`te `TraceLevel`właściwości logiczne: , , i .</span><span class="sxs-lookup"><span data-stu-id="8f40d-125">This can be done by accessing the [AppDomainInfo](appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="8f40d-126">W związku z tym jeśli skonfigurujesz odbiornik śledzenia do `false` rejestrowania wiadomości, ale ustaw `true` te opcje w konfiguracji, można później zmienić je na gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="8f40d-126">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="8f40d-127">Umożliwi to skuteczne rejestrowanie komunikatów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8f40d-127">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="8f40d-128">Podobnie po włączeniu rejestrowania wiadomości w pliku konfiguracji, można go wyłączyć w czasie wykonywania przy użyciu usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="8f40d-128">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="8f40d-129">Należy pamiętać, że jeśli w pliku konfiguracyjnym nie `System.ServiceModel` określono żadnych odbiorników śledzenia rejestrowania komunikatów do rejestrowania komunikatów lub nie określono odbiorników śledzenia śledzenia, żadne zmiany nie zostaną wprowadzone, nawet jeśli zmiany zostaną zaakceptowane przez usługę WMI.</span><span class="sxs-lookup"><span data-stu-id="8f40d-129">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="8f40d-130">Aby uzyskać więcej informacji na temat prawidłowego konfigurowania odpowiednich odbiorników, zobacz [Konfigurowanie rejestrowania wiadomości](../configuring-message-logging.md) i [konfigurowanie śledzenia](../tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="8f40d-130">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../configuring-message-logging.md) and [Configuring Tracing](../tracing/configuring-tracing.md).</span></span> <span data-ttu-id="8f40d-131">Poziom śledzenia wszystkich innych źródeł śledzenia określonych przez konfigurację jest skuteczny po uruchomieniu aplikacji i nie można go zmienić.</span><span class="sxs-lookup"><span data-stu-id="8f40d-131">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 <span data-ttu-id="8f40d-132">WCF udostępnia `GetOperationCounterInstanceName` metodę skryptów.</span><span class="sxs-lookup"><span data-stu-id="8f40d-132">WCF exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="8f40d-133">Ta metoda zwraca nazwę wystąpienia licznika wydajności, jeśli podasz jej nazwę operacji.</span><span class="sxs-lookup"><span data-stu-id="8f40d-133">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="8f40d-134">Jednak nie sprawdza poprawności danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="8f40d-134">However, it does not validate your input.</span></span> <span data-ttu-id="8f40d-135">W związku z tym jeśli podasz niepoprawną nazwę operacji, zwracana jest nieprawidłowa nazwa licznika.</span><span class="sxs-lookup"><span data-stu-id="8f40d-135">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="8f40d-136">Właściwość `OutgoingChannel` `Service` wystąpienia nie zlicza kanałów otwartych przez usługę w celu połączenia się z inną usługą, jeśli klient WCF do usługi docelowej nie jest tworzony w ramach `Service` metody.</span><span class="sxs-lookup"><span data-stu-id="8f40d-136">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the WCF client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="8f40d-137">**Uwaga** WMI obsługuje <xref:System.TimeSpan> tylko wartość do 3 przecinkami po przecinku.</span><span class="sxs-lookup"><span data-stu-id="8f40d-137">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="8f40d-138">Na przykład jeśli usługa ustawia jedną z <xref:System.TimeSpan.MaxValue>jego właściwości, jej wartość jest obcinana po 3 przecinkach po przecinku podczas wyświetlania za pośrednictwem usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="8f40d-138">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="8f40d-139">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="8f40d-139">Security</span></span>  
 <span data-ttu-id="8f40d-140">Ponieważ dostawca WCF WMI umożliwia odnajdowanie usług w środowisku, należy zachować szczególną ostrożność podczas udzielania dostępu do niego.</span><span class="sxs-lookup"><span data-stu-id="8f40d-140">Because the WCF WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="8f40d-141">Jeśli rozluźnisz domyślny dostęp tylko dla administratora, możesz zezwolić mniej zaufanym stronom na dostęp do poufnych danych w danym środowisku.</span><span class="sxs-lookup"><span data-stu-id="8f40d-141">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="8f40d-142">W szczególności, jeśli poluzujesz uprawnienia do zdalnego dostępu WMI, może wystąpić ataki zalewające.</span><span class="sxs-lookup"><span data-stu-id="8f40d-142">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="8f40d-143">Jeśli proces jest zalany przez nadmierne żądania WMI, jego wydajność może ulec pogorszeniu.</span><span class="sxs-lookup"><span data-stu-id="8f40d-143">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="8f40d-144">Ponadto w przypadku rozluźnienia uprawnień dostępu do pliku MOF mniej zaufanych stron można manipulować zachowaniem usługi WMI i zmieniać obiekty, które są ładowane w schemacie WMI.</span><span class="sxs-lookup"><span data-stu-id="8f40d-144">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="8f40d-145">Na przykład pola można usunąć w taki sposób, że dane krytyczne są ukryte przed administratorem lub że pola, które nie wypełniają lub powodują wyjątki, są dodawane do pliku.</span><span class="sxs-lookup"><span data-stu-id="8f40d-145">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="8f40d-146">Domyślnie dostawca WCF WMI udziela uprawnień "execute method", "provider write" i "enable account" dla administratora oraz uprawnień "włącz konto" dla ASP.NET, usługi lokalnej i usługi sieciowej.</span><span class="sxs-lookup"><span data-stu-id="8f40d-146">By default, the WCF WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="8f40d-147">W szczególności na platformach innych niż Windows Vista konto ASP.NET ma dostęp do odczytu do przestrzeni nazw WMI ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="8f40d-147">In particular, on non-Windows Vista platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="8f40d-148">Jeśli nie chcesz przyznawać tych uprawnień określonej grupie użytkowników, należy dezaktywować dostawcę usługi WMI (jest on domyślnie wyłączony) lub wyłączyć dostęp dla określonej grupy użytkowników.</span><span class="sxs-lookup"><span data-stu-id="8f40d-148">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="8f40d-149">Ponadto podczas próby włączenia usługi WMI za pośrednictwem konfiguracji usługa WMI może nie być włączona z powodu niewystarczających uprawnień użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8f40d-149">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="8f40d-150">Jednak żadne zdarzenie nie jest zapisywane w dzienniku zdarzeń, aby zarejestrować ten błąd.</span><span class="sxs-lookup"><span data-stu-id="8f40d-150">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="8f40d-151">Aby zmodyfikować poziomy uprawnień użytkownika, należy wykonać następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="8f40d-151">To modify user privilege levels, use the following steps.</span></span>  
  
1. <span data-ttu-id="8f40d-152">Kliknij przycisk Start, a następnie pozycję Uruchom i wpisz **plik compmgmt.msc**.</span><span class="sxs-lookup"><span data-stu-id="8f40d-152">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2. <span data-ttu-id="8f40d-153">Kliknij prawym przyciskiem myszy **pozycję Usługi i kontrolki aplikacji/WMI,** aby wybrać polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="8f40d-153">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3. <span data-ttu-id="8f40d-154">Wybierz kartę **Zabezpieczenia** i przejdź do obszaru nazw **Root/ServiceModel.**</span><span class="sxs-lookup"><span data-stu-id="8f40d-154">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="8f40d-155">Kliknij przycisk **Zabezpieczenia.**</span><span class="sxs-lookup"><span data-stu-id="8f40d-155">Click the **Security** button.</span></span>  
  
4. <span data-ttu-id="8f40d-156">Zaznacz określoną grupę lub użytkownika, do którego chcesz kontrolować dostęp, i użyj pola wyboru **Zezwalaj** lub **Odmów,** aby skonfigurować uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="8f40d-156">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="8f40d-157">Udzielanie uprawnień rejestracyjnych WCF WMI dodatkowym użytkownikom</span><span class="sxs-lookup"><span data-stu-id="8f40d-157">Granting WCF WMI Registration Permissions to Additional Users</span></span>  
 <span data-ttu-id="8f40d-158">WCF udostępnia dane zarządzania do WMI.</span><span class="sxs-lookup"><span data-stu-id="8f40d-158">WCF exposes management data to WMI.</span></span> <span data-ttu-id="8f40d-159">Robi to, hostując w procesie dostawcę WMI, czasami nazywanego "dostawcą oddzielonym od produkcji".</span><span class="sxs-lookup"><span data-stu-id="8f40d-159">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="8f40d-160">Aby dane zarządzania mają być udostępniane, konto, które rejestruje tego dostawcy musi mieć odpowiednie uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="8f40d-160">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="8f40d-161">W systemie Windows tylko niewielki zestaw kont uprzywilejowanych można domyślnie zarejestrować dostawców oddzielonych od produkcji.</span><span class="sxs-lookup"><span data-stu-id="8f40d-161">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="8f40d-162">Jest to problem, ponieważ użytkownicy często chcą udostępnić dane WMI z usługi WCF uruchomionej na koncie, które nie znajduje się w zestawie domyślnym.</span><span class="sxs-lookup"><span data-stu-id="8f40d-162">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="8f40d-163">Aby zapewnić ten dostęp, administrator musi udzielić następujących uprawnień do dodatkowego konta w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="8f40d-163">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1. <span data-ttu-id="8f40d-164">Uprawnienie dostępu do obszaru nazw WCF WMI.</span><span class="sxs-lookup"><span data-stu-id="8f40d-164">Permission to access to the WCF WMI Namespace.</span></span>  
  
2. <span data-ttu-id="8f40d-165">Uprawnienie do rejestracji dostawcy WMI odłączonych od produkcji WCF.</span><span class="sxs-lookup"><span data-stu-id="8f40d-165">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="8f40d-166">Aby udzielić uprawnień dostępu do obszaru nazw WMI</span><span class="sxs-lookup"><span data-stu-id="8f40d-166">To grant WMI namespace access permission</span></span>  
  
1. <span data-ttu-id="8f40d-167">Uruchom następujący skrypt programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f40d-167">Run the following PowerShell script.</span></span>  
  
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
  
     <span data-ttu-id="8f40d-168">Ten skrypt programu PowerShell używa języka definicji deskryptora zabezpieczeń (SDDL) w celu przyznania grupie wbudowanych użytkowników dostępu do obszaru nazw WMI "root/servicemodel".</span><span class="sxs-lookup"><span data-stu-id="8f40d-168">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="8f40d-169">Określa następujące listy ACL:</span><span class="sxs-lookup"><span data-stu-id="8f40d-169">It specifies the following ACLs:</span></span>  
  
    - <span data-ttu-id="8f40d-170">Wbudowany administrator (BA) - miał już dostęp.</span><span class="sxs-lookup"><span data-stu-id="8f40d-170">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="8f40d-171">Usługa sieciowa (NS) - miał już dostęp.</span><span class="sxs-lookup"><span data-stu-id="8f40d-171">Network Service (NS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="8f40d-172">System lokalny (LS) - miał już dostęp.</span><span class="sxs-lookup"><span data-stu-id="8f40d-172">Local System (LS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="8f40d-173">Wbudowane użytkowników — grupa, do aby udzielić dostępu do.</span><span class="sxs-lookup"><span data-stu-id="8f40d-173">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="8f40d-174">Aby udzielić dostępu do rejestracji dostawcy</span><span class="sxs-lookup"><span data-stu-id="8f40d-174">To grant provider registration access</span></span>  
  
1. <span data-ttu-id="8f40d-175">Uruchom następujący skrypt programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f40d-175">Run the following PowerShell script.</span></span>  
  
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
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="8f40d-176">Udzielanie dostępu do dowolnych użytkowników lub grup</span><span class="sxs-lookup"><span data-stu-id="8f40d-176">Granting Access to Arbitrary Users or Groups</span></span>  
 <span data-ttu-id="8f40d-177">W tym przykładzie w tej sekcji przyznaje uprawnienia rejestracji dostawcy usługi WMI dla wszystkich użytkowników lokalnych.</span><span class="sxs-lookup"><span data-stu-id="8f40d-177">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="8f40d-178">Jeśli chcesz udzielić dostępu do użytkownika lub grupy, która nie jest wbudowana, należy uzyskać identyfikator zabezpieczeń tego użytkownika lub grupy (SID).</span><span class="sxs-lookup"><span data-stu-id="8f40d-178">If you want to grant access to a user or group that is not built in, then you must obtain that user or group’s Security Identifier (SID).</span></span> <span data-ttu-id="8f40d-179">Nie ma prostego sposobu, aby uzyskać identyfikator SID dla dowolnego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8f40d-179">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="8f40d-180">Jedną z metod jest zalogowanie się jako żądany użytkownik, a następnie wydanie następującego polecenia powłoki.</span><span class="sxs-lookup"><span data-stu-id="8f40d-180">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```console
Whoami /user  
```  
  
 <span data-ttu-id="8f40d-181">Zapewnia to identyfikator SID bieżącego użytkownika, ale ta metoda nie może służyć do uzyskania identyfikatora SID na dowolnego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8f40d-181">This provides the SID of the current user, but this method cannot be used to get the SID on any arbitrary user.</span></span> <span data-ttu-id="8f40d-182">Inną metodą uzyskania identyfikatora SID jest użycie narzędzia [getsid.exe](/windows/win32/wmisdk/using-wmi) z narzędzi zestawu zasobów systemu Windows 2000 do wykonywania zadań administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="8f40d-182">Another method to get the SID is to use the [getsid.exe](/windows/win32/wmisdk/using-wmi) tool from the Windows 2000 Resource Kit Tools for administrative tasks.</span></span> <span data-ttu-id="8f40d-183">To narzędzie porównuje identyfikator SID dwóch użytkowników (lokalnego lub domeny) i jako efekt uboczny drukuje dwa identyfikatory SID z wierszem polecenia.</span><span class="sxs-lookup"><span data-stu-id="8f40d-183">This tool compares the SID of two users (local or domain), and as a side effect prints the two SIDs to the command line.</span></span> <span data-ttu-id="8f40d-184">Aby uzyskać więcej informacji, zobacz [Dobrze znane identyfikatory SID](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="8f40d-184">For more information, see [Well Known SIDs](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="8f40d-185">Uzyskiwanie dostępu do zdalnych wystąpień obiektów usługi WMI</span><span class="sxs-lookup"><span data-stu-id="8f40d-185">Accessing Remote WMI Object Instances</span></span>  
 <span data-ttu-id="8f40d-186">Jeśli chcesz uzyskać dostęp do wystąpień WCF WMI na komputerze zdalnym, należy włączyć prywatność pakietów na narzędziach, które są używane do uzyskiwania dostępu.</span><span class="sxs-lookup"><span data-stu-id="8f40d-186">If you need to access WCF WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="8f40d-187">W poniższej sekcji opisano sposób ich osiągnięcia przy użyciu programu WMI CIM Studio, testera instrumentacji zarządzania windowsem oraz narzędzia .NET SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="8f40d-187">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="8f40d-188">WMI CIM Studio</span><span class="sxs-lookup"><span data-stu-id="8f40d-188">WMI CIM Studio</span></span>  
 <span data-ttu-id="8f40d-189">Jeśli zainstalowano [narzędzia administracyjne WMI,](https://go.microsoft.com/fwlink/?LinkId=95185)można użyć programu WMI CIM Studio, aby uzyskać dostęp do wystąpień usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="8f40d-189">If you have installed [WMI Administrative Tools](https://go.microsoft.com/fwlink/?LinkId=95185), you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="8f40d-190">Narzędzia znajdują się w następującym folderze</span><span class="sxs-lookup"><span data-stu-id="8f40d-190">The tools are in the following folder</span></span>  
  
 <span data-ttu-id="8f40d-191">**%windir%\Pliki programów\Narzędzia WMI\\**</span><span class="sxs-lookup"><span data-stu-id="8f40d-191">**%windir%\Program Files\WMI Tools\\**</span></span>  
  
1. <span data-ttu-id="8f40d-192">W oknie **Połącz z obszarem nazw wpisz** **root\ServiceModel** i kliknij przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="8f40d-192">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2. <span data-ttu-id="8f40d-193">W oknie **Logowania WMI CIM Studio** kliknij przycisk **Opcje >>,** aby rozwinąć okno.</span><span class="sxs-lookup"><span data-stu-id="8f40d-193">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="8f40d-194">Wybierz **pozycję Prywatność pakietów** dla **poziomu uwierzytelniania**i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8f40d-194">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="8f40d-195">Tester instrumentacji zarządzania windowsem</span><span class="sxs-lookup"><span data-stu-id="8f40d-195">Windows Management Instrumentation Tester</span></span>  
 <span data-ttu-id="8f40d-196">To narzędzie jest instalowane przez system Windows.</span><span class="sxs-lookup"><span data-stu-id="8f40d-196">This tool is installed by Windows.</span></span> <span data-ttu-id="8f40d-197">Aby go uruchomić, uruchom konsolę poleceń, wpisując **program cmd.exe** w oknie dialogowym **Start/Run** i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8f40d-197">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="8f40d-198">Następnie wpisz **wbemtest.exe** w oknie polecenia.</span><span class="sxs-lookup"><span data-stu-id="8f40d-198">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="8f40d-199">Następnie uruchamiane jest narzędzie Tester instrumentacji zarządzania windowsem.</span><span class="sxs-lookup"><span data-stu-id="8f40d-199">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1. <span data-ttu-id="8f40d-200">Kliknij przycisk **Połącz** w prawym górnym rogu okna.</span><span class="sxs-lookup"><span data-stu-id="8f40d-200">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2. <span data-ttu-id="8f40d-201">W nowym oknie wprowadź **katalog główny\ServiceModel** dla pola **Obszar nazw** i wybierz pozycję **Prywatność pakietów** dla **poziomu uwierzytelniania**.</span><span class="sxs-lookup"><span data-stu-id="8f40d-201">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="8f40d-202">Kliknij pozycję **Połącz**.</span><span class="sxs-lookup"><span data-stu-id="8f40d-202">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="8f40d-203">Korzystanie z kodu zarządzanego</span><span class="sxs-lookup"><span data-stu-id="8f40d-203">Using Managed Code</span></span>  
 <span data-ttu-id="8f40d-204">Można również uzyskać dostęp do zdalnych wystąpień WMI <xref:System.Management> programowo przy użyciu klas dostarczonych przez obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="8f40d-204">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="8f40d-205">Poniższy przykład kodu pokazuje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="8f40d-205">The following code sample demonstrates how to do this.</span></span>  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
