---
title: Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 664785bc97574eff73dc1c2be64f407641df6b00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484572"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a><span data-ttu-id="95d48-102">Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia</span><span class="sxs-lookup"><span data-stu-id="95d48-102">Security Concerns and Useful Tips for Tracing</span></span>
<span data-ttu-id="95d48-103">W tym temacie opisano, jak możesz chronić poufne informacje z widoczne, a także przydatne porady, korzystając z hostem sieci Web.</span><span class="sxs-lookup"><span data-stu-id="95d48-103">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a><span data-ttu-id="95d48-104">Przy użyciu odbiornika śledzenia niestandardowych z hostem sieci Web</span><span class="sxs-lookup"><span data-stu-id="95d48-104">Using a Custom Trace Listener with WebHost</span></span>  
 <span data-ttu-id="95d48-105">Podczas pisania własnych nasłuchującego śledzenia, należy zwrócić uwagę możliwość, że śladów mogą zostać utracone w przypadku usługi hostowanej w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="95d48-105">If you are writing your own trace listener, you should be aware of the possibility that traces might be lost in the case of a Web-hosted service.</span></span> <span data-ttu-id="95d48-106">Podczas odtwarzania WebHost, zamykania procesu na żywo podczas ma duplikat.</span><span class="sxs-lookup"><span data-stu-id="95d48-106">When WebHost recycles, it shuts down the live process while a duplicate takes over.</span></span> <span data-ttu-id="95d48-107">Jednak dwa procesy muszą mieć dostęp do tego samego zasobu przez pewien czas, który jest zależny od typu odbiornika.</span><span class="sxs-lookup"><span data-stu-id="95d48-107">However, the two processes must still have access to the same resource for some time, which is dependent on the listener type.</span></span> <span data-ttu-id="95d48-108">W takim przypadku, `XmlWriterTraceListener` tworzy nowy plik śledzenia dla procesu drugi; podczas śledzenia zdarzeń systemu Windows zarządza wiele procesów w tej samej sesji i zapewnia dostęp do tego samego pliku.</span><span class="sxs-lookup"><span data-stu-id="95d48-108">In this case, , `XmlWriterTraceListener` creates a new trace file for the second process; while Windows event tracing manages multiple processes within the same session and gives access to the same file.</span></span> <span data-ttu-id="95d48-109">Jeśli własne odbiornik nie zapewnia funkcje podobne, dane śledzenia mogą zostać utracone, jeśli plik jest zablokowane przez dwa procesy.</span><span class="sxs-lookup"><span data-stu-id="95d48-109">If your own listener does not provide similar functionalities, traces can be lost when the file is locked up by the two processes.</span></span>  
  
 <span data-ttu-id="95d48-110">Należy również pamiętać, że odbiornik śledzenia niestandardowych można wysyłać ślady i wiadomości w sieci, na przykład ze zdalną bazą danych.</span><span class="sxs-lookup"><span data-stu-id="95d48-110">You should also be aware that a custom trace listener can send traces and messages on the wire, for example, to a remote database.</span></span> <span data-ttu-id="95d48-111">Jako narzędzie wdrażania aplikacji należy skonfigurować niestandardowe odbiorniki z kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="95d48-111">As an application deployer, you should configure custom listeners with appropriate access control.</span></span> <span data-ttu-id="95d48-112">Należy także zastosować kontrolę zabezpieczeń na informacje osobiste, które można uwidocznić w lokalizacjach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="95d48-112">You should also apply security control on any personal information that can be exposed at the remote location.</span></span>  
  
## <a name="logging-sensitive-information"></a><span data-ttu-id="95d48-113">Rejestrowanie informacji poufnych</span><span class="sxs-lookup"><span data-stu-id="95d48-113">Logging Sensitive Information</span></span>  
 <span data-ttu-id="95d48-114">Ślady zawierał nagłówków komunikatów, gdy komunikat jest w zakresie.</span><span class="sxs-lookup"><span data-stu-id="95d48-114">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="95d48-115">Gdy jest włączone śledzenie, informacje osobiste w nagłówkach specyficzne dla aplikacji, takich jak ciąg zapytania. i body informacje, takie jak numer karty kredytowej, może stać się widoczne w dziennikach.</span><span class="sxs-lookup"><span data-stu-id="95d48-115">When tracing is enabled, personal information in application-specific headers, such as, a query string; and body information, such as, a credit card number, can become visible in the logs.</span></span> <span data-ttu-id="95d48-116">Narzędzia wdrażania aplikacji jest odpowiedzialny za wymuszanie kontroli dostępu do plików konfiguracji i śledzenia.</span><span class="sxs-lookup"><span data-stu-id="95d48-116">The application deployer is responsible for enforcing access control on the configuration and trace files.</span></span> <span data-ttu-id="95d48-117">Jeśli nie chcesz, tego rodzaju informacje są widoczne, należy wyłączyć śledzenie lub odfiltrowywania części danych, jeśli chcesz udostępnić dzienniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="95d48-117">If you do not want this kind of information to be visible, you should disable tracing, or filter out part of the data if you want to share the trace logs.</span></span>  
  
 <span data-ttu-id="95d48-118">Poniższe porady może pomóc zapobiec przypadkowym ujawnieniem zawartość pliku śledzenia:</span><span class="sxs-lookup"><span data-stu-id="95d48-118">The following tips can help you to prevent the content of a trace file from being exposed unintentionally:</span></span>  
  
