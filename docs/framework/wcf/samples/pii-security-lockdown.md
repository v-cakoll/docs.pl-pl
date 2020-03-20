---
title: Blokada zabezpieczeń PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: ad4f4a024b04a028b815faedded58713e001cab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144269"
---
# <a name="pii-security-lockdown"></a><span data-ttu-id="8e0d2-102">Blokada zabezpieczeń PII</span><span class="sxs-lookup"><span data-stu-id="8e0d2-102">PII Security Lockdown</span></span>
<span data-ttu-id="8e0d2-103">W tym przykładzie pokazano, jak kontrolować kilka funkcji związanych z zabezpieczeniami usługi Windows Communication Foundation (WCF) przez:</span><span class="sxs-lookup"><span data-stu-id="8e0d2-103">This sample demonstrates how to control several security-related features of a Windows Communication Foundation (WCF) service by:</span></span>  
  
- <span data-ttu-id="8e0d2-104">Szyfrowanie poufnych informacji w pliku konfiguracyjnym usługi.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-104">Encrypting sensitive information in a service's configuration file.</span></span>  
  
- <span data-ttu-id="8e0d2-105">Blokowanie elementów w pliku konfiguracyjnym, tak aby zagnieżdżone podkatalogi usługi nie mogły zastąpić ustawień.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-105">Locking elements in the configuration file so that nested service subdirectories cannot override settings.</span></span>  
  
