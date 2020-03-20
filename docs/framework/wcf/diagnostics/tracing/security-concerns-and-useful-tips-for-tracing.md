---
title: Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 5ced4f3a3a5e83564703db88b28ee2b3c6eeb1a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185721"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a><span data-ttu-id="4dffe-102">Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia</span><span class="sxs-lookup"><span data-stu-id="4dffe-102">Security Concerns and Useful Tips for Tracing</span></span>
<span data-ttu-id="4dffe-103">W tym temacie opisano, jak można chronić poufne informacje przed narażoną, a także przydatne wskazówki podczas korzystania z webhost.</span><span class="sxs-lookup"><span data-stu-id="4dffe-103">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a><span data-ttu-id="4dffe-104">Korzystanie z niestandardowego odbiornika śledzenia za pomocą usługi WebHost</span><span class="sxs-lookup"><span data-stu-id="4dffe-104">Using a Custom Trace Listener with WebHost</span></span>  
 <span data-ttu-id="4dffe-105">Jeśli piszesz własny odbiornik śledzenia, należy pamiętać o możliwości, że ślady mogą zostać utracone w przypadku usługi hostowane w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4dffe-105">If you are writing your own trace listener, you should be aware of the possibility that traces might be lost in the case of a Web-hosted service.</span></span> <span data-ttu-id="4dffe-106">Gdy WebHost odtwarza, zamyka proces na żywo, podczas gdy duplikat przejmuje.</span><span class="sxs-lookup"><span data-stu-id="4dffe-106">When WebHost recycles, it shuts down the live process while a duplicate takes over.</span></span> <span data-ttu-id="4dffe-107">Jednak dwa procesy muszą nadal mieć dostęp do tego samego zasobu przez pewien czas, który jest zależny od typu odbiornika.</span><span class="sxs-lookup"><span data-stu-id="4dffe-107">However, the two processes must still have access to the same resource for some time, which is dependent on the listener type.</span></span> <span data-ttu-id="4dffe-108">W takim przypadku `XmlWriterTraceListener` , tworzy nowy plik śledzenia dla drugiego procesu; podczas śledzenia zdarzeń systemu Windows zarządza wieloma procesami w ramach tej samej sesji i daje dostęp do tego samego pliku.</span><span class="sxs-lookup"><span data-stu-id="4dffe-108">In this case, , `XmlWriterTraceListener` creates a new trace file for the second process; while Windows event tracing manages multiple processes within the same session and gives access to the same file.</span></span> <span data-ttu-id="4dffe-109">Jeśli własny odbiornik nie zapewnia podobnych funkcji, ślady mogą zostać utracone, gdy plik jest zablokowany przez dwa procesy.</span><span class="sxs-lookup"><span data-stu-id="4dffe-109">If your own listener does not provide similar functionalities, traces can be lost when the file is locked up by the two processes.</span></span>  
  
 <span data-ttu-id="4dffe-110">Należy również pamiętać, że niestandardowy odbiornik śledzenia może wysyłać ślady i wiadomości w sieci, na przykład do zdalnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="4dffe-110">You should also be aware that a custom trace listener can send traces and messages on the wire, for example, to a remote database.</span></span> <span data-ttu-id="4dffe-111">Jako wdrażający aplikację należy skonfigurować niestandardowe odbiorniki z odpowiednią kontrolą dostępu.</span><span class="sxs-lookup"><span data-stu-id="4dffe-111">As an application deployer, you should configure custom listeners with appropriate access control.</span></span> <span data-ttu-id="4dffe-112">Należy również zastosować kontrolę zabezpieczeń w odniesieniu do wszelkich informacji osobistych, które mogą być ujawnione w lokalizacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="4dffe-112">You should also apply security control on any personal information that can be exposed at the remote location.</span></span>  
  
## <a name="logging-sensitive-information"></a><span data-ttu-id="4dffe-113">Rejestrowanie poufnych informacji</span><span class="sxs-lookup"><span data-stu-id="4dffe-113">Logging Sensitive Information</span></span>  
 <span data-ttu-id="4dffe-114">Ślady zawierają nagłówki wiadomości, gdy wiadomość jest w zakresie.</span><span class="sxs-lookup"><span data-stu-id="4dffe-114">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="4dffe-115">Gdy śledzenie jest włączone, informacje osobiste w nagłówkach specyficznych dla aplikacji, takich jak ciąg zapytania; informacje o treści, takie jak numer karty kredytowej, mogą stać się widoczne w dziennikach.</span><span class="sxs-lookup"><span data-stu-id="4dffe-115">When tracing is enabled, personal information in application-specific headers, such as, a query string; and body information, such as, a credit card number, can become visible in the logs.</span></span> <span data-ttu-id="4dffe-116">Wdrażający aplikację jest odpowiedzialny za wymuszanie kontroli dostępu w plikach konfiguracji i śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4dffe-116">The application deployer is responsible for enforcing access control on the configuration and trace files.</span></span> <span data-ttu-id="4dffe-117">Jeśli nie chcesz, aby tego rodzaju informacje były widoczne, należy wyłączyć śledzenie lub odfiltrować część danych, jeśli chcesz udostępnić dzienniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4dffe-117">If you do not want this kind of information to be visible, you should disable tracing, or filter out part of the data if you want to share the trace logs.</span></span>  
  
 <span data-ttu-id="4dffe-118">Poniższe wskazówki mogą pomóc w zapobieganiu niezamierzonej instynkowaniu zawartości pliku śledzenia:</span><span class="sxs-lookup"><span data-stu-id="4dffe-118">The following tips can help you to prevent the content of a trace file from being exposed unintentionally:</span></span>  
  
