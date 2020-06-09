---
title: 'Instrukcje: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: 36cf5ce1aa6e0eef80123ac7008294062d7faf82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598908"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="4ac81-102">Instrukcje: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="4ac81-102">How to: Create a Security Context Token for a Secure Session</span></span>
<span data-ttu-id="4ac81-103">Przy użyciu tokenu stanowego kontekstu zabezpieczeń (SCT) w bezpiecznej sesji, sesja może przetrzymywać odtwarzanie usługi.</span><span class="sxs-lookup"><span data-stu-id="4ac81-103">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="4ac81-104">Na przykład gdy w bezpiecznej sesji jest używany niestanowy SCT, a Internet Information Services (IIS) jest resetowany, dane sesji skojarzone z usługą zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="4ac81-104">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="4ac81-105">Dane sesji obejmują pamięć podręczną tokenów SCT.</span><span class="sxs-lookup"><span data-stu-id="4ac81-105">This session data includes an SCT token cache.</span></span> <span data-ttu-id="4ac81-106">W związku z tym następnym razem, gdy klient wysyła usługę do bezstanowego SCT, zwracany jest błąd, ponieważ nie można pobrać klucza skojarzonego z SCT.</span><span class="sxs-lookup"><span data-stu-id="4ac81-106">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="4ac81-107">Jeśli jednak używany jest stanowy SCT, wówczas klucz skojarzony z SCT jest zawarty w SCT.</span><span class="sxs-lookup"><span data-stu-id="4ac81-107">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="4ac81-108">Ponieważ klucz znajduje się w obrębie SCT i w związku z tym jest zawarty w komunikacie, usługa nie ma na nie wpływ na bezpieczną sesję.</span><span class="sxs-lookup"><span data-stu-id="4ac81-108">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="4ac81-109">Domyślnie Windows Communication Foundation (WCF) używa bezstanowej SCTs w bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="4ac81-109">By default, Windows Communication Foundation (WCF) uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="4ac81-110">W tym temacie szczegółowo opisano sposób używania SCTs stanowej w bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="4ac81-110">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ac81-111">Stanowej SCTs nie można używać w bezpiecznej sesji, która obejmuje kontrakt pochodzący z <xref:System.ServiceModel.Channels.IDuplexChannel> .</span><span class="sxs-lookup"><span data-stu-id="4ac81-111">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ac81-112">W przypadku aplikacji korzystających ze stanowych SCTs w bezpiecznej sesji tożsamość wątku dla usługi musi być kontem użytkownika, które ma skojarzony profil użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4ac81-112">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="4ac81-113">Gdy usługa jest uruchamiana przy użyciu konta, które nie ma profilu użytkownika, takiego jak `Local Service` , może zostać zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="4ac81-113">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ac81-114">Jeśli w systemie Windows XP jest wymagana personifikacja, należy użyć bezpiecznej sesji bez stanowego SCT.</span><span class="sxs-lookup"><span data-stu-id="4ac81-114">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="4ac81-115">Gdy stanowe SCTs są używane z personifikacją, <xref:System.InvalidOperationException> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="4ac81-115">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="4ac81-116">Aby uzyskać więcej informacji, zobacz [scenariusze nieobsługiwane](unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="4ac81-116">For more information, see [Unsupported Scenarios](unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="4ac81-117">Aby użyć SCTs stanowej w bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="4ac81-117">To use stateful SCTs in a secure session</span></span>  
  
- <span data-ttu-id="4ac81-118">Tworzenie niestandardowego powiązania, które określa, że komunikaty protokołu SOAP są chronione za pomocą bezpiecznej sesji, która korzysta ze stanowego SCT.</span><span class="sxs-lookup"><span data-stu-id="4ac81-118">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1. <span data-ttu-id="4ac81-119">Zdefiniuj niestandardowe powiązanie, dodając [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) do pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="4ac81-119">Define a custom binding, by adding a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        </customBinding>
        ```  
  
    2. <span data-ttu-id="4ac81-120">Dodaj [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element podrzędny do elementu [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="4ac81-120">Add a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) child element to the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="4ac81-121">Określ nazwę powiązania przez ustawienie `name` atrybutu na unikatową nazwę w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4ac81-121">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        </binding>
        ```  
  
    3. <span data-ttu-id="4ac81-122">Określ tryb uwierzytelniania dla komunikatów wysyłanych do i z tej usługi przez dodanie [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu podrzędnego do [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="4ac81-122">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="4ac81-123">Określ, że bezpieczna sesja jest używana przez ustawienie `authenticationMode` atrybutu na `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="4ac81-123">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="4ac81-124">Określ, że stanowe SCTs są używane przez ustawienie `requireSecurityContextCancellation` atrybutu na `false` .</span><span class="sxs-lookup"><span data-stu-id="4ac81-124">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">
        </security>
        ```  
  
    4. <span data-ttu-id="4ac81-125">Określ sposób uwierzytelniania klienta podczas ustanawiania bezpiecznej sesji przez dodanie [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) elementu podrzędnego do [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="4ac81-125">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="4ac81-126">Określ sposób uwierzytelniania klienta przez ustawienie `authenticationMode` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4ac81-126">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. <span data-ttu-id="4ac81-127">Określ kodowanie wiadomości poprzez dodanie elementu kodowania, takiego jak [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) .</span><span class="sxs-lookup"><span data-stu-id="4ac81-127">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. <span data-ttu-id="4ac81-128">Określ transport poprzez dodanie elementu transportu, takiego jak [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) .</span><span class="sxs-lookup"><span data-stu-id="4ac81-128">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="4ac81-129">Poniższy przykład kodu używa konfiguracji do określenia niestandardowego powiązania, które mogą być używane przez komunikaty ze stanem SCTs w bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="4ac81-129">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="StatefulSCTSecureSession">  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
          <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        </security>  
        <textMessageEncoding />  
        <httpTransport />  
      </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="4ac81-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ac81-130">Example</span></span>  
 <span data-ttu-id="4ac81-131">Poniższy przykład kodu tworzy niestandardowe powiązanie, które używa <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> trybu uwierzytelniania do uruchamiania bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="4ac81-131">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="4ac81-132">Gdy uwierzytelnianie systemu Windows jest używane w połączeniu z stanem SCT, funkcja WCF nie wypełnia <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwości przy użyciu tożsamości rzeczywistego obiektu wywołującego, ale ustawia właściwość na wartość anonimowe.</span><span class="sxs-lookup"><span data-stu-id="4ac81-132">When Windows authentication is used in combination with a stateful SCT, WCF does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="4ac81-133">Ze względu na to, że zabezpieczenia WCF muszą ponownie utworzyć zawartość kontekstu zabezpieczeń usługi dla każdego żądania z nieprzychodzącego SCT, serwer nie śledzi sesji zabezpieczeń w pamięci.</span><span class="sxs-lookup"><span data-stu-id="4ac81-133">Because WCF security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="4ac81-134">Ponieważ nie można serializować <xref:System.Security.Principal.WindowsIdentity> wystąpienia do SCT, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> Właściwość zwraca tożsamość anonimową.</span><span class="sxs-lookup"><span data-stu-id="4ac81-134">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="4ac81-135">W poniższej konfiguracji przedstawiono takie zachowanie.</span><span class="sxs-lookup"><span data-stu-id="4ac81-135">The following configuration exhibits this behavior.</span></span>  
  
```xml  
<customBinding>  
  <binding name="Cancellation">  
       <textMessageEncoding />  
        <security
            requireSecurityContextCancellation="false">  
              <secureConversationBootstrap />  
        </security>  
    <httpTransport />  
  </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ac81-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ac81-136">See also</span></span>

- [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)