- <span data-ttu-id="8e0d2-106">Kontrolowanie rejestrowania informacji umożliwiających identyfikację użytkownika w dziennikach śledzenia i wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-106">Controlling the logging of Personally Identifiable Information (PII) in trace and message logs.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8e0d2-107">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8e0d2-108">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8e0d2-109">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8e0d2-110">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a><span data-ttu-id="8e0d2-111">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="8e0d2-111">Discussion</span></span>  
 <span data-ttu-id="8e0d2-112">Każda z tych funkcji może być używana oddzielnie lub razem do kontrolowania aspektów zabezpieczeń usługi.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-112">Each of these features can be used separately or together to control aspects of a service's security.</span></span> <span data-ttu-id="8e0d2-113">Nie jest to ostateczny przewodnik do zabezpieczania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-113">This is not a definitive guide to securing a WCF service.</span></span>  
  
 <span data-ttu-id="8e0d2-114">Pliki konfiguracyjne programu .NET Framework mogą zawierać poufne informacje, takie jak parametry połączenia umożliwiające łączenie się z bazami danych.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-114">The .NET Framework configuration files can contain sensitive information such as connection strings to connect to databases.</span></span> <span data-ttu-id="8e0d2-115">W scenariuszach udostępnionych hostowanych w sieci Web może być pożądane zaszyfrowanie tych informacji w pliku konfiguracyjnym dla usługi, tak aby dane zawarte w pliku konfiguracyjnym były odporne na zwykłe wyświetlanie.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-115">In shared, Web-hosted scenarios it may be desirable to encrypt this information in the configuration file for a service so that the data contained within the configuration file is resistant to casual viewing.</span></span> <span data-ttu-id="8e0d2-116">Program .NET Framework 2.0 i nowsze elementy mają możliwość szyfrowania części pliku konfiguracyjnego przy użyciu interfejsu programowania aplikacji ochrony danych systemu Windows (DPAPI) lub dostawcy kryptograficznego RSA.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-116">.NET Framework 2.0 and later has the ability to encrypt portions of the configuration file using the Windows Data Protection application programming interface (DPAPI) or the RSA Cryptographic provider.</span></span> <span data-ttu-id="8e0d2-117">Program aspnet_regiis.exe korzystający z dpapi lub rsa może szyfrować wybrane części pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-117">The aspnet_regiis.exe using the DPAPI or RSA can encrypt select portions of a configuration file.</span></span>  
  
 <span data-ttu-id="8e0d2-118">W scenariuszach hostowanych w sieci Web można mieć usługi w podkatalogach innych usług.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-118">In Web-hosted scenarios it is possible to have services in subdirectories of other services.</span></span> <span data-ttu-id="8e0d2-119">Domyślna semantyczna do określania wartości konfiguracji umożliwia plikom konfiguracyjnym w katalogach zagnieżdżonych zastępowanie wartości konfiguracji w katalogu nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-119">The default semantic for determining configuration values allows configuration files in the nested directories to override the configuration values in the parent directory.</span></span> <span data-ttu-id="8e0d2-120">W niektórych sytuacjach może to być niepożądane z różnych powodów.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-120">In certain situations this may be undesirable for a variety of reasons.</span></span> <span data-ttu-id="8e0d2-121">Konfiguracja usługi WCF obsługuje blokowanie wartości konfiguracji, dzięki czemu zagnieżdżona konfiguracja generuje wyjątki, gdy usługa zagnieżdżona jest uruchamiana przy użyciu zastąpionych wartości konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-121">WCF service configuration supports the locking of configuration values so that nested configuration generates exceptions when a nested service is run using overridden configuration values.</span></span>  
  
 <span data-ttu-id="8e0d2-122">W tym przykładzie pokazano, jak kontrolować rejestrowanie znanych informacji umożliwiających identyfikację użytkownika w dziennikach śledzenia i wiadomości, takich jak nazwa użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-122">This sample demonstrates how to control the logging of known Personally Identifiable Information (PII) in trace and message logs, such as username and password.</span></span> <span data-ttu-id="8e0d2-123">Domyślnie rejestrowanie znanych identyfikatorów umożliwiających identyfikację jest wyłączone, jednak w niektórych sytuacjach rejestrowanie danych umożliwiających identyfikację może być ważne podczas debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-123">By default, logging of known PII is disabled however in certain situations logging of PII can be important in debugging an application.</span></span> <span data-ttu-id="8e0d2-124">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8e0d2-124">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="8e0d2-125">Ponadto w tym przykładzie używa śledzenia i rejestrowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-125">In addition, this sample uses tracing and message logging.</span></span> <span data-ttu-id="8e0d2-126">Aby uzyskać więcej informacji, zobacz [śledzenie i rejestrowanie wiadomości](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-126">For more information, see the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="encrypting-configuration-file-elements"></a><span data-ttu-id="8e0d2-127">Szyfrowanie elementów plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8e0d2-127">Encrypting Configuration File Elements</span></span>  
 <span data-ttu-id="8e0d2-128">Ze względów bezpieczeństwa w środowisku hostingu sieci Web udostępnionego hostingu sieci Web może być pożądane szyfrowanie niektórych elementów konfiguracji, takich jak parametry połączenia bazy danych, które mogą zawierać poufne informacje.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-128">For security purposes in a shared Web-hosting environment, it may be desirable to encrypt certain configuration elements, such as database connection strings that may contain sensitive information.</span></span> <span data-ttu-id="8e0d2-129">Element konfiguracji może być szyfrowany przy użyciu narzędzia aspnet_regiis.exe znajdującego się w folderze .NET Framework Na przykład %WINDIR%\Microsoft.NET\Framework\v4.0.20728.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-129">A configuration element may be encrypted using the aspnet_regiis.exe tool found in the .NET Framework folder For example, %WINDIR%\Microsoft.NET\Framework\v4.0.20728.</span></span>  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a><span data-ttu-id="8e0d2-130">Aby zaszyfrować wartości w sekcji appSettings w witrynie Web.config dla przykładu</span><span class="sxs-lookup"><span data-stu-id="8e0d2-130">To encrypt the values in the appSettings section in Web.config for the sample</span></span>  
  
1. <span data-ttu-id="8e0d2-131">Otwórz wiersz polecenia przy użyciu polecenia Start->Run....</span><span class="sxs-lookup"><span data-stu-id="8e0d2-131">Open a command prompt by using Start->Run….</span></span> <span data-ttu-id="8e0d2-132">Wpisz `cmd` i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-132">Type in `cmd` and click **OK**.</span></span>  
  
2. <span data-ttu-id="8e0d2-133">Przejdź do bieżącego katalogu programu .NET Framework, `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`wydając następujące polecenie: .</span><span class="sxs-lookup"><span data-stu-id="8e0d2-133">Navigate to the current .NET Framework directory by issuing the following command: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span></span>  
  
3. <span data-ttu-id="8e0d2-134">Zaszyfruj ustawienia konfiguracji appSettings w folderze Web.config, wydając następujące polecenie: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-134">Encrypt the appSettings configuration settings in the Web.config folder by issuing the following command: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span></span>  
  
 <span data-ttu-id="8e0d2-135">Więcej informacji na temat szyfrowania sekcji plików konfiguracyjnych można znaleźć, czytając instrukcje dotyczące DPAPI w ASP.NET konfiguracji[(Tworzenie bezpiecznych aplikacji ASP.NET: Uwierzytelnianie, autoryzacja i bezpieczna komunikacja)](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))oraz instrukcje dotyczące rsa w konfiguracji ASP.NET[(How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))).</span><span class="sxs-lookup"><span data-stu-id="8e0d2-135">More information about encrypting sections of configuration files can be found by reading a how-to on DPAPI in ASP.NET configuration ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))) and a how-to on RSA in ASP.NET configuration ([How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))).</span></span>  
  
