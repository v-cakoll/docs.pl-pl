---
title: '&lt;message&gt; w &lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: b636a22fe7c6bcfae5b8f81c1566ea39c9f8ced5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683745"
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="ad5a6-102">&lt;message&gt; w &lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="ad5a6-102">&lt;message&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="ad5a6-103">Definiuje ustawienia zabezpieczeń wiadomości protokołu SOAP w tym `netMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>  
  
 <span data-ttu-id="ad5a6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ad5a6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ad5a6-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="ad5a6-105">\<bindings></span></span>  
<span data-ttu-id="ad5a6-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="ad5a6-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="ad5a6-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="ad5a6-107">\<binding></span></span>  
<span data-ttu-id="ad5a6-108">\<security></span><span class="sxs-lookup"><span data-stu-id="ad5a6-108">\<security></span></span>  
<span data-ttu-id="ad5a6-109">\<message></span><span class="sxs-lookup"><span data-stu-id="ad5a6-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad5a6-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad5a6-110">Syntax</span></span>  
  
```xml  
<netMsmqBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
    </security>
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad5a6-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ad5a6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ad5a6-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad5a6-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ad5a6-113">Attributes</span></span>  
  
|<span data-ttu-id="ad5a6-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ad5a6-114">Attribute</span></span>|<span data-ttu-id="ad5a6-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ad5a6-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad5a6-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="ad5a6-116">algorithmSuite</span></span>|<span data-ttu-id="ad5a6-117">Ustawia komunikat algorytmów szyfrowania i klucz wrap, które są używane do uzyskania zabezpieczenia oparte na komunikatu dla komunikatów wysyłanych za pośrednictwem transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-117">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="ad5a6-118">Wartość domyślna to `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-118">The default value is `Aes256`.</span></span> <span data-ttu-id="ad5a6-119">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|  
|<span data-ttu-id="ad5a6-120">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="ad5a6-120">clientCredentialType</span></span>|<span data-ttu-id="ad5a6-121">Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta dla wiadomości wysłanych przez usługę transportową MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-121">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="ad5a6-122">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="ad5a6-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ad5a6-123">-Brak: Dzięki usłudze na współdziałanie z anonimowych klientów.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-123">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="ad5a6-124">Usługa ani klient wymaga poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-124">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="ad5a6-125">-Windows: Dzięki temu wymiany protokołu SOAP i znajdować się w kontekście uwierzytelnionych poświadczeń Windows.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-125">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="ad5a6-126">To jest zawsze przeprowadza uwierzytelnianie za pomocą protokołu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-126">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="ad5a6-127">— Nazwa użytkownika: Dzięki temu usługi wymagać który uwierzytelnienia klienta przy użyciu poświadczeń UserName.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-127">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="ad5a6-128">Poświadczenia w takim przypadku należy także określić przy użyciu `clientCredentials` zachowanie **Uwaga:**  Windows Communication Foundation (WCF) nie obsługuje wysyłanie skrótu hasła lub wyprowadzanie kluczy przy użyciu hasła i rozpoczęcie używania te klucze dla zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-128">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="ad5a6-129">Usługi WCF wymusza w związku z tym, że programu exchange jest zabezpieczone, korzystając z poświadczeń UserName.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-129">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="ad5a6-130">Ten tryb wymaga określenia certyfikatu usługi na po stronie klienta za pomocą `clientCredential` zachowanie i `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-130">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="ad5a6-131">-Certyfikat: Dzięki temu usługi wymagać który uwierzytelnienia klienta za pomocą certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-131">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="ad5a6-132">Poświadczeń klienta w tym przypadku musi być określona za pomocą `clientCredentials` zachowanie.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-132">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="ad5a6-133">Poświadczenia usługi w tym przypadku należy także określić przy użyciu `clientCredentials` zachowanie, określając `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-133">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="ad5a6-134">-CardSpace: Dzięki temu usługi wymagać, za pomocą CardSpace uwierzytelnienia klienta.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-134">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="ad5a6-135">`serviceCertiifcate` Musi być obsługiwana w `clientCredential` zachowanie.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-135">The `serviceCertiifcate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="ad5a6-136">Wartość domyślna to `Windows`.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-136">The default value is `Windows`.</span></span> <span data-ttu-id="ad5a6-137">Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-137">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad5a6-138">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ad5a6-138">Child Elements</span></span>  
 <span data-ttu-id="ad5a6-139">Brak</span><span class="sxs-lookup"><span data-stu-id="ad5a6-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad5a6-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ad5a6-140">Parent Elements</span></span>  
  
|<span data-ttu-id="ad5a6-141">Element</span><span class="sxs-lookup"><span data-stu-id="ad5a6-141">Element</span></span>|<span data-ttu-id="ad5a6-142">Opis</span><span class="sxs-lookup"><span data-stu-id="ad5a6-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad5a6-143">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="ad5a6-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="ad5a6-144">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="ad5a6-144">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad5a6-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad5a6-145">See also</span></span>
- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="ad5a6-146">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="ad5a6-146">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="ad5a6-147">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="ad5a6-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ad5a6-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ad5a6-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="ad5a6-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="ad5a6-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ad5a6-150">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="ad5a6-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ad5a6-151">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="ad5a6-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
