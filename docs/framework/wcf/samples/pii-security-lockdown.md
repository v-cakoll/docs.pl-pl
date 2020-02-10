---
title: Blokada zabezpieczeń PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: 56c8acbe53f1e0243f7c679da6ef04f7135bcd3a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094972"
---
# <a name="pii-security-lockdown"></a><span data-ttu-id="12482-102">Blokada zabezpieczeń PII</span><span class="sxs-lookup"><span data-stu-id="12482-102">PII Security Lockdown</span></span>
<span data-ttu-id="12482-103">Ten przykład pokazuje, jak kontrolować kilka funkcji związanych z zabezpieczeniami usługi Windows Communication Foundation (WCF) przez:</span><span class="sxs-lookup"><span data-stu-id="12482-103">This sample demonstrates how to control several security-related features of a Windows Communication Foundation (WCF) service by:</span></span>  
  
- <span data-ttu-id="12482-104">Szyfrowanie poufnych informacji w pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="12482-104">Encrypting sensitive information in a service's configuration file.</span></span>  
  
- <span data-ttu-id="12482-105">Blokowanie elementów w pliku konfiguracji, aby zagnieżdżone podkatalogi usługi nie można zastąpić ustawień.</span><span class="sxs-lookup"><span data-stu-id="12482-105">Locking elements in the configuration file so that nested service subdirectories cannot override settings.</span></span>  
  
