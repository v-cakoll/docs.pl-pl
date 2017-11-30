---
title: "Instrukcje: Włączanie wykrywania powtarzania komunikatu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed0bca649e7e94ff94a7dab6191c59e48c0bec3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="ed86c-102">Instrukcje: Włączanie wykrywania powtarzania komunikatu</span><span class="sxs-lookup"><span data-stu-id="ed86c-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="ed86c-103">Atak powtarzania występuje, gdy osoba atakująca kopiuje strumienia komunikatów między dwiema stronami i odtwarzaniem strumienia do jednego lub więcej stron.</span><span class="sxs-lookup"><span data-stu-id="ed86c-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="ed86c-104">O ile skorygowane, komputery mogą ulec ataku zostaną przetworzone strumienia jako istotnych wiadomości, co w zakresie zły konsekwencje, takie jak nadmiarowe zamówień elementu.</span><span class="sxs-lookup"><span data-stu-id="ed86c-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ed86c-105">wykrywanie powtarzania, zobacz [wykrywania powtarzania komunikatu](http://go.microsoft.com/fwlink/?LinkId=88536).</span><span class="sxs-lookup"><span data-stu-id="ed86c-105"> message replay detection, see [Message Replay Detection](http://go.microsoft.com/fwlink/?LinkId=88536).</span></span>  
  
 <span data-ttu-id="ed86c-106">W poniższej procedurze przedstawiono różne właściwości, które służy do sterowania powtarzania wykrywania przy użyciu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ed86c-106">The following procedure demonstrates various properties that you can use to control replay detection using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="ed86c-107">Aby kontrolować wykrywania powtórzeń na kliencie przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="ed86c-107">To control replay detection on the client using code</span></span>  
  
1.  <span data-ttu-id="ed86c-108">Utwórz <xref:System.ServiceModel.Channels.SecurityBindingElement> do użycia w <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="ed86c-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="ed86c-109">[Porady: Tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="ed86c-109"> [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="ed86c-110">W poniższym przykładzie użyto <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> utworzone za pomocą <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> z <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="ed86c-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2.  <span data-ttu-id="ed86c-111">Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> zwraca odwołanie do właściwości <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> klasy i ustaw dowolne z poniższych właściwości, zależnie od potrzeb:</span><span class="sxs-lookup"><span data-stu-id="ed86c-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1.  <span data-ttu-id="ed86c-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="ed86c-112">`DetectReplay`.</span></span> <span data-ttu-id="ed86c-113">Wartość logiczna.</span><span class="sxs-lookup"><span data-stu-id="ed86c-113">A Boolean value.</span></span> <span data-ttu-id="ed86c-114">Decyduje to, czy klient powinien wykryć odtworzenie z serwera.</span><span class="sxs-lookup"><span data-stu-id="ed86c-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="ed86c-115">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="ed86c-115">The default is `true`.</span></span>  
  
    2.  <span data-ttu-id="ed86c-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="ed86c-116">`MaxClockSkew`.</span></span> <span data-ttu-id="ed86c-117">A <xref:System.TimeSpan> wartość.</span><span class="sxs-lookup"><span data-stu-id="ed86c-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="ed86c-118">Kontroluje ilość czasu zegara, mechanizmu powtarzania może tolerować między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="ed86c-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="ed86c-119">Mechanizm zabezpieczeń sprawdza, czy czas sygnatury wysyłane i określa, czy została ona wysłana zbyt daleko w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="ed86c-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="ed86c-120">Wartość domyślna to 5 minut.</span><span class="sxs-lookup"><span data-stu-id="ed86c-120">The default is 5 minutes.</span></span>  
  
    3.  <span data-ttu-id="ed86c-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="ed86c-121">`ReplayWindow`.</span></span> <span data-ttu-id="ed86c-122">A `TimeSpan` wartość.</span><span class="sxs-lookup"><span data-stu-id="ed86c-122">A `TimeSpan` value.</span></span> <span data-ttu-id="ed86c-123">Kontroluje to czas przechowywania wiadomości może współdziałać w sieci po serwer wysyła on (za pośrednictwem pośredników) przed osiągnięciem klienta.</span><span class="sxs-lookup"><span data-stu-id="ed86c-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="ed86c-124">Klient śledzi podpisy wiadomości wysłane w najnowszej `ReplayWindow` na potrzeby wykrywania powtarzania.</span><span class="sxs-lookup"><span data-stu-id="ed86c-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4.  <span data-ttu-id="ed86c-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="ed86c-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="ed86c-126">Wartość całkowita.</span><span class="sxs-lookup"><span data-stu-id="ed86c-126">An integer value.</span></span> <span data-ttu-id="ed86c-127">Klient przechowuje podpisy wiadomości w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ed86c-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="ed86c-128">To ustawienie określa, ile podpisów mogą być przechowywane w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ed86c-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="ed86c-129">Jeśli liczbę komunikatów wysłanych w oknie powtarzania ostatniego osiągnie limit pamięci podręcznej, nowe komunikaty są odrzucane, dopóki najstarsze podpisów buforowane osiągnięcia limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="ed86c-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="ed86c-130">Wartość domyślna wynosi 500 000.</span><span class="sxs-lookup"><span data-stu-id="ed86c-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="ed86c-131">Aby kontrolować wykrywania powtórzeń w usłudze przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="ed86c-131">To control replay detection on the service using code</span></span>  
  
