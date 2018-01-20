---
title: "Szybki start: rozwiązywanie problemów z architekturą WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d0bcd7d08a698a2a839094204dcc5f7105ef8f6b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="wcf-troubleshooting-quickstart"></a><span data-ttu-id="f5530-102">Szybki start: rozwiązywanie problemów z architekturą WCF</span><span class="sxs-lookup"><span data-stu-id="f5530-102">WCF Troubleshooting Quickstart</span></span>
<span data-ttu-id="f5530-103">W tym temacie zamieszczono listę znanych problemów, które klienci mają uruchamiać do podczas opracowywania WCF klientów i usług.</span><span class="sxs-lookup"><span data-stu-id="f5530-103">This topic lists a number of known issues customers have run into while developing WCF clients and services.</span></span> <span data-ttu-id="f5530-104">Jeśli problem, którego używasz do nie jest na liście, zaleca się Konfiguruj śledzenie dla usługi.</span><span class="sxs-lookup"><span data-stu-id="f5530-104">If the issue you are running into is not in this list, we recommend you configure tracing for your service.</span></span> <span data-ttu-id="f5530-105">Spowoduje to wygenerowanie pliku śledzenia można wyświetlić podgląd pliku śledzenia i uzyskać szczegółowe informacje dotyczące wyjątków, który może być przeprowadzana w ramach usługi.</span><span class="sxs-lookup"><span data-stu-id="f5530-105">This will generate a trace file that you can view with the trace file viewer and get detailed information about exceptions that may be occurring within the service.</span></span> <span data-ttu-id="f5530-106">Aby uzyskać więcej informacji na temat konfigurowania śledzenia, zobacz: [Konfigurowanie śledzenia](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="f5530-106">For more information on configuring tracing, see: [Configuring Tracing](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="f5530-107">Aby uzyskać więcej informacji na przeglądarka plików śledzenia, zobacz: [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f5530-107">For more information on the trace file viewer, see: [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span>  
  
1.  [<span data-ttu-id="f5530-108">Po zainstalowaniu systemu Windows 7 i IIS, gdy próbuję przejdź do usługi WCF pojawia się następujący komunikat o błędzie: HTTP Błąd 404.3 — nie znaleziono</span><span class="sxs-lookup"><span data-stu-id="f5530-108">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#bkmk_0)  
  
     <span data-ttu-id="f5530-109">Błąd HTTP 404.3 — nie żądanej strony FoundThe nie może zostać wyświetlona z powodu konfiguracji rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="f5530-109">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="f5530-110">Jeśli strona jest skryptem, Dodaj program obsługi.</span><span class="sxs-lookup"><span data-stu-id="f5530-110">If the page is a script, add a handler.</span></span> <span data-ttu-id="f5530-111">Jeśli plik powinien zostać pobrany, Dodaj mapowanie MIME.</span><span class="sxs-lookup"><span data-stu-id="f5530-111">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="f5530-112">Szczegółowe informacje o błędzie InformationModule StaticFileModule.</span><span class="sxs-lookup"><span data-stu-id="f5530-112">Detailed Error InformationModule StaticFileModule.</span></span>  
  
2.  [<span data-ttu-id="f5530-113">Czasami pojawia się messagesecurityexception — na drugie żądanie Jeśli mój klient bezczynności przez pewien czas po wykonaniu pierwszego żądania. Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="f5530-113">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request. What is happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q1)  
  
3.  [<span data-ttu-id="f5530-114">Moja usługa jest uruchamiana do odrzucania nowych klientów po około 10 klientów są interakcję z nią. Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="f5530-114">My service starts to reject new clients after about 10 clients are interacting with it. What is happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q2)  
  
4.  [<span data-ttu-id="f5530-115">Czy można załadować Moje konfiguracji usługi, w innym miejscu niż pliku konfiguracji aplikacji WCF?</span><span class="sxs-lookup"><span data-stu-id="f5530-115">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q3)  
  
5.  [<span data-ttu-id="f5530-116">Moje usługi i doskonałym pracy klienta, ale nie można pobrać im pracę, gdy klient znajduje się na innym komputerze? Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="f5530-116">My service and client work great, but I can’t get them to work when the client is on another computer? What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q4)  
  
6.  [<span data-ttu-id="f5530-117">Gdy I zgłoszenie wyjątku FaultException\<wyjątku > Typ w przypadku wyjątku, wyświetlany jest zawsze ogólne typu wyjątku FaultException na kliencie, a nie typu ogólnego. Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="f5530-117">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type. What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q5)  
  
7.  [<span data-ttu-id="f5530-118">Wydaje się, jak jednokierunkowe i operacji żądanie odpowiedź zwracanie w przybliżeniu szybkości odpowiedzi nie zawiera żadnych danych. Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="f5530-118">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data. What's happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q6)  
  
8.  [<span data-ttu-id="f5530-119">Używam certyfikat X.509 z mojej usługi i uzyskać System.Security.Cryptography.CryptographicException. Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="f5530-119">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException. What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q77)  
  
9. [<span data-ttu-id="f5530-120">Pierwszy parametr operację po zmianie wielkie na małe litery; teraz moje klienta zgłasza wyjątek. Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="f5530-120">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception. What's happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q88)  
  
10. [<span data-ttu-id="f5530-121">Używam Moje śledzenia narzędzia i uzyskać endpointnotfoundexception —. Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="f5530-121">I’m using one of my tracing tools and I get an EndpointNotFoundException. What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q99)  
  
11. [<span data-ttu-id="f5530-122">Podczas wywoływania aplikacji protokołu HTTP sieci Web WCF z aplikacji WCF SOAP usługi zwraca następujący błąd: niedozwolone 405 — metoda</span><span class="sxs-lookup"><span data-stu-id="f5530-122">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BK_MK99)  
  
 [<span data-ttu-id="f5530-123">Co to jest adres podstawowy? Jaki związek między adres punktu końcowego?</span><span class="sxs-lookup"><span data-stu-id="f5530-123">What is the base address? How does it relate to an endpoint address?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a><span data-ttu-id="f5530-124">Po zainstalowaniu systemu Windows 7 i IIS, gdy próbuję przejdź do usługi WCF pojawia się następujący komunikat o błędzie: HTTP Błąd 404.3 — nie znaleziono</span><span class="sxs-lookup"><span data-stu-id="f5530-124">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>  
 <span data-ttu-id="f5530-125">Jest pełny komunikat o błędzie:</span><span class="sxs-lookup"><span data-stu-id="f5530-125">The full error message is:</span></span>  
  
 <span data-ttu-id="f5530-126">Błąd HTTP 404.3 — nie żądanej strony FoundThe nie może zostać wyświetlona z powodu konfiguracji rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="f5530-126">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="f5530-127">Jeśli strona jest skryptem, Dodaj program obsługi.</span><span class="sxs-lookup"><span data-stu-id="f5530-127">If the page is a script, add a handler.</span></span> <span data-ttu-id="f5530-128">Jeśli plik powinien zostać pobrany, Dodaj mapowanie MIME.</span><span class="sxs-lookup"><span data-stu-id="f5530-128">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="f5530-129">Szczegółowe informacje o błędzie InformationModule StaticFileModule.</span><span class="sxs-lookup"><span data-stu-id="f5530-129">Detailed Error InformationModule StaticFileModule.</span></span>  
  
 <span data-ttu-id="f5530-130">Ten błąd występuje, gdy "Windows Communication Foundation Aktywacja HTTP" nie jest jawnie ustawiona w Panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="f5530-130">This error message occurs when "Windows Communication Foundation HTTP Activation" is not explicitly set in the Control Panel.</span></span> <span data-ttu-id="f5530-131">Aby ustawić przejdź do panelu sterowania, kliknij polecenie programy w dolnym lewym dolnym rogu okna.</span><span class="sxs-lookup"><span data-stu-id="f5530-131">To set this go to the Control Panel, click Programs in the lower left hand corner of the window.</span></span> <span data-ttu-id="f5530-132">Kliknij przycisk Włącz funkcje systemu Windows lub wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="f5530-132">Click Turn Windows features on or off.</span></span> <span data-ttu-id="f5530-133">Rozwiń węzeł systemu Microsoft .NET Framework 3.5.1, a następnie wybierz Aktywacja HTTP programu Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="f5530-133">Expand Microsoft .NET Framework 3.5.1 and select Windows Communication Foundation HTTP Activation.</span></span>  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a><span data-ttu-id="f5530-134">Czasami pojawia się messagesecurityexception — na drugie żądanie Jeśli mój klient bezczynności przez pewien czas po wykonaniu pierwszego żądania.</span><span class="sxs-lookup"><span data-stu-id="f5530-134">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request.</span></span> <span data-ttu-id="f5530-135">Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="f5530-135">What is happening?</span></span>  
 <span data-ttu-id="f5530-136">Drugie żądanie może zakończyć się niepowodzeniem głównie z dwóch przyczyn: Upłynął limit czasu sesji (1 lub (2 serwera sieci Web, który jest hostem usługi zostanie odtworzony.</span><span class="sxs-lookup"><span data-stu-id="f5530-136">The second request can fail primarily for two reasons: (1) the session has timed out or (2) the Web server that is hosting the service is recycled.</span></span> <span data-ttu-id="f5530-137">W pierwszym przypadku sesji jest prawidłowa, dopóki nie upłynie limit czasu usługi. Jeśli usługa nie otrzyma żądanie od klienta w określonym przedziale czasu określony w powiązaniu usługi (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), usługa kończy sesji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f5530-137">In the first case, the session is valid until the service times out. When the service does not receive a request from the client within the period of time specified in the service's binding (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), the service terminates the security session.</span></span> <span data-ttu-id="f5530-138">Powoduje klientów kolejnych komunikatów <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="f5530-138">Subsequent client messages result in the <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="f5530-139">Klient musi ponownie ustanowić bezpiecznej sesji z usługą, aby wysyłać przyszłych lub użyj token kontekstu zabezpieczeń stanowych.</span><span class="sxs-lookup"><span data-stu-id="f5530-139">The client must re-establish a secure session with the service to send future messages or use a stateful security context token.</span></span> <span data-ttu-id="f5530-140">Tokenów kontekstów zabezpieczeń stanową również umożliwić bezpiecznej sesji na serwerze sieci Web odtwarzane przetrwanie.</span><span class="sxs-lookup"><span data-stu-id="f5530-140">Stateful security context tokens also allow a secure session to survive a Web server being recycled.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="f5530-141">w ramach bezpiecznej sesji przy użyciu tokenów kontekstów bezpiecznego stanowe, zobacz [porady: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="f5530-141"> using stateful secure context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span> <span data-ttu-id="f5530-142">Alternatywnie możesz wyłączyć bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="f5530-142">Alternatively, you can disable secure sessions.</span></span> <span data-ttu-id="f5530-143">Jeśli używasz [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) powiązanie, można ustawić `establishSecurityContext` właściwości `false` wyłączyć bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="f5530-143">When you use the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) binding, you can set the `establishSecurityContext` property to `false` to disable secure sessions.</span></span> <span data-ttu-id="f5530-144">Aby wyłączyć bezpiecznej sesji dla pozostałych powiązaniach, należy utworzyć niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f5530-144">To disable secure sessions for other bindings, you must create a custom binding.</span></span> <span data-ttu-id="f5530-145">Aby uzyskać więcej informacji o tworzeniu niestandardowego powiązania, zobacz [porady: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="f5530-145">For details about creating a custom binding, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="f5530-146">Przed zastosowaniem dowolnej z tych opcji, należy zrozumieć wymagania dotyczące zabezpieczeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f5530-146">Before you apply any of these options, you must understand your application's security requirements.</span></span>  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a><span data-ttu-id="f5530-147">Moja usługa jest uruchamiana do odrzucania nowych klientów po około 10 klientów są interakcję z nią.</span><span class="sxs-lookup"><span data-stu-id="f5530-147">My service starts to reject new clients after about 10 clients are interacting with it.</span></span> <span data-ttu-id="f5530-148">Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="f5530-148">What is happening?</span></span>  
 <span data-ttu-id="f5530-149">Domyślnie usługi może mieć tylko 10 równoczesnych sesji.</span><span class="sxs-lookup"><span data-stu-id="f5530-149">By default, services can have only 10 concurrent sessions.</span></span> <span data-ttu-id="f5530-150">W związku z tym powiązania usługi użycie sesji usługi akceptować nowe połączenia klientów, dopóki nie osiągnie ten numer, po upływie którego odrzuca nowe połączenia klientów do jednego z końców bieżących sesji.</span><span class="sxs-lookup"><span data-stu-id="f5530-150">Therefore, if the service bindings use sessions, the service accepts new client connections until it reaches that number, after which it refuses new client connections until one of the current sessions ends.</span></span> <span data-ttu-id="f5530-151">Większej liczby klientów może obsługiwać wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="f5530-151">You can support more clients in a number of ways.</span></span> <span data-ttu-id="f5530-152">Jeśli usługa nie wymaga sesji, nie należy używać powiązania sesyjnych.</span><span class="sxs-lookup"><span data-stu-id="f5530-152">If your service does not require sessions, do not use a sessionful binding.</span></span> <span data-ttu-id="f5530-153">([!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Przy użyciu sesji](../../../docs/framework/wcf/using-sessions.md).) Można zwiększyć, zmieniając wartość limitu czasu sesji <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> właściwości do liczby całkowitej odpowiednią dla Twojego okoliczności.</span><span class="sxs-lookup"><span data-stu-id="f5530-153">([!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Using Sessions](../../../docs/framework/wcf/using-sessions.md).) Another option is to increase the session limit by changing the value of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> property to the number appropriate to your circumstance.</span></span>  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a><span data-ttu-id="f5530-154">Czy można załadować Moje konfiguracji usługi, w innym miejscu niż pliku konfiguracji aplikacji WCF?</span><span class="sxs-lookup"><span data-stu-id="f5530-154">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>  
 <span data-ttu-id="f5530-155">Tak, jednak należy utworzyć niestandardowego <xref:System.ServiceModel.ServiceHost> klasy, która zastępuje <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f5530-155">Yes, however, you have to create a custom <xref:System.ServiceModel.ServiceHost> class that overrides the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method.</span></span> <span data-ttu-id="f5530-156">Wewnątrz tej metody należy wywołać base najpierw załadować konfiguracji (Jeśli chcesz załadować standardowe informacje o konfiguracji również), ale można również całkowicie zastąpić konfiguracji ładowania systemu.</span><span class="sxs-lookup"><span data-stu-id="f5530-156">Inside that method, you can call the base to load configuration first (if you want to load the standard configuration information as well) but you can also entirely replace the configuration loading system.</span></span> <span data-ttu-id="f5530-157">Należy pamiętać, że jeśli chcesz załadować konfiguracji z pliku konfiguracji, który różni się od pliku konfiguracji aplikacji, należy przeanalizować pliku konfiguracji użytkownika i załadować konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f5530-157">Note that if you want to load configuration from a configuration file that is different from the application configuration file, you must parse the configuration file yourself and load the configuration.</span></span>  
  
 <span data-ttu-id="f5530-158">Poniższy przykładowy kod przedstawia sposób przesłonięcia <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> — metoda i bezpośrednio Skonfiguruj punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="f5530-158">The following code example shows how to override the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method and directly configure an endpoint.</span></span>  
  
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
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a><span data-ttu-id="f5530-159">Moje usługi i doskonałym pracy klienta, ale nie można pobrać im pracę, gdy klient znajduje się na innym komputerze?</span><span class="sxs-lookup"><span data-stu-id="f5530-159">My service and client work great, but I can’t get them to work when the client is on another computer?</span></span> <span data-ttu-id="f5530-160">Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="f5530-160">What’s happening?</span></span>  
 <span data-ttu-id="f5530-161">W zależności od wyjątek, może istnieć kilka problemów:</span><span class="sxs-lookup"><span data-stu-id="f5530-161">Depending upon the exception, there may be several issues:</span></span>  
  
-   <span data-ttu-id="f5530-162">Może być konieczna zmiana adresy punktów końcowych klienta na nazwę hosta, a nie "localhost".</span><span class="sxs-lookup"><span data-stu-id="f5530-162">You might need to change the client endpoint addresses to the host name and not "localhost".</span></span>  
  
-   <span data-ttu-id="f5530-163">Może być konieczne otwarcie portu używanego do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f5530-163">You might need to open the port to the application.</span></span> <span data-ttu-id="f5530-164">Aby uzyskać więcej informacji, zobacz [instrukcje dotyczące zapory](../../../docs/framework/wcf/samples/firewall-instructions.md) z próbek zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="f5530-164">For details, see [Firewall Instructions](../../../docs/framework/wcf/samples/firewall-instructions.md) from the SDK samples.</span></span>  
  
-   <span data-ttu-id="f5530-165">W przypadku innych możliwych problemów, zobacz temat przykłady [uruchamiania przykładów w grupie roboczej przez maszyny](http://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113).</span><span class="sxs-lookup"><span data-stu-id="f5530-165">For other possible issues, see the samples topic [Running the Samples in a Workgroup and Across Machines](http://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113).</span></span>  
  
-   <span data-ttu-id="f5530-166">Jeśli klient korzysta z poświadczeń systemu Windows i jest wyjątek <xref:System.ServiceModel.Security.SecurityNegotiationException>, skonfiguruj protokołu Kerberos w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="f5530-166">If your client is using Windows credentials and the exception is a <xref:System.ServiceModel.Security.SecurityNegotiationException>, configure Kerberos as follows.</span></span>  
  
    1.  <span data-ttu-id="f5530-167">Dodaj poświadczenia tożsamości elementu punktu końcowego w pliku App.config klienta:</span><span class="sxs-lookup"><span data-stu-id="f5530-167">Add the identity credentials to the endpoint element in the client’s App.config file:</span></span>  
  
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
  
    2.  <span data-ttu-id="f5530-168">Uruchom usługę siebie na koncie systemu lub NetworkService.</span><span class="sxs-lookup"><span data-stu-id="f5530-168">Run the self-hosted service under the System or NetworkService account.</span></span> <span data-ttu-id="f5530-169">Możesz uruchomić to polecenie, aby utworzyć okno polecenia na koncie systemu:</span><span class="sxs-lookup"><span data-stu-id="f5530-169">You can run this command to create a command window under the System account:</span></span>  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3.  <span data-ttu-id="f5530-170">Host usługi w obszarze Internet Information Services (IIS), która domyślnie używa głównej nazwy (usługi SPN) konta usługi.</span><span class="sxs-lookup"><span data-stu-id="f5530-170">Host the service under Internet Information Services (IIS), which, by default, uses the service principal name (SPN) account.</span></span>  
  
    4.  <span data-ttu-id="f5530-171">Zarejestruj nowy SPN z domeny za pomocą narzędzia SetSPN.</span><span class="sxs-lookup"><span data-stu-id="f5530-171">Register a new SPN with the domain using SetSPN.</span></span> <span data-ttu-id="f5530-172">Należy pamiętać, że musisz być administratorem domeny w tym celu.</span><span class="sxs-lookup"><span data-stu-id="f5530-172">Note that you will need to be a domain administrator in order to do this.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="f5530-173">Protokół Kerberos, zobacz [zabezpieczeń pojęcia używane w programie WCF](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md) oraz:</span><span class="sxs-lookup"><span data-stu-id="f5530-173"> the Kerberos protocol, see [Security Concepts Used in WCF](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md) and:</span></span>  
  
-   [<span data-ttu-id="f5530-174">Debugowanie błędów uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f5530-174">Debugging Windows Authentication Errors</span></span>](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
  
-   [<span data-ttu-id="f5530-175">Zarejestrowanie nazwy głównej usługi Kerberos za pomocą pliku Http.sys</span><span class="sxs-lookup"><span data-stu-id="f5530-175">Registering Kerberos Service Principal Names by Using Http.sys</span></span>](http://go.microsoft.com/fwlink/?LinkId=86943)  
  
-   [<span data-ttu-id="f5530-176">Kerberos Explained</span><span class="sxs-lookup"><span data-stu-id="f5530-176">Kerberos Explained</span></span>](http://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a><span data-ttu-id="f5530-177">Gdy I zgłoszenie wyjątku FaultException\<wyjątku > Typ w przypadku wyjątku, wyświetlany jest zawsze ogólne typu wyjątku FaultException na kliencie, a nie typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="f5530-177">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type.</span></span> <span data-ttu-id="f5530-178">Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="f5530-178">What’s happening?</span></span>  
 <span data-ttu-id="f5530-179">Zdecydowanie zaleca się utworzenie własnych błąd niestandardowy typ danych i zadeklarować, że jako typ szczegółów umowy błędów.</span><span class="sxs-lookup"><span data-stu-id="f5530-179">It is highly recommended that you create your own custom error data type and declare that as the detail type in your fault contract.</span></span> <span data-ttu-id="f5530-180">Przyczyną jest to, że przy użyciu typów wyjątków dostarczane przez system:</span><span class="sxs-lookup"><span data-stu-id="f5530-180">The reason is that using system-provided exception types:</span></span>  
  
-   <span data-ttu-id="f5530-181">Tworzy zależność typu, która usuwa jeden z największych sile aplikacje zorientowane na usługę.</span><span class="sxs-lookup"><span data-stu-id="f5530-181">Creates a type dependency that removes one of the biggest strengths of service-oriented applications.</span></span>  
  
-   <span data-ttu-id="f5530-182">Nie zależą od serializacji w standardowy sposób wyjątków.</span><span class="sxs-lookup"><span data-stu-id="f5530-182">Cannot depend upon exceptions serializing in a standard way.</span></span> <span data-ttu-id="f5530-183">Niektóre — podobnie jak <xref:System.Security.SecurityException>— może nie być możliwy do serializacji w ogóle.</span><span class="sxs-lookup"><span data-stu-id="f5530-183">Some—like <xref:System.Security.SecurityException>—may not be serializable at all.</span></span>  
  
-   <span data-ttu-id="f5530-184">Przedstawia szczegóły implementacji wewnętrzny do klientów.</span><span class="sxs-lookup"><span data-stu-id="f5530-184">Exposes internal implementation details to clients.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="f5530-185">[Określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="f5530-185"> [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
 <span data-ttu-id="f5530-186">Jeśli debugowania aplikacji, jednak można serializować informacje o wyjątku i przywrócić go do klienta przy użyciu <xref:System.ServiceModel.Description.ServiceDebugBehavior> klasy.</span><span class="sxs-lookup"><span data-stu-id="f5530-186">If you are debugging an application, however, you can serialize exception information and return it to the client by using the <xref:System.ServiceModel.Description.ServiceDebugBehavior> class.</span></span>  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a><span data-ttu-id="f5530-187">Wydaje się, jak jednokierunkowe i operacji żądanie odpowiedź zwracanie w przybliżeniu szybkości odpowiedzi nie zawiera żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="f5530-187">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data.</span></span> <span data-ttu-id="f5530-188">Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="f5530-188">What's happening?</span></span>  
 <span data-ttu-id="f5530-189">Określanie, czy operacja jest jednym ze sposobów oznacza tylko, że kontrakt operacji akceptuje komunikat wejściowy i nie może zwracać komunikatu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="f5530-189">Specifying that an operation is one way means only that the operation contract accepts an input message and does not return an output message.</span></span> <span data-ttu-id="f5530-190">W [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], wszystkich wywołań klientów zwracanie danych wychodzących został zapisany do przesyłania lub jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f5530-190">In [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], all client invocations return when the outbound data has been written to the wire or an exception is thrown.</span></span> <span data-ttu-id="f5530-191">Operacje jednokierunkowe działają tak samo, a ich zgłoszenie, jeśli usługi nie można zlokalizować lub zablokować, jeśli usługa nie jest przygotowany do akceptowania danych z sieci.</span><span class="sxs-lookup"><span data-stu-id="f5530-191">One-way operations work the same way, and they can throw if the service cannot be located or block if the service is not prepared to accept the data from the network.</span></span> <span data-ttu-id="f5530-192">Zwykle w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], powoduje to jednokierunkowe wywołania zwracanie szybciej niż żądanie odpowiedź do klienta, ale wszystkie warunek, który spowalnia wysyłania danych wychodzących za pośrednictwem sieci spowalnia operacji jednokierunkowych, a także operacje żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="f5530-192">Typically in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], this results in one-way calls returning to the client more quickly than request-reply; but any condition that slows the sending of the outbound data over the network slows one-way operations as well as request-reply operations.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="f5530-193">[Usługi jednokierunkowe](../../../docs/framework/wcf/feature-details/one-way-services.md) i [dostęp do usług za pomocą klienta WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).</span><span class="sxs-lookup"><span data-stu-id="f5530-193"> [One-Way Services](../../../docs/framework/wcf/feature-details/one-way-services.md) and [Accessing Services Using a WCF Client](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).</span></span>  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a><span data-ttu-id="f5530-194">Używam certyfikat X.509 z mojej usługi i uzyskać System.Security.Cryptography.CryptographicException.</span><span class="sxs-lookup"><span data-stu-id="f5530-194">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException.</span></span> <span data-ttu-id="f5530-195">Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="f5530-195">What’s happening?</span></span>  
 <span data-ttu-id="f5530-196">Częstą przyczyną po zmianie konta użytkownika, w którym uruchamia proces roboczy usług IIS.</span><span class="sxs-lookup"><span data-stu-id="f5530-196">This commonly occurs after changing the user account under which the IIS worker process runs.</span></span> <span data-ttu-id="f5530-197">Na przykład w [!INCLUDE[wxp](../../../includes/wxp-md.md)], w przypadku zmiany domyślnego konta użytkownika, Aspnet_wp.exe zgodną z ASPNET na konto użytkownika, zostanie wyświetlony ten błąd.</span><span class="sxs-lookup"><span data-stu-id="f5530-197">For example, in [!INCLUDE[wxp](../../../includes/wxp-md.md)], if you change the default user account that the Aspnet_wp.exe runs under from ASPNET to a custom user account, you may see this error.</span></span> <span data-ttu-id="f5530-198">Jeśli przy użyciu klucza prywatnego, proces, który korzysta z niego należy mieć uprawnienia dostępu do pliku przechowywaniu tego klucza.</span><span class="sxs-lookup"><span data-stu-id="f5530-198">If using a private key, the process that uses it will need to have permissions to access the file storing that key.</span></span>  
  
 <span data-ttu-id="f5530-199">Jest to możliwe, należy nadać uprawnienia dostępu do odczytu dla konta procesu plik zawierający klucz prywatny.</span><span class="sxs-lookup"><span data-stu-id="f5530-199">If this is the case, you must give read access privileges to the process's account for the file containing the private key.</span></span> <span data-ttu-id="f5530-200">Na przykład jeśli proces roboczy programu IIS działa na koncie Roberta, następnie konieczne będzie daje Bob dostęp do odczytu pliku zawierającego klucz prywatny.</span><span class="sxs-lookup"><span data-stu-id="f5530-200">For example, if the IIS worker process is running under the Bob account, then you will need to give Bob read access to the file containing the private key.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="f5530-201">Aby udzielić dostępu konta użytkownika do pliku, który zawiera klucz prywatny dla określonego certyfikatu X.509, zobacz [porady: X.509 certyfikaty Udostępnij do programu WCF](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="f5530-201"> how to give the correct user account access to the file that contains the private key for a specific X.509 certificate, see [How to: Make X.509 Certificates Accessible to WCF](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span></span>  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a><span data-ttu-id="f5530-202">Pierwszy parametr operację po zmianie wielkie na małe litery; teraz moje klienta zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f5530-202">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception.</span></span> <span data-ttu-id="f5530-203">Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="f5530-203">What's happening?</span></span>  
 <span data-ttu-id="f5530-204">Wartość nazwy parametrów w podpisie operacji są częścią kontraktu i jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="f5530-204">The value of the parameter names in the operation signature are part of the contract and are case-sensitive.</span></span> <span data-ttu-id="f5530-205">Użyj <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> atrybutu, gdy potrzebne do rozróżniania nazwę parametru lokalnych i metadanych, które opisują operacji dla aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="f5530-205">Use the <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> attribute when you need to distinguish between the local parameter name and the metadata that describes the operation for client applications.</span></span>  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a><span data-ttu-id="f5530-206">Używam Moje śledzenia narzędzia i uzyskać endpointnotfoundexception —.</span><span class="sxs-lookup"><span data-stu-id="f5530-206">I’m using one of my tracing tools and I get an EndpointNotFoundException.</span></span> <span data-ttu-id="f5530-207">Co się dzieje?</span><span class="sxs-lookup"><span data-stu-id="f5530-207">What’s happening?</span></span>  
 <span data-ttu-id="f5530-208">Jeśli używasz narzędzia śledzenia, który nie jest dostarczane przez system [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] mechanizm śledzenia i możesz otrzymywać <xref:System.ServiceModel.EndpointNotFoundException> wskazuje, że wystąpiła niezgodność filtru adresu, należy użyć <xref:System.ServiceModel.Description.ClientViaBehavior> klasy do kierowania wiadomości śledzenie Narzędzia i narzędzie przekierowania tych wiadomości na adres usługi.</span><span class="sxs-lookup"><span data-stu-id="f5530-208">If you are using a tracing tool that is not the system-provided [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] tracing mechanism and you receive an <xref:System.ServiceModel.EndpointNotFoundException> that indicates that there was an address filter mismatch, you need to use the <xref:System.ServiceModel.Description.ClientViaBehavior> class to direct the messages to the tracing utility and have the utility redirect those messages to the service address.</span></span> <span data-ttu-id="f5530-209"><xref:System.ServiceModel.Description.ClientViaBehavior> Zmienia klasy `Via` adresowania nagłówka, aby określić adres sieciowy dalej niezależnie od odbiornika ultimate, wskazane przez `To` adresowania nagłówka.</span><span class="sxs-lookup"><span data-stu-id="f5530-209">The <xref:System.ServiceModel.Description.ClientViaBehavior> class alters the `Via` addressing header to specify the next network address separately from the ultimate receiver, indicated by the `To` addressing header.</span></span> <span data-ttu-id="f5530-210">W ten sposób, jednak nie należy zmieniać adresu punktu końcowego, który jest używany do ustanawiania `To` wartość.</span><span class="sxs-lookup"><span data-stu-id="f5530-210">When doing this, however, do not change the endpoint address, which is used to establish the `To` value.</span></span>  
  
 <span data-ttu-id="f5530-211">Poniższy przykładowy kod przedstawia przykład klienta pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f5530-211">The following code example shows an example client configuration file.</span></span>  
  
```xml
<endpoint   
  address=http://localhost:8000/MyServer/  
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
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a><span data-ttu-id="f5530-212">Co to jest adres podstawowy?</span><span class="sxs-lookup"><span data-stu-id="f5530-212">What is the base address?</span></span> <span data-ttu-id="f5530-213">Jaki związek między adres punktu końcowego?</span><span class="sxs-lookup"><span data-stu-id="f5530-213">How does it relate to an endpoint address?</span></span>  
 <span data-ttu-id="f5530-214">Podstawowy adres jest adresem głównego dla <xref:System.ServiceModel.ServiceHost> klasy.</span><span class="sxs-lookup"><span data-stu-id="f5530-214">A base address is the root address for a <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="f5530-215">Domyślnie po dodaniu <xref:System.ServiceModel.Description.ServiceMetadataBehavior> klasy do konfiguracji usługi sieci Web Services Description Language (WSDL) dla wszystkich punktów końcowych hosta publikuje są pobierane z podstawowy adres HTTP, a także wszelkie adres względny dostarczony do zachowania metadanych oraz "? wsdl".</span><span class="sxs-lookup"><span data-stu-id="f5530-215">By default, if you add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class into your service configuration, the Web Services Description Language (WSDL) for all endpoints the host publishes are retrieved from the HTTP base address, plus any relative address provided to the metadata behavior, plus "?wsdl".</span></span> <span data-ttu-id="f5530-216">Jeśli znasz [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] i IIS, adres podstawowy jest odpowiednikiem katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="f5530-216">If you are familiar with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] and IIS, the base address is equivalent to the virtual directory.</span></span>  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a><span data-ttu-id="f5530-217">Udostępnianie portów między punkt końcowy usługi i punktu końcowego mex przy użyciu NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="f5530-217">Sharing a port between a service endpoint and a mex endpoint using the NetTcpBinding</span></span>  
 <span data-ttu-id="f5530-218">Jeśli adres podstawowy usługi można określić jako net.tcp://MyServer: 8080/Moja_usługa i dodaj następujące punkty końcowe:</span><span class="sxs-lookup"><span data-stu-id="f5530-218">If you specify the base address for a service as net.tcp://MyServer:8080/MyService and add the following endpoints:</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 <span data-ttu-id="f5530-219">A jeśli jedno z ustawień NetTcpBinding zmodyfikujesz pokazane na poniższy fragment konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="f5530-219">And if you modify one of the NetTcpBinding settings as shown in the following configuration snippet:</span></span>  
  
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
  
 <span data-ttu-id="f5530-220">Zostanie wyświetlony błąd podobnie do następującej: nieobsługiwany wyjątek: System.ServiceModel.AddressAlreadyInUseException: istnieje już odbiornik na ten błąd można obejść, określając w pełni kwalifikowanego adres URL z innego portu dla 0.0.0.0:9000 punkt końcowy IP punkt końcowy MEX pokazane na poniższy fragment konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="f5530-220">You will see an error like the following: Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000 You can work around this error by specifying a fully qualified URL with a different port for the MEX endpoint as shown in the following configuration snippet:</span></span>  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a><span data-ttu-id="f5530-221">Podczas wywoływania aplikacji protokołu HTTP sieci Web WCF z aplikacji WCF SOAP usługi zwraca następujący błąd: niedozwolone 405 — metoda</span><span class="sxs-lookup"><span data-stu-id="f5530-221">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>  
 <span data-ttu-id="f5530-222">Wywoływanie aplikacji protokołu HTTP sieci Web WCF (usługa, która używa <xref:System.ServiceModel.WebHttpBinding> i <xref:System.ServiceModel.Description.WebHttpBehavior>) z usługą platformy WCF usługa może generować następujący wyjątek: `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: serwer zdalny zwrócił nieoczekiwaną odpowiedź : (405) — metoda nie dozwolone. "ten wyjątek spowodowany WCF zastępuje wychodzącej <xref:System.ServiceModel.OperationContext> z przychodzącego <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="f5530-222">Calling a WCF Web HTTP application (a service that uses the <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior>) from a WCF service may generate the following exception: `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.\` This exception occurs because WCF overwrites the outgoing <xref:System.ServiceModel.OperationContext> with the incoming <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="f5530-223">Aby rozwiązać ten problem utworzyć <xref:System.ServiceModel.OperationContextScope> w ramach operacji usługi WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="f5530-223">To solve this problem create an <xref:System.ServiceModel.OperationContextScope> within the WCF Web HTTP service operation.</span></span> <span data-ttu-id="f5530-224">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f5530-224">For example:</span></span>  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5530-225">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5530-225">See Also</span></span>  
 [<span data-ttu-id="f5530-226">Debugowanie błędów uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f5530-226">Debugging Windows Authentication Errors</span></span>](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)