## <a name="locking-configuration-file-elements"></a><span data-ttu-id="8e0d2-136">Blokowanie elementów pliku konfiguracyjnego</span><span class="sxs-lookup"><span data-stu-id="8e0d2-136">Locking configuration file elements</span></span>  
 <span data-ttu-id="8e0d2-137">W scenariuszach hostowanych w sieci Web jest możliwe, aby mieć usługi w podkatalogach usług.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-137">In Web-hosted scenarios, it is possible to have services in subdirectories of services.</span></span> <span data-ttu-id="8e0d2-138">W takich sytuacjach wartości konfiguracyjne usługi w podkatalogu są obliczane przez badanie wartości w pliku Machine.config i sukcesywne scalanie z dowolnymi plikami Web.config w katalogach nadrzędnych przechodzących w dół drzewa katalogów i wreszcie scalających Web.config w katalogu zawierającym usługę.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-138">In these situations, configuration values for the service in the subdirectory are calculated by examining values in Machine.config and successively merging with any Web.config files in parent directories moving down the directory tree and finally merging the Web.config file in the directory that contains the service.</span></span> <span data-ttu-id="8e0d2-139">Domyślnym zachowaniem większości elementów konfiguracji jest zezwolenie na zastąpienie wartości ustawionych w katalogach nadrzędnych przez pliki konfiguracyjne w podkatalogach.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-139">The default behavior for most configuration elements is to allow configuration files in subdirectories to override the values set in parent directories.</span></span> <span data-ttu-id="8e0d2-140">W niektórych sytuacjach może być pożądane uniemożliwienie plików konfiguracyjnych w podkatalogach zastępowania wartości ustawionych w konfiguracji katalogu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-140">In certain situations it may be desirable to prevent configuration files in subdirectories from overriding values set in parent directory configuration.</span></span>  
  
 <span data-ttu-id="8e0d2-141">.NET Framework umożliwia zablokowanie elementów pliku konfiguracji, dzięki czemu konfiguracje, które zastępują zablokowane elementy konfiguracji, zgłaszają wyjątki czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-141">The .NET Framework provides a way to lock configuration file elements so that configurations that override locked configuration elements throw run-time exceptions.</span></span>  
  
 <span data-ttu-id="8e0d2-142">Element konfiguracji można zablokować, określając `lockItem` atrybut węzła w pliku konfiguracyjnym, na przykład, aby zablokować węzeł CalculatorServiceBehavior w pliku konfiguracyjnym, tak aby usługi kalkulatora w zagnieżdżonych plikach konfiguracyjnych nie mogły zmienić zachowania, można użyć następującej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-142">A configuration element can be locked by specifying the `lockItem` attribute for a node in the configuration file, for example, to lock the CalculatorServiceBehavior node in the configuration file so that calculator services in nested configuration files cannot change the behavior, the following configuration can be used.</span></span>  
  
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
  
 <span data-ttu-id="8e0d2-143">Blokowanie elementów konfiguracyjnych może być bardziej szczegółowe.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-143">Locking of configuration elements can be more specific.</span></span> <span data-ttu-id="8e0d2-144">Listę elementów można określić jako `lockElements` wartość, aby zablokować zestaw elementów w kolekcji podelementów.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-144">A list of elements can be specified as the value to the `lockElements` to lock a set of elements within a collection of sub-elements.</span></span> <span data-ttu-id="8e0d2-145">Listę atrybutów można określić jako `lockAttributes` wartość, aby zablokować zestaw atrybutów w elemencie.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-145">A list of attributes can be specified as the value to the `lockAttributes` to lock a set of attributes within an element.</span></span> <span data-ttu-id="8e0d2-146">Cała kolekcja elementów lub atrybutów może być zablokowana z `lockAllElementsExcept` `lockAllAttributesExcept` wyjątkiem określonej listy, określając atrybuty lub w węźle.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-146">An entire collection of elements or attributes can be locked except for a specified list by specifying the `lockAllElementsExcept` or `lockAllAttributesExcept` attributes on a node.</span></span>  
  
