---
title: 'Instrukcje: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: 4e91580035d4de23ae90cd0d59a08f321ae70a1c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464148"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="6db62-102">Instrukcje: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="6db62-102">How to: Create a Security Context Token for a Secure Session</span></span>
<span data-ttu-id="6db62-103">Za pomocą tokenu kontekstu zabezpieczeń stanowego (SCT) w bezpiecznej sesji, sesja może wytrzymać usługi są poddawane recyklingowi.</span><span class="sxs-lookup"><span data-stu-id="6db62-103">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="6db62-104">Na przykład, gdy bezstanowy SCT jest używany w bezpiecznej sesji i internet information services (IIS) jest resetowany, a następnie dane sesji, który jest skojarzony z usługą jest tracona.</span><span class="sxs-lookup"><span data-stu-id="6db62-104">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="6db62-105">Te dane sesji obejmują pamięć podręczną tokenów SCT.</span><span class="sxs-lookup"><span data-stu-id="6db62-105">This session data includes an SCT token cache.</span></span> <span data-ttu-id="6db62-106">Tak więc następnym razem, gdy klient wysyła usługę bezstanowy SCT, zwracany jest błąd, ponieważ nie można pobrać klucza skojarzonego z SCT.</span><span class="sxs-lookup"><span data-stu-id="6db62-106">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="6db62-107">Jeśli jednak używany jest stanowy SCT, klucz, który jest skojarzony z SCT jest zawarty w SCT.</span><span class="sxs-lookup"><span data-stu-id="6db62-107">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="6db62-108">Ponieważ klucz jest zawarty w SCT i w związku z tym zawarte w wiadomości, bezpiecznej sesji nie ma wpływu na usługi są poddawane recyklingowi.</span><span class="sxs-lookup"><span data-stu-id="6db62-108">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="6db62-109">Domyślnie Windows Communication Foundation (WCF) używa bezstanowych SCT w bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="6db62-109">By default, Windows Communication Foundation (WCF) uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="6db62-110">W tym temacie szczegółowo opisano, jak używać stanowych SCT w bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="6db62-110">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6db62-111">Stateful SCTs nie mogą być używane w bezpiecznej sesji, która obejmuje umowy, która pochodzi z <xref:System.ServiceModel.Channels.IDuplexChannel>.</span><span class="sxs-lookup"><span data-stu-id="6db62-111">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6db62-112">W przypadku aplikacji, które używają stanowych SCT w bezpiecznej sesji, tożsamość wątku dla usługi musi być kontem użytkownika, które ma skojarzony profil użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6db62-112">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="6db62-113">Gdy usługa jest uruchamiana na koncie, które nie `Local Service`ma profilu użytkownika, na przykład , może zostać zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6db62-113">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6db62-114">Gdy personifikacja jest wymagana w systemie Windows XP, należy użyć bezpiecznej sesji bez stanowego SCT.</span><span class="sxs-lookup"><span data-stu-id="6db62-114">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="6db62-115">Gdy stanowe SCTs są używane <xref:System.InvalidOperationException> z personifikacji, jest generowany.</span><span class="sxs-lookup"><span data-stu-id="6db62-115">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="6db62-116">Aby uzyskać więcej informacji, zobacz [Nieobsługiwały scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="6db62-116">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="6db62-117">Aby użyć stanowych sct w bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="6db62-117">To use stateful SCTs in a secure session</span></span>  
  
- <span data-ttu-id="6db62-118">Utwórz niestandardowe powiązanie, które określa, że wiadomości PROTOKOŁU SOAP są chronione przez bezpieczną sesję, która używa stanowego SCT.</span><span class="sxs-lookup"><span data-stu-id="6db62-118">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1. <span data-ttu-id="6db62-119">Zdefiniuj niestandardowe powiązanie, dodając [ \<niestandardowy>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="6db62-119">Define a custom binding, by adding a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        </customBinding>
        ```  
  
    2. <span data-ttu-id="6db62-120">Dodaj [ \<element](../../configure-apps/file-schema/wcf/bindings.md) podrzędny wiązania>do [ \<niestandardowego>. ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="6db62-120">Add a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="6db62-121">Określ nazwę powiązania, `name` ustawiając atrybut na unikatową nazwę w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="6db62-121">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        </binding>
        ```  
  
    3. <span data-ttu-id="6db62-122">Określ tryb uwierzytelniania wiadomości wysyłanych do i z tej usługi, dodając [ \<element podrzędny>zabezpieczeń](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) do [ \<niestandardowego>. ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="6db62-122">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="6db62-123">Określ, że bezpieczna sesja `authenticationMode` jest `SecureConversation`używana, ustawiając atrybut .</span><span class="sxs-lookup"><span data-stu-id="6db62-123">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="6db62-124">Określ, że stany SC są `requireSecurityContextCancellation` używane `false`przez ustawienie atrybutu .</span><span class="sxs-lookup"><span data-stu-id="6db62-124">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">
        </security>
        ```  
  
    4. <span data-ttu-id="6db62-125">Określ sposób uwierzytelniania klienta podczas ustanawiania bezpiecznej sesji, dodając [ \<element podrzędny secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) do [ \<>zabezpieczeń ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="6db62-125">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="6db62-126">Określ sposób uwierzytelniania klienta, `authenticationMode` ustawiając atrybut.</span><span class="sxs-lookup"><span data-stu-id="6db62-126">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. <span data-ttu-id="6db62-127">Określ kodowanie wiadomości, dodając element kodowania, taki jak [ \<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="6db62-127">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. <span data-ttu-id="6db62-128">Określ transport, dodając element transportu, taki jak [ \<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="6db62-128">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="6db62-129">Poniższy przykład kodu używa konfiguracji, aby określić niestandardowe powiązanie, którego wiadomości mogą używać ze stanowymi sct w bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="6db62-129">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="6db62-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="6db62-130">Example</span></span>  
 <span data-ttu-id="6db62-131">Poniższy przykład kodu tworzy niestandardowe <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> powiązanie, które używa trybu uwierzytelniania do uruchamiania bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="6db62-131">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="6db62-132">Gdy uwierzytelnianie systemu Windows jest używany w połączeniu ze stanowym SCT, WCF nie wypełnia <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwość z tożsamością rzeczywistego obiektu wywołującego, ale zamiast tego ustawia właściwość na anonimową.</span><span class="sxs-lookup"><span data-stu-id="6db62-132">When Windows authentication is used in combination with a stateful SCT, WCF does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="6db62-133">Ponieważ zabezpieczenia WCF musi ponownie utworzyć zawartość kontekstu zabezpieczeń usługi dla każdego żądania z przychodzącego SCT, serwer nie śledzi sesji zabezpieczeń w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6db62-133">Because WCF security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="6db62-134">Ponieważ nie można serializować <xref:System.Security.Principal.WindowsIdentity> wystąpienia w SCT, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwość zwraca anonimową tożsamość.</span><span class="sxs-lookup"><span data-stu-id="6db62-134">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="6db62-135">Następująca konfiguracja wykazuje to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="6db62-135">The following configuration exhibits this behavior.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6db62-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6db62-136">See also</span></span>

- [<span data-ttu-id="6db62-137">\<>niestandardowe</span><span class="sxs-lookup"><span data-stu-id="6db62-137">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
