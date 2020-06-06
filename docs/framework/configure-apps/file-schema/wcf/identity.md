---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 15c9e38a141fc294c47863b1a932711444ac079a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855152"
---
# \<identity>
<span data-ttu-id="715f6-101">Element Identity pozwala deweloperowi klienta określić w czasie projektowania oczekiwaną tożsamość usługi.</span><span class="sxs-lookup"><span data-stu-id="715f6-101">The identity element allows a client developer to specify at design time the expected identity of the service.</span></span> <span data-ttu-id="715f6-102">W procesie uzgadniania między klientem a usługą infrastruktura Windows Communication Foundation (WCF) zapewni, że tożsamość oczekiwanej usługi jest zgodna z wartościami tego elementu i w ten sposób może być uwierzytelniona.</span><span class="sxs-lookup"><span data-stu-id="715f6-102">In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element, and thus can be authenticated.</span></span> <span data-ttu-id="715f6-103">Aby uzyskać więcej informacji, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="715f6-103">For more information, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<identity>**  
  
## <a name="syntax"></a><span data-ttu-id="715f6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="715f6-104">Syntax</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="String" />
  <certificateReference findValue="String"
                        isChainIncluded="Boolean"
                        storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                        storeLocation="LocalMachine/CurrentUser"
                        X509FindType="Enumeration" />
  <dns value="String" />
  <rsa value="String" />
  <servicePrincipalName value="String" />
  <userPrincipalName value="String" />
</identity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="715f6-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="715f6-105">Attributes and Elements</span></span>  
 <span data-ttu-id="715f6-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="715f6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="715f6-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="715f6-107">Attributes</span></span>  
 <span data-ttu-id="715f6-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="715f6-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="715f6-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="715f6-109">Child Elements</span></span>  
  
|<span data-ttu-id="715f6-110">Element</span><span class="sxs-lookup"><span data-stu-id="715f6-110">Element</span></span>|<span data-ttu-id="715f6-111">Opis</span><span class="sxs-lookup"><span data-stu-id="715f6-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="715f6-112">certyfikat</span><span class="sxs-lookup"><span data-stu-id="715f6-112">certificate</span></span>|<span data-ttu-id="715f6-113">Określa ustawienia certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="715f6-113">Specifies settings of an X.509 certificate.</span></span> <span data-ttu-id="715f6-114">Ten element jest typu <xref:System.ServiceModel.Configuration.CertificateElement> .</span><span class="sxs-lookup"><span data-stu-id="715f6-114">This element is of type <xref:System.ServiceModel.Configuration.CertificateElement>.</span></span> <span data-ttu-id="715f6-115">Zawiera atrybut `encodedValue` , który jest ciągiem, który określa wartość zakodowaną przez ten certyfikat.</span><span class="sxs-lookup"><span data-stu-id="715f6-115">It contains an attribute `encodedValue` that is a string, which specifies the value encoded by this certificate.</span></span>|  
|<span data-ttu-id="715f6-116">certificateReference</span><span class="sxs-lookup"><span data-stu-id="715f6-116">certificateReference</span></span>|<span data-ttu-id="715f6-117">Określa ustawienia dla walidacji certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="715f6-117">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="715f6-118">Ten element jest typu <xref:System.ServiceModel.Configuration.CertificateReferenceElement> .</span><span class="sxs-lookup"><span data-stu-id="715f6-118">This element is of type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span></span>|  
|<span data-ttu-id="715f6-119">dns</span><span class="sxs-lookup"><span data-stu-id="715f6-119">dns</span></span>|<span data-ttu-id="715f6-120">Określa serwer DNS certyfikatu X. 509 używany do uwierzytelniania usługi.</span><span class="sxs-lookup"><span data-stu-id="715f6-120">Specifies the DNS of an X.509 certificate used to authenticate a service.</span></span> <span data-ttu-id="715f6-121">Ten element zawiera atrybut `value` , który jest ciągiem i zawiera rzeczywistą tożsamość.</span><span class="sxs-lookup"><span data-stu-id="715f6-121">This element contains an attribute `value` that is a string, and contains the actual identity.</span></span>|  
|<span data-ttu-id="715f6-122">rsa</span><span class="sxs-lookup"><span data-stu-id="715f6-122">rsa</span></span>|<span data-ttu-id="715f6-123">Określa wartość pola RSA certyfikatu X. 509 używanego do uwierzytelniania usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="715f6-123">Specifies the value of the RSA field of an X.509 certificate used to authenticate a service to a client.</span></span> <span data-ttu-id="715f6-124">Ten element zawiera atrybut `value` , który jest ciągiem i zawiera rzeczywistą tożsamość</span><span class="sxs-lookup"><span data-stu-id="715f6-124">This element contains an attribute `value` that is a string, and contains the actual identity</span></span>|  
|<span data-ttu-id="715f6-125">servicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="715f6-125">servicePrincipalName</span></span>|<span data-ttu-id="715f6-126">Określa tożsamość głównej nazwy serwera (SPN), która jest główną nazwą używaną przez klienta do unikatowego identyfikowania wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="715f6-126">Specifies a server principal name (SPN) identity, which is the principal name used by a client to uniquely identify an instance of a service.</span></span> <span data-ttu-id="715f6-127">Ten element zawiera atrybut `value` , który jest ciągiem i zawiera rzeczywistą nazwę główną.</span><span class="sxs-lookup"><span data-stu-id="715f6-127">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="715f6-128">Ten element jest typu <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement> .</span><span class="sxs-lookup"><span data-stu-id="715f6-128">This element is of type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span></span>|  
|<span data-ttu-id="715f6-129">userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="715f6-129">userPrincipalName</span></span>|<span data-ttu-id="715f6-130">Określa tożsamość głównej nazwy użytkownika (UPN), która jest typem nazwy logowania użytkownika w sieci.</span><span class="sxs-lookup"><span data-stu-id="715f6-130">Specifies a user principal name (UPN) identity, which is the logon name type of a user on a network.</span></span> <span data-ttu-id="715f6-131">Główna nazwa użytkownika składa się z nazwy obiektu użytkownika używanej w Active Directory, a po niej symbol ( \@ ), a następnie zazwyczaj domena nadrzędna systemu nazw domen.</span><span class="sxs-lookup"><span data-stu-id="715f6-131">The user principal name consists of the user object name used in Active Directory, followed by the at symbol (\@) and then, typically, the Domain Name System parent domain.</span></span> <span data-ttu-id="715f6-132">Na przykład Jan w drzewie domeny Fabrikam.com może mieć główną nazwę użytkownika [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com) .</span><span class="sxs-lookup"><span data-stu-id="715f6-132">For example, Jeff in the Fabrikam.com domain tree might have the user principal name [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com).</span></span>  <span data-ttu-id="715f6-133">Ten element zawiera atrybut `value` , który jest ciągiem i zawiera rzeczywistą nazwę główną.</span><span class="sxs-lookup"><span data-stu-id="715f6-133">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="715f6-134">Ten element jest typu <xref:System.ServiceModel.Configuration.UserPrincipalNameElement> .</span><span class="sxs-lookup"><span data-stu-id="715f6-134">This element is of type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="715f6-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="715f6-135">Parent Elements</span></span>  
  
