---
title: 'Szybki start: rozwiązywanie problemów z architekturą WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: f85d37fde19767d7fd1e3002776b4816666cc7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183056"
---
# <a name="wcf-troubleshooting-quickstart"></a><span data-ttu-id="4c984-102">Szybki start: rozwiązywanie problemów z architekturą WCF</span><span class="sxs-lookup"><span data-stu-id="4c984-102">WCF Troubleshooting Quickstart</span></span>
<span data-ttu-id="4c984-103">W tym temacie wymieniono szereg znanych problemów, na które napotkali klienci podczas opracowywania klientów i usług WCF.</span><span class="sxs-lookup"><span data-stu-id="4c984-103">This topic lists a number of known issues customers have run into while developing WCF clients and services.</span></span> <span data-ttu-id="4c984-104">Jeśli problem, na który się nadajesz, nie znajduje się na tej liście, zaleca się skonfigurowanie śledzenia dla usługi.</span><span class="sxs-lookup"><span data-stu-id="4c984-104">If the issue you are running into is not in this list, we recommend you configure tracing for your service.</span></span> <span data-ttu-id="4c984-105">Spowoduje to wygenerowanie pliku śledzenia, który można wyświetlić za pomocą przeglądarki plików śledzenia i uzyskać szczegółowe informacje o wyjątkach, które mogą występować w usłudze.</span><span class="sxs-lookup"><span data-stu-id="4c984-105">This will generate a trace file that you can view with the trace file viewer and get detailed information about exceptions that may be occurring within the service.</span></span> <span data-ttu-id="4c984-106">Aby uzyskać więcej informacji na temat konfigurowania śledzenia, zobacz: [Konfigurowanie śledzenia](./diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="4c984-106">For more information on configuring tracing, see: [Configuring Tracing](./diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="4c984-107">Aby uzyskać więcej informacji na temat przeglądarki plików śledzenia, zobacz: [Narzędzie Podgląd śledzenia usług (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4c984-107">For more information on the trace file viewer, see: [Service Trace Viewer Tool (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md).</span></span>  
  
1. [<span data-ttu-id="4c984-108">Po zainstalowaniu systemu Windows 7 i IIS, gdy próbuję przejść do usługi WCF pojawia się następujący komunikat o błędzie: Błąd HTTP 404.3 — Nie znaleziono</span><span class="sxs-lookup"><span data-stu-id="4c984-108">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>](#bkmk_0)  
  
     <span data-ttu-id="4c984-109">Błąd HTTP 404.3 — nie znalezionoNa stronie, której żądasz, nie można obsługiwać ze względu na konfigurację rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="4c984-109">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="4c984-110">Jeśli strona jest skryptem, dodaj program obsługi.</span><span class="sxs-lookup"><span data-stu-id="4c984-110">If the page is a script, add a handler.</span></span> <span data-ttu-id="4c984-111">Jeśli plik powinien zostać pobrany, dodaj mapę MIME.</span><span class="sxs-lookup"><span data-stu-id="4c984-111">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="4c984-112">Szczegółowe informacje o błędzieModule statyczny.</span><span class="sxs-lookup"><span data-stu-id="4c984-112">Detailed Error InformationModule StaticFileModule.</span></span>  
  
2. [<span data-ttu-id="4c984-113">Czasami otrzymuję MessageSecurityException na drugie żądanie, jeśli mój klient jest bezczynny przez jakiś czas po pierwszym żądaniu. Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="4c984-113">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request. What is happening?</span></span>](#BKMK_q1)  
  
3. [<span data-ttu-id="4c984-114">Moja usługa zaczyna odrzucać nowych klientów po tym, jak około 10 klientów wchodzi z nią w interakcję. Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="4c984-114">My service starts to reject new clients after about 10 clients are interacting with it. What is happening?</span></span>](#BKMK_q2)  
  
4. [<span data-ttu-id="4c984-115">Czy mogę załadować konfigurację usługi z innego miejsca niż plik konfiguracyjny aplikacji WCF?</span><span class="sxs-lookup"><span data-stu-id="4c984-115">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>](#BKMK_q3)  
  
5. [<span data-ttu-id="4c984-116">Moja usługa i klient działają świetnie, ale nie mogę ich do pracy, gdy klient jest na innym komputerze? Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="4c984-116">My service and client work great, but I can’t get them to work when the client is on another computer? What’s happening?</span></span>](#BKMK_q4)  
  
6. [<span data-ttu-id="4c984-117">Gdy zgłaszam Exception FaultException\<>, w którym typ jest wyjątkiem, zawsze otrzymuję ogólny typ FaultException na kliencie, a nie typ ogólny. Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="4c984-117">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type. What’s happening?</span></span>](#BKMK_q5)  
  
7. [<span data-ttu-id="4c984-118">Wydaje się, że operacje jednokierunkowe i żądanie odpowiedzi zwracają z grubszą taką samą prędkością, gdy odpowiedź nie zawiera żadnych danych. Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="4c984-118">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data. What's happening?</span></span>](#BKMK_q6)  
  
8. [<span data-ttu-id="4c984-119">Używam certyfikatu X.509 z moją usługą i otrzymuję system.Security.Cryptography.CryptographicException. Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="4c984-119">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException. What’s happening?</span></span>](#BKMK_q77)  
  
9. [<span data-ttu-id="4c984-120">Zmieniłem pierwszy parametr operacji z wielkich na małe; teraz mój klient zgłasza wyjątek. Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="4c984-120">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception. What's happening?</span></span>](#BKMK_q88)  
  
10. [<span data-ttu-id="4c984-121">Używam jednego z moich narzędzi śledzenia i otrzymuję EndpointNotFoundException. Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="4c984-121">I’m using one of my tracing tools and I get an EndpointNotFoundException. What’s happening?</span></span>](#BKMK_q99)  
  
11. [<span data-ttu-id="4c984-122">Podczas wywoływania aplikacji WCF Web HTTP z aplikacji WCF SOAP usługa zwraca następujący błąd: 405 Metoda niedozwolona</span><span class="sxs-lookup"><span data-stu-id="4c984-122">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>](#BK_MK99)  
  
 [<span data-ttu-id="4c984-123">Jaki jest adres podstawowy? Jak odnosi się do adresu punktu końcowego?</span><span class="sxs-lookup"><span data-stu-id="4c984-123">What is the base address? How does it relate to an endpoint address?</span></span>](#BKMK_q10)  
  
<a name="bkmk_0"></a>
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a><span data-ttu-id="4c984-124">Po zainstalowaniu systemu Windows 7 i IIS, gdy próbuję przejść do usługi WCF pojawia się następujący komunikat o błędzie: Błąd HTTP 404.3 — Nie znaleziono</span><span class="sxs-lookup"><span data-stu-id="4c984-124">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>  
 <span data-ttu-id="4c984-125">Pełny komunikat o błędzie to:</span><span class="sxs-lookup"><span data-stu-id="4c984-125">The full error message is:</span></span>  
  
 <span data-ttu-id="4c984-126">Błąd HTTP 404.3 — nie znalezionoNa stronie, której żądasz, nie można obsługiwać ze względu na konfigurację rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="4c984-126">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="4c984-127">Jeśli strona jest skryptem, dodaj program obsługi.</span><span class="sxs-lookup"><span data-stu-id="4c984-127">If the page is a script, add a handler.</span></span> <span data-ttu-id="4c984-128">Jeśli plik powinien zostać pobrany, dodaj mapę MIME.</span><span class="sxs-lookup"><span data-stu-id="4c984-128">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="4c984-129">Szczegółowe informacje o błędzieModule statyczny.</span><span class="sxs-lookup"><span data-stu-id="4c984-129">Detailed Error InformationModule StaticFileModule.</span></span>  
  
 <span data-ttu-id="4c984-130">Ten komunikat o błędzie występuje, gdy "Aktywacja HTTP programu Windows Communication Foundation" nie jest jawnie ustawiona w Panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="4c984-130">This error message occurs when "Windows Communication Foundation HTTP Activation" is not explicitly set in the Control Panel.</span></span> <span data-ttu-id="4c984-131">Aby ustawić tę opcję, przejdź do Panelu sterowania, kliknij pozycję Programy w lewym dolnym rogu okna.</span><span class="sxs-lookup"><span data-stu-id="4c984-131">To set this go to the Control Panel, click Programs in the lower left-hand corner of the window.</span></span> <span data-ttu-id="4c984-132">Kliknij pozycję Włączanie lub wyłączanie funkcji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4c984-132">Click Turn Windows features on or off.</span></span> <span data-ttu-id="4c984-133">Rozwiń węzeł Microsoft .NET Framework 3.5.1 i wybierz pozycję Aktywacja HTTP programu Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="4c984-133">Expand Microsoft .NET Framework 3.5.1 and select Windows Communication Foundation HTTP Activation.</span></span>  
  
<a name="BKMK_q1"></a>
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a><span data-ttu-id="4c984-134">Czasami otrzymuję MessageSecurityException na drugie żądanie, jeśli mój klient jest bezczynny przez jakiś czas po pierwszym żądaniu.</span><span class="sxs-lookup"><span data-stu-id="4c984-134">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request.</span></span> <span data-ttu-id="4c984-135">Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="4c984-135">What is happening?</span></span>  
 <span data-ttu-id="4c984-136">Drugie żądanie może zakończyć się niepowodzeniem głównie z dwóch powodów: (1) sesja została przesuń lub (2) serwer sieci Web, który hostuje usługę jest odtworzony.</span><span class="sxs-lookup"><span data-stu-id="4c984-136">The second request can fail primarily for two reasons: (1) the session has timed out or (2) the Web server that is hosting the service is recycled.</span></span> <span data-ttu-id="4c984-137">W pierwszym przypadku sesja jest prawidłowa do czasu przesunienia się usługi. Gdy usługa nie otrzyma żądania od klienta w okresie określonym w powiązaniu usługi (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), usługa kończy sesję zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="4c984-137">In the first case, the session is valid until the service times out. When the service does not receive a request from the client within the period of time specified in the service's binding (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), the service terminates the security session.</span></span> <span data-ttu-id="4c984-138">Kolejne komunikaty <xref:System.ServiceModel.Security.MessageSecurityException>klienta powodują .</span><span class="sxs-lookup"><span data-stu-id="4c984-138">Subsequent client messages result in the <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="4c984-139">Klient musi ponownie ustanowić bezpieczną sesję z usługą, aby wysyłać przyszłe wiadomości lub używać stanowego tokenu kontekstu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="4c984-139">The client must re-establish a secure session with the service to send future messages or use a stateful security context token.</span></span> <span data-ttu-id="4c984-140">Tokeny kontekstu zabezpieczeń stanowe umożliwiają również bezpieczną sesję, aby przetrwać serwer sieci Web poddawany recyklingowi.</span><span class="sxs-lookup"><span data-stu-id="4c984-140">Stateful security context tokens also allow a secure session to survive a Web server being recycled.</span></span> <span data-ttu-id="4c984-141">Aby uzyskać więcej informacji na temat używania stanowych tokenów bezpiecznego kontekstu w bezpiecznej sesji, zobacz [Jak: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="4c984-141">For more information about using stateful secure context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span> <span data-ttu-id="4c984-142">Alternatywnie można wyłączyć bezpieczne sesje.</span><span class="sxs-lookup"><span data-stu-id="4c984-142">Alternatively, you can disable secure sessions.</span></span> <span data-ttu-id="4c984-143">Korzystając z powiązania [ \<>wsHttpBinding,](../configure-apps/file-schema/wcf/wshttpbinding.md) można ustawić `establishSecurityContext` właściwość `false` tak, aby wyłączyła bezpieczne sesje.</span><span class="sxs-lookup"><span data-stu-id="4c984-143">When you use the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) binding, you can set the `establishSecurityContext` property to `false` to disable secure sessions.</span></span> <span data-ttu-id="4c984-144">Aby wyłączyć bezpieczne sesje dla innych powiązań, należy utworzyć niestandardowe powiązanie.</span><span class="sxs-lookup"><span data-stu-id="4c984-144">To disable secure sessions for other bindings, you must create a custom binding.</span></span> <span data-ttu-id="4c984-145">Aby uzyskać szczegółowe informacje na temat tworzenia niestandardowego powiązania, zobacz [Jak: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="4c984-145">For details about creating a custom binding, see [How to: Create a Custom Binding Using the SecurityBindingElement](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="4c984-146">Przed zastosowaniem dowolnej z tych opcji należy zapoznać się z wymaganiami dotyczącymi zabezpieczeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4c984-146">Before you apply any of these options, you must understand your application's security requirements.</span></span>  
  
<a name="BKMK_q2"></a>
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a><span data-ttu-id="4c984-147">Moja usługa zaczyna odrzucać nowych klientów po tym, jak około 10 klientów wchodzi z nią w interakcję.</span><span class="sxs-lookup"><span data-stu-id="4c984-147">My service starts to reject new clients after about 10 clients are interacting with it.</span></span> <span data-ttu-id="4c984-148">Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="4c984-148">What is happening?</span></span>  
 <span data-ttu-id="4c984-149">Domyślnie usługi mogą mieć tylko 10 równoczesnych sesji.</span><span class="sxs-lookup"><span data-stu-id="4c984-149">By default, services can have only 10 concurrent sessions.</span></span> <span data-ttu-id="4c984-150">W związku z tym jeśli powiązania usługi używać sesji, usługa akceptuje nowe połączenia klienta, dopóki nie osiągnie tego numeru, po czym odrzuca nowe połączenia klienta, aż do zakończenia jednej z bieżących sesji.</span><span class="sxs-lookup"><span data-stu-id="4c984-150">Therefore, if the service bindings use sessions, the service accepts new client connections until it reaches that number, after which it refuses new client connections until one of the current sessions ends.</span></span> <span data-ttu-id="4c984-151">Możesz obsługiwać więcej klientów na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="4c984-151">You can support more clients in a number of ways.</span></span> <span data-ttu-id="4c984-152">Jeśli usługa nie wymaga sesji, nie należy używać powiązania sesyjnego.</span><span class="sxs-lookup"><span data-stu-id="4c984-152">If your service does not require sessions, do not use a sessionful binding.</span></span> <span data-ttu-id="4c984-153">(Aby uzyskać więcej informacji, zobacz [Korzystanie z sesji](using-sessions.md).) Inną opcją jest zwiększenie limitu sesji poprzez <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> zmianę wartości właściwości na liczbę odpowiednią do danego okoliczności.</span><span class="sxs-lookup"><span data-stu-id="4c984-153">(For more information, see [Using Sessions](using-sessions.md).) Another option is to increase the session limit by changing the value of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> property to the number appropriate to your circumstance.</span></span>  
  
<a name="BKMK_q3"></a>
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a><span data-ttu-id="4c984-154">Czy mogę załadować konfigurację usługi z innego miejsca niż plik konfiguracyjny aplikacji WCF?</span><span class="sxs-lookup"><span data-stu-id="4c984-154">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>  
 <span data-ttu-id="4c984-155">Tak, jednak należy utworzyć klasę <xref:System.ServiceModel.ServiceHost> niestandardową, która <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> zastępuje metodę.</span><span class="sxs-lookup"><span data-stu-id="4c984-155">Yes, however, you have to create a custom <xref:System.ServiceModel.ServiceHost> class that overrides the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method.</span></span> <span data-ttu-id="4c984-156">Wewnątrz tej metody można wywołać podstawowej do obciążenia konfiguracji pierwszy (jeśli chcesz załadować standardowe informacje o konfiguracji, jak również), ale można również całkowicie zastąpić system ładowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4c984-156">Inside that method, you can call the base to load configuration first (if you want to load the standard configuration information as well) but you can also entirely replace the configuration loading system.</span></span> <span data-ttu-id="4c984-157">Jeśli chcesz załadować konfigurację z pliku konfiguracyjnego, który różni się od pliku konfiguracji aplikacji, należy przeanalizować plik konfiguracyjny samodzielnie i załadować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="4c984-157">If you want to load configuration from a configuration file that is different from the application configuration file, you must parse the configuration file yourself and load the configuration.</span></span>  
  
 <span data-ttu-id="4c984-158">Poniższy przykład kodu pokazuje, jak <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> zastąpić metodę i bezpośrednio skonfigurować punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="4c984-158">The following code example shows how to override the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method and directly configure an endpoint.</span></span>  
  
```csharp
public class MyServiceHost : ServiceHost  
{  
    public MyServiceHost(Type serviceType, params Uri[] baseAddresses)
      : base(serviceType, baseAddresses)  
    {
        Console.WriteLine("MyServiceHost Constructor");
    }  
  
    protected override void ApplyConfiguration()  
    {  
        string straddress = GetAddress();  
        Uri address = new Uri(straddress);  
        Binding binding = GetBinding();  
        base.AddServiceEndpoint(typeof(IData), binding, address);  
    }  
  
    string GetAddress()  
    {
        return "http://MyMachine:7777/MyEndpointAddress/";
    }  
  
    Binding GetBinding()  
    {  
        WSHttpBinding binding = new WSHttpBinding();  
        binding.Security.Mode = SecurityMode.None;  
        return binding;  
    }  
}  
```  
  
<a name="BKMK_q4"></a>
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a><span data-ttu-id="4c984-159">Moja usługa i klient działają świetnie, ale nie mogę ich do pracy, gdy klient jest na innym komputerze?</span><span class="sxs-lookup"><span data-stu-id="4c984-159">My service and client work great, but I can’t get them to work when the client is on another computer?</span></span> <span data-ttu-id="4c984-160">Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="4c984-160">What’s happening?</span></span>  
 <span data-ttu-id="4c984-161">W zależności od wyjątku może istnieć kilka problemów:</span><span class="sxs-lookup"><span data-stu-id="4c984-161">Depending upon the exception, there may be several issues:</span></span>  
  
- <span data-ttu-id="4c984-162">Może być konieczna zmiana adresów punktu końcowego klienta na nazwę hosta, a nie na "localhost".</span><span class="sxs-lookup"><span data-stu-id="4c984-162">You might need to change the client endpoint addresses to the host name and not "localhost".</span></span>  
  
- <span data-ttu-id="4c984-163">Może być konieczne otwarcie portu do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4c984-163">You might need to open the port to the application.</span></span> <span data-ttu-id="4c984-164">Aby uzyskać szczegółowe informacje, zobacz [Instrukcje zapory](./samples/firewall-instructions.md) z przykładów SDK.</span><span class="sxs-lookup"><span data-stu-id="4c984-164">For details, see [Firewall Instructions](./samples/firewall-instructions.md) from the SDK samples.</span></span>  
  
- <span data-ttu-id="4c984-165">Aby uzyskać inne możliwe problemy, zobacz temat przykładów [Uruchamianie przykładów fundacji komunikacji systemu Windows](./samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4c984-165">For other possible issues, see the samples topic [Running the Windows Communication Foundation Samples](./samples/running-the-samples.md).</span></span>  
  
- <span data-ttu-id="4c984-166">Jeśli klient używa poświadczeń systemu <xref:System.ServiceModel.Security.SecurityNegotiationException>Windows, a wyjątkiem jest , skonfigurować protokół Kerberos w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="4c984-166">If your client is using Windows credentials and the exception is a <xref:System.ServiceModel.Security.SecurityNegotiationException>, configure Kerberos as follows.</span></span>  
  
    1. <span data-ttu-id="4c984-167">Dodaj poświadczenia tożsamości do elementu punktu końcowego w pliku App.config klienta:</span><span class="sxs-lookup"><span data-stu-id="4c984-167">Add the identity credentials to the endpoint element in the client’s App.config file:</span></span>  
  
        ```xml
        <endpoint
          address="http://MyServer:8000/MyService/"
          binding="wsHttpBinding"
          bindingConfiguration="WSHttpBinding_IServiceExample"
          contract="IServiceExample"
          behaviorConfiguration="ClientCredBehavior"
          name="WSHttpBinding_IServiceExample">  
          <identity>  
            <userPrincipalName value="name@corp.contoso.com"/>  
          </identity>  
        </endpoint>  
        ```  
  
    2. <span data-ttu-id="4c984-168">Uruchom usługę hostowania samodzielnie na koncie System lub NetworkService.</span><span class="sxs-lookup"><span data-stu-id="4c984-168">Run the self-hosted service under the System or NetworkService account.</span></span> <span data-ttu-id="4c984-169">To polecenie można uruchomić, aby utworzyć okno polecenia w obszarze konto systemowe:</span><span class="sxs-lookup"><span data-stu-id="4c984-169">You can run this command to create a command window under the System account:</span></span>  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3. <span data-ttu-id="4c984-170">Hostuj usługę w obszarze internetowe usługi informacyjne (IIS), która domyślnie używa konta głównej nazwy usługi (SPN).</span><span class="sxs-lookup"><span data-stu-id="4c984-170">Host the service under Internet Information Services (IIS), which, by default, uses the service principal name (SPN) account.</span></span>  
  
    4. <span data-ttu-id="4c984-171">Zarejestruj nową nazwę SPN w domenie przy użyciu SetSPN.</span><span class="sxs-lookup"><span data-stu-id="4c984-171">Register a new SPN with the domain using SetSPN.</span></span> <span data-ttu-id="4c984-172">Aby to zrobić, musisz być administratorem domeny.</span><span class="sxs-lookup"><span data-stu-id="4c984-172">You need to be a domain administrator in order to do this.</span></span>  
  
 <span data-ttu-id="4c984-173">Aby uzyskać więcej informacji na temat protokołu Kerberos, zobacz [Pojęcia zabezpieczeń używane w WCF](./feature-details/security-concepts-used-in-wcf.md) i:</span><span class="sxs-lookup"><span data-stu-id="4c984-173">For more information about the Kerberos protocol, see [Security Concepts Used in WCF](./feature-details/security-concepts-used-in-wcf.md) and:</span></span>  
  
- [<span data-ttu-id="4c984-174">Debugowanie błędów uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4c984-174">Debugging Windows Authentication Errors</span></span>](./feature-details/debugging-windows-authentication-errors.md)  
  
- <span data-ttu-id="4c984-175">[Rejestrowanie głównych nazw usługi Kerberos przy użyciu protokołu Http.sys](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="4c984-175">[Registering Kerberos Service Principal Names by Using Http.sys](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))</span></span>  
  
- <span data-ttu-id="4c984-176">[Objaśnienie protokołu Kerberos](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v%3dtechnet.10))</span><span class="sxs-lookup"><span data-stu-id="4c984-176">[Kerberos Explained](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v%3dtechnet.10))</span></span>  
  
<a name="BKMK_q5"></a>
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a><span data-ttu-id="4c984-177">Gdy zgłaszam Exception FaultException\<>, w którym typ jest wyjątkiem, zawsze otrzymuję ogólny typ FaultException na kliencie, a nie typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="4c984-177">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type.</span></span> <span data-ttu-id="4c984-178">Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="4c984-178">What’s happening?</span></span>  
 <span data-ttu-id="4c984-179">Zdecydowanie zaleca się utworzenie własnego typu danych błędu niestandardowego i zadeklarowanie tego jako typu szczegółów w umowie z błędami.</span><span class="sxs-lookup"><span data-stu-id="4c984-179">It is highly recommended that you create your own custom error data type and declare that as the detail type in your fault contract.</span></span> <span data-ttu-id="4c984-180">Powodem jest to, że przy użyciu typów wyjątków dostarczonych przez system:</span><span class="sxs-lookup"><span data-stu-id="4c984-180">The reason is that using system-provided exception types:</span></span>  
  
- <span data-ttu-id="4c984-181">Tworzy zależność typu, która usuwa jedną z największych zalet aplikacji zorientowanych na usługi.</span><span class="sxs-lookup"><span data-stu-id="4c984-181">Creates a type dependency that removes one of the biggest strengths of service-oriented applications.</span></span>  
  
- <span data-ttu-id="4c984-182">Nie może zależeć od wyjątków serializacji w standardowy sposób.</span><span class="sxs-lookup"><span data-stu-id="4c984-182">Cannot depend upon exceptions serializing in a standard way.</span></span> <span data-ttu-id="4c984-183">Niektóre — <xref:System.Security.SecurityException>jak — mogą nie być serializable w ogóle.</span><span class="sxs-lookup"><span data-stu-id="4c984-183">Some—like <xref:System.Security.SecurityException>—may not be serializable at all.</span></span>  
  
- <span data-ttu-id="4c984-184">Udostępnia klientom szczegóły implementacji wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="4c984-184">Exposes internal implementation details to clients.</span></span> <span data-ttu-id="4c984-185">Aby uzyskać więcej informacji, zobacz [Określanie i obsługa usterek w umowach i usługach](specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="4c984-185">For more information, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
 <span data-ttu-id="4c984-186">Jeśli debugowanie aplikacji, jednak można serializować informacje o wyjątku i <xref:System.ServiceModel.Description.ServiceDebugBehavior> zwrócić je do klienta przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="4c984-186">If you are debugging an application, however, you can serialize exception information and return it to the client by using the <xref:System.ServiceModel.Description.ServiceDebugBehavior> class.</span></span>  
  
<a name="BKMK_q6"></a>
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a><span data-ttu-id="4c984-187">Wydaje się, że operacje jednokierunkowe i żądanie odpowiedzi zwracają z grubszą taką samą prędkością, gdy odpowiedź nie zawiera żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="4c984-187">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data.</span></span> <span data-ttu-id="4c984-188">Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="4c984-188">What's happening?</span></span>  
 <span data-ttu-id="4c984-189">Określenie, że operacja jest jednym ze sposobów oznacza tylko, że umowa operacji akceptuje komunikat wejściowy i nie zwraca komunikatu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="4c984-189">Specifying that an operation is one way means only that the operation contract accepts an input message and does not return an output message.</span></span> <span data-ttu-id="4c984-190">W WCF wszystkie wywołania klienta zwracają, gdy dane wychodzące zostały zapisane w sieci lub zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="4c984-190">In WCF, all client invocations return when the outbound data has been written to the wire or an exception is thrown.</span></span> <span data-ttu-id="4c984-191">Operacje jednokierunkowe działają w ten sam sposób i mogą zgłosić, jeśli usługa nie może być zlokalizowana lub zablokowana, jeśli usługa nie jest przygotowana do zaakceptowania danych z sieci.</span><span class="sxs-lookup"><span data-stu-id="4c984-191">One-way operations work the same way, and they can throw if the service cannot be located or block if the service is not prepared to accept the data from the network.</span></span> <span data-ttu-id="4c984-192">Zazwyczaj w WCF powoduje to jednokierunkowe wywołania zwrotne do klienta szybciej niż żądanie odpowiedzi; ale każdy warunek, który spowalnia wysyłanie danych wychodzących przez sieć spowalnia operacje jednokierunkowe, a także operacje żądania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="4c984-192">Typically in WCF, this results in one-way calls returning to the client more quickly than request-reply; but any condition that slows the sending of the outbound data over the network slows one-way operations as well as request-reply operations.</span></span> <span data-ttu-id="4c984-193">Aby uzyskać więcej informacji, zobacz [Usługi jednokierunkowe](./feature-details/one-way-services.md) i [uzyskiwanie dostępu do usług przy użyciu klienta WCF](./feature-details/accessing-services-using-a-client.md).</span><span class="sxs-lookup"><span data-stu-id="4c984-193">For more information, see [One-Way Services](./feature-details/one-way-services.md) and [Accessing Services Using a WCF Client](./feature-details/accessing-services-using-a-client.md).</span></span>  
  
<a name="BKMK_q77"></a>
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a><span data-ttu-id="4c984-194">Używam certyfikatu X.509 z moją usługą i otrzymuję system.Security.Cryptography.CryptographicException.</span><span class="sxs-lookup"><span data-stu-id="4c984-194">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException.</span></span> <span data-ttu-id="4c984-195">Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="4c984-195">What’s happening?</span></span>  
 <span data-ttu-id="4c984-196">Dzieje się tak często po zmianie konta użytkownika, w ramach którego działa proces roboczy IIS.</span><span class="sxs-lookup"><span data-stu-id="4c984-196">This commonly occurs after changing the user account under which the IIS worker process runs.</span></span> <span data-ttu-id="4c984-197">Na przykład w systemie Windows XP, jeśli zmienisz domyślne konto użytkownika, które Aspnet_wp.exe działa w obszarze z ASPNET do niestandardowego konta użytkownika, może pojawić się ten błąd.</span><span class="sxs-lookup"><span data-stu-id="4c984-197">For example, in Windows XP, if you change the default user account that the Aspnet_wp.exe runs under from ASPNET to a custom user account, you may see this error.</span></span> <span data-ttu-id="4c984-198">Jeśli używasz klucza prywatnego, proces, który go używa, będzie musiał mieć uprawnienia dostępu do pliku przechowującego ten klucz.</span><span class="sxs-lookup"><span data-stu-id="4c984-198">If using a private key, the process that uses it will need to have permissions to access the file storing that key.</span></span>  
  
 <span data-ttu-id="4c984-199">W takim przypadku należy przyznać uprawnienia dostępu do odczytu do konta procesu dla pliku zawierającego klucz prywatny.</span><span class="sxs-lookup"><span data-stu-id="4c984-199">If this is the case, you must give read access privileges to the process's account for the file containing the private key.</span></span> <span data-ttu-id="4c984-200">Na przykład jeśli proces roboczy usługi IIS jest uruchomiony na koncie Roberta, należy przyznać Robertowi dostęp do odczytu do pliku zawierającego klucz prywatny.</span><span class="sxs-lookup"><span data-stu-id="4c984-200">For example, if the IIS worker process is running under the Bob account, then you will need to give Bob read access to the file containing the private key.</span></span>  
  
 <span data-ttu-id="4c984-201">Aby uzyskać więcej informacji na temat udzielania poprawnego dostępu do pliku zawierającego klucz prywatny dla określonego certyfikatu X.509, zobacz [Jak: Udostępnić certyfikaty X.509 WCF](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="4c984-201">For more information about how to give the correct user account access to the file that contains the private key for a specific X.509 certificate, see [How to: Make X.509 Certificates Accessible to WCF](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span></span>  
  
<a name="BKMK_q88"></a>
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a><span data-ttu-id="4c984-202">Zmieniłem pierwszy parametr operacji z wielkich na małe; teraz mój klient zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="4c984-202">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception.</span></span> <span data-ttu-id="4c984-203">Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="4c984-203">What's happening?</span></span>  
 <span data-ttu-id="4c984-204">Wartości nazw parametrów w podpisie operacji są częścią umowy i są rozróżniane.</span><span class="sxs-lookup"><span data-stu-id="4c984-204">The values of the parameter names in the operation signature are part of the contract and are case-sensitive.</span></span> <span data-ttu-id="4c984-205">Użyj <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> atrybutu, gdy trzeba odróżnić nazwę parametru lokalnego i metadanych, które opisuje operację dla aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="4c984-205">Use the <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> attribute when you need to distinguish between the local parameter name and the metadata that describes the operation for client applications.</span></span>  
  
<a name="BKMK_q99"></a>
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a><span data-ttu-id="4c984-206">Używam jednego z moich narzędzi śledzenia i otrzymuję EndpointNotFoundException.</span><span class="sxs-lookup"><span data-stu-id="4c984-206">I’m using one of my tracing tools and I get an EndpointNotFoundException.</span></span> <span data-ttu-id="4c984-207">Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="4c984-207">What’s happening?</span></span>  
 <span data-ttu-id="4c984-208">Jeśli używasz narzędzia śledzenia, który nie jest mechanizm śledzenia WCF dostarczonych przez system i <xref:System.ServiceModel.EndpointNotFoundException> otrzymasz, który wskazuje, że <xref:System.ServiceModel.Description.ClientViaBehavior> nie było niezgodności filtru adresu, należy użyć klasy, aby skierować wiadomości do narzędzia śledzenia i narzędzie przekierowanie tych wiadomości do adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="4c984-208">If you are using a tracing tool that is not the system-provided WCF tracing mechanism and you receive an <xref:System.ServiceModel.EndpointNotFoundException> that indicates that there was an address filter mismatch, you need to use the <xref:System.ServiceModel.Description.ClientViaBehavior> class to direct the messages to the tracing utility and have the utility redirect those messages to the service address.</span></span> <span data-ttu-id="4c984-209">Klasa <xref:System.ServiceModel.Description.ClientViaBehavior> zmienia nagłówek `Via` adresowania, aby określić następny adres sieciowy oddzielnie `To` od odbiornika końcowego, wskazywany przez nagłówek adresowania.</span><span class="sxs-lookup"><span data-stu-id="4c984-209">The <xref:System.ServiceModel.Description.ClientViaBehavior> class alters the `Via` addressing header to specify the next network address separately from the ultimate receiver, indicated by the `To` addressing header.</span></span> <span data-ttu-id="4c984-210">Podczas wykonywania tej pracy, jednak nie należy zmieniać adres punktu `To` końcowego, który jest używany do ustalenia wartości.</span><span class="sxs-lookup"><span data-stu-id="4c984-210">When doing this, however, do not change the endpoint address, which is used to establish the `To` value.</span></span>  
  
 <span data-ttu-id="4c984-211">Poniższy przykładowy kod przedstawia przykładowy plik konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="4c984-211">The following code example shows an example client configuration file.</span></span>  
  
```xml
<endpoint
  address="http://localhost:8000/MyServer/"  
  binding="wsHttpBinding"  
  bindingConfiguration="WSHttpBinding_IMyContract"  
  behaviorConfiguration="MyClient"
  contract="IMyContract"
  name="WSHttpBinding_IMyContract">  
</endpoint>  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="MyClient">  
      <clientVia viaUri="http://localhost:8001/MyServer/"/>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
<a name="BKMK_q10"></a>
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a><span data-ttu-id="4c984-212">Jaki jest adres podstawowy?</span><span class="sxs-lookup"><span data-stu-id="4c984-212">What is the base address?</span></span> <span data-ttu-id="4c984-213">Jak odnosi się do adresu punktu końcowego?</span><span class="sxs-lookup"><span data-stu-id="4c984-213">How does it relate to an endpoint address?</span></span>  
 <span data-ttu-id="4c984-214">Adres podstawowy jest adresem głównym <xref:System.ServiceModel.ServiceHost> klasy.</span><span class="sxs-lookup"><span data-stu-id="4c984-214">A base address is the root address for a <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="4c984-215">Domyślnie po dodaniu <xref:System.ServiceModel.Description.ServiceMetadataBehavior> klasy do konfiguracji usługi język opisu usług sieci Web (WSDL) dla wszystkich punktów końcowych publikowanych przez hosta są pobierane z adresu podstawowego HTTP, a także dowolny adres względny podany do zachowania metadanych oraz "?wsdl".</span><span class="sxs-lookup"><span data-stu-id="4c984-215">By default, if you add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class into your service configuration, the Web Services Description Language (WSDL) for all endpoints the host publishes are retrieved from the HTTP base address, plus any relative address provided to the metadata behavior, plus "?wsdl".</span></span> <span data-ttu-id="4c984-216">Jeśli znasz ASP.NET i usług IIS, adres podstawowy jest odpowiednikiem katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="4c984-216">If you are familiar with ASP.NET and IIS, the base address is equivalent to the virtual directory.</span></span>  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a><span data-ttu-id="4c984-217">Udostępnianie portu między punktem końcowym usługi a punktem końcowym mex przy użyciu nettcpbinding</span><span class="sxs-lookup"><span data-stu-id="4c984-217">Sharing a port between a service endpoint and a mex endpoint using the NetTcpBinding</span></span>  
 <span data-ttu-id="4c984-218">Jeśli określisz adres podstawowy usługi jako net.tcp://MyServer:8080/MyService i dodasz następujące punkty końcowe:</span><span class="sxs-lookup"><span data-stu-id="4c984-218">If you specify the base address for a service as net.tcp://MyServer:8080/MyService and add the following endpoints:</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 <span data-ttu-id="4c984-219">A jeśli zmodyfikujesz jedno z ustawień NetTcpBinding, jak pokazano w poniższym fragmentie konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="4c984-219">And if you modify one of the NetTcpBinding settings as shown in the following configuration snippet:</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding closeTimeout="00:01:00" openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00" transactionFlow="false" transferMode="Buffered" transactionProtocol="OleTransactions" hostNameComparisonMode="StrongWildcard" listenBacklog="10" maxBufferPoolSize="524288" maxBufferSize="65536" maxConnections="11" maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384"/>  
      <reliableSession ordered="true" inactivityTimeout="00:10:00" enabled="false"/>  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign"/>  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="4c984-220">Zostanie wyświetlony błąd podobny do następującego: Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: Istnieje już odbiornik w punkcie końcowym IP 0.0.0.0:9000 Można obejść ten błąd, określając w pełni kwalifikowany adres URL z innym portem punktu końcowego MEX, jak pokazano w poniższym urywek konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="4c984-220">You will see an error like the following: Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000 You can work around this error by specifying a fully qualified URL with a different port for the MEX endpoint as shown in the following configuration snippet:</span></span>  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a><span data-ttu-id="4c984-221">Podczas wywoływania aplikacji WCF Web HTTP z aplikacji WCF SOAP usługa zwraca następujący błąd: 405 Metoda niedozwolona</span><span class="sxs-lookup"><span data-stu-id="4c984-221">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>  
 <span data-ttu-id="4c984-222">Wywołanie aplikacji <xref:System.ServiceModel.WebHttpBinding> WCF Web HTTP (usługa, <xref:System.ServiceModel.Description.WebHttpBehavior>która używa i ) z usługi ``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.`` WCF może wygenerować następujący <xref:System.ServiceModel.OperationContext> wyjątek: Ten wyjątek występuje, ponieważ WCF zastępuje wychodzące z przychodzącym <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="4c984-222">Calling a WCF Web HTTP application (a service that uses the <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior>) from a WCF service may generate the following exception: ``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.`` This exception occurs because WCF overwrites the outgoing <xref:System.ServiceModel.OperationContext> with the incoming <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="4c984-223">Aby rozwiązać ten problem, należy utworzyć <xref:System.ServiceModel.OperationContextScope> w ramach WCF Web HTTP operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="4c984-223">To solve this problem, create an <xref:System.ServiceModel.OperationContextScope> within the WCF Web HTTP service operation.</span></span> <span data-ttu-id="4c984-224">Przykład:</span><span class="sxs-lookup"><span data-stu-id="4c984-224">For example:</span></span>  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c984-225">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c984-225">See also</span></span>

- [<span data-ttu-id="4c984-226">Debugowanie błędów uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4c984-226">Debugging Windows Authentication Errors</span></span>](./feature-details/debugging-windows-authentication-errors.md)