## <a name="pii-logging-configuration"></a><span data-ttu-id="8e0d2-147">Konfiguracja rejestrowania pii</span><span class="sxs-lookup"><span data-stu-id="8e0d2-147">PII Logging Configuration</span></span>  
 <span data-ttu-id="8e0d2-148">Rejestrowanie danych umożliwiających identyfikację użytkownika jest kontrolowane przez dwa przełączniki: ustawienie dla całego komputera w pliku Machine.config, które umożliwia administratorowi komputera zezwalanie lub odmawianie rejestrowania danych umożliwiających identyfikację użytkownika oraz ustawienie aplikacji, które umożliwia administratorowi aplikacji przełączanie rejestrowania danych umożliwiających identyfikację użytkownika dla każdego źródła w pliku Web.config lub App.config.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-148">Logging of PII is controlled by two switches: a computer-wide setting found in Machine.config that allows a computer administrator to permit or deny logging of PII and an application setting that allows an application administrator to toggle logging of PII for each source in a Web.config or App.config file.</span></span>  
  
 <span data-ttu-id="8e0d2-149">Ustawienie dla całego komputera jest `enableLoggingKnownPii` `true` kontrolowane `false`przez `machineSettings` ustawienie lub , w elemencie w Machine.config. Na przykład następujące umożliwia aplikacjom włączyć rejestrowanie identyfikatorów PII.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-149">The computer-wide setting is controlled by setting `enableLoggingKnownPii` to `true` or `false`, in the `machineSettings` element in Machine.config. For example, the following allows applications to turn on logging of PII.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> <span data-ttu-id="8e0d2-150">Plik Machine.config ma domyślną lokalizację: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-150">The Machine.config file has a default location: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span></span>  
  
 <span data-ttu-id="8e0d2-151">Jeśli `enableLoggingKnownPii` atrybut nie jest obecny w Machine.config, rejestrowanie identyfikatorów PII jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-151">If the `enableLoggingKnownPii` attribute is not present in Machine.config, logging of PII is not allowed.</span></span>  
  
 <span data-ttu-id="8e0d2-152">Włączenie rejestrowania danych umożliwiających identyfikację użytkownika `logKnownPii` dla aplikacji odbywa się `true` `false` przez ustawienie atrybutu elementu źródłowego na lub w pliku Web.config lub App.config.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-152">Enabling logging of PII for an application is done by setting the `logKnownPii` attribute of the source element to `true` or `false` in the Web.config or App.config file.</span></span> <span data-ttu-id="8e0d2-153">Na przykład następujące umożliwia rejestrowanie identyfikatorów umożliwiających identyfikację podczas rejestrowania wiadomości i rejestrowania śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-153">For example, the following enables logging of PII for both message logging and trace logging.</span></span>  
  
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
  
 <span data-ttu-id="8e0d2-154">Jeśli `logKnownPii` atrybut nie jest określony, informacje umożliwiające identyfikację nie są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-154">If the `logKnownPii` attribute is not specified, then PII is not logged.</span></span>  
  
 <span data-ttu-id="8e0d2-155">Dane umożliwiające identyfikację `enableLoggingKnownPii` jest rejestrowane `true`tylko `logKnownPii` wtedy, `true`gdy oba są ustawione na , i jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="8e0d2-155">PII is only logged if both `enableLoggingKnownPii` is set to `true`, and `logKnownPii` is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e0d2-156">System.Diagnostics ignoruje wszystkie atrybuty we wszystkich źródłach z wyjątkiem pierwszego wymienionego w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-156">System.Diagnostics ignores all attributes on all sources except the first one listed in the configuration file.</span></span> <span data-ttu-id="8e0d2-157">Dodanie `logKnownPii` atrybutu do drugiego źródła w pliku konfiguracyjnym nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-157">Adding the `logKnownPii` attribute to the second source in the configuration file has no effect.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8e0d2-158">Aby uruchomić ten przykład obejmuje ręczną modyfikację Machine.config. Należy zwrócić uwagę podczas modyfikowania Machine.config jako niepoprawne wartości lub składni może uniemożliwić wszystkie aplikacje .NET Framework z systemem.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-158">To run this sample involves manual modification of Machine.config. Care should be taken when modifying Machine.config as incorrect values or syntax may prevent all .NET Framework applications from running.</span></span>  
  
 <span data-ttu-id="8e0d2-159">Możliwe jest również szyfrowanie elementów pliku konfiguracji przy użyciu DPAPI i RSA.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-159">It is also possible to encrypt configuration file elements using DPAPI and RSA.</span></span> <span data-ttu-id="8e0d2-160">Aby uzyskać więcej informacji, skorzystaj z następujących linków:</span><span class="sxs-lookup"><span data-stu-id="8e0d2-160">For more information, see the following links:</span></span>  
  
