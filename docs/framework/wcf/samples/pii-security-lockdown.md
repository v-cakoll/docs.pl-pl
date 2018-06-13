---
title: Blokada zabezpieczeń PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ec8af8c7df9335774b1f3953f88c2aad438963b6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809033"
---
# <a name="pii-security-lockdown"></a><span data-ttu-id="5ca6f-102">Blokada zabezpieczeń PII</span><span class="sxs-lookup"><span data-stu-id="5ca6f-102">PII Security Lockdown</span></span>
<span data-ttu-id="5ca6f-103">W tym przykładzie pokazano, jak kontrolować kilka funkcji związanych z zabezpieczeniami usług Windows Communication Foundation (WCF) przez:</span><span class="sxs-lookup"><span data-stu-id="5ca6f-103">This sample demonstrates how to control several security-related features of a Windows Communication Foundation (WCF) service by:</span></span>  
  
-   <span data-ttu-id="5ca6f-104">Szyfrowanie poufnych informacji w pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-104">Encrypting sensitive information in a service's configuration file.</span></span>  
  
-   <span data-ttu-id="5ca6f-105">Blokowanie elementów w pliku konfiguracji, aby zagnieździć podkatalogów usługi nie może zastąpić ustawienia.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-105">Locking elements in the configuration file so that nested service subdirectories cannot override settings.</span></span>  
  
