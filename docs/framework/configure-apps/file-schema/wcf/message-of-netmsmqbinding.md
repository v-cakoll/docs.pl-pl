---
title: <message> dla <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 09d9d4a5d1967afaf9a6ed5756c309e78fee0923
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400254"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="22e0e-102">\<> \<komunikatu usługi msmqbinding ></span><span class="sxs-lookup"><span data-stu-id="22e0e-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="22e0e-103">Definiuje ustawienia zabezpieczeń wiadomości protokołu SOAP dla tego `netMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="22e0e-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

<span data-ttu-id="22e0e-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="22e0e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="22e0e-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="22e0e-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="22e0e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="22e0e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="22e0e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> usługi Msmqbinding**](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="22e0e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="22e0e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="22e0e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="22e0e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="22e0e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)</span></span>\
<span data-ttu-id="22e0e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> komunikatu**</span><span class="sxs-lookup"><span data-stu-id="22e0e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="22e0e-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="22e0e-111">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="22e0e-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="22e0e-112">Attributes and Elements</span></span>

<span data-ttu-id="22e0e-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="22e0e-113">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="22e0e-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="22e0e-114">Attributes</span></span>

|<span data-ttu-id="22e0e-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="22e0e-115">Attribute</span></span>|<span data-ttu-id="22e0e-116">Opis</span><span class="sxs-lookup"><span data-stu-id="22e0e-116">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="22e0e-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="22e0e-117">algorithmSuite</span></span>|<span data-ttu-id="22e0e-118">Ustawia szyfrowanie komunikatów i algorytmy zawijania kluczy, które są używane do uzyskania zabezpieczeń opartych na komunikatach wysyłanych za pośrednictwem transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="22e0e-118">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="22e0e-119">Wartość domyślna to `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="22e0e-119">The default value is `Aes256`.</span></span> <span data-ttu-id="22e0e-120">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="22e0e-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="22e0e-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="22e0e-121">clientCredentialType</span></span>|<span data-ttu-id="22e0e-122">Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta dla wiadomości wysyłanych za pośrednictwem transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="22e0e-122">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="22e0e-123">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="22e0e-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="22e0e-124">Dawaj Dzięki temu usługa może korzystać z anonimowych klientów.</span><span class="sxs-lookup"><span data-stu-id="22e0e-124">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="22e0e-125">Żadna usługa ani klient nie wymagają podania poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="22e0e-125">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="22e0e-126">Systemy Dzięki temu wymiana protokołu SOAP będzie odbywać się w ramach uwierzytelnionego kontekstu poświadczeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="22e0e-126">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="22e0e-127">Jest to zawsze wykonywane uwierzytelnianie oparte na protokole Kerberos.</span><span class="sxs-lookup"><span data-stu-id="22e0e-127">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="22e0e-128">Uż Dzięki temu usługa musi wymagać uwierzytelnienia klienta przy użyciu poświadczeń nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="22e0e-128">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="22e0e-129">Poświadczenie w tym przypadku należy określić przy użyciu `clientCredentials` zachowania **ostrożności:**  Windows Communication Foundation (WCF) nie obsługuje wysyłania skrótu hasła ani wyprowadzania kluczy przy użyciu hasła i używania tych kluczy do zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="22e0e-129">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="22e0e-130">W związku z tym WCF wymusza, aby program Exchange był zabezpieczony przy użyciu poświadczeń nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="22e0e-130">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="22e0e-131">Ten tryb wymaga, aby certyfikat usługi był określony po stronie klienta przy użyciu `clientCredential` zachowań i `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="22e0e-131">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="22e0e-132">Certyfikatu Dzięki temu usługa musi wymagać uwierzytelnienia klienta przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="22e0e-132">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="22e0e-133">Poświadczenia klienta w tym przypadku należy określić przy użyciu `clientCredentials` zachowania.</span><span class="sxs-lookup"><span data-stu-id="22e0e-133">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="22e0e-134">Poświadczenia usługi w tym przypadku należy określić przy użyciu `clientCredentials` zachowania przez `serviceCertificate`określenie.</span><span class="sxs-lookup"><span data-stu-id="22e0e-134">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="22e0e-135">CardSpace Dzięki temu usługa musi wymagać uwierzytelnienia klienta przy użyciu programu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="22e0e-135">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="22e0e-136">W zachowaniu `serviceCertificate` musi być obsługiwana `clientCredential` obsługa administracyjna.</span><span class="sxs-lookup"><span data-stu-id="22e0e-136">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="22e0e-137">Wartość domyślna to `Windows`.</span><span class="sxs-lookup"><span data-stu-id="22e0e-137">The default value is `Windows`.</span></span> <span data-ttu-id="22e0e-138">Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="22e0e-138">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="22e0e-139">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="22e0e-139">Child Elements</span></span>

<span data-ttu-id="22e0e-140">Brak</span><span class="sxs-lookup"><span data-stu-id="22e0e-140">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="22e0e-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="22e0e-141">Parent Elements</span></span>

|<span data-ttu-id="22e0e-142">Element</span><span class="sxs-lookup"><span data-stu-id="22e0e-142">Element</span></span>|<span data-ttu-id="22e0e-143">Opis</span><span class="sxs-lookup"><span data-stu-id="22e0e-143">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="22e0e-144">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="22e0e-144">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="22e0e-145">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="22e0e-145">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="22e0e-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22e0e-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="22e0e-147">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="22e0e-147">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="22e0e-148">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="22e0e-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="22e0e-149">Powiązania</span><span class="sxs-lookup"><span data-stu-id="22e0e-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="22e0e-150">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="22e0e-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="22e0e-151">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="22e0e-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="22e0e-152">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="22e0e-152">\<binding></span></span>](../../../misc/binding.md)
