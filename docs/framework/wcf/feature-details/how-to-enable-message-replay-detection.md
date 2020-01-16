---
title: 'Instrukcje: Włączanie wykrywania powtarzania komunikatu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
ms.openlocfilehash: 450a99fc6604ccb3fa796e8a73e1ddc3e3adff9e
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964661"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="ccd39-102">Instrukcje: Włączanie wykrywania powtarzania komunikatu</span><span class="sxs-lookup"><span data-stu-id="ccd39-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="ccd39-103">Ataku powtarzania występuje, gdy osoba atakująca kopiuje strumień komunikatów między dwiema stronami i odtwarza strumień do co najmniej jednej ze stron.</span><span class="sxs-lookup"><span data-stu-id="ccd39-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="ccd39-104">O ile nie zostanie to skorygowane, komputery, które podlegają atakom, przetworzyją strumień jako wiarygodne komunikaty, co skutkuje zakresem nieprawidłowych skutków, takich jak nadmiarowe zamówienia elementu.</span><span class="sxs-lookup"><span data-stu-id="ccd39-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="ccd39-105">Aby uzyskać więcej informacji na temat wykrywania powtarzania wiadomości, zobacz [wykrywanie powtarzania komunikatów](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="ccd39-105">For more information about message replay detection, see [Message Replay Detection](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="ccd39-106">Poniższa procedura przedstawia różne właściwości, których można użyć do kontrolowania wykrywania powtarzania przy użyciu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ccd39-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="ccd39-107">Aby kontrolować wykrywanie powtarzania na kliencie przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="ccd39-107">To control replay detection on the client using code</span></span>  
  
1. <span data-ttu-id="ccd39-108">Utwórz <xref:System.ServiceModel.Channels.SecurityBindingElement> do użycia w <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="ccd39-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="ccd39-109">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="ccd39-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="ccd39-110">Poniższy przykład używa <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> utworzonego za pomocą <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> klasy <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="ccd39-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2. <span data-ttu-id="ccd39-111">Użyj właściwości <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>, aby zwrócić odwołanie do klasy <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> i ustawić dowolne z następujących właściwości, zgodnie z potrzebami:</span><span class="sxs-lookup"><span data-stu-id="ccd39-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1. <span data-ttu-id="ccd39-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="ccd39-112">`DetectReplay`.</span></span> <span data-ttu-id="ccd39-113">Wartość logiczna.</span><span class="sxs-lookup"><span data-stu-id="ccd39-113">A Boolean value.</span></span> <span data-ttu-id="ccd39-114">Reguluje to, czy klient powinien wykryć odtwarzanie z serwera.</span><span class="sxs-lookup"><span data-stu-id="ccd39-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="ccd39-115">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="ccd39-115">The default is `true`.</span></span>  
  
    2. <span data-ttu-id="ccd39-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="ccd39-116">`MaxClockSkew`.</span></span> <span data-ttu-id="ccd39-117">Wartość <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="ccd39-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="ccd39-118">Decyduje o tym, ile czasu może odchylać mechanizm powtarzania między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="ccd39-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="ccd39-119">Mechanizm zabezpieczeń sprawdza, czy sygnatura czasowa jest wysyłana, i określa, czy wysłano ją zbyt długo w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="ccd39-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="ccd39-120">Wartość domyślna to 5 minut.</span><span class="sxs-lookup"><span data-stu-id="ccd39-120">The default is 5 minutes.</span></span>  
  
    3. <span data-ttu-id="ccd39-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="ccd39-121">`ReplayWindow`.</span></span> <span data-ttu-id="ccd39-122">Wartość `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="ccd39-122">A `TimeSpan` value.</span></span> <span data-ttu-id="ccd39-123">Reguluje to, jak długo komunikat może być aktywny w sieci po wysłaniu go przez serwer (za pośrednictwem pośredników) przed osiągnięciem klienta.</span><span class="sxs-lookup"><span data-stu-id="ccd39-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="ccd39-124">Klient śledzi sygnatury komunikatów wysyłanych w ciągu najnowszych `ReplayWindow` na potrzeby wykrywania powtarzania.</span><span class="sxs-lookup"><span data-stu-id="ccd39-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4. <span data-ttu-id="ccd39-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="ccd39-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="ccd39-126">Wartość całkowita.</span><span class="sxs-lookup"><span data-stu-id="ccd39-126">An integer value.</span></span> <span data-ttu-id="ccd39-127">Klient przechowuje podpisy wiadomości w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ccd39-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="ccd39-128">To ustawienie określa, ile sygnatur może być przechowywanych w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ccd39-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="ccd39-129">Jeśli liczba komunikatów wysłanych w ramach ostatniego okna powtarzania osiągnie limit pamięci podręcznej, nowe komunikaty są odrzucane do momentu osiągnięcia limitu czasu dla najstarszych podpisów w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ccd39-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="ccd39-130">Wartość domyślna to 500000.</span><span class="sxs-lookup"><span data-stu-id="ccd39-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="ccd39-131">Aby kontrolować wykrywanie powtarzania w usłudze przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="ccd39-131">To control replay detection on the service using code</span></span>  
  
1. <span data-ttu-id="ccd39-132">Utwórz <xref:System.ServiceModel.Channels.SecurityBindingElement> do użycia w <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="ccd39-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2. <span data-ttu-id="ccd39-133">Użyj właściwości <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>, aby zwrócić odwołanie do klasy <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> i ustawić właściwości zgodnie z opisem wcześniej.</span><span class="sxs-lookup"><span data-stu-id="ccd39-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="ccd39-134">Aby kontrolować wykrywanie powtarzania w konfiguracji dla klienta lub usługi</span><span class="sxs-lookup"><span data-stu-id="ccd39-134">To control replay detection in configuration for the client or service</span></span>  
  
1. <span data-ttu-id="ccd39-135">Utwórz [\<niestandardowebinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="ccd39-135">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2. <span data-ttu-id="ccd39-136">Utwórz element `<security>`.</span><span class="sxs-lookup"><span data-stu-id="ccd39-136">Create a `<security>` element.</span></span>  
  
3. <span data-ttu-id="ccd39-137">Utwórz [\<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) lub [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="ccd39-137">Create a [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4. <span data-ttu-id="ccd39-138">Ustaw następujące wartości atrybutów, zgodnie z potrzebami: `detectReplays`, `maxClockSkew`, `replayWindow`i `replayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="ccd39-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="ccd39-139">Poniższy przykład ustawia atrybuty elementu `<localServiceSettings>` i `<localClientSettings>`:</span><span class="sxs-lookup"><span data-stu-id="ccd39-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="ccd39-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="ccd39-140">Example</span></span>  
 <span data-ttu-id="ccd39-141">Poniższy przykład tworzy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> przy użyciu metody <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> i ustawia właściwości powtarzania powiązania.</span><span class="sxs-lookup"><span data-stu-id="ccd39-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="ccd39-142">Zakres powtarzania: tylko zabezpieczenia wiadomości</span><span class="sxs-lookup"><span data-stu-id="ccd39-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="ccd39-143">Należy zauważyć, że poniższe procedury dotyczą tylko trybu zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ccd39-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="ccd39-144">W przypadku transportu i transportu z trybami poświadczeń wiadomości mechanizmy transportu wykrywają odtwarzanie.</span><span class="sxs-lookup"><span data-stu-id="ccd39-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="ccd39-145">Uwagi dotyczące bezpiecznej konwersacji</span><span class="sxs-lookup"><span data-stu-id="ccd39-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="ccd39-146">W przypadku powiązań umożliwiających bezpieczne konwersacje można dostosować te ustawienia zarówno dla kanału aplikacji, jak i dla powiązania inicjowania bezpiecznego konwersacji.</span><span class="sxs-lookup"><span data-stu-id="ccd39-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="ccd39-147">Można na przykład wyłączyć odtwarzanie dla kanału aplikacji, ale włączyć je dla kanału ładowania początkowego, który nawiązuje bezpieczną konwersację.</span><span class="sxs-lookup"><span data-stu-id="ccd39-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="ccd39-148">Jeśli nie używasz sesji bezpiecznych konwersacji, wykrywanie powtarzania nie gwarantuje wykrywania operacji odtwarzania w scenariuszach farmy serwerów i podczas odtwarzania procesu.</span><span class="sxs-lookup"><span data-stu-id="ccd39-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="ccd39-149">Dotyczy to następujących powiązań dostarczonych przez system:</span><span class="sxs-lookup"><span data-stu-id="ccd39-149">This applies to the following system-provided bindings:</span></span>  
  
- <span data-ttu-id="ccd39-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="ccd39-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
- <span data-ttu-id="ccd39-151"><xref:System.ServiceModel.WSHttpBinding> z właściwością <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> ustawioną na `false`.</span><span class="sxs-lookup"><span data-stu-id="ccd39-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ccd39-152">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ccd39-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="ccd39-153">Do skompilowania kodu wymagane są następujące przestrzenie nazw:</span><span class="sxs-lookup"><span data-stu-id="ccd39-153">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="ccd39-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ccd39-154">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="ccd39-155">Bezpieczne konwersacje i bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="ccd39-155">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [<span data-ttu-id="ccd39-156">\<localClientSettings></span><span class="sxs-lookup"><span data-stu-id="ccd39-156">\<localClientSettings></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="ccd39-157">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ccd39-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