- <span data-ttu-id="8e0d2-161">[Tworzenie bezpiecznych aplikacji ASP.NET: uwierzytelnianie, autoryzacja i bezpieczna komunikacja](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="8e0d2-161">[Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))</span></span>  
  
- <span data-ttu-id="8e0d2-162">[Jak: Szyfrowanie sekcji konfiguracji w ASP.NET 2.0 Przy użyciu rsa](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="8e0d2-162">[How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8e0d2-163">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="8e0d2-163">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="8e0d2-164">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8e0d2-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8e0d2-165">Edytuj plik Machine.config, `enableLoggingKnownPii` aby `true`ustawić atrybut , dodając węzły nadrzędne, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="8e0d2-165">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `true`, adding the parent nodes if necessary.</span></span>  
  
3. <span data-ttu-id="8e0d2-166">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8e0d2-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="8e0d2-167">Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8e0d2-167">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
#### <a name="to-clean-up-the-sample"></a><span data-ttu-id="8e0d2-168">Aby wyczyścić próbkę</span><span class="sxs-lookup"><span data-stu-id="8e0d2-168">To clean up the sample</span></span>  
  
1. <span data-ttu-id="8e0d2-169">Edytuj plik Machine.config, `enableLoggingKnownPii` aby `false`ustawić atrybut na .</span><span class="sxs-lookup"><span data-stu-id="8e0d2-169">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e0d2-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e0d2-170">See also</span></span>

- <span data-ttu-id="8e0d2-171">[Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8e0d2-171">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