- <span data-ttu-id="12482-106">Kontrolowanie rejestrowania danych osobowych (dane osobowe) w dziennikach śledzenia i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="12482-106">Controlling the logging of Personally Identifiable Information (PII) in trace and message logs.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="12482-107">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="12482-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="12482-108">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="12482-108">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="12482-109">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12482-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="12482-110">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="12482-110">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a><span data-ttu-id="12482-111">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="12482-111">Discussion</span></span>  
 <span data-ttu-id="12482-112">Każda z tych funkcji może być używana osobno lub razem w celu kontrolowania aspektów zabezpieczeń usługi.</span><span class="sxs-lookup"><span data-stu-id="12482-112">Each of these features can be used separately or together to control aspects of a service's security.</span></span> <span data-ttu-id="12482-113">Nie jest to ostateczny Przewodnik dotyczący zabezpieczania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="12482-113">This is not a definitive guide to securing a WCF service.</span></span>  
  
 <span data-ttu-id="12482-114">Pliki konfiguracji .NET Framework mogą zawierać informacje poufne, takie jak parametry połączenia do łączenia się z bazami danych.</span><span class="sxs-lookup"><span data-stu-id="12482-114">The .NET Framework configuration files can contain sensitive information such as connection strings to connect to databases.</span></span> <span data-ttu-id="12482-115">W udostępnionych scenariuszach hostowanych w sieci Web może być pożądane zaszyfrowanie tych informacji w pliku konfiguracji usługi, dzięki czemu dane zawarte w pliku konfiguracyjnym są odporne na wyświetlanie.</span><span class="sxs-lookup"><span data-stu-id="12482-115">In shared, Web-hosted scenarios it may be desirable to encrypt this information in the configuration file for a service so that the data contained within the configuration file is resistant to casual viewing.</span></span> <span data-ttu-id="12482-116">.NET Framework 2,0 i nowsze mogą szyfrować fragmenty pliku konfiguracji przy użyciu interfejsu programowania aplikacji ochrony danych (DPAPI) systemu Windows lub dostawcy usług kryptograficznych RSA.</span><span class="sxs-lookup"><span data-stu-id="12482-116">.NET Framework 2.0 and later has the ability to encrypt portions of the configuration file using the Windows Data Protection application programming interface (DPAPI) or the RSA Cryptographic provider.</span></span> <span data-ttu-id="12482-117">Aspnet_regiis. exe przy użyciu interfejsu DPAPI lub RSA może szyfrować wybrane fragmenty pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="12482-117">The aspnet_regiis.exe using the DPAPI or RSA can encrypt select portions of a configuration file.</span></span>  
  
 <span data-ttu-id="12482-118">W scenariuszach hostowanych w sieci Web można korzystać z usług w podkatalogach innych usług.</span><span class="sxs-lookup"><span data-stu-id="12482-118">In Web-hosted scenarios it is possible to have services in subdirectories of other services.</span></span> <span data-ttu-id="12482-119">Domyślna semantyka do określania wartości konfiguracyjnych zezwala na pliki konfiguracyjne w katalogach zagnieżdżonych w celu zastąpienia wartości konfiguracji w katalogu nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="12482-119">The default semantic for determining configuration values allows configuration files in the nested directories to override the configuration values in the parent directory.</span></span> <span data-ttu-id="12482-120">W niektórych sytuacjach może to być niepożądane z różnych powodów.</span><span class="sxs-lookup"><span data-stu-id="12482-120">In certain situations this may be undesirable for a variety of reasons.</span></span> <span data-ttu-id="12482-121">Konfiguracja usługi WCF obsługuje blokowanie wartości konfiguracyjnych, dzięki czemu konfiguracja zagnieżdżona generuje wyjątki, gdy usługa zagnieżdżona jest uruchamiana przy użyciu zastąpionych wartości konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="12482-121">WCF service configuration supports the locking of configuration values so that nested configuration generates exceptions when a nested service is run using overridden configuration values.</span></span>  
  
 <span data-ttu-id="12482-122">Ten przykład pokazuje, jak sterować rejestrowaniem znanych danych osobowych użytkownika w dziennikach śledzenia i komunikatów, takich jak nazwa użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="12482-122">This sample demonstrates how to control the logging of known Personally Identifiable Information (PII) in trace and message logs, such as username and password.</span></span> <span data-ttu-id="12482-123">Domyślnie rejestrowanie znanego elementu dane OSOBowe jest wyłączone, jednak w niektórych sytuacjach rejestrowanie się w charakterze dane OSOBowe może być ważne podczas debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="12482-123">By default, logging of known PII is disabled however in certain situations logging of PII can be important in debugging an application.</span></span> <span data-ttu-id="12482-124">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="12482-124">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="12482-125">Ponadto ten przykład używa śledzenia i rejestrowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="12482-125">In addition, this sample uses tracing and message logging.</span></span> <span data-ttu-id="12482-126">Aby uzyskać więcej informacji, zobacz [śledzenie i rejestrowanie komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) .</span><span class="sxs-lookup"><span data-stu-id="12482-126">For more information, see the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="encrypting-configuration-file-elements"></a><span data-ttu-id="12482-127">Szyfrowanie elementów pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="12482-127">Encrypting Configuration File Elements</span></span>  
 <span data-ttu-id="12482-128">Ze względów bezpieczeństwa w udostępnianym środowisku hostingu sieci Web może być pożądane zaszyfrowanie niektórych elementów konfiguracji, takich jak parametry połączenia bazy danych, które mogą zawierać informacje poufne.</span><span class="sxs-lookup"><span data-stu-id="12482-128">For security purposes in a shared Web-hosting environment, it may be desirable to encrypt certain configuration elements, such as database connection strings that may contain sensitive information.</span></span> <span data-ttu-id="12482-129">Element konfiguracji można zaszyfrować za pomocą narzędzia aspnet_regiis. exe dostępnego w folderze .NET Framework na przykład%WINDIR%\Microsoft.NET\Framework\v4.0.20728.</span><span class="sxs-lookup"><span data-stu-id="12482-129">A configuration element may be encrypted using the aspnet_regiis.exe tool found in the .NET Framework folder For example, %WINDIR%\Microsoft.NET\Framework\v4.0.20728.</span></span>  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a><span data-ttu-id="12482-130">Aby zaszyfrować wartości w sekcji appSettings w pliku Web. config dla przykładu</span><span class="sxs-lookup"><span data-stu-id="12482-130">To encrypt the values in the appSettings section in Web.config for the sample</span></span>  
  
1. <span data-ttu-id="12482-131">Otwórz wiersz polecenia, korzystając z uruchamiania > Uruchom....</span><span class="sxs-lookup"><span data-stu-id="12482-131">Open a command prompt by using Start->Run….</span></span> <span data-ttu-id="12482-132">Wpisz w `cmd` i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="12482-132">Type in `cmd` and click **OK**.</span></span>  
  
