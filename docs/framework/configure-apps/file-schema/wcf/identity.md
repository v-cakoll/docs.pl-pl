---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 262ac9be6d5ce6466cf9aff33c0c2791c0e149dd
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988377"
---
# <a name="identity"></a><span data-ttu-id="a6749-101">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="a6749-101">\<identity></span></span>
<span data-ttu-id="a6749-102">Element Identity pozwala deweloperowi klienta określić w czasie projektowania oczekiwaną tożsamość usługi.</span><span class="sxs-lookup"><span data-stu-id="a6749-102">The identity element allows a client developer to specify at design time the expected identity of the service.</span></span> <span data-ttu-id="a6749-103">W procesie uzgadniania między klientem a usługą infrastruktura Windows Communication Foundation (WCF) zapewni, że tożsamość oczekiwanej usługi jest zgodna z wartościami tego elementu i w ten sposób może być uwierzytelniona.</span><span class="sxs-lookup"><span data-stu-id="a6749-103">In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element, and thus can be authenticated.</span></span> <span data-ttu-id="a6749-104">Aby uzyskać więcej informacji, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a6749-104">For more information, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="a6749-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a6749-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a6749-106">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="a6749-106">\<client></span></span>  
<span data-ttu-id="a6749-107">\<> punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="a6749-107">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6749-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6749-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6749-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a6749-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a6749-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a6749-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6749-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a6749-111">Attributes</span></span>  
 <span data-ttu-id="a6749-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="a6749-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a6749-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a6749-113">Child Elements</span></span>  
  
|<span data-ttu-id="a6749-114">Element</span><span class="sxs-lookup"><span data-stu-id="a6749-114">Element</span></span>|<span data-ttu-id="a6749-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a6749-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a6749-116">certificate</span><span class="sxs-lookup"><span data-stu-id="a6749-116">certificate</span></span>|<span data-ttu-id="a6749-117">Określa ustawienia certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="a6749-117">Specifies settings of an X.509 certificate.</span></span> <span data-ttu-id="a6749-118">Ten element jest typu <xref:System.ServiceModel.Configuration.CertificateElement>.</span><span class="sxs-lookup"><span data-stu-id="a6749-118">This element is of type <xref:System.ServiceModel.Configuration.CertificateElement>.</span></span> <span data-ttu-id="a6749-119">Zawiera atrybut `encodedValue` , który jest ciągiem, który określa wartość zakodowaną przez ten certyfikat.</span><span class="sxs-lookup"><span data-stu-id="a6749-119">It contains an attribute `encodedValue` that is a string, which specifies the value encoded by this certificate.</span></span>|  
|<span data-ttu-id="a6749-120">certificateReference</span><span class="sxs-lookup"><span data-stu-id="a6749-120">certificateReference</span></span>|<span data-ttu-id="a6749-121">Określa ustawienia dla walidacji certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="a6749-121">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="a6749-122">Ten element jest typu <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span><span class="sxs-lookup"><span data-stu-id="a6749-122">This element is of type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span></span>|  
|<span data-ttu-id="a6749-123">dns</span><span class="sxs-lookup"><span data-stu-id="a6749-123">dns</span></span>|<span data-ttu-id="a6749-124">Określa serwer DNS certyfikatu X. 509 używany do uwierzytelniania usługi.</span><span class="sxs-lookup"><span data-stu-id="a6749-124">Specifies the DNS of an X.509 certificate used to authenticate a service.</span></span> <span data-ttu-id="a6749-125">Ten element zawiera atrybut `value` , który jest ciągiem i zawiera rzeczywistą tożsamość.</span><span class="sxs-lookup"><span data-stu-id="a6749-125">This element contains an attribute `value` that is a string, and contains the actual identity.</span></span>|  
|<span data-ttu-id="a6749-126">rsa</span><span class="sxs-lookup"><span data-stu-id="a6749-126">rsa</span></span>|<span data-ttu-id="a6749-127">Określa wartość pola RSA certyfikatu X. 509 używanego do uwierzytelniania usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="a6749-127">Specifies the value of the RSA field of an X.509 certificate used to authenticate a service to a client.</span></span> <span data-ttu-id="a6749-128">Ten element zawiera atrybut `value` , który jest ciągiem i zawiera rzeczywistą tożsamość</span><span class="sxs-lookup"><span data-stu-id="a6749-128">This element contains an attribute `value` that is a string, and contains the actual identity</span></span>|  
|<span data-ttu-id="a6749-129">servicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="a6749-129">servicePrincipalName</span></span>|<span data-ttu-id="a6749-130">Określa tożsamość głównej nazwy serwera (SPN), która jest główną nazwą używaną przez klienta do unikatowego identyfikowania wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="a6749-130">Specifies a server principal name (SPN) identity, which is the principal name used by a client to uniquely identify an instance of a service.</span></span> <span data-ttu-id="a6749-131">Ten element zawiera atrybut `value` , który jest ciągiem i zawiera rzeczywistą nazwę główną.</span><span class="sxs-lookup"><span data-stu-id="a6749-131">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="a6749-132">Ten element jest typu <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span><span class="sxs-lookup"><span data-stu-id="a6749-132">This element is of type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span></span>|  
|<span data-ttu-id="a6749-133">userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="a6749-133">userPrincipalName</span></span>|<span data-ttu-id="a6749-134">Określa tożsamość głównej nazwy użytkownika (UPN), która jest typem nazwy logowania użytkownika w sieci.</span><span class="sxs-lookup"><span data-stu-id="a6749-134">Specifies a user principal name (UPN) identity, which is the logon name type of a user on a network.</span></span> <span data-ttu-id="a6749-135">Główna nazwa użytkownika składa się z nazwy obiektu użytkownika używanej w Active Directory, a po niej symbol (\@), a następnie zazwyczaj domena nadrzędna systemu nazw domen.</span><span class="sxs-lookup"><span data-stu-id="a6749-135">The user principal name consists of the user object name used in Active Directory, followed by the at symbol (\@) and then, typically, the Domain Name System parent domain.</span></span> <span data-ttu-id="a6749-136">Na przykład Jan w drzewie domeny Fabrikam.com może mieć główną nazwę [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com)użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a6749-136">For example, Jeff in the Fabrikam.com domain tree might have the user principal name [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com).</span></span>  <span data-ttu-id="a6749-137">Ten element zawiera atrybut `value` , który jest ciągiem i zawiera rzeczywistą nazwę główną.</span><span class="sxs-lookup"><span data-stu-id="a6749-137">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="a6749-138">Ten element jest typu <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span><span class="sxs-lookup"><span data-stu-id="a6749-138">This element is of type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6749-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a6749-139">Parent Elements</span></span>  
  