-   <span data-ttu-id="5ca6f-106">Kontrolowanie logowania z osobiście informacji osobowych w dziennikach śledzenia i wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-106">Controlling the logging of Personally Identifiable Information (PII) in trace and message logs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5ca6f-107">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5ca6f-108">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="5ca6f-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5ca6f-109">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5ca6f-110">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a><span data-ttu-id="5ca6f-111">Omówienie</span><span class="sxs-lookup"><span data-stu-id="5ca6f-111">Discussion</span></span>  
 <span data-ttu-id="5ca6f-112">Każda z tych funkcji może być używane razem lub osobno aspektów kontroli zabezpieczeń usługi.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-112">Each of these features can be used separately or together to control aspects of a service's security.</span></span> <span data-ttu-id="5ca6f-113">To nie jest wyczerpujący do zabezpieczania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-113">This is not a definitive guide to securing a WCF service.</span></span>  
  
 <span data-ttu-id="5ca6f-114">Pliki konfiguracji .NET Framework mogą zawierać poufne informacje, takie jak parametry połączenia z bazami danych.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-114">The .NET Framework configuration files can contain sensitive information such as connection strings to connect to databases.</span></span> <span data-ttu-id="5ca6f-115">W scenariuszach udostępnionego, hostowanych w sieci Web może być pożądane, aby zaszyfrować te informacje w pliku konfiguracji dla usługi tak, aby dane zawarte w pliku konfiguracji jest odporna na wyświetlanie zwykłych.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-115">In shared, Web-hosted scenarios it may be desirable to encrypt this information in the configuration file for a service so that the data contained within the configuration file is resistant to casual viewing.</span></span> <span data-ttu-id="5ca6f-116">.NET framework 2.0 lub nowszy ma możliwość szyfrowania części pliku konfiguracji za pomocą programowania interfejsu (DPAPI) lub dostawcy usług kryptograficznych RSA aplikacji ochrony danych systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-116">.NET Framework 2.0 and later has the ability to encrypt portions of the configuration file using the Windows Data Protection application programming interface (DPAPI) or the RSA Cryptographic provider.</span></span> <span data-ttu-id="5ca6f-117">Aspnet_regiis.exe przy użyciu DPAPI lub RSA można zaszyfrować wybierz części pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-117">The aspnet_regiis.exe using the DPAPI or RSA can encrypt select portions of a configuration file.</span></span>  
  
 <span data-ttu-id="5ca6f-118">W scenariuszach hostowanych w sieci Web jest możliwe usług w podkatalogach innych usług.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-118">In Web-hosted scenarios it is possible to have services in subdirectories of other services.</span></span> <span data-ttu-id="5ca6f-119">Domyślne semantycznego określania wartości konfiguracji umożliwia pliki konfiguracyjne w katalogach zagnieżdżone, aby zastąpić wartości konfiguracji w katalogu nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-119">The default semantic for determining configuration values allows configuration files in the nested directories to override the configuration values in the parent directory.</span></span> <span data-ttu-id="5ca6f-120">W niektórych sytuacjach może to być niepożądane z różnych przyczyn.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-120">In certain situations this may be undesirable for a variety of reasons.</span></span> <span data-ttu-id="5ca6f-121">Obsługa konfiguracji usługi WCF blokowania wartości konfiguracji, dzięki czemu zagnieżdżone konfiguracji generuje wyjątki, gdy jest uruchamiana usługa zagnieżdżonych przy użyciu przesłonięcia wartości konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-121">WCF service configuration supports the locking of configuration values so that nested configuration generates exceptions when a nested service is run using overridden configuration values.</span></span>  
  
 <span data-ttu-id="5ca6f-122">W tym przykładzie pokazano, jak sterujące rejestrowaniem z znane osobiście informacji osobowych w dziennikach śledzenia i wiadomości, takie jak nazwa użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-122">This sample demonstrates how to control the logging of known Personally Identifiable Information (PII) in trace and message logs, such as username and password.</span></span> <span data-ttu-id="5ca6f-123">Domyślnie rejestrowanie znanych danych jest wyłączona, jednak w niektórych sytuacjach może być ważne dla debugowania aplikacji rejestrowanie danych osobowych.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-123">By default, logging of known PII is disabled however in certain situations logging of PII can be important in debugging an application.</span></span> <span data-ttu-id="5ca6f-124">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5ca6f-124">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="5ca6f-125">Ponadto w tym przykładzie użyto śledzenie i rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-125">In addition, this sample uses tracing and message logging.</span></span> <span data-ttu-id="5ca6f-126">Aby uzyskać więcej informacji, zobacz [śledzenie i rejestrowanie komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-126">For more information, see the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="encrypting-configuration-file-elements"></a><span data-ttu-id="5ca6f-127">Elementy konfiguracji szyfrowania w pliku</span><span class="sxs-lookup"><span data-stu-id="5ca6f-127">Encrypting Configuration File Elements</span></span>  
 <span data-ttu-id="5ca6f-128">Ze względów bezpieczeństwa w udostępnionym środowisku hostingu sieci Web może być pożądane, aby zaszyfrować niektórych elementów konfiguracji, takich jak parametry połączenia bazy danych, które mogą zawierać poufne informacje.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-128">For security purposes in a shared Web-hosting environment, it may be desirable to encrypt certain configuration elements, such as database connection strings that may contain sensitive information.</span></span> <span data-ttu-id="5ca6f-129">Element konfiguracji może być szyfrowana przy użyciu narzędzia aspnet_regiis.exe w folderze na przykład % WINDIR%\Micrsoft.NET\Framework\v4.0.20728 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-129">A configuration element may be encrypted using the aspnet_regiis.exe tool found in the .NET Framework folder For example, %WINDIR%\Micrsoft.NET\Framework\v4.0.20728.</span></span>  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a><span data-ttu-id="5ca6f-130">Aby zaszyfrować wartości w sekcji appSettings w pliku Web.config dla próbki</span><span class="sxs-lookup"><span data-stu-id="5ca6f-130">To encrypt the values in the appSettings section in Web.config for the sample</span></span>  
  
1.  <span data-ttu-id="5ca6f-131">Otwórz wiersz polecenia przy użyciu Start -> Uruchom...</span><span class="sxs-lookup"><span data-stu-id="5ca6f-131">Open a command prompt by using Start->Run….</span></span> <span data-ttu-id="5ca6f-132">Wpisz w `cmd` i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-132">Type in `cmd` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="5ca6f-133">Przejdź do bieżącego katalogu .NET Framework, wydając polecenie: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-133">Navigate to the current .NET Framework directory by issuing the following command: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span></span>  
  
3.  <span data-ttu-id="5ca6f-134">Szyfrowanie ustawienia konfiguracji appSettings w pliku Web.config folderu wydając polecenie: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-134">Encrypt the appSettings configuration settings in the Web.config folder by issuing the following command: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span></span>  
  
 <span data-ttu-id="5ca6f-135">Przeczytaj instrukcje na interfejsie DPAPI w konfiguracji platformy ASP.NET można znaleźć więcej informacji na temat szyfrowania plików konfiguracji ([tworzenie zabezpieczanie aplikacji ASP.NET: uwierzytelnianie, autoryzację i bezpieczna komunikacja](http://go.microsoft.com/fwlink/?LinkId=95137)) i opisy na RSA w konfiguracji platformy ASP.NET ([jak: szyfrowanie sekcji konfiguracyjnych w programie ASP.NET 2.0 przy użyciu RSA](http://go.microsoft.com/fwlink/?LinkId=95138)).</span><span class="sxs-lookup"><span data-stu-id="5ca6f-135">More information about encrypting sections of configuration files can be found by reading a how-to on DPAPI in ASP.NET configuration ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](http://go.microsoft.com/fwlink/?LinkId=95137)) and a how-to on RSA in ASP.NET configuration ([How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](http://go.microsoft.com/fwlink/?LinkId=95138)).</span></span>  
  
## <a name="locking-configuration-file-elements"></a><span data-ttu-id="5ca6f-136">Blokowanie elementów pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5ca6f-136">Locking configuration file elements</span></span>  
 <span data-ttu-id="5ca6f-137">W scenariuszach hostowanych w sieci Web prawdopodobnie zostały usługi podkatalogi usług.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-137">In Web-hosted scenarios, it is possible to have services in subdirectories of services.</span></span> <span data-ttu-id="5ca6f-138">W takich przypadkach wartości konfiguracji dla usługi w podkatalogu mają być obliczane, sprawdzając wartości w pliku Machine.config i kolejno scalanie z żadnych plików Web.config w katalogach nadrzędnych przeniesienie w dół drzewa katalogów i na koniec scalania Plik Web.config w katalogu, który zawiera tę usługę.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-138">In these situations, configuration values for the service in the subdirectory are calculated by examining values in Machine.config and successively merging with any Web.config files in parent directories moving down the directory tree and finally merging the Web.config file in the directory that contains the service.</span></span> <span data-ttu-id="5ca6f-139">Domyślne zachowanie dla większości elementów konfiguracji jest umożliwienie pliki konfiguracyjne w podkatalogach, aby zastąpić wartości w katalogach nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-139">The default behavior for most configuration elements is to allow configuration files in subdirectories to override the values set in parent directories.</span></span> <span data-ttu-id="5ca6f-140">W niektórych sytuacjach może być pożądane, aby zapobiec pliki konfiguracyjne w podkatalogach zastępowanie wartości w konfiguracji katalogu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-140">In certain situations it may be desirable to prevent configuration files in subdirectories from overriding values set in parent directory configuration.</span></span>  
  
 <span data-ttu-id="5ca6f-141">.NET Framework zapewnia sposób blokowania elementy pliku konfiguracji, tak aby konfiguracje, które zastępują elementy konfiguracji zablokowanym zgłaszają wyjątki czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-141">The .NET Framework provides a way to lock configuration file elements so that configurations that override locked configuration elements throw run-time exceptions.</span></span>  
  
 <span data-ttu-id="5ca6f-142">Element konfiguracji można zablokować, określając `lockItem` atrybutu dla węzła w pliku konfiguracji, na przykład w celu blokowania węzła CalculatorServiceBehavior w pliku konfiguracji, tak aby usługi Kalkulator w zagnieżdżone pliki konfiguracji nie zmiany zachowania następującej konfiguracji można użyć.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-142">A configuration element can be locked by specifying the `lockItem` attribute for a node in the configuration file, for example, to lock the CalculatorServiceBehavior node in the configuration file so that calculator services in nested configuration files cannot change the behavior, the following configuration can be used.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>   
          <serviceBehaviors>   
             <behavior name="CalculatorServiceBehavior" lockItem="true">   
               <serviceMetadata httpGetEnabled="True"/>   
               <serviceDebug includeExceptionDetailInFaults="False" />   
             </behavior>   
          </serviceBehaviors>   
       </behaviors>   
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="5ca6f-143">Blokowanie elementów konfiguracji mogą być bardziej szczegółowych.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-143">Locking of configuration elements can be more specific.</span></span> <span data-ttu-id="5ca6f-144">Lista elementów może być określona jako wartość `lockElements` zablokować zestaw elementów w kolekcji elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-144">A list of elements can be specified as the value to the `lockElements` to lock a set of elements within a collection of sub-elements.</span></span> <span data-ttu-id="5ca6f-145">Lista atrybutów, można określić jako wartość `lockAttributes` zablokować zestaw atrybutów w obrębie elementu.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-145">A list of attributes can be specified as the value to the `lockAttributes` to lock a set of attributes within an element.</span></span> <span data-ttu-id="5ca6f-146">Z wyjątkiem określonej listy można zablokować cały zbiór elementów lub atrybutów, określając `lockAllElementsExcept` lub `lockAllAttributesExcept` atrybutów w węźle.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-146">An entire collection of elements or attributes can be locked except for a specified list by specifying the `lockAllElementsExcept` or `lockAllAttributesExcept` attributes on a node.</span></span>  
  
## <a name="pii-logging-configuration"></a><span data-ttu-id="5ca6f-147">Konfiguracja rejestrowania danych osobowych</span><span class="sxs-lookup"><span data-stu-id="5ca6f-147">PII Logging Configuration</span></span>  
 <span data-ttu-id="5ca6f-148">Rejestrowanie danych osobowych jest kontrolowany przez dwa przełączniki: ustawienie komputera znaleziono w pliku Machine.config, umożliwiający administratora komputera zezwolić lub odmówić rejestrowanie danych osobowych i ustawienie aplikacji, który umożliwia administratorowi aplikacji Włącz rejestrowanie danych osobowych dla każdego Źródło w pliku Web.config lub App.config.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-148">Logging of PII is controlled by two switches: a computer-wide setting found in Machine.config that allows a computer administrator to permit or deny logging of PII and an application setting that allows an application administrator to toggle logging of PII for each source in a Web.config or App.config file.</span></span>  
  
 <span data-ttu-id="5ca6f-149">Ustawienia komputera jest kontrolowany przez ustawienie `enableLoggingKnownPii` do `true` lub `false`w `machineSettings` elementu w pliku Machine.config. Na przykład poniżej umożliwia aplikacji włączyć rejestrowanie danych osobowych.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-149">The computer-wide setting is controlled by setting `enableLoggingKnownPii` to `true` or `false`, in the `machineSettings` element in Machine.config. For example, the following allows applications to turn on logging of PII.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="5ca6f-150">Plik Machine.config ma domyślnej lokalizacji: % WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-150">The Machine.config file has a default location: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span></span>  
  
 <span data-ttu-id="5ca6f-151">Jeśli `enableLoggingKnownPii` atrybut nie jest obecny w pliku Machine.config, rejestrowanie danych osobowych jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-151">If the `enableLoggingKnownPii` attribute is not present in Machine.config, logging of PII is not allowed.</span></span>  
  
 <span data-ttu-id="5ca6f-152">Włączanie rejestrowania danych osobowych dla aplikacji odbywa się przez ustawienie `logKnownPii` atrybut elementu źródłowego do `true` lub `false` w pliku Web.config lub App.config.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-152">Enabling logging of PII for an application is done by setting the `logKnownPii` attribute of the source element to `true` or `false` in the Web.config or App.config file.</span></span> <span data-ttu-id="5ca6f-153">Na przykład poniżej umożliwia rejestrowanie danych osobowych dotyczących rejestrowania komunikatów, jak i rejestrowania śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-153">For example, the following enables logging of PII for both message logging and trace logging.</span></span>  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel.MessageLogging" logKnownPii="true">  
                <listeners>   
                ...   
                </listeners>  
            </source>  
            <source name="System.ServiceModel" switchValue="Verbose, ActivityTracing">  
            <listeners>  
        ...   
            </listeners>  
            </source>  
        </sources>  
    </system.diagnostics>  
</configuration>  
```  
  
 <span data-ttu-id="5ca6f-154">Jeśli `logKnownPii` atrybut nie jest określony, a następnie dane osobowe nie jest zalogowany.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-154">If the `logKnownPii` attribute is not specified, then PII is not logged.</span></span>  
  
 <span data-ttu-id="5ca6f-155">Dane osobowe jest rejestrowane tylko, jeśli obie `enableLoggingKnownPii` ustawiono `true`, i `logKnownPii` ma ustawioną wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-155">PII is only logged if both `enableLoggingKnownPii` is set to `true`, and `logKnownPii` is set to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ca6f-156">System.Diagnostics ignoruje wszystkie atrybuty wszystkich źródeł z wyjątkiem pierwszej wymienione w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-156">System.Diagnostics ignores all attributes on all sources except the first one listed in the configuration file.</span></span> <span data-ttu-id="5ca6f-157">Dodawanie `logKnownPii` atrybut do drugiego źródła w pliku konfiguracji nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-157">Adding the `logKnownPii` attribute to the second source in the configuration file has no effect.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5ca6f-158">Aby uruchomić ten przykład obejmuje zmodyfikowania pliku Machine.config. Należy zachować ostrożność podczas modyfikacji pliku Machine.config lub niepoprawne wartości składni spowodować, że wszystkie działania aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-158">To run this sample involves manual modification of Machine.config. Care should be taken when modifying Machine.config as incorrect values or syntax may prevent all .NET Framework applications from running.</span></span>  
  
 <span data-ttu-id="5ca6f-159">Istnieje również możliwość szyfrowania przy użyciu DPAPI i RSA elementy pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-159">It is also possible to encrypt configuration file elements using DPAPI and RSA.</span></span> <span data-ttu-id="5ca6f-160">Aby uzyskać więcej informacji zobacz następujące linki:</span><span class="sxs-lookup"><span data-stu-id="5ca6f-160">For more information, see the following links:</span></span>  
  
-   [<span data-ttu-id="5ca6f-161">Tworzenie aplikacji ASP.NET bezpiecznego: Uwierzytelniania, autoryzacji i zapewnienia bezpiecznej komunikacji</span><span class="sxs-lookup"><span data-stu-id="5ca6f-161">Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication</span></span>](http://go.microsoft.com/fwlink/?LinkId=95137)  
  
-   [<span data-ttu-id="5ca6f-162">Porady: Szyfrowanie sekcji konfiguracyjnych w programie ASP.NET 2.0 przy użyciu RSA</span><span class="sxs-lookup"><span data-stu-id="5ca6f-162">How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA</span></span>](http://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5ca6f-163">Aby skonfigurować, tworzenie i uruchamianie próbki</span><span class="sxs-lookup"><span data-stu-id="5ca6f-163">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="5ca6f-164">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5ca6f-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5ca6f-165">Edytuj Machine.config, aby ustawić `enableLoggingKnownPii` atrybutu `true`, dodawanie węzłów nadrzędnych, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-165">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `true`, adding the parent nodes if necessary.</span></span>  
  
3.  <span data-ttu-id="5ca6f-166">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5ca6f-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="5ca6f-167">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5ca6f-167">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
#### <a name="to-clean-up-the-sample"></a><span data-ttu-id="5ca6f-168">Aby wyczyścić próbki</span><span class="sxs-lookup"><span data-stu-id="5ca6f-168">To clean up the sample</span></span>  
  
1.  <span data-ttu-id="5ca6f-169">Edytuj Machine.config, aby ustawić `enableLoggingKnownPii` atrybutu `false`.</span><span class="sxs-lookup"><span data-stu-id="5ca6f-169">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ca6f-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ca6f-170">See Also</span></span>  
 [<span data-ttu-id="5ca6f-171">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="5ca6f-171">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