2. <span data-ttu-id="12482-133">Przejdź do bieżącego katalogu .NET Framework, wydając następujące polecenie: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span><span class="sxs-lookup"><span data-stu-id="12482-133">Navigate to the current .NET Framework directory by issuing the following command: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span></span>  
  
3. <span data-ttu-id="12482-134">Zaszyfruj ustawienia konfiguracji appSettings w folderze Web. config, wydając następujące polecenie: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span><span class="sxs-lookup"><span data-stu-id="12482-134">Encrypt the appSettings configuration settings in the Web.config folder by issuing the following command: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span></span>  
  
 <span data-ttu-id="12482-135">Więcej informacji na temat szyfrowania sekcji plików konfiguracji można znaleźć, odczytując instrukcje dotyczące interfejsu DPAPI w konfiguracji ASP.NET ([Tworzenie bezpiecznych aplikacji ASP.NET: uwierzytelnianie, autoryzacja i Bezpieczna komunikacja](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))) oraz informacje o kluczu RSA w konfiguracji ASP.NET ([instrukcje: szyfrowanie sekcji konfiguracyjnych w ASP.NET 2,0 przy użyciu RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))).</span><span class="sxs-lookup"><span data-stu-id="12482-135">More information about encrypting sections of configuration files can be found by reading a how-to on DPAPI in ASP.NET configuration ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))) and a how-to on RSA in ASP.NET configuration ([How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))).</span></span>  
  
## <a name="locking-configuration-file-elements"></a><span data-ttu-id="12482-136">Blokowanie elementów pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="12482-136">Locking configuration file elements</span></span>  
 <span data-ttu-id="12482-137">W scenariuszach hostowanych w sieci Web możliwe jest posiadanie usług w podkatalogach usług.</span><span class="sxs-lookup"><span data-stu-id="12482-137">In Web-hosted scenarios, it is possible to have services in subdirectories of services.</span></span> <span data-ttu-id="12482-138">W takich sytuacjach wartości konfiguracyjne usługi w podkatalogu są obliczane przez badanie wartości w pliku Machine. config i ponowne scalanie z dowolnym plikami Web. config w katalogach nadrzędnych, przenosząc drzewo katalogów i wreszcie scalając Plik Web. config w katalogu zawierającym usługę.</span><span class="sxs-lookup"><span data-stu-id="12482-138">In these situations, configuration values for the service in the subdirectory are calculated by examining values in Machine.config and successively merging with any Web.config files in parent directories moving down the directory tree and finally merging the Web.config file in the directory that contains the service.</span></span> <span data-ttu-id="12482-139">Domyślne zachowanie większości elementów konfiguracji polega na umożliwieniu plików konfiguracji w podkatalogach w celu zastąpienia wartości ustawionych w katalogach nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="12482-139">The default behavior for most configuration elements is to allow configuration files in subdirectories to override the values set in parent directories.</span></span> <span data-ttu-id="12482-140">W niektórych sytuacjach może być wskazane, aby zapobiec zastępowaniu plików konfiguracji w podkatalogach przed zastępowaniem wartości ustawionych w konfiguracji katalogu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="12482-140">In certain situations it may be desirable to prevent configuration files in subdirectories from overriding values set in parent directory configuration.</span></span>  
  
 <span data-ttu-id="12482-141">.NET Framework umożliwia zablokowanie elementów pliku konfiguracji, aby konfiguracje, które przesłaniają zablokowane elementy konfiguracji, zgłaszają wyjątki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="12482-141">The .NET Framework provides a way to lock configuration file elements so that configurations that override locked configuration elements throw run-time exceptions.</span></span>  
  
 <span data-ttu-id="12482-142">Element konfiguracji można zablokować, określając atrybut `lockItem` węzła w pliku konfiguracji, na przykład, aby zablokować węzeł CalculatorServiceBehavior w pliku konfiguracji, tak aby usługi kalkulatora w zagnieżdżonych plikach konfiguracji nie mogły zmienić zachowania, można użyć poniższej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="12482-142">A configuration element can be locked by specifying the `lockItem` attribute for a node in the configuration file, for example, to lock the CalculatorServiceBehavior node in the configuration file so that calculator services in nested configuration files cannot change the behavior, the following configuration can be used.</span></span>  
  
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
  
 <span data-ttu-id="12482-143">Blokowanie elementów konfiguracji może być bardziej szczegółowe.</span><span class="sxs-lookup"><span data-stu-id="12482-143">Locking of configuration elements can be more specific.</span></span> <span data-ttu-id="12482-144">Listę elementów można określić jako wartość `lockElements`, aby zablokować zestaw elementów w kolekcji elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="12482-144">A list of elements can be specified as the value to the `lockElements` to lock a set of elements within a collection of sub-elements.</span></span> <span data-ttu-id="12482-145">Listę atrybutów można określić jako wartość `lockAttributes`, aby zablokować zestaw atrybutów w obrębie elementu.</span><span class="sxs-lookup"><span data-stu-id="12482-145">A list of attributes can be specified as the value to the `lockAttributes` to lock a set of attributes within an element.</span></span> <span data-ttu-id="12482-146">Cała kolekcja elementów lub atrybutów można zablokować z wyjątkiem określonej listy przez określenie atrybutów `lockAllElementsExcept` lub `lockAllAttributesExcept` w węźle.</span><span class="sxs-lookup"><span data-stu-id="12482-146">An entire collection of elements or attributes can be locked except for a specified list by specifying the `lockAllElementsExcept` or `lockAllAttributesExcept` attributes on a node.</span></span>  
  