|<span data-ttu-id="a6749-140">Element</span><span class="sxs-lookup"><span data-stu-id="a6749-140">Element</span></span>|<span data-ttu-id="a6749-141">Opis</span><span class="sxs-lookup"><span data-stu-id="a6749-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6749-142">\<> niestandardowe</span><span class="sxs-lookup"><span data-stu-id="a6749-142">\<custom></span></span>](custom.md)|<span data-ttu-id="a6749-143">Określa niestandardowy program rozpoznawania elementów równorzędnych dla netPeerTcpBinding.</span><span class="sxs-lookup"><span data-stu-id="a6749-143">Specifies a custom peer resolver for a netPeerTcpBinding.</span></span>|  
|[<span data-ttu-id="a6749-144">\<> punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="a6749-144">\<endpoint></span></span>](endpoint-element.md)|<span data-ttu-id="a6749-145">Konfiguruje punkty końcowe usługi.</span><span class="sxs-lookup"><span data-stu-id="a6749-145">Configures service endpoints.</span></span>|  
|[<span data-ttu-id="a6749-146">\<> punktu końcowego \<> klienta</span><span class="sxs-lookup"><span data-stu-id="a6749-146">\<endpoint> of \<client></span></span>](endpoint-of-client.md)|<span data-ttu-id="a6749-147">Konfiguruje punkty końcowe kanału.</span><span class="sxs-lookup"><span data-stu-id="a6749-147">Configures channel endpoints.</span></span>|  
|[<span data-ttu-id="a6749-148">\<> wystawcy</span><span class="sxs-lookup"><span data-stu-id="a6749-148">\<issuer></span></span>](issuer.md)|<span data-ttu-id="a6749-149">Określa usługę tokenu zabezpieczającego (STS) dla usługi federacyjnej.</span><span class="sxs-lookup"><span data-stu-id="a6749-149">Specifies the Security Token Service (STS) for the federated service.</span></span>|  
|[<span data-ttu-id="a6749-150">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="a6749-150">\<issuerMetadata></span></span>](issuermetadata.md)|<span data-ttu-id="a6749-151">Określa punkt końcowy metadanych usługi federacyjnej (Security Token Service).</span><span class="sxs-lookup"><span data-stu-id="a6749-151">Specifies the metadata endpoint for the Security Token Service (STS) of a federated service.</span></span>|  
|[<span data-ttu-id="a6749-152">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="a6749-152">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="a6749-153">Definiuje parametry wystawionego tokenu w niestandardowym powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="a6749-153">Defines parameters for an issued token in a custom binding.</span></span>|  
|[<span data-ttu-id="a6749-154">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="a6749-154">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="a6749-155">Określa usługę lokalnego tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="a6749-155">Specifies a local Security Token Service (STS).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6749-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6749-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [<span data-ttu-id="a6749-157">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="a6749-157">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a6749-158">Punktów końcowych Adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="a6749-158">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