-   <span data-ttu-id="95d48-119">Upewnij się, że dziennika, które pliki są chronione przez kontroli dostępu zawiera listę (ACL) hosta sieci Web i scenariusze hosta samodzielnego.</span><span class="sxs-lookup"><span data-stu-id="95d48-119">Ensure that the log files are protected by Access Control Lists (ACL) both in WebHost and self-host scenarios.</span></span>  
  
-   <span data-ttu-id="95d48-120">Wybierz rozszerzenie pliku, który nie może być łatwo przekazywane za pomocą żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="95d48-120">Choose a file extension that cannot be easily served using a Web request.</span></span> <span data-ttu-id="95d48-121">Na przykład rozszerzenie pliku XML nie jest bezpiecznym wyborem.</span><span class="sxs-lookup"><span data-stu-id="95d48-121">For example, the .xml file extension is not a safe choice.</span></span> <span data-ttu-id="95d48-122">Możesz sprawdzić podręczniku administratora usług IIS umożliwia wyświetlenie listy rozszerzeń, które mogą być przekazywane.</span><span class="sxs-lookup"><span data-stu-id="95d48-122">You can check the IIS administration guide to see a list of extensions that can be served.</span></span>  
  
-   <span data-ttu-id="95d48-123">Określ ścieżkę bezwzględną do lokalizacji pliku dziennika, która powinna być spoza vroot WebHost publicznego katalogu aby zapobiec uzyskiwany przez innych firm za pomocą przeglądarki sieci Web.</span><span class="sxs-lookup"><span data-stu-id="95d48-123">Specify an absolute path for the log file location, which should be outside of the WebHost vroot public directory to prevent it from being accessed by an external party using a Web browser.</span></span>  
  
 <span data-ttu-id="95d48-124">Domyślnie klucze i dane osobowe lub informacje takie jak nazwa użytkownika i hasło nie jest zalogowany śladów i rejestrowane wiadomości.</span><span class="sxs-lookup"><span data-stu-id="95d48-124">By default, keys and personally identifiable information (PII) such as username and password are not logged in traces and logged messages.</span></span> <span data-ttu-id="95d48-125">Administrator maszyny, jednak można użyć `enableLoggingKnownPII` atrybutu w `machineSettings` elementu w pliku Machine.config, aby umożliwić aplikacji uruchomionych na maszynie dziennika znane dane osobowe (dane osobowe) w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="95d48-125">A machine administrator, however, can use the `enableLoggingKnownPII` attribute in the `machineSettings` element of the Machine.config file to permit applications running on the machine to log known personally identifiable information (PII) as follows:</span></span>  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>   
