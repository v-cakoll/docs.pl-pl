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
ms.openlocfilehash: 8a5f693b98d1437ccf0c8a373fcb11aa96ee6191
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653583"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="fedcd-102">Instrukcje: Włączanie wykrywania powtarzania komunikatu</span><span class="sxs-lookup"><span data-stu-id="fedcd-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="fedcd-103">Atak przez powtarzanie występuje, gdy osoba atakująca kopiuje strumienia komunikatów między dwiema stronami i odtwarza strumienia do jednego lub więcej stron.</span><span class="sxs-lookup"><span data-stu-id="fedcd-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="fedcd-104">Chyba że skorygowane, komputery, które podlegają ataku przetworzy strumienia jako wiarygodnego wiadomości, co w zakresie zły konsekwencje, takie jak nadmiarowe zamówienia elementu.</span><span class="sxs-lookup"><span data-stu-id="fedcd-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="fedcd-105">Aby uzyskać więcej informacji na temat wykrywania powtarzania komunikatu zobacz [wykrywania powtarzania komunikatu](https://go.microsoft.com/fwlink/?LinkId=88536).</span><span class="sxs-lookup"><span data-stu-id="fedcd-105">For more information about message replay detection, see [Message Replay Detection](https://go.microsoft.com/fwlink/?LinkId=88536).</span></span>  
  
 <span data-ttu-id="fedcd-106">Poniższa procedura demonstruje różne właściwości, które służą do kontrolowania wykrywania powtarzania przy użyciu usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="fedcd-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="fedcd-107">Aby kontrolować wykrywania powtarzania na kliencie przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="fedcd-107">To control replay detection on the client using code</span></span>  
  
1.  <span data-ttu-id="fedcd-108">Tworzenie <xref:System.ServiceModel.Channels.SecurityBindingElement> do użycia w <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="fedcd-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="fedcd-109">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="fedcd-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="fedcd-110">W poniższym przykładzie użyto <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> utworzone za pomocą <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> z <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="fedcd-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2.  <span data-ttu-id="fedcd-111">Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> właściwość, aby zwrócić odwołanie do <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> klasy i skonfiguruj następujące właściwości zgodnie z potrzebami:</span><span class="sxs-lookup"><span data-stu-id="fedcd-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1.  <span data-ttu-id="fedcd-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="fedcd-112">`DetectReplay`.</span></span> <span data-ttu-id="fedcd-113">Wartość logiczna.</span><span class="sxs-lookup"><span data-stu-id="fedcd-113">A Boolean value.</span></span> <span data-ttu-id="fedcd-114">To decyduje, czy klient powinien wykryć odtworzenie z serwera.</span><span class="sxs-lookup"><span data-stu-id="fedcd-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="fedcd-115">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="fedcd-115">The default is `true`.</span></span>  
  
    2.  <span data-ttu-id="fedcd-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="fedcd-116">`MaxClockSkew`.</span></span> <span data-ttu-id="fedcd-117">A <xref:System.TimeSpan> wartość.</span><span class="sxs-lookup"><span data-stu-id="fedcd-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="fedcd-118">Określa, ile czasu przesunięcia czasowego, mechanizm powtórzeń może tolerować między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="fedcd-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="fedcd-119">Mechanizm zabezpieczeń sprawdza, czy czas sygnaturę wysyłane i określa, czy wysłano zbyt daleko w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="fedcd-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="fedcd-120">Wartość domyślna to 5 minut.</span><span class="sxs-lookup"><span data-stu-id="fedcd-120">The default is 5 minutes.</span></span>  
  
    3.  <span data-ttu-id="fedcd-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="fedcd-121">`ReplayWindow`.</span></span> <span data-ttu-id="fedcd-122">A `TimeSpan` wartość.</span><span class="sxs-lookup"><span data-stu-id="fedcd-122">A `TimeSpan` value.</span></span> <span data-ttu-id="fedcd-123">To decyduje, jak długo komunikat może na żywo w sieci po serwer wysyła on (za pośrednictwem pośredników) przed dotarciem do klienta.</span><span class="sxs-lookup"><span data-stu-id="fedcd-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="fedcd-124">Klient śledzi podpisy komunikaty wysyłane w ramach najnowsze `ReplayWindow` na potrzeby wykrywania powtarzania.</span><span class="sxs-lookup"><span data-stu-id="fedcd-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4.  <span data-ttu-id="fedcd-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="fedcd-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="fedcd-126">Wartość całkowitą.</span><span class="sxs-lookup"><span data-stu-id="fedcd-126">An integer value.</span></span> <span data-ttu-id="fedcd-127">Klient przechowuje podpisów wiadomości w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="fedcd-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="fedcd-128">To ustawienie określa, ile podpisów, które mogą być przechowywane w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="fedcd-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="fedcd-129">Jeśli liczba wiadomości wysyłanych w ramach ostatniego okna powtarzania osiągnie limit pamięci podręcznej, nowe wiadomości są odrzucane, najstarsze podpisów pamięci podręcznej aż limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="fedcd-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="fedcd-130">Wartość domyślna wynosi 500 000.</span><span class="sxs-lookup"><span data-stu-id="fedcd-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="fedcd-131">Aby kontrolować wykrywania powtarzania w usłudze przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="fedcd-131">To control replay detection on the service using code</span></span>  
  
1.  <span data-ttu-id="fedcd-132">Tworzenie <xref:System.ServiceModel.Channels.SecurityBindingElement> do użycia w <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="fedcd-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2.  <span data-ttu-id="fedcd-133">Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> właściwość, aby zwrócić odwołanie do <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> klasy, a następnie ustaw właściwości, zgodnie z wcześniejszym opisem.</span><span class="sxs-lookup"><span data-stu-id="fedcd-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="fedcd-134">Aby kontrolować wykrywania powtarzania w konfiguracji dla klienta lub usługę</span><span class="sxs-lookup"><span data-stu-id="fedcd-134">To control replay detection in configuration for the client or service</span></span>  
  
1.  <span data-ttu-id="fedcd-135">Tworzenie [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="fedcd-135">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2.  <span data-ttu-id="fedcd-136">Utwórz `<security>` elementu.</span><span class="sxs-lookup"><span data-stu-id="fedcd-136">Create a `<security>` element.</span></span>  
  
3.  <span data-ttu-id="fedcd-137">Tworzenie [ \<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) lub [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="fedcd-137">Create a [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4.  <span data-ttu-id="fedcd-138">Ustaw następujące wartości atrybutów zgodnie z potrzebami: `detectReplays`, `maxClockSkew`, `replayWindow`, i `replayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="fedcd-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="fedcd-139">W poniższym przykładzie ustawiono oba atrybuty `<localServiceSettings>` i `<localClientSettings>` elementu:</span><span class="sxs-lookup"><span data-stu-id="fedcd-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="fedcd-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="fedcd-140">Example</span></span>  
 <span data-ttu-id="fedcd-141">Poniższy przykład tworzy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> przy użyciu <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> metody i zestawy właściwości powtarzania wiązania.</span><span class="sxs-lookup"><span data-stu-id="fedcd-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="fedcd-142">Zakres powtarzania: Tylko zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="fedcd-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="fedcd-143">Należy pamiętać, że poniższe procedury dotyczą tylko trybu zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="fedcd-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="fedcd-144">Transport i Transport z poświadczeniami komunikatu tryby mechanizmy transportu wykryć odtworzenie.</span><span class="sxs-lookup"><span data-stu-id="fedcd-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="fedcd-145">Zabezpieczanie uwagi konwersacji</span><span class="sxs-lookup"><span data-stu-id="fedcd-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="fedcd-146">Dla powiązania, które umożliwiają bezpieczne konwersacje można dostosować te ustawienia, zarówno dla kanału aplikacji, a także dla powiązania uruchamiania bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="fedcd-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="fedcd-147">Na przykład możesz wyłączyć odtworzenie dla kanału aplikacji, ale włączyć je do ładowania początkowego kanału, który ustanawia bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="fedcd-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="fedcd-148">Jeśli nie używasz sesji bezpiecznej konwersacji, wykrywania powtarzania nie gwarantuje wykrywania odtworzenie w scenariuszach z farmami serwera i po ten proces zostanie odtworzony.</span><span class="sxs-lookup"><span data-stu-id="fedcd-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="fedcd-149">Dotyczy to następujących powiązania dostarczane przez system:</span><span class="sxs-lookup"><span data-stu-id="fedcd-149">This applies to the following system-provided bindings:</span></span>  
  
-   <span data-ttu-id="fedcd-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="fedcd-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
-   <span data-ttu-id="fedcd-151"><xref:System.ServiceModel.WSHttpBinding> za pomocą <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwością `false`.</span><span class="sxs-lookup"><span data-stu-id="fedcd-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fedcd-152">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="fedcd-152">Compiling the Code</span></span>  
  
-   <span data-ttu-id="fedcd-153">Następujące przestrzenie nazw są wymagane, aby skompilować kod:</span><span class="sxs-lookup"><span data-stu-id="fedcd-153">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="fedcd-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fedcd-154">See also</span></span>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="fedcd-155">Bezpieczne konwersacje i bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="fedcd-155">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [<span data-ttu-id="fedcd-156">\<localClientSettings></span><span class="sxs-lookup"><span data-stu-id="fedcd-156">\<localClientSettings></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="fedcd-157">Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="fedcd-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
