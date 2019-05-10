---
title: 'Instrukcje: tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: e425db792a2aec562eb0c4f90463eb861eb80f63
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650267"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="ad618-102">Instrukcje: tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="ad618-102">How to: Create a Security Context Token for a Secure Session</span></span>
<span data-ttu-id="ad618-103">Za pomocą tokenu kontekstu zabezpieczeń stanową (SCT) w ramach bezpiecznej sesji, sesja może wytrzymać usługi odtwarzania.</span><span class="sxs-lookup"><span data-stu-id="ad618-103">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="ad618-104">Na przykład gdy bezstanowe SCT jest używany w ramach bezpiecznej sesji i Internet Information Services (IIS) jest resetowany, następnie dane sesji, który jest skojarzony z usługą jest utracone.</span><span class="sxs-lookup"><span data-stu-id="ad618-104">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="ad618-105">Te dane sesji obejmuje pamięci podręcznej SCT tokenu.</span><span class="sxs-lookup"><span data-stu-id="ad618-105">This session data includes an SCT token cache.</span></span> <span data-ttu-id="ad618-106">Tak przy następnym klient wysyła usługi bezstanowej SCT, zwracany jest błąd, ponieważ nie można pobrać klucza, który jest skojarzony z SCT.</span><span class="sxs-lookup"><span data-stu-id="ad618-106">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="ad618-107">Jeśli jednak stanowych SCT jest używany, klucz, który jest skojarzony z SCT jest zawarty w SCT.</span><span class="sxs-lookup"><span data-stu-id="ad618-107">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="ad618-108">Ponieważ klucz jest zawarty w SCT i dlatego zawarte w wiadomości, bezpiecznej sesji nie występuje w usłudze odtwarzania.</span><span class="sxs-lookup"><span data-stu-id="ad618-108">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="ad618-109">Domyślnie program Windows Communication Foundation (WCF) używa SCTs o bezstanowa w ramach bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="ad618-109">By default, Windows Communication Foundation (WCF) uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="ad618-110">W tym temacie przedstawiono sposób użycia SCTs stanowych w ramach bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="ad618-110">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad618-111">Stanowe SCTs nie można używać w ramach bezpiecznej sesji, która obejmuje kontraktu, który pochodzi od klasy <xref:System.ServiceModel.Channels.IDuplexChannel>.</span><span class="sxs-lookup"><span data-stu-id="ad618-111">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad618-112">W przypadku aplikacji korzystających z SCTs stanowych w ramach bezpiecznej sesji tożsamość wątku dla usługi musi być konta użytkownika, który ma profil skojarzone z użytkownikami.</span><span class="sxs-lookup"><span data-stu-id="ad618-112">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="ad618-113">Gdy uruchomiona jest usługa przy użyciu konta, który nie ma profilu użytkownika, takie jak `Local Service`, może być zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ad618-113">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad618-114">Podczas personifikacji jest wymagane w systemie Windows XP, należy użyć bezpiecznej sesji bez SCT stanowych.</span><span class="sxs-lookup"><span data-stu-id="ad618-114">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="ad618-115">Stosowania stanowych SCTs personifikacji, <xref:System.InvalidOperationException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="ad618-115">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="ad618-116">Aby uzyskać więcej informacji, zobacz [nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="ad618-116">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="ad618-117">Aby użyć SCTs stanowych w ramach bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="ad618-117">To use stateful SCTs in a secure session</span></span>  
  
- <span data-ttu-id="ad618-118">Tworzenie niestandardowego powiązania, określający, że komunikaty protokołu SOAP są chronione przez bezpiecznej sesji, która używa SCT stanowych.</span><span class="sxs-lookup"><span data-stu-id="ad618-118">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1. <span data-ttu-id="ad618-119">Definiowanie niestandardowego powiązania, dodając [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="ad618-119">Define a custom binding, by adding a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        ```  
  
    2. <span data-ttu-id="ad618-120">Dodaj [ \<powiązania >](../../../../docs/framework/misc/binding.md) element podrzędny do [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="ad618-120">Add a [\<binding>](../../../../docs/framework/misc/binding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="ad618-121">Określ nazwę powiązania, ustawiając `name` atrybutu unikatową nazwę w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ad618-121">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3. <span data-ttu-id="ad618-122">Określa tryb uwierzytelniania dla wiadomości wysyłanych do i z tej usługi, dodając [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element podrzędny do [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="ad618-122">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="ad618-123">Określ, że bezpiecznej sesji jest używany przez ustawienie `authenticationMode` atrybutu `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="ad618-123">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="ad618-124">Określ, że stanowych SCTs są używane przez ustawienie `requireSecurityContextCancellation` atrybutu `false`.</span><span class="sxs-lookup"><span data-stu-id="ad618-124">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4. <span data-ttu-id="ad618-125">Określ, jak klient jest uwierzytelniany podczas nawiązywania bezpiecznej sesji nawiązaniu przez dodanie [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element podrzędny do [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="ad618-125">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="ad618-126">Określ, jak klient jest uwierzytelniany, ustawiając `authenticationMode` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ad618-126">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. <span data-ttu-id="ad618-127">Określ kodowanie komunikatu przez dodanie elementu kodowania, takich jak [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="ad618-127">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. <span data-ttu-id="ad618-128">Określ transportu, dodając element transportu, takich jak [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="ad618-128">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="ad618-129">Poniższy przykład kodu używa konfiguracji do określenia niestandardowego powiązania, który komunikatów za pomocą SCTs stanowych w ramach bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="ad618-129">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="ad618-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad618-130">Example</span></span>  
 <span data-ttu-id="ad618-131">Poniższy przykład kodu tworzy niestandardowego powiązania, który używa <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> tryb uwierzytelniania uruchomienie bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="ad618-131">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="ad618-132">Podczas uwierzytelniania Windows jest używany w połączeniu z SCT stanowe, usługi WCF nie wypełnia <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwości z funkcją wywołującą rzeczywistej tożsamości użytkownika, ale zamiast tego do nadawania właściwości anonimowych.</span><span class="sxs-lookup"><span data-stu-id="ad618-132">When Windows authentication is used in combination with a stateful SCT, WCF does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="ad618-133">Ponieważ w zabezpieczenia WCF, należy ponownie utworzyć zawartość usługi kontekstu zabezpieczeń dla każdego żądania z przychodzącego SCT, serwer nie zachować informacje o sesji zabezpieczeń w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ad618-133">Because WCF security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="ad618-134">Ponieważ nie jest możliwe do serializacji <xref:System.Security.Principal.WindowsIdentity> wystąpienie do SCT <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwość zwraca Tożsamość anonimowa.</span><span class="sxs-lookup"><span data-stu-id="ad618-134">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="ad618-135">Następująca konfiguracja wykazuje to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="ad618-135">The following configuration exhibits this behavior.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ad618-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad618-136">See also</span></span>

- [<span data-ttu-id="ad618-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ad618-137">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