```  
  
 <span data-ttu-id="95d48-126">Następnie można użyć narzędzia wdrażania aplikacji `logKnownPii` atrybutu w pliku App.config lub Web.config, aby włączyć dane osobowe rejestrowania w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="95d48-126">An application deployer can then use the `logKnownPii` attribute in either the App.config or Web.config file to enable PII logging as follows:</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="true">  
        <listeners>  
                 <add name="messages"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="95d48-127">Tylko wtedy, gdy oba ustawienia są `true` jest włączone rejestrowanie danych osobowych.</span><span class="sxs-lookup"><span data-stu-id="95d48-127">Only when both settings are `true` is PII logging enabled.</span></span> <span data-ttu-id="95d48-128">Kombinacja dwa przełączniki zapewnia elastyczność do logowania znane dane osobowe dla każdej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="95d48-128">The combination of two switches allows the flexibility to log known PII for each application.</span></span>  
  
 <span data-ttu-id="95d48-129">Należy zwrócić uwagę, jeśli określisz dwóch lub więcej źródeł niestandardowych w pliku konfiguracji, tylko atrybuty pierwszego źródła są odczytywane.</span><span class="sxs-lookup"><span data-stu-id="95d48-129">You should be aware that if you specify two or more custom sources in a configuration file, only the attributes of the first source are read.</span></span> <span data-ttu-id="95d48-130">Pozostałe są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="95d48-130">The others are ignored.</span></span> <span data-ttu-id="95d48-131">Oznacza to, że dla następującego pliku App.config, plik, dane osobowe nie jest zalogowany dla obu źródeł, mimo że jawnie włączono rejestrowanie danych osobowych drugie źródło.</span><span class="sxs-lookup"><span data-stu-id="95d48-131">This means that, for the following App.config, file, PII is not logged for both sources even though PII logging is explicitly enabled for the second source.</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="false">  
        <listeners>  
           <add name="messages"  
                type="System.Diagnostics.XmlWriterTraceListener"  
                initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
      <source name="System.ServiceModel"   
         logKnownPii="true">  
         <listeners>  
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="95d48-132">Jeśli `<machineSettings enableLoggingKnownPii="Boolean"/>` istnieje element poza pliku Machine.config, system generuje <xref:System.Configuration.ConfigurationErrorsException>.</span><span class="sxs-lookup"><span data-stu-id="95d48-132">If the `<machineSettings enableLoggingKnownPii="Boolean"/>` element exists outside the Machine.config file, the system throws a <xref:System.Configuration.ConfigurationErrorsException>.</span></span>  
  
 <span data-ttu-id="95d48-133">Zmiany zaczynają obowiązywać, tylko wtedy, gdy rozpoczyna się lub ponowne uruchomienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="95d48-133">The changes are effective only when the application starts or restarts.</span></span> <span data-ttu-id="95d48-134">Zdarzenie jest rejestrowane podczas uruchamiania, gdy oba atrybuty są ustawione na `true`.</span><span class="sxs-lookup"><span data-stu-id="95d48-134">An event is logged at startup when both attributes are set to `true`.</span></span> <span data-ttu-id="95d48-135">Jeśli również zostanie zarejestrowane zdarzenie `logKnownPii` ustawiono `true` , ale `enableLoggingKnownPii` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="95d48-135">An event is also logged if `logKnownPii` is set to `true` but `enableLoggingKnownPii` is `false`.</span></span>  
  
 <span data-ttu-id="95d48-136">Aby uzyskać więcej informacji na rejestrowanie danych osobowych, zobacz [blokada zabezpieczeń PII](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="95d48-136">For more information on PII logging, see [PII Security Lockdown](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) sample.</span></span>  
  
 <span data-ttu-id="95d48-137">Administrator maszyny i wdrażania aplikacji należy zachować wyjątkową ostrożność, korzystając z tych dwóch parametrów.</span><span class="sxs-lookup"><span data-stu-id="95d48-137">The machine administrator and application deployer should exercise extreme caution when using these two switches.</span></span> <span data-ttu-id="95d48-138">Jeśli włączono rejestrowanie danych osobowych, są rejestrowane kluczy zabezpieczeń i dane osobowe.</span><span class="sxs-lookup"><span data-stu-id="95d48-138">If PII logging is enabled, security keys and PII are logged.</span></span> <span data-ttu-id="95d48-139">Jeśli jest wyłączona, dane poufne i specyficzne dla aplikacji jest nadal rejestrowane w nagłówkach wiadomości i treści.</span><span class="sxs-lookup"><span data-stu-id="95d48-139">If it is disabled, sensitive and application-specific data is still logged in message headers and bodies.</span></span> <span data-ttu-id="95d48-140">Aby uzyskać dokładniejsze omówienie prywatności i ochrony danych osobowych przed przypadkowym, zobacz [zasady zachowania poufności użytkownika](http://go.microsoft.com/fwlink/?LinkID=94647).</span><span class="sxs-lookup"><span data-stu-id="95d48-140">For a more thorough discussion on privacy and protecting PII from being exposed, see [User Privacy](http://go.microsoft.com/fwlink/?LinkID=94647).</span></span>  
  
 <span data-ttu-id="95d48-141">Ponadto adres nadawcy wiadomości jest rejestrowane raz dla każdego połączenia dla transportu z nawiązaniem połączenia i raz na wiadomością wysłaną w przeciwnym razie wartość.</span><span class="sxs-lookup"><span data-stu-id="95d48-141">In addition, the IP address of the message sender is logged once per connection for connection-oriented transports, and once per message sent otherwise.</span></span> <span data-ttu-id="95d48-142">Można to zrobić bez zgody nadawcy.</span><span class="sxs-lookup"><span data-stu-id="95d48-142">This is done without the consent of the sender.</span></span> <span data-ttu-id="95d48-143">Jednak rejestrowanie występuje tylko w informacji lub pełne poziomy śledzenia, które nie są domyślnie lub zalecane poziomy śledzenia w środowisku produkcyjnym, z wyjątkiem live debugowania.</span><span class="sxs-lookup"><span data-stu-id="95d48-143">However, this logging only occurs at the Information or Verbose tracing levels, which are not the default or recommended tracing levels in production, except for live debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95d48-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95d48-144">See Also</span></span>  
 [<span data-ttu-id="95d48-145">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="95d48-145">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
