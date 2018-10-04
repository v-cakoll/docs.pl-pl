---
title: '&lt;message&gt; w &lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 124d53ae24b627c35863fda4cd8f404057978f1e
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48579088"
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="62335-102">&lt;message&gt; w &lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="62335-102">&lt;message&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="62335-103">Definiuje ustawienia zabezpieczeń wiadomości protokołu SOAP w tym `netMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="62335-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>  
  
 <span data-ttu-id="62335-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="62335-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="62335-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="62335-105">\<bindings></span></span>  
<span data-ttu-id="62335-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="62335-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="62335-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="62335-107">\<binding></span></span>  
<span data-ttu-id="62335-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="62335-108">\<security></span></span>  
<span data-ttu-id="62335-109">\<message></span><span class="sxs-lookup"><span data-stu-id="62335-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62335-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="62335-110">Syntax</span></span>  
  
```xml  
<netMsmqBinding>  
    <binding>  
      <security>  
         <message   
                      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
    </security>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62335-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="62335-111">Attributes and Elements</span></span>  
 <span data-ttu-id="62335-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="62335-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62335-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="62335-113">Attributes</span></span>  
  
|<span data-ttu-id="62335-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="62335-114">Attribute</span></span>|<span data-ttu-id="62335-115">Opis</span><span class="sxs-lookup"><span data-stu-id="62335-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62335-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="62335-116">algorithmSuite</span></span>|<span data-ttu-id="62335-117">Ustawia komunikat algorytmów szyfrowania i klucz wrap, które są używane do uzyskania zabezpieczenia oparte na komunikatu dla komunikatów wysyłanych za pośrednictwem transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="62335-117">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="62335-118">Wartość domyślna to `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="62335-118">The default value is `Aes256`.</span></span> <span data-ttu-id="62335-119">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="62335-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|  
|<span data-ttu-id="62335-120">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="62335-120">clientCredentialType</span></span>|<span data-ttu-id="62335-121">Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta dla wiadomości wysłanych przez usługę transportową MSMQ.</span><span class="sxs-lookup"><span data-stu-id="62335-121">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="62335-122">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="62335-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="62335-123">-Brak: Dzięki usłudze na współdziałanie z anonimowych klientów.</span><span class="sxs-lookup"><span data-stu-id="62335-123">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="62335-124">Usługa ani klient wymaga poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="62335-124">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="62335-125">-Windows: Umożliwia wymianę SOAP się być pod kontekst uwierzytelniania poświadczeń Windows.</span><span class="sxs-lookup"><span data-stu-id="62335-125">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="62335-126">To jest zawsze przeprowadza uwierzytelnianie za pomocą protokołu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="62335-126">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="62335-127">-UserName: Włącza usługę wymagać który uwierzytelnienia klienta przy użyciu poświadczeń UserName.</span><span class="sxs-lookup"><span data-stu-id="62335-127">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="62335-128">Poświadczenia w takim przypadku należy także określić przy użyciu `clientCredentials` zachowanie **Przestroga:** Windows Communication Foundation (WCF) nie obsługuje wysyłanie hasła szyfrowane lub wyprowadzanie kluczy przy użyciu hasła i przy użyciu tych kluczy dla zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="62335-128">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="62335-129">Usługi WCF wymusza w związku z tym, że programu exchange jest zabezpieczone, korzystając z poświadczeń UserName.</span><span class="sxs-lookup"><span data-stu-id="62335-129">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="62335-130">Ten tryb wymaga określenia certyfikatu usługi na po stronie klienta za pomocą `clientCredential` zachowanie i `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="62335-130">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="62335-131">-Certyfikat: Włącza usługę wymagać który uwierzytelnienia klienta za pomocą certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="62335-131">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="62335-132">Poświadczeń klienta w tym przypadku musi być określona za pomocą `clientCredentials` zachowanie.</span><span class="sxs-lookup"><span data-stu-id="62335-132">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="62335-133">Poświadczenia usługi w tym przypadku należy także określić przy użyciu `clientCredentials` zachowanie, określając `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="62335-133">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="62335-134">-CardSpace: Dzięki temu usługi wymagać, za pomocą CardSpace uwierzytelnienia klienta.</span><span class="sxs-lookup"><span data-stu-id="62335-134">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="62335-135">`serviceCertiifcate` Musi być obsługiwana w `clientCredential` zachowanie.</span><span class="sxs-lookup"><span data-stu-id="62335-135">The `serviceCertiifcate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="62335-136">Wartość domyślna to `Windows`.</span><span class="sxs-lookup"><span data-stu-id="62335-136">The default value is `Windows`.</span></span> <span data-ttu-id="62335-137">Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="62335-137">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62335-138">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="62335-138">Child Elements</span></span>  
 <span data-ttu-id="62335-139">Brak</span><span class="sxs-lookup"><span data-stu-id="62335-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62335-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="62335-140">Parent Elements</span></span>  
  
|<span data-ttu-id="62335-141">Element</span><span class="sxs-lookup"><span data-stu-id="62335-141">Element</span></span>|<span data-ttu-id="62335-142">Opis</span><span class="sxs-lookup"><span data-stu-id="62335-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62335-143">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="62335-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="62335-144">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="62335-144">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62335-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62335-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq>  
 [<span data-ttu-id="62335-146">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="62335-146">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="62335-147">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="62335-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="62335-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="62335-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="62335-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="62335-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="62335-150">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="62335-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="62335-151">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="62335-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
