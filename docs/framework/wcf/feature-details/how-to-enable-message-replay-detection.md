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
ms.openlocfilehash: 05bcddabf625e478616cce39f08b0ff8af282716
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184951"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="3fa9e-102">Instrukcje: Włączanie wykrywania powtarzania komunikatu</span><span class="sxs-lookup"><span data-stu-id="3fa9e-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="3fa9e-103">Atak powtarzania występuje, gdy osoba atakująca kopiuje strumień wiadomości między dwiema stronami i odtwarza strumień do jednej lub więcej stron.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="3fa9e-104">O ile nie zostanie złagodzone, komputery podlegające atakowi będą przetwarzać strumień jako prawidłowe wiadomości, co spowoduje szereg złych konsekwencji, takich jak zbędne zamówienia elementu.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="3fa9e-105">Aby uzyskać więcej informacji na temat wykrywania powtarzania [komunikatów, zobacz Wykrywanie odtwolień komunikatów](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="3fa9e-105">For more information about message replay detection, see [Message Replay Detection](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="3fa9e-106">Poniższa procedura pokazuje różne właściwości, których można użyć do kontrolowania wykrywania powtarzania przy użyciu programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3fa9e-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="3fa9e-107">Aby kontrolować wykrywanie powtórzeń na kliencie przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="3fa9e-107">To control replay detection on the client using code</span></span>  
  
1. <span data-ttu-id="3fa9e-108">Utwórz <xref:System.ServiceModel.Channels.SecurityBindingElement> a do <xref:System.ServiceModel.Channels.CustomBinding>użycia w pliku .</span><span class="sxs-lookup"><span data-stu-id="3fa9e-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="3fa9e-109">Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="3fa9e-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="3fa9e-110">W poniższym przykładzie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> użyto utworzonego <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> z <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2. <span data-ttu-id="3fa9e-111">Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> właściwości, aby zwrócić <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> odwołanie do klasy i ustawić dowolną z następujących właściwości, odpowiednio:</span><span class="sxs-lookup"><span data-stu-id="3fa9e-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1. <span data-ttu-id="3fa9e-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-112">`DetectReplay`.</span></span> <span data-ttu-id="3fa9e-113">Wartość logiczna.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-113">A Boolean value.</span></span> <span data-ttu-id="3fa9e-114">Określa, czy klient powinien wykryć powtórki z serwera.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="3fa9e-115">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-115">The default is `true`.</span></span>  
  
    2. <span data-ttu-id="3fa9e-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-116">`MaxClockSkew`.</span></span> <span data-ttu-id="3fa9e-117">Wartość. <xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="3fa9e-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="3fa9e-118">Określa, ile czasu pochylić mechanizm powtarzania może tolerować między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="3fa9e-119">Mechanizm zabezpieczeń sprawdza sygnaturę czasową wysłano i określa, czy został wysłany zbyt daleko wstecz w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="3fa9e-120">Wartość domyślna to 5 minut.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-120">The default is 5 minutes.</span></span>  
  
    3. <span data-ttu-id="3fa9e-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-121">`ReplayWindow`.</span></span> <span data-ttu-id="3fa9e-122">Wartość. `TimeSpan`</span><span class="sxs-lookup"><span data-stu-id="3fa9e-122">A `TimeSpan` value.</span></span> <span data-ttu-id="3fa9e-123">Określa to, jak długo wiadomość może być owakowany w sieci po wysłaniu jej przez serwer (za pośrednictwem pośredników) przed dotarciem do klienta.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="3fa9e-124">Klient śledzi podpisy wiadomości wysłanych w `ReplayWindow` ciągu najnowszych do celów wykrywania powtórzeń.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4. <span data-ttu-id="3fa9e-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="3fa9e-126">Wartość całkowita.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-126">An integer value.</span></span> <span data-ttu-id="3fa9e-127">Klient przechowuje podpisy wiadomości w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="3fa9e-128">To ustawienie określa, ile podpisów może przechowywać pamięć podręczna.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="3fa9e-129">Jeśli liczba wiadomości wysłanych w ostatnim oknie powtarzania osiągnie limit pamięci podręcznej, nowe wiadomości są odrzucane, dopóki najstarsze buforowane podpisy nie osiągną limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="3fa9e-130">Wartość domyślna to 500000.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="3fa9e-131">Aby kontrolować wykrywanie powtórzeń w usłudze przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="3fa9e-131">To control replay detection on the service using code</span></span>  
  
1. <span data-ttu-id="3fa9e-132">Utwórz <xref:System.ServiceModel.Channels.SecurityBindingElement> a do <xref:System.ServiceModel.Channels.CustomBinding>użycia w pliku .</span><span class="sxs-lookup"><span data-stu-id="3fa9e-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2. <span data-ttu-id="3fa9e-133">Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> właściwości, aby zwrócić <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> odwołanie do klasy i ustawić właściwości, jak opisano wcześniej.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="3fa9e-134">Aby kontrolować wykrywanie powtarzania w konfiguracji dla klienta lub usługi</span><span class="sxs-lookup"><span data-stu-id="3fa9e-134">To control replay detection in configuration for the client or service</span></span>  
  
1. <span data-ttu-id="3fa9e-135">Utwórz [ \<>niestandardowego. ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="3fa9e-135">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2. <span data-ttu-id="3fa9e-136">Utwórz `<security>` element.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-136">Create a `<security>` element.</span></span>  
  
3. <span data-ttu-id="3fa9e-137">Utwórz [ \<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) lub [ \<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="3fa9e-137">Create a [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4. <span data-ttu-id="3fa9e-138">Ustaw następujące wartości atrybutów, `detectReplays`odpowiednio: `replayWindow`, `replayCacheSize` `maxClockSkew`, , i .</span><span class="sxs-lookup"><span data-stu-id="3fa9e-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="3fa9e-139">Poniższy przykład ustawia atrybuty `<localServiceSettings>` zarówno `<localClientSettings>` a, jak i elementu:</span><span class="sxs-lookup"><span data-stu-id="3fa9e-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="3fa9e-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fa9e-140">Example</span></span>  
 <span data-ttu-id="3fa9e-141">Poniższy przykład <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> tworzy <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> przy użyciu metody i ustawia właściwości powtarzania powiązania.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="3fa9e-142">Zakres powtórki: tylko zabezpieczenia wiadomości</span><span class="sxs-lookup"><span data-stu-id="3fa9e-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="3fa9e-143">Należy zauważyć, że poniższe procedury dotyczą tylko trybu zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="3fa9e-144">W przypadku transportu i transportu z trybami poświadczeń wiadomości mechanizmy transportu wykrywają powtórki.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="3fa9e-145">Bezpieczne notatki do konwersacji</span><span class="sxs-lookup"><span data-stu-id="3fa9e-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="3fa9e-146">W przypadku powiązań, które umożliwiają bezpieczne konwersacje, można dostosować te ustawienia zarówno dla kanału aplikacji, jak i dla powiązania boottrap bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="3fa9e-147">Na przykład można wyłączyć powtórki dla kanału aplikacji, ale włączyć je dla kanału bootstrap, który ustanawia bezpieczną konwersację.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="3fa9e-148">Jeśli nie używasz bezpiecznych sesji konwersacji, wykrywanie powtarzania nie gwarantuje wykrywania powtórek w scenariuszach farmy serwerów i po odtwoniu procesu.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="3fa9e-149">Dotyczy to następujących powiązań dostarczonych przez system:</span><span class="sxs-lookup"><span data-stu-id="3fa9e-149">This applies to the following system-provided bindings:</span></span>  
  
- <span data-ttu-id="3fa9e-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="3fa9e-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
- <span data-ttu-id="3fa9e-151"><xref:System.ServiceModel.WSHttpBinding>z <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwością `false`ustawioną na .</span><span class="sxs-lookup"><span data-stu-id="3fa9e-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3fa9e-152">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3fa9e-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="3fa9e-153">Następujące obszary nazw są wymagane do skompilowania kodu:</span><span class="sxs-lookup"><span data-stu-id="3fa9e-153">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="3fa9e-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3fa9e-154">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="3fa9e-155">Bezpieczne konwersacje i bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="3fa9e-155">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [<span data-ttu-id="3fa9e-156">\<localClientSettings></span><span class="sxs-lookup"><span data-stu-id="3fa9e-156">\<localClientSettings></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="3fa9e-157">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="3fa9e-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