- <span data-ttu-id="4dffe-119">Upewnij się, że pliki dziennika są chronione przez listy kontroli dostępu (ACL) zarówno w webhost i scenariuszy hosta własnego.</span><span class="sxs-lookup"><span data-stu-id="4dffe-119">Ensure that the log files are protected by Access Control Lists (ACL) both in WebHost and self-host scenarios.</span></span>  
  
- <span data-ttu-id="4dffe-120">Wybierz rozszerzenie pliku, które nie może być łatwo obsługiwane za pomocą żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4dffe-120">Choose a file extension that cannot be easily served using a Web request.</span></span> <span data-ttu-id="4dffe-121">Na przykład rozszerzenie pliku xml nie jest bezpiecznym wyborem.</span><span class="sxs-lookup"><span data-stu-id="4dffe-121">For example, the .xml file extension is not a safe choice.</span></span> <span data-ttu-id="4dffe-122">Można zapoznać się z przewodnikiem administracyjnym iis, aby wyświetlić listę rozszerzeń, które mogą być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="4dffe-122">You can check the IIS administration guide to see a list of extensions that can be served.</span></span>  
  
- <span data-ttu-id="4dffe-123">Określ ścieżkę bezwzględną dla lokalizacji pliku dziennika, która powinna znajdować się poza katalogiem publicznym WebHost vroot, aby uniemożliwić dostęp do niej przez stronę zewnętrzną za pomocą przeglądarki sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4dffe-123">Specify an absolute path for the log file location, which should be outside of the WebHost vroot public directory to prevent it from being accessed by an external party using a Web browser.</span></span>  
  
 <span data-ttu-id="4dffe-124">Domyślnie klucze i informacje umożliwiające identyfikację użytkownika, takie jak nazwa użytkownika i hasło, nie są rejestrowane w ślady i rejestrowane wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4dffe-124">By default, keys and personally identifiable information (PII) such as username and password are not logged in traces and logged messages.</span></span> <span data-ttu-id="4dffe-125">Administrator komputera może jednak użyć `enableLoggingKnownPII` atrybutu `machineSettings` w elemencie pliku Machine.config, aby umożliwić aplikacjom uruchomionym na komputerze rejestrowanie znanych informacji umożliwiających identyfikację użytkownika w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4dffe-125">A machine administrator, however, can use the `enableLoggingKnownPII` attribute in the `machineSettings` element of the Machine.config file to permit applications running on the machine to log known personally identifiable information (PII) as follows:</span></span>  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>
