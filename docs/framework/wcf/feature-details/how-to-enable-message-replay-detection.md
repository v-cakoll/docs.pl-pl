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
ms.openlocfilehash: bf45b39f59e2fe38fec88d1fac23ab824c009546
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597088"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="6ea16-102">Instrukcje: Włączanie wykrywania powtarzania komunikatu</span><span class="sxs-lookup"><span data-stu-id="6ea16-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="6ea16-103">Ataku powtarzania występuje, gdy osoba atakująca kopiuje strumień komunikatów między dwiema stronami i odtwarza strumień do co najmniej jednej ze stron.</span><span class="sxs-lookup"><span data-stu-id="6ea16-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="6ea16-104">O ile nie zostanie to skorygowane, komputery, które podlegają atakom, przetworzyją strumień jako wiarygodne komunikaty, co skutkuje zakresem nieprawidłowych skutków, takich jak nadmiarowe zamówienia elementu.</span><span class="sxs-lookup"><span data-stu-id="6ea16-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="6ea16-105">Aby uzyskać więcej informacji na temat wykrywania powtarzania wiadomości, zobacz [wykrywanie powtarzania komunikatów](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="6ea16-105">For more information about message replay detection, see [Message Replay Detection](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="6ea16-106">Poniższa procedura przedstawia różne właściwości, których można użyć do kontrolowania wykrywania powtarzania przy użyciu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6ea16-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="6ea16-107">Aby kontrolować wykrywanie powtarzania na kliencie przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="6ea16-107">To control replay detection on the client using code</span></span>  
  
1. <span data-ttu-id="6ea16-108">Utwórz element <xref:System.ServiceModel.Channels.SecurityBindingElement> do użycia w <xref:System.ServiceModel.Channels.CustomBinding> .</span><span class="sxs-lookup"><span data-stu-id="6ea16-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="6ea16-109">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="6ea16-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="6ea16-110">W poniższym przykładzie zastosowano element <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> utworzony z <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> <xref:System.ServiceModel.Channels.SecurityBindingElement> klasą.</span><span class="sxs-lookup"><span data-stu-id="6ea16-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2. <span data-ttu-id="6ea16-111">Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> właściwości, aby zwrócić odwołanie do <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> klasy i ustawić dowolne z następujących właściwości, zgodnie z potrzebami:</span><span class="sxs-lookup"><span data-stu-id="6ea16-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1. <span data-ttu-id="6ea16-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="6ea16-112">`DetectReplay`.</span></span> <span data-ttu-id="6ea16-113">Wartość logiczna.</span><span class="sxs-lookup"><span data-stu-id="6ea16-113">A Boolean value.</span></span> <span data-ttu-id="6ea16-114">Reguluje to, czy klient powinien wykryć odtwarzanie z serwera.</span><span class="sxs-lookup"><span data-stu-id="6ea16-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="6ea16-115">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="6ea16-115">The default is `true`.</span></span>  
  
    2. <span data-ttu-id="6ea16-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="6ea16-116">`MaxClockSkew`.</span></span> <span data-ttu-id="6ea16-117"><xref:System.TimeSpan>Wartość.</span><span class="sxs-lookup"><span data-stu-id="6ea16-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="6ea16-118">Decyduje o tym, ile czasu może odchylać mechanizm powtarzania między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="6ea16-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="6ea16-119">Mechanizm zabezpieczeń sprawdza, czy sygnatura czasowa jest wysyłana, i określa, czy wysłano ją zbyt długo w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="6ea16-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="6ea16-120">Wartość domyślna to 5 minut.</span><span class="sxs-lookup"><span data-stu-id="6ea16-120">The default is 5 minutes.</span></span>  
  
    3. <span data-ttu-id="6ea16-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="6ea16-121">`ReplayWindow`.</span></span> <span data-ttu-id="6ea16-122">`TimeSpan`Wartość.</span><span class="sxs-lookup"><span data-stu-id="6ea16-122">A `TimeSpan` value.</span></span> <span data-ttu-id="6ea16-123">Reguluje to, jak długo komunikat może być aktywny w sieci po wysłaniu go przez serwer (za pośrednictwem pośredników) przed osiągnięciem klienta.</span><span class="sxs-lookup"><span data-stu-id="6ea16-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="6ea16-124">Klient śledzi sygnatury komunikatów wysłanych w ciągu najnowszej wersji `ReplayWindow` na potrzeby wykrywania powtarzania.</span><span class="sxs-lookup"><span data-stu-id="6ea16-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4. <span data-ttu-id="6ea16-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="6ea16-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="6ea16-126">Wartość całkowita.</span><span class="sxs-lookup"><span data-stu-id="6ea16-126">An integer value.</span></span> <span data-ttu-id="6ea16-127">Klient przechowuje podpisy wiadomości w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6ea16-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="6ea16-128">To ustawienie określa, ile sygnatur może być przechowywanych w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6ea16-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="6ea16-129">Jeśli liczba komunikatów wysłanych w ramach ostatniego okna powtarzania osiągnie limit pamięci podręcznej, nowe komunikaty są odrzucane do momentu osiągnięcia limitu czasu dla najstarszych podpisów w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6ea16-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="6ea16-130">Wartość domyślna to 500000.</span><span class="sxs-lookup"><span data-stu-id="6ea16-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="6ea16-131">Aby kontrolować wykrywanie powtarzania w usłudze przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="6ea16-131">To control replay detection on the service using code</span></span>  
  
1. <span data-ttu-id="6ea16-132">Utwórz element <xref:System.ServiceModel.Channels.SecurityBindingElement> do użycia w <xref:System.ServiceModel.Channels.CustomBinding> .</span><span class="sxs-lookup"><span data-stu-id="6ea16-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2. <span data-ttu-id="6ea16-133">Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> właściwości, aby zwrócić odwołanie do <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> klasy, i ustaw właściwości zgodnie z opisem wcześniej.</span><span class="sxs-lookup"><span data-stu-id="6ea16-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="6ea16-134">Aby kontrolować wykrywanie powtarzania w konfiguracji dla klienta lub usługi</span><span class="sxs-lookup"><span data-stu-id="6ea16-134">To control replay detection in configuration for the client or service</span></span>  
  
1. <span data-ttu-id="6ea16-135">Utwórz [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="6ea16-135">Create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2. <span data-ttu-id="6ea16-136">Utwórz `<security>` element.</span><span class="sxs-lookup"><span data-stu-id="6ea16-136">Create a `<security>` element.</span></span>  
  
3. <span data-ttu-id="6ea16-137">Utwórz [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) lub [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) .</span><span class="sxs-lookup"><span data-stu-id="6ea16-137">Create a [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4. <span data-ttu-id="6ea16-138">W razie potrzeby ustaw następujące wartości atrybutów: `detectReplays` ,, `maxClockSkew` `replayWindow` , i `replayCacheSize` .</span><span class="sxs-lookup"><span data-stu-id="6ea16-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="6ea16-139">Poniższy przykład ustawia atrybuty obu `<localServiceSettings>` i `<localClientSettings>` elementów:</span><span class="sxs-lookup"><span data-stu-id="6ea16-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="6ea16-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ea16-140">Example</span></span>  
 <span data-ttu-id="6ea16-141">Poniższy przykład tworzy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> metodę i ustawia właściwości powtarzania powiązania.</span><span class="sxs-lookup"><span data-stu-id="6ea16-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="6ea16-142">Zakres powtarzania: tylko zabezpieczenia wiadomości</span><span class="sxs-lookup"><span data-stu-id="6ea16-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="6ea16-143">Należy zauważyć, że poniższe procedury dotyczą tylko trybu zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6ea16-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="6ea16-144">W przypadku transportu i transportu z trybami poświadczeń wiadomości mechanizmy transportu wykrywają odtwarzanie.</span><span class="sxs-lookup"><span data-stu-id="6ea16-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="6ea16-145">Uwagi dotyczące bezpiecznej konwersacji</span><span class="sxs-lookup"><span data-stu-id="6ea16-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="6ea16-146">W przypadku powiązań umożliwiających bezpieczne konwersacje można dostosować te ustawienia zarówno dla kanału aplikacji, jak i dla powiązania inicjowania bezpiecznego konwersacji.</span><span class="sxs-lookup"><span data-stu-id="6ea16-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="6ea16-147">Można na przykład wyłączyć odtwarzanie dla kanału aplikacji, ale włączyć je dla kanału ładowania początkowego, który nawiązuje bezpieczną konwersację.</span><span class="sxs-lookup"><span data-stu-id="6ea16-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="6ea16-148">Jeśli nie używasz sesji bezpiecznych konwersacji, wykrywanie powtarzania nie gwarantuje wykrywania operacji odtwarzania w scenariuszach farmy serwerów i podczas odtwarzania procesu.</span><span class="sxs-lookup"><span data-stu-id="6ea16-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="6ea16-149">Dotyczy to następujących powiązań dostarczonych przez system:</span><span class="sxs-lookup"><span data-stu-id="6ea16-149">This applies to the following system-provided bindings:</span></span>  
  
- <span data-ttu-id="6ea16-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="6ea16-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
- <span data-ttu-id="6ea16-151"><xref:System.ServiceModel.WSHttpBinding>z <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwością ustawioną na `false` .</span><span class="sxs-lookup"><span data-stu-id="6ea16-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6ea16-152">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6ea16-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="6ea16-153">Do skompilowania kodu wymagane są następujące przestrzenie nazw:</span><span class="sxs-lookup"><span data-stu-id="6ea16-153">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="6ea16-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ea16-154">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="6ea16-155">Bezpieczne konwersacje i bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="6ea16-155">Secure Conversations and Secure Sessions</span></span>](secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="6ea16-156">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="6ea16-156">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
