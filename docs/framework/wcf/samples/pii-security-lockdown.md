---
title: Blokada zabezpieczeń PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: 18095845db094f0911578816e6bacdb7f3776156
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664783"
---
# <a name="pii-security-lockdown"></a><span data-ttu-id="4d6d4-102">Blokada zabezpieczeń PII</span><span class="sxs-lookup"><span data-stu-id="4d6d4-102">PII Security Lockdown</span></span>
<span data-ttu-id="4d6d4-103">W tym przykładzie pokazano, jak kontrolować kilka funkcji związanych z zabezpieczeniami usługi Windows Communication Foundation (WCF) przez:</span><span class="sxs-lookup"><span data-stu-id="4d6d4-103">This sample demonstrates how to control several security-related features of a Windows Communication Foundation (WCF) service by:</span></span>  
  
- <span data-ttu-id="4d6d4-104">Szyfrowanie poufnych informacji w pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-104">Encrypting sensitive information in a service's configuration file.</span></span>  
  
- <span data-ttu-id="4d6d4-105">Blokowanie elementów w pliku konfiguracji, tak, aby zagnieżdżone podkatalogów usługi nie może przesłonić ustawienia.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-105">Locking elements in the configuration file so that nested service subdirectories cannot override settings.</span></span>  
  
- <span data-ttu-id="4d6d4-106">Kontrolowanie logowania z osobiście identyfikowalne dane osobowe w dziennikach śledzenia i wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-106">Controlling the logging of Personally Identifiable Information (PII) in trace and message logs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4d6d4-107">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4d6d4-108">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4d6d4-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4d6d4-109">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4d6d4-110">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a><span data-ttu-id="4d6d4-111">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="4d6d4-111">Discussion</span></span>  
 <span data-ttu-id="4d6d4-112">Każda z tych funkcji może być używane razem lub osobno do sterowania aspektami zabezpieczeń usługi.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-112">Each of these features can be used separately or together to control aspects of a service's security.</span></span> <span data-ttu-id="4d6d4-113">Nie jest wyczerpujący zabezpieczaniem usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-113">This is not a definitive guide to securing a WCF service.</span></span>  
  
 <span data-ttu-id="4d6d4-114">Pliki konfiguracji .NET Framework mogą zawierać poufne informacje, takie jak parametry połączenia z bazami danych.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-114">The .NET Framework configuration files can contain sensitive information such as connection strings to connect to databases.</span></span> <span data-ttu-id="4d6d4-115">W scenariuszach hostowanych w sieci Web, współdzielonych może być pożądane, aby zaszyfrować te informacje w pliku konfiguracji dla usługi tak, aby dane zawarte w pliku konfiguracji jest odporna na zwykłych wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-115">In shared, Web-hosted scenarios it may be desirable to encrypt this information in the configuration file for a service so that the data contained within the configuration file is resistant to casual viewing.</span></span> <span data-ttu-id="4d6d4-116">.NET framework 2.0 i nowszych ma możliwość szyfrowania części pliku konfiguracji, za pomocą aplikacji Windows Data Protection programowania interfejsu (DPAPI) lub dostawcy usług kryptograficznych RSA.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-116">.NET Framework 2.0 and later has the ability to encrypt portions of the configuration file using the Windows Data Protection application programming interface (DPAPI) or the RSA Cryptographic provider.</span></span> <span data-ttu-id="4d6d4-117">Umożliwia ona szyfrowanie aspnet_regiis.exe przy użyciu interfejsu DPAPI lub RSA wybierz części pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-117">The aspnet_regiis.exe using the DPAPI or RSA can encrypt select portions of a configuration file.</span></span>  
  
 <span data-ttu-id="4d6d4-118">W scenariuszach hostowanych w sieci Web jest możliwość usługi w podkatalogach innych usług.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-118">In Web-hosted scenarios it is possible to have services in subdirectories of other services.</span></span> <span data-ttu-id="4d6d4-119">Semantyczne podczas określania wartości konfiguracji domyślnej umożliwia pliki konfiguracyjne w katalogach zagnieżdżone, aby zastąpić wartości konfiguracji w katalogu nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-119">The default semantic for determining configuration values allows configuration files in the nested directories to override the configuration values in the parent directory.</span></span> <span data-ttu-id="4d6d4-120">W niektórych sytuacjach może to być niepożądane różnych powodów.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-120">In certain situations this may be undesirable for a variety of reasons.</span></span> <span data-ttu-id="4d6d4-121">Konfiguracja obsługuje usługi WCF, blokowanie wartości konfiguracji, tak, aby zagnieżdżone konfiguracji generuje wyjątki, gdy zagnieżdżony usługa jest uruchomiona, przy użyciu przesłonić wartości konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-121">WCF service configuration supports the locking of configuration values so that nested configuration generates exceptions when a nested service is run using overridden configuration values.</span></span>  
  
 <span data-ttu-id="4d6d4-122">W tym przykładzie pokazano, jak do sterowania rejestrowaniem z znanych osobiście identyfikowalne dane osobowe w dziennikach śledzenia i wiadomości, takich jak nazwa użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-122">This sample demonstrates how to control the logging of known Personally Identifiable Information (PII) in trace and message logs, such as username and password.</span></span> <span data-ttu-id="4d6d4-123">Domyślnie rejestrowanie znane też danych osobowych jest wyłączone, jednak w niektórych sytuacjach rejestrowania danych osobowych może być istotne w debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-123">By default, logging of known PII is disabled however in certain situations logging of PII can be important in debugging an application.</span></span> <span data-ttu-id="4d6d4-124">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4d6d4-124">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="4d6d4-125">Ponadto w tym przykładzie użyto śledzenie i rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-125">In addition, this sample uses tracing and message logging.</span></span> <span data-ttu-id="4d6d4-126">Aby uzyskać więcej informacji, zobacz [śledzenia i rejestrowania komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-126">For more information, see the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="encrypting-configuration-file-elements"></a><span data-ttu-id="4d6d4-127">Szyfrowanie elementy pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4d6d4-127">Encrypting Configuration File Elements</span></span>  
 <span data-ttu-id="4d6d4-128">Ze względów bezpieczeństwa we współużytkowanym środowisku hostingu w sieci Web może być pożądane, aby zaszyfrować niektórych elementów konfiguracji, takich jak parametry połączenia bazy danych, które mogą zawierać poufne informacje.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-128">For security purposes in a shared Web-hosting environment, it may be desirable to encrypt certain configuration elements, such as database connection strings that may contain sensitive information.</span></span> <span data-ttu-id="4d6d4-129">Element konfiguracji, może być zaszyfrowany za pomocą narzędzia aspnet_regiis.exe znaleziony w folderze .NET Framework, na przykład % WINDIR%\Micrsoft.NET\Framework\v4.0.20728.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-129">A configuration element may be encrypted using the aspnet_regiis.exe tool found in the .NET Framework folder For example, %WINDIR%\Micrsoft.NET\Framework\v4.0.20728.</span></span>  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a><span data-ttu-id="4d6d4-130">Aby zaszyfrować wartości w sekcji appSettings w pliku Web.config dla przykładu</span><span class="sxs-lookup"><span data-stu-id="4d6d4-130">To encrypt the values in the appSettings section in Web.config for the sample</span></span>  
  
1. <span data-ttu-id="4d6d4-131">Otwórz wiersz polecenia przy użyciu Start -> Uruchom...</span><span class="sxs-lookup"><span data-stu-id="4d6d4-131">Open a command prompt by using Start->Run….</span></span> <span data-ttu-id="4d6d4-132">Wpisz `cmd` i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-132">Type in `cmd` and click **OK**.</span></span>  
  
2. <span data-ttu-id="4d6d4-133">Przejdź do bieżącego katalogu .NET Framework, wydając polecenie: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-133">Navigate to the current .NET Framework directory by issuing the following command: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span></span>  
  
3. <span data-ttu-id="4d6d4-134">Szyfrowanie ustawienia konfiguracji appSettings w folderze Web.config przy wykonaniu poniższego polecenia: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-134">Encrypt the appSettings configuration settings in the Web.config folder by issuing the following command: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span></span>  
  
 <span data-ttu-id="4d6d4-135">Więcej informacji o szyfrowaniu sekcje pliki konfiguracji można znaleźć, przeczytaj instrukcje na interfejsie DPAPI w konfiguracji platformy ASP.NET ([tworzenie zabezpieczanie aplikacji ASP.NET: Uwierzytelniania, autoryzacji i bezpieczna komunikacja](https://go.microsoft.com/fwlink/?LinkId=95137)) i porad na RSA w konfiguracji platformy ASP.NET ([How to: Szyfrowanie sekcji konfiguracyjnych w programie ASP.NET 2.0 przy użyciu RSA](https://go.microsoft.com/fwlink/?LinkId=95138)).</span><span class="sxs-lookup"><span data-stu-id="4d6d4-135">More information about encrypting sections of configuration files can be found by reading a how-to on DPAPI in ASP.NET configuration ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](https://go.microsoft.com/fwlink/?LinkId=95137)) and a how-to on RSA in ASP.NET configuration ([How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](https://go.microsoft.com/fwlink/?LinkId=95138)).</span></span>  
  
## <a name="locking-configuration-file-elements"></a><span data-ttu-id="4d6d4-136">Blokujące elementy pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4d6d4-136">Locking configuration file elements</span></span>  
 <span data-ttu-id="4d6d4-137">W scenariuszach hostowanych w sieci Web jest możliwość usługi w podkatalogach usług.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-137">In Web-hosted scenarios, it is possible to have services in subdirectories of services.</span></span> <span data-ttu-id="4d6d4-138">W takich przypadkach wartości konfiguracji dla usługi w podkatalogu są obliczane, sprawdzając wartości w pliku Machine.config i kolejno scalanie z wszelkich plikach Web.config w katalogi nadrzędne przenoszenia w dół drzewa katalogów i na koniec scalania Plik Web.config w katalogu, który zawiera usługi.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-138">In these situations, configuration values for the service in the subdirectory are calculated by examining values in Machine.config and successively merging with any Web.config files in parent directories moving down the directory tree and finally merging the Web.config file in the directory that contains the service.</span></span> <span data-ttu-id="4d6d4-139">Domyślne zachowanie dla większości elementów konfiguracji jest umożliwienie plików konfiguracji w podkatalogach do zastąpienie wartości ustawionych w katalogi nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-139">The default behavior for most configuration elements is to allow configuration files in subdirectories to override the values set in parent directories.</span></span> <span data-ttu-id="4d6d4-140">W niektórych sytuacjach może być pożądane, aby uniemożliwić pliki konfiguracyjne w podkatalogach zastąpienie wartości ustawionych w konfiguracji katalogu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-140">In certain situations it may be desirable to prevent configuration files in subdirectories from overriding values set in parent directory configuration.</span></span>  
  
 <span data-ttu-id="4d6d4-141">.NET Framework umożliwia zablokowanie elementy pliku konfiguracji, tak, aby konfiguracje, które zastępują elementy konfiguracji zablokowane zgłaszają wyjątki czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-141">The .NET Framework provides a way to lock configuration file elements so that configurations that override locked configuration elements throw run-time exceptions.</span></span>  
  
 <span data-ttu-id="4d6d4-142">Element konfiguracji można zablokować, określając `lockItem` atrybutu dla węzła w pliku konfiguracji, na przykład, aby zablokować węzła CalculatorServiceBehavior w pliku konfiguracji usługi Kalkulator w zagnieżdżone pliki konfiguracji Nie można można użyć zmiany zachowania następującą konfigurację.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-142">A configuration element can be locked by specifying the `lockItem` attribute for a node in the configuration file, for example, to lock the CalculatorServiceBehavior node in the configuration file so that calculator services in nested configuration files cannot change the behavior, the following configuration can be used.</span></span>  
  
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
  
 <span data-ttu-id="4d6d4-143">Blokowanie elementów konfiguracji, może być bardziej szczegółowe.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-143">Locking of configuration elements can be more specific.</span></span> <span data-ttu-id="4d6d4-144">Lista elementów, które można określić jako wartość `lockElements` zablokować zestaw elementów w obrębie kolekcji elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-144">A list of elements can be specified as the value to the `lockElements` to lock a set of elements within a collection of sub-elements.</span></span> <span data-ttu-id="4d6d4-145">Lista atrybutów, można określić jako wartość `lockAttributes` zablokować zestaw atrybutów w obrębie elementu.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-145">A list of attributes can be specified as the value to the `lockAttributes` to lock a set of attributes within an element.</span></span> <span data-ttu-id="4d6d4-146">Można zablokować cały zbiór elementów lub atrybutów z wyjątkiem określonej listy, określając `lockAllElementsExcept` lub `lockAllAttributesExcept` atrybutów w węźle.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-146">An entire collection of elements or attributes can be locked except for a specified list by specifying the `lockAllElementsExcept` or `lockAllAttributesExcept` attributes on a node.</span></span>  
  
## <a name="pii-logging-configuration"></a><span data-ttu-id="4d6d4-147">Konfiguracja rejestrowania danych osobowych</span><span class="sxs-lookup"><span data-stu-id="4d6d4-147">PII Logging Configuration</span></span>  
 <span data-ttu-id="4d6d4-148">Rejestrowanie danych osobowych jest kontrolowane przez dwa przełączniki: ustawienie komputera znajduje się w pliku Machine.config, który umożliwia akceptowanie lub odrzucanie rejestrowanie dane osobowe i ustawienia aplikacji, umożliwiający administrator aplikacji włączyć rejestrowanie danych osobowych dla każdego administratora komputera Źródło w pliku Web.config lub App.config.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-148">Logging of PII is controlled by two switches: a computer-wide setting found in Machine.config that allows a computer administrator to permit or deny logging of PII and an application setting that allows an application administrator to toggle logging of PII for each source in a Web.config or App.config file.</span></span>  
  
 <span data-ttu-id="4d6d4-149">Ustawienia komputera jest kontrolowany przez ustawienie `enableLoggingKnownPii` do `true` lub `false`w `machineSettings` elementu w pliku Machine.config. Na przykład poniżej umożliwia aplikacji włączyć rejestrowanie danych osobowych.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-149">The computer-wide setting is controlled by setting `enableLoggingKnownPii` to `true` or `false`, in the `machineSettings` element in Machine.config. For example, the following allows applications to turn on logging of PII.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="4d6d4-150">Plik Machine.config zawiera domyślna lokalizacja: % WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-150">The Machine.config file has a default location: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span></span>  
  
 <span data-ttu-id="4d6d4-151">Jeśli `enableLoggingKnownPii` atrybut nie jest obecny w pliku Machine.config, rejestrowanie danych osobowych jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-151">If the `enableLoggingKnownPii` attribute is not present in Machine.config, logging of PII is not allowed.</span></span>  
  
 <span data-ttu-id="4d6d4-152">Włączanie rejestrowania dla aplikacji odbywa się przez ustawienie właściwości PII `logKnownPii` atrybut elementu źródłowego do `true` lub `false` w pliku Web.config lub App.config.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-152">Enabling logging of PII for an application is done by setting the `logKnownPii` attribute of the source element to `true` or `false` in the Web.config or App.config file.</span></span> <span data-ttu-id="4d6d4-153">Na przykład poniżej umożliwia rejestrowanie danych osobowych dotyczących rejestrowania śledzenia i rejestrowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-153">For example, the following enables logging of PII for both message logging and trace logging.</span></span>  
  
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
  
 <span data-ttu-id="4d6d4-154">Jeśli `logKnownPii` atrybut nie jest określony, a następnie dane osobowe nie jest zalogowany.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-154">If the `logKnownPii` attribute is not specified, then PII is not logged.</span></span>  
  
 <span data-ttu-id="4d6d4-155">Dane osobowe tylko jest rejestrowane, jeśli obie `enableLoggingKnownPii` ustawiono `true`, i `logKnownPii` ustawiono `true`.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-155">PII is only logged if both `enableLoggingKnownPii` is set to `true`, and `logKnownPii` is set to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d6d4-156">System.Diagnostics ignoruje wszystkie atrybuty wszystkich źródeł, z wyjątkiem pierwszej wymienione w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-156">System.Diagnostics ignores all attributes on all sources except the first one listed in the configuration file.</span></span> <span data-ttu-id="4d6d4-157">Dodawanie `logKnownPii` atrybut do drugiego źródła w pliku konfiguracji nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-157">Adding the `logKnownPii` attribute to the second source in the configuration file has no effect.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4d6d4-158">Aby uruchomić ten przykład obejmuje ręcznej modyfikacji pliku Machine.config. Należy uważać podczas modyfikujących Machine.config niepoprawne wartości lub nieprawidłowa składnia może uniemożliwiać uruchomienia wszystkich aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-158">To run this sample involves manual modification of Machine.config. Care should be taken when modifying Machine.config as incorrect values or syntax may prevent all .NET Framework applications from running.</span></span>  
  
 <span data-ttu-id="4d6d4-159">Istnieje również możliwość szyfrowania przy użyciu interfejsu DPAPI i RSA elementy pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-159">It is also possible to encrypt configuration file elements using DPAPI and RSA.</span></span> <span data-ttu-id="4d6d4-160">Aby uzyskać więcej informacji zobacz następujące linki:</span><span class="sxs-lookup"><span data-stu-id="4d6d4-160">For more information, see the following links:</span></span>  
  
- [<span data-ttu-id="4d6d4-161">Tworzenie aplikacji ASP.NET bezpiecznego: Uwierzytelniania, autoryzacji i bezpiecznej komunikacji</span><span class="sxs-lookup"><span data-stu-id="4d6d4-161">Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication</span></span>](https://go.microsoft.com/fwlink/?LinkId=95137)  
  
- [<span data-ttu-id="4d6d4-162">Instrukcje: Szyfrowanie sekcji konfiguracyjnych w programie ASP.NET 2.0 przy użyciu RSA</span><span class="sxs-lookup"><span data-stu-id="4d6d4-162">How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA</span></span>](https://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4d6d4-163">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="4d6d4-163">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="4d6d4-164">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d6d4-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4d6d4-165">Edytowanie pliku Machine.config można ustawić `enableLoggingKnownPii` atrybutu `true`, dodając węzły nadrzędne, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-165">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `true`, adding the parent nodes if necessary.</span></span>  
  
3. <span data-ttu-id="4d6d4-166">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d6d4-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="4d6d4-167">Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d6d4-167">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
#### <a name="to-clean-up-the-sample"></a><span data-ttu-id="4d6d4-168">Aby wyczyścić próbki</span><span class="sxs-lookup"><span data-stu-id="4d6d4-168">To clean up the sample</span></span>  
  
1. <span data-ttu-id="4d6d4-169">Edytowanie pliku Machine.config można ustawić `enableLoggingKnownPii` atrybutu `false`.</span><span class="sxs-lookup"><span data-stu-id="4d6d4-169">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d6d4-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d6d4-170">See also</span></span>

- [<span data-ttu-id="4d6d4-171">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="4d6d4-171">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