## <a name="pii-logging-configuration"></a><span data-ttu-id="12482-147">Konfiguracja rejestrowania dane OSOBowe</span><span class="sxs-lookup"><span data-stu-id="12482-147">PII Logging Configuration</span></span>  
 <span data-ttu-id="12482-148">Rejestrowanie dane OSOBowe są kontrolowane przez dwa przełączniki: ustawienie na poziomie całego komputera w pliku Machine. config pozwala administratorowi komputera zezwolić na logowanie się lub odmówić rejestrowania dane OSOBowe oraz ustawienia aplikacji, które umożliwiają administratorowi aplikacji przełączanie rejestrowania elementów osobowych dla każdej z nich Źródło w pliku Web. config lub App. config.</span><span class="sxs-lookup"><span data-stu-id="12482-148">Logging of PII is controlled by two switches: a computer-wide setting found in Machine.config that allows a computer administrator to permit or deny logging of PII and an application setting that allows an application administrator to toggle logging of PII for each source in a Web.config or App.config file.</span></span>  
  
 <span data-ttu-id="12482-149">Ustawienie na poziomie całego komputera jest kontrolowane przez ustawienie `enableLoggingKnownPii` `true` lub `false`w elemencie `machineSettings` w pliku Machine. config. Na przykład następujące polecenie umożliwia aplikacjom włączenie rejestrowania danych osobowych.</span><span class="sxs-lookup"><span data-stu-id="12482-149">The computer-wide setting is controlled by setting `enableLoggingKnownPii` to `true` or `false`, in the `machineSettings` element in Machine.config. For example, the following allows applications to turn on logging of PII.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> <span data-ttu-id="12482-150">Plik Machine. config ma domyślną lokalizację:%WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="12482-150">The Machine.config file has a default location: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span></span>  
  
 <span data-ttu-id="12482-151">Jeśli atrybut `enableLoggingKnownPii` nie jest obecny w pliku Machine. config, rejestrowanie dane OSOBowe nie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="12482-151">If the `enableLoggingKnownPii` attribute is not present in Machine.config, logging of PII is not allowed.</span></span>  
  
 <span data-ttu-id="12482-152">Włączanie rejestrowania danych osobowych dla aplikacji odbywa się przez ustawienie atrybutu `logKnownPii` elementu Source na `true` lub `false` w pliku Web. config lub App. config.</span><span class="sxs-lookup"><span data-stu-id="12482-152">Enabling logging of PII for an application is done by setting the `logKnownPii` attribute of the source element to `true` or `false` in the Web.config or App.config file.</span></span> <span data-ttu-id="12482-153">Na przykład następujące umożliwia rejestrowanie danych osobowych zarówno w przypadku rejestrowania komunikatów, jak i rejestrowania śledzenia.</span><span class="sxs-lookup"><span data-stu-id="12482-153">For example, the following enables logging of PII for both message logging and trace logging.</span></span>  
  
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
  
 <span data-ttu-id="12482-154">Jeśli atrybut `logKnownPii` nie zostanie określony, dane OSOBowe nie będą rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="12482-154">If the `logKnownPii` attribute is not specified, then PII is not logged.</span></span>  
  
 <span data-ttu-id="12482-155">Dane OSOBowe są rejestrowane tylko wtedy, gdy oba `enableLoggingKnownPii` są ustawione na `true`, a `logKnownPii` jest ustawiony na `true`.</span><span class="sxs-lookup"><span data-stu-id="12482-155">PII is only logged if both `enableLoggingKnownPii` is set to `true`, and `logKnownPii` is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12482-156">System. Diagnostics ignoruje wszystkie atrybuty we wszystkich źródłach z wyjątkiem pierwszego z nich wymienionych w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="12482-156">System.Diagnostics ignores all attributes on all sources except the first one listed in the configuration file.</span></span> <span data-ttu-id="12482-157">Dodanie `logKnownPii` atrybutu do drugiego źródła w pliku konfiguracji nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="12482-157">Adding the `logKnownPii` attribute to the second source in the configuration file has no effect.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="12482-158">Do uruchomienia tego przykładu zawarto ręczną modyfikację pliku Machine. config. Należy zachować ostrożność podczas modyfikowania pliku Machine. config, ponieważ nieprawidłowe wartości lub Składnia mogą uniemożliwić uruchamianie wszystkich aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="12482-158">To run this sample involves manual modification of Machine.config. Care should be taken when modifying Machine.config as incorrect values or syntax may prevent all .NET Framework applications from running.</span></span>  
  
 <span data-ttu-id="12482-159">Istnieje również możliwość szyfrowania elementów plików konfiguracji przy użyciu funkcji DPAPI i RSA.</span><span class="sxs-lookup"><span data-stu-id="12482-159">It is also possible to encrypt configuration file elements using DPAPI and RSA.</span></span> <span data-ttu-id="12482-160">Aby uzyskać więcej informacji, skorzystaj z następujących linków:</span><span class="sxs-lookup"><span data-stu-id="12482-160">For more information, see the following links:</span></span>  
  