```  
  
 <span data-ttu-id="4dffe-126">Wdrażający aplikację może następnie `logKnownPii` użyć atrybutu w pliku App.config lub Web.config, aby włączyć rejestrowanie danych umożliwiających identyfikację użytkowników w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4dffe-126">An application deployer can then use the `logKnownPii` attribute in either the App.config or Web.config file to enable PII logging as follows:</span></span>  
  
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
  
 <span data-ttu-id="4dffe-127">Tylko wtedy, `true` gdy oba ustawienia są włączone rejestrowanie pii.</span><span class="sxs-lookup"><span data-stu-id="4dffe-127">Only when both settings are `true` is PII logging enabled.</span></span> <span data-ttu-id="4dffe-128">Połączenie dwóch przełączników umożliwia elastyczność rejestrowania znanych identyfikatorów umożliwiających identyfikację dla każdej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dffe-128">The combination of two switches allows the flexibility to log known PII for each application.</span></span>  
  
 <span data-ttu-id="4dffe-129">Należy pamiętać, że jeśli określisz dwa lub więcej źródeł niestandardowych w pliku konfiguracyjnym, odczytywane są tylko atrybuty pierwszego źródła.</span><span class="sxs-lookup"><span data-stu-id="4dffe-129">You should be aware that if you specify two or more custom sources in a configuration file, only the attributes of the first source are read.</span></span> <span data-ttu-id="4dffe-130">Pozostałe są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="4dffe-130">The others are ignored.</span></span> <span data-ttu-id="4dffe-131">Oznacza to, że dla następującego pliku App.config, informacje umożliwiające identyfikację nie są rejestrowane dla obu źródeł, mimo że rejestrowanie danych umożliwiających identyfikację jest jawnie włączone dla drugiego źródła.</span><span class="sxs-lookup"><span data-stu-id="4dffe-131">This means that, for the following App.config, file, PII is not logged for both sources even though PII logging is explicitly enabled for the second source.</span></span>  
  
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
  
 <span data-ttu-id="4dffe-132">Jeśli `<machineSettings enableLoggingKnownPii="Boolean"/>` element istnieje poza plikiem Machine.config, system <xref:System.Configuration.ConfigurationErrorsException>zgłasza plik .</span><span class="sxs-lookup"><span data-stu-id="4dffe-132">If the `<machineSettings enableLoggingKnownPii="Boolean"/>` element exists outside the Machine.config file, the system throws a <xref:System.Configuration.ConfigurationErrorsException>.</span></span>  
  
 <span data-ttu-id="4dffe-133">Zmiany są skuteczne tylko wtedy, gdy aplikacja zostanie uruchomiona lub ponownie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="4dffe-133">The changes are effective only when the application starts or restarts.</span></span> <span data-ttu-id="4dffe-134">Zdarzenie jest rejestrowane podczas uruchamiania, gdy `true`oba atrybuty są ustawione na .</span><span class="sxs-lookup"><span data-stu-id="4dffe-134">An event is logged at startup when both attributes are set to `true`.</span></span> <span data-ttu-id="4dffe-135">Zdarzenie jest również rejestrowane, `logKnownPii` jeśli `true` `enableLoggingKnownPii` jest `false`ustawione, ale jest .</span><span class="sxs-lookup"><span data-stu-id="4dffe-135">An event is also logged if `logKnownPii` is set to `true` but `enableLoggingKnownPii` is `false`.</span></span>  
  
 <span data-ttu-id="4dffe-136">Aby uzyskać więcej informacji na temat rejestrowania informacji umożliwiających identyfikację, zobacz przykład [blokady zabezpieczeń pii.](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md)</span><span class="sxs-lookup"><span data-stu-id="4dffe-136">For more information on PII logging, see [PII Security Lockdown](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) sample.</span></span>  
  
 <span data-ttu-id="4dffe-137">Administrator komputera i wdrażający aplikacje powinni zachować szczególną ostrożność podczas korzystania z tych dwóch przełączników.</span><span class="sxs-lookup"><span data-stu-id="4dffe-137">The machine administrator and application deployer should exercise extreme caution when using these two switches.</span></span> <span data-ttu-id="4dffe-138">Jeśli rejestrowanie danych umożliwiających identyfikację jest włączone, rejestrowane są klucze zabezpieczeń i dane umożliwiające identyfikację.</span><span class="sxs-lookup"><span data-stu-id="4dffe-138">If PII logging is enabled, security keys and PII are logged.</span></span> <span data-ttu-id="4dffe-139">Jeśli jest wyłączona, poufne i specyficzne dla aplikacji dane są nadal rejestrowane w nagłówkach wiadomości i treści.</span><span class="sxs-lookup"><span data-stu-id="4dffe-139">If it is disabled, sensitive and application-specific data is still logged in message headers and bodies.</span></span> <span data-ttu-id="4dffe-140">Aby uzyskać dokładniejszą dyskusję na temat prywatności i ochrony informacji umożliwiających identyfikację użytkownika przed narażeniem, zobacz [Prywatność użytkowników](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="4dffe-140">For a more thorough discussion on privacy and protecting PII from being exposed, see [User Privacy](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="4dffe-141">Ponadto adres IP nadawcy wiadomości jest rejestrowany raz na połączenie dla transportów zorientowanych na połączenie, a raz na wiadomość wysłaną w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="4dffe-141">In addition, the IP address of the message sender is logged once per connection for connection-oriented transports, and once per message sent otherwise.</span></span> <span data-ttu-id="4dffe-142">Odbywa się to bez zgody nadawcy.</span><span class="sxs-lookup"><span data-stu-id="4dffe-142">This is done without the consent of the sender.</span></span> <span data-ttu-id="4dffe-143">Jednak to rejestrowanie występuje tylko na poziomach śledzenia informacji lub pełnej, które nie są domyślnymi lub zalecanymi poziomami śledzenia w produkcji, z wyjątkiem debugowania na żywo.</span><span class="sxs-lookup"><span data-stu-id="4dffe-143">However, this logging only occurs at the Information or Verbose tracing levels, which are not the default or recommended tracing levels in production, except for live debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dffe-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4dffe-144">See also</span></span>

- [<span data-ttu-id="4dffe-145">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="4dffe-145">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
