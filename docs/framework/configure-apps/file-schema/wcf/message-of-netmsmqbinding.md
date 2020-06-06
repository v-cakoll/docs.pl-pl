---
title: <message> dla <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 5a4a4e8b645ee2c607988ac3031af537c93ca8c0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736760"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="a34d3-102">\<message> dla \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="a34d3-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="a34d3-103">Definiuje ustawienia zabezpieczeń wiadomości protokołu SOAP dla tego `netMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="a34d3-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  

## <a name="syntax"></a><span data-ttu-id="a34d3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a34d3-104">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="a34d3-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a34d3-105">Attributes and Elements</span></span>

<span data-ttu-id="a34d3-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a34d3-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a34d3-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a34d3-107">Attributes</span></span>

|<span data-ttu-id="a34d3-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a34d3-108">Attribute</span></span>|<span data-ttu-id="a34d3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a34d3-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="a34d3-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="a34d3-110">algorithmSuite</span></span>|<span data-ttu-id="a34d3-111">Ustawia szyfrowanie komunikatów i algorytmy zawijania kluczy, które są używane do uzyskania zabezpieczeń opartych na komunikatach wysyłanych za pośrednictwem transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a34d3-111">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="a34d3-112">Wartość domyślna to `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="a34d3-112">The default value is `Aes256`.</span></span> <span data-ttu-id="a34d3-113">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .</span><span class="sxs-lookup"><span data-stu-id="a34d3-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="a34d3-114">Powiązania ClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="a34d3-114">clientCredentialType</span></span>|<span data-ttu-id="a34d3-115">Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta dla wiadomości wysyłanych za pośrednictwem transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a34d3-115">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="a34d3-116">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="a34d3-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a34d3-117">-Brak: umożliwia to usłudze współpracującie z anonimowymi klientami.</span><span class="sxs-lookup"><span data-stu-id="a34d3-117">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="a34d3-118">Żadna usługa ani klient nie wymagają podania poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="a34d3-118">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="a34d3-119">-Windows: umożliwia to wymianę protokołu SOAP w ramach uwierzytelnionego kontekstu poświadczeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a34d3-119">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="a34d3-120">Jest to zawsze wykonywane uwierzytelnianie oparte na protokole Kerberos.</span><span class="sxs-lookup"><span data-stu-id="a34d3-120">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="a34d3-121">-UserName: umożliwia usłudze wymaganie uwierzytelnienia klienta przy użyciu poświadczeń nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a34d3-121">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="a34d3-122">Poświadczenie w tym przypadku należy określić przy użyciu `clientCredentials` zachowania **ostrożności:** Windows Communication Foundation (WCF) nie obsługuje wysyłania skrótu hasła ani wyprowadzania kluczy przy użyciu hasła i używania tych kluczy do zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a34d3-122">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="a34d3-123">W związku z tym WCF wymusza, aby program Exchange był zabezpieczony przy użyciu poświadczeń nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a34d3-123">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="a34d3-124">Ten tryb wymaga, aby certyfikat usługi był określony po stronie klienta przy użyciu `clientCredential` zachowań i `serviceCertificate` .</span><span class="sxs-lookup"><span data-stu-id="a34d3-124">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="a34d3-125">-Certificate: umożliwia usłudze wymaganie uwierzytelniania klienta przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="a34d3-125">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="a34d3-126">Poświadczenia klienta w tym przypadku należy określić przy użyciu `clientCredentials` zachowania.</span><span class="sxs-lookup"><span data-stu-id="a34d3-126">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="a34d3-127">Poświadczenia usługi w tym przypadku należy określić przy użyciu `clientCredentials` zachowania przez określenie `serviceCertificate` .</span><span class="sxs-lookup"><span data-stu-id="a34d3-127">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="a34d3-128">-CardSpace: umożliwia usłudze wymaganie uwierzytelniania klienta przy użyciu programu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="a34d3-128">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="a34d3-129">`serviceCertificate`W zachowaniu musi być obsługiwana obsługa administracyjna `clientCredential` .</span><span class="sxs-lookup"><span data-stu-id="a34d3-129">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="a34d3-130">Wartość domyślna to `Windows`.</span><span class="sxs-lookup"><span data-stu-id="a34d3-130">The default value is `Windows`.</span></span> <span data-ttu-id="a34d3-131">Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="a34d3-131">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a34d3-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a34d3-132">Child Elements</span></span>

<span data-ttu-id="a34d3-133">Brak</span><span class="sxs-lookup"><span data-stu-id="a34d3-133">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a34d3-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a34d3-134">Parent Elements</span></span>

|<span data-ttu-id="a34d3-135">Element</span><span class="sxs-lookup"><span data-stu-id="a34d3-135">Element</span></span>|<span data-ttu-id="a34d3-136">Opis</span><span class="sxs-lookup"><span data-stu-id="a34d3-136">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-netmsmqbinding.md)|<span data-ttu-id="a34d3-137">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="a34d3-137">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="a34d3-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a34d3-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="a34d3-139">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="a34d3-139">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="a34d3-140">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="a34d3-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a34d3-141">Powiązania</span><span class="sxs-lookup"><span data-stu-id="a34d3-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a34d3-142">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="a34d3-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a34d3-143">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="a34d3-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