- <span data-ttu-id="12482-161">[Tworzenie bezpiecznych aplikacji ASP.NET: uwierzytelnianie, autoryzacja i Bezpieczna komunikacja](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="12482-161">[Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))</span></span>  
  
- <span data-ttu-id="12482-162">[Instrukcje: szyfrowanie sekcji konfiguracyjnych w ASP.NET 2,0 przy użyciu RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="12482-162">[How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="12482-163">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="12482-163">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="12482-164">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="12482-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="12482-165">Edytuj plik Machine. config, aby ustawić atrybut `enableLoggingKnownPii` na `true`, dodając węzły nadrzędne w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="12482-165">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `true`, adding the parent nodes if necessary.</span></span>  
  
3. <span data-ttu-id="12482-166">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="12482-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="12482-167">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="12482-167">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
#### <a name="to-clean-up-the-sample"></a><span data-ttu-id="12482-168">Aby oczyścić przykład</span><span class="sxs-lookup"><span data-stu-id="12482-168">To clean up the sample</span></span>  
  
1. <span data-ttu-id="12482-169">Edytuj plik Machine. config, aby ustawić atrybut `enableLoggingKnownPii` na `false`.</span><span class="sxs-lookup"><span data-stu-id="12482-169">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12482-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12482-170">See also</span></span>

- <span data-ttu-id="12482-171">[Przykłady monitorowania oprogramowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="12482-171">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
