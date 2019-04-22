---
title: <message> dla <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: c623b7daf1e91c9c1800b9653525cd51b1087506
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58890569"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="8ac6b-102">\<komunikat > z \<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="8ac6b-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="8ac6b-103">Definiuje ustawienia zabezpieczeń wiadomości protokołu SOAP w tym `netMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

```xml
<system.ServiceModel>
  <bindings>
    <netMsmqBinding>
      <binding>
        <security>
          <message>
```

## <a name="syntax"></a><span data-ttu-id="8ac6b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ac6b-104">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="8ac6b-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8ac6b-105">Attributes and Elements</span></span>

<span data-ttu-id="8ac6b-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8ac6b-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8ac6b-107">Attributes</span></span>

|<span data-ttu-id="8ac6b-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8ac6b-108">Attribute</span></span>|<span data-ttu-id="8ac6b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8ac6b-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="8ac6b-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="8ac6b-110">algorithmSuite</span></span>|<span data-ttu-id="8ac6b-111">Ustawia komunikat algorytmów szyfrowania i klucz wrap, które są używane do uzyskania zabezpieczenia oparte na komunikatu dla komunikatów wysyłanych za pośrednictwem transportu MSMQ.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-111">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="8ac6b-112">Wartość domyślna to `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-112">The default value is `Aes256`.</span></span> <span data-ttu-id="8ac6b-113">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="8ac6b-114">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="8ac6b-114">clientCredentialType</span></span>|<span data-ttu-id="8ac6b-115">Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta dla wiadomości wysłanych przez usługę transportową MSMQ.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-115">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="8ac6b-116">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="8ac6b-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8ac6b-117">-Brak: Dzięki usłudze na współdziałanie z anonimowych klientów.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-117">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="8ac6b-118">Usługa ani klient wymaga poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-118">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="8ac6b-119">-Windows: Dzięki temu wymiany protokołu SOAP i znajdować się w kontekście uwierzytelnionych poświadczeń Windows.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-119">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="8ac6b-120">To jest zawsze przeprowadza uwierzytelnianie za pomocą protokołu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-120">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="8ac6b-121">— Nazwa użytkownika: Dzięki temu usługi wymagać który uwierzytelnienia klienta przy użyciu poświadczeń UserName.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-121">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="8ac6b-122">Poświadczenia w takim przypadku należy także określić przy użyciu `clientCredentials` zachowanie **Uwaga:**  Windows Communication Foundation (WCF) nie obsługuje wysyłanie skrótu hasła lub wyprowadzanie kluczy przy użyciu hasła i rozpoczęcie używania te klucze dla zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-122">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="8ac6b-123">Usługi WCF wymusza w związku z tym, że programu exchange jest zabezpieczone, korzystając z poświadczeń UserName.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-123">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="8ac6b-124">Ten tryb wymaga określenia certyfikatu usługi na po stronie klienta za pomocą `clientCredential` zachowanie i `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-124">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="8ac6b-125">-Certyfikat: Dzięki temu usługi wymagać który uwierzytelnienia klienta za pomocą certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-125">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="8ac6b-126">Poświadczeń klienta w tym przypadku musi być określona za pomocą `clientCredentials` zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-126">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="8ac6b-127">Poświadczenia usługi w tym przypadku należy także określić przy użyciu `clientCredentials` zachowanie, określając `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-127">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="8ac6b-128">-CardSpace: Dzięki temu usługi wymagać, za pomocą CardSpace uwierzytelnienia klienta.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-128">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="8ac6b-129">`serviceCertificate` Musi być obsługiwana w `clientCredential` zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-129">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="8ac6b-130">Wartość domyślna to `Windows`.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-130">The default value is `Windows`.</span></span> <span data-ttu-id="8ac6b-131">Ten atrybut jest typu <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-131">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8ac6b-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8ac6b-132">Child Elements</span></span>

<span data-ttu-id="8ac6b-133">Brak</span><span class="sxs-lookup"><span data-stu-id="8ac6b-133">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8ac6b-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8ac6b-134">Parent Elements</span></span>

|<span data-ttu-id="8ac6b-135">Element</span><span class="sxs-lookup"><span data-stu-id="8ac6b-135">Element</span></span>|<span data-ttu-id="8ac6b-136">Opis</span><span class="sxs-lookup"><span data-stu-id="8ac6b-136">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8ac6b-137">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="8ac6b-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="8ac6b-138">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="8ac6b-138">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="8ac6b-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ac6b-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="8ac6b-140">Kolejki programu WCF</span><span class="sxs-lookup"><span data-stu-id="8ac6b-140">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="8ac6b-141">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="8ac6b-141">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8ac6b-142">Powiązania</span><span class="sxs-lookup"><span data-stu-id="8ac6b-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="8ac6b-143">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="8ac6b-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8ac6b-144">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="8ac6b-144">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="8ac6b-145">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="8ac6b-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
