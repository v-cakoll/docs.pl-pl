---
title: <message> dla <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 5a4a4e8b645ee2c607988ac3031af537c93ca8c0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736760"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="8a789-102">\<komunikat > \<ow Msmqbinding ></span><span class="sxs-lookup"><span data-stu-id="8a789-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="8a789-103">Definiuje ustawienia zabezpieczeń wiadomości protokołu SOAP dla tego powiązania `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="8a789-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

<span data-ttu-id="8a789-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="8a789-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8a789-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="8a789-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8a789-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="8a789-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="8a789-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Telemsmqbinding**](netmsmqbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="8a789-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="8a789-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="8a789-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="8a789-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpieczeń**](security-of-netmsmqbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="8a789-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)</span></span>\
<span data-ttu-id="8a789-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<komunikat >**</span><span class="sxs-lookup"><span data-stu-id="8a789-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="8a789-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a789-111">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="8a789-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8a789-112">Attributes and Elements</span></span>

<span data-ttu-id="8a789-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8a789-113">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8a789-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8a789-114">Attributes</span></span>

|<span data-ttu-id="8a789-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8a789-115">Attribute</span></span>|<span data-ttu-id="8a789-116">Opis</span><span class="sxs-lookup"><span data-stu-id="8a789-116">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="8a789-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="8a789-117">algorithmSuite</span></span>|<span data-ttu-id="8a789-118">Ustawia szyfrowanie komunikatów i algorytmy zawijania kluczy, które są używane do uzyskania zabezpieczeń opartych na komunikatach wysyłanych za pośrednictwem transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="8a789-118">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="8a789-119">Wartość domyślna to `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="8a789-119">The default value is `Aes256`.</span></span> <span data-ttu-id="8a789-120">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="8a789-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="8a789-121">Powiązania ClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="8a789-121">clientCredentialType</span></span>|<span data-ttu-id="8a789-122">Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta dla wiadomości wysyłanych za pośrednictwem transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="8a789-122">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="8a789-123">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="8a789-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8a789-124">-Brak: umożliwia to usłudze współpracującie z anonimowymi klientami.</span><span class="sxs-lookup"><span data-stu-id="8a789-124">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="8a789-125">Żadna usługa ani klient nie wymagają podania poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="8a789-125">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="8a789-126">-Windows: umożliwia to wymianę protokołu SOAP w ramach uwierzytelnionego kontekstu poświadczeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8a789-126">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="8a789-127">Jest to zawsze wykonywane uwierzytelnianie oparte na protokole Kerberos.</span><span class="sxs-lookup"><span data-stu-id="8a789-127">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="8a789-128">-UserName: umożliwia usłudze wymaganie uwierzytelnienia klienta przy użyciu poświadczeń nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8a789-128">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="8a789-129">Poświadczenie w tym przypadku należy określić przy użyciu zachowania `clientCredentials` **Przestroga:** Windows Communication Foundation (WCF) nie obsługuje wysyłania skrótu hasła ani wyprowadzania kluczy przy użyciu hasła i używania tych kluczy do zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8a789-129">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="8a789-130">W związku z tym WCF wymusza, aby program Exchange był zabezpieczony przy użyciu poświadczeń nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8a789-130">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="8a789-131">Ten tryb wymaga, aby certyfikat usługi był określony po stronie klienta przy użyciu `clientCredential` zachowanie i `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="8a789-131">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="8a789-132">-Certificate: umożliwia usłudze wymaganie uwierzytelniania klienta przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="8a789-132">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="8a789-133">Poświadczenia klienta w tym przypadku należy określić przy użyciu zachowania `clientCredentials`.</span><span class="sxs-lookup"><span data-stu-id="8a789-133">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="8a789-134">Poświadczenia usługi w tym przypadku należy określić przy użyciu zachowania `clientCredentials`, określając `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="8a789-134">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="8a789-135">-CardSpace: umożliwia usłudze wymaganie uwierzytelniania klienta przy użyciu programu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="8a789-135">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="8a789-136">`serviceCertificate` musi być inicjowana w zachowaniu `clientCredential`.</span><span class="sxs-lookup"><span data-stu-id="8a789-136">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="8a789-137">Wartość domyślna to `Windows`.</span><span class="sxs-lookup"><span data-stu-id="8a789-137">The default value is `Windows`.</span></span> <span data-ttu-id="8a789-138">Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="8a789-138">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8a789-139">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8a789-139">Child Elements</span></span>

<span data-ttu-id="8a789-140">Brak</span><span class="sxs-lookup"><span data-stu-id="8a789-140">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8a789-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8a789-141">Parent Elements</span></span>

|<span data-ttu-id="8a789-142">Element</span><span class="sxs-lookup"><span data-stu-id="8a789-142">Element</span></span>|<span data-ttu-id="8a789-143">Opis</span><span class="sxs-lookup"><span data-stu-id="8a789-143">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8a789-144">> zabezpieczeń \<</span><span class="sxs-lookup"><span data-stu-id="8a789-144">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="8a789-145">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="8a789-145">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="8a789-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a789-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="8a789-147">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="8a789-147">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="8a789-148">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="8a789-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8a789-149">Powiązania</span><span class="sxs-lookup"><span data-stu-id="8a789-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8a789-150">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="8a789-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8a789-151">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="8a789-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="8a789-152">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="8a789-152">\<binding></span></span>](bindings.md)