|<span data-ttu-id="715f6-136">Element</span><span class="sxs-lookup"><span data-stu-id="715f6-136">Element</span></span>|<span data-ttu-id="715f6-137">Opis</span><span class="sxs-lookup"><span data-stu-id="715f6-137">Description</span></span>|  
|-------------|-----------------|  
|[\<custom>](custom.md)|<span data-ttu-id="715f6-138">Określa niestandardowy program rozpoznawania elementów równorzędnych dla netPeerTcpBinding.</span><span class="sxs-lookup"><span data-stu-id="715f6-138">Specifies a custom peer resolver for a netPeerTcpBinding.</span></span>|  
|[\<endpoint>](endpoint-element.md)|<span data-ttu-id="715f6-139">Konfiguruje punkty końcowe usługi.</span><span class="sxs-lookup"><span data-stu-id="715f6-139">Configures service endpoints.</span></span>|  
|[<span data-ttu-id="715f6-140">\<endpoint>z\<client></span><span class="sxs-lookup"><span data-stu-id="715f6-140">\<endpoint> of \<client></span></span>](endpoint-of-client.md)|<span data-ttu-id="715f6-141">Konfiguruje punkty końcowe kanału.</span><span class="sxs-lookup"><span data-stu-id="715f6-141">Configures channel endpoints.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="715f6-142">Określa usługę tokenu zabezpieczającego (STS) dla usługi federacyjnej.</span><span class="sxs-lookup"><span data-stu-id="715f6-142">Specifies the Security Token Service (STS) for the federated service.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="715f6-143">Określa punkt końcowy metadanych usługi federacyjnej (Security Token Service).</span><span class="sxs-lookup"><span data-stu-id="715f6-143">Specifies the metadata endpoint for the Security Token Service (STS) of a federated service.</span></span>|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="715f6-144">Definiuje parametry wystawionego tokenu w niestandardowym powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="715f6-144">Defines parameters for an issued token in a custom binding.</span></span>|  
|[\<localIssuer>](localissuer.md)|<span data-ttu-id="715f6-145">Określa usługę lokalnego tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="715f6-145">Specifies a local Security Token Service (STS).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="715f6-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="715f6-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [<span data-ttu-id="715f6-147">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="715f6-147">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="715f6-148">Punkty końcowe: Adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="715f6-148">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