1.  <span data-ttu-id="ed86c-132">Utwórz <xref:System.ServiceModel.Channels.SecurityBindingElement> do użycia w <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="ed86c-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2.  <span data-ttu-id="ed86c-133">Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> zwraca odwołanie do właściwości <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> klasy, a następnie ustaw właściwości opisanych powyżej.</span><span class="sxs-lookup"><span data-stu-id="ed86c-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="ed86c-134">Aby kontrolować wykrywania powtórzeń w konfiguracji dla klienta lub usługi</span><span class="sxs-lookup"><span data-stu-id="ed86c-134">To control replay detection in configuration for the client or service</span></span>  
  
1.  <span data-ttu-id="ed86c-135">Utwórz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="ed86c-135">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2.  <span data-ttu-id="ed86c-136">Utwórz `<security>` elementu.</span><span class="sxs-lookup"><span data-stu-id="ed86c-136">Create a `<security>` element.</span></span>  
  
3.  <span data-ttu-id="ed86c-137">Utwórz [ \<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) lub [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="ed86c-137">Create a [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4.  <span data-ttu-id="ed86c-138">Ustaw następujące wartości atrybutów odpowiednio: `detectReplays`, `maxClockSkew`, `replayWindow`, i `replayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="ed86c-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="ed86c-139">W poniższym przykładzie ustawiono oba atrybuty `<localServiceSettings>` i `<localClientSettings>` elementu:</span><span class="sxs-lookup"><span data-stu-id="ed86c-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="NewBinding0">  
       <textMessageEncoding />  
        <security>  
         <localClientSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
         <localServiceSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
        <secureConversationBootstrap />  
       </security>  
      <httpTransport />  
     </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="ed86c-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="ed86c-140">Example</span></span>  
 <span data-ttu-id="ed86c-141">Poniższy przykład tworzy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> przy użyciu <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> — metoda i ustawia właściwości powtarzania powiązania.</span><span class="sxs-lookup"><span data-stu-id="ed86c-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="ed86c-142">Zakres powtarzania: zabezpieczenia wiadomości tylko</span><span class="sxs-lookup"><span data-stu-id="ed86c-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="ed86c-143">Należy pamiętać, że poniższe procedury dotyczą tylko tryb zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ed86c-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="ed86c-144">Dla transportu i transportu z poświadczeniami komunikatu trybami mechanizmów transportu wykryć odtworzenie.</span><span class="sxs-lookup"><span data-stu-id="ed86c-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="ed86c-145">Zabezpieczanie konwersacji uwagi</span><span class="sxs-lookup"><span data-stu-id="ed86c-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="ed86c-146">Dla powiązania, które umożliwiają bezpiecznych konwersacji można dostosować te ustawienia, zarówno dla kanału aplikacji, a także ładowania początkowego powiązania bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="ed86c-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="ed86c-147">Na przykład można wyłączyć odtworzenie dla kanału aplikacji, ale włączyć je do ładowania początkowego kanału, który określa bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="ed86c-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="ed86c-148">Jeśli nie używasz sesji bezpiecznej konwersacji, wykrywania powtórzeń nie gwarantuje wykrywania odtworzenie w scenariusze farmy serwera i gdy proces zostanie odtworzony.</span><span class="sxs-lookup"><span data-stu-id="ed86c-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="ed86c-149">Dotyczy to następujących powiązania dostarczane przez system:</span><span class="sxs-lookup"><span data-stu-id="ed86c-149">This applies to the following system-provided bindings:</span></span>  
  
-   <span data-ttu-id="ed86c-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="ed86c-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
-   <span data-ttu-id="ed86c-151"><xref:System.ServiceModel.WSHttpBinding>z <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> ustawioną właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="ed86c-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ed86c-152">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ed86c-152">Compiling the Code</span></span>  
  
-   <span data-ttu-id="ed86c-153">Następujących przestrzeni nazw są wymagane, aby skompilować kod:</span><span class="sxs-lookup"><span data-stu-id="ed86c-153">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="ed86c-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed86c-154">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [<span data-ttu-id="ed86c-155">Bezpieczne konwersacje i bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="ed86c-155">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)  
 [<span data-ttu-id="ed86c-156">\<localClientSettings ></span><span class="sxs-lookup"><span data-stu-id="ed86c-156">\<localClientSettings></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)  
 [<span data-ttu-id="ed86c-157">Porady: Tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ed86c-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
