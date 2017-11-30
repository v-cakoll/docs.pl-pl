---
title: "&lt;tożsamości&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fa6bfdf72bd292599867bf7a9571ecd6b408a2c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltidentitygt"></a><span data-ttu-id="7a5e0-102">&lt;tożsamości&gt;</span><span class="sxs-lookup"><span data-stu-id="7a5e0-102">&lt;identity&gt;</span></span>
<span data-ttu-id="7a5e0-103">Element tożsamości pozwala deweloperowi klienta określić w czasie projektu oczekiwaną tożsamość usługi.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-103">The identity element allows a client developer to specify at design time the expected identity of the service.</span></span> <span data-ttu-id="7a5e0-104">W ramach procesu uzgadniania między klientem a usługą [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] infrastruktury zapewnia, że odpowiada wartości tego elementu tożsamość oczekiwanej usługi i w związku z tym mogą być uwierzytelniane.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-104">In the handshake process between the client and service, the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] infrastructure will ensure that the identity of the expected service matches the values of this element, and thus can be authenticated.</span></span> <span data-ttu-id="7a5e0-105">Aby uzyskać więcej informacji, zobacz [uwierzytelnianie i tożsamość usługi](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7a5e0-105">For more information, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="7a5e0-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7a5e0-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="7a5e0-107">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="7a5e0-107">\<client></span></span>  
<span data-ttu-id="7a5e0-108">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="7a5e0-108">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a5e0-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a5e0-109">Syntax</span></span>  
  
```xml  
<identity>  
    <certificate encodedValue="String"/>  
    <certificateReference findValue="String"   
       isChainIncluded="Boolean"  
       storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"storeName="  
       storeLocation="LocalMachine/CurrentUser"  
       X509FindType= Enumeration./>  
    <dns value="String"/>  
    <rsa value="String"/>  
    <servicePrincipalName value="String"/>  
    <usePrincipalName value="String"/>  
</identity>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a5e0-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7a5e0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7a5e0-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a5e0-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7a5e0-112">Attributes</span></span>  
 <span data-ttu-id="7a5e0-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7a5e0-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7a5e0-114">Child Elements</span></span>  
  
|<span data-ttu-id="7a5e0-115">Element</span><span class="sxs-lookup"><span data-stu-id="7a5e0-115">Element</span></span>|<span data-ttu-id="7a5e0-116">Opis</span><span class="sxs-lookup"><span data-stu-id="7a5e0-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7a5e0-117">certificate</span><span class="sxs-lookup"><span data-stu-id="7a5e0-117">certificate</span></span>|<span data-ttu-id="7a5e0-118">Określa ustawienia certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-118">Specifies settings of an X.509 certificate.</span></span> <span data-ttu-id="7a5e0-119">Ten element jest typu <xref:System.ServiceModel.Configuration.CertificateElement>.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-119">This element is of type <xref:System.ServiceModel.Configuration.CertificateElement>.</span></span> <span data-ttu-id="7a5e0-120">Zawiera ona atrybut `encodedValue` oznacza to ciąg, który określa wartość kodowane przez ten certyfikat.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-120">It contains an attribute `encodedValue` that is a string, which specifies the value encoded by this certificate.</span></span>|  
|<span data-ttu-id="7a5e0-121">certificateReference</span><span class="sxs-lookup"><span data-stu-id="7a5e0-121">certificateReference</span></span>|<span data-ttu-id="7a5e0-122">Określa ustawienia dla walidacji certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-122">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="7a5e0-123">Ten element jest typu <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-123">This element is of type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span></span>|  
|<span data-ttu-id="7a5e0-124">dns</span><span class="sxs-lookup"><span data-stu-id="7a5e0-124">dns</span></span>|<span data-ttu-id="7a5e0-125">Określa certyfikat X.509 używany do uwierzytelniania usługi DNS.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-125">Specifies the DNS of an X.509 certificate used to authenticate a service.</span></span> <span data-ttu-id="7a5e0-126">Ten element zawiera atrybut `value` jest ciągiem i zawiera rzeczywistej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-126">This element contains an attribute `value` that is a string, and contains the actual identity.</span></span>|  
|<span data-ttu-id="7a5e0-127">rsa</span><span class="sxs-lookup"><span data-stu-id="7a5e0-127">rsa</span></span>|<span data-ttu-id="7a5e0-128">Określa wartość pola RSA certyfikat X.509 używany do uwierzytelniania usługi na kliencie.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-128">Specifies the value of the RSA field of an X.509 certificate used to authenticate a service to a client.</span></span> <span data-ttu-id="7a5e0-129">Ten element zawiera atrybut `value` jest ciągiem i zawiera rzeczywistej tożsamości</span><span class="sxs-lookup"><span data-stu-id="7a5e0-129">This element contains an attribute `value` that is a string, and contains the actual identity</span></span>|  
|<span data-ttu-id="7a5e0-130">servicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="7a5e0-130">servicePrincipalName</span></span>|<span data-ttu-id="7a5e0-131">Określa tożsamość głównej nazwy (usługi SPN) serwera, który jest nazwa główna używana przez klienta do unikatowej identyfikacji wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-131">Specifies a server principal name (SPN) identity, which is the principal name used by a client to uniquely identify an instance of a service.</span></span> <span data-ttu-id="7a5e0-132">Ten element zawiera atrybut `value` jest ciągiem i zawiera rzeczywistą nazwą podmiotu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-132">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="7a5e0-133">Ten element jest typu <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-133">This element is of type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span></span>|  
|<span data-ttu-id="7a5e0-134">userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="7a5e0-134">userPrincipalName</span></span>|<span data-ttu-id="7a5e0-135">Określa tożsamość głównej nazwy (UPN) użytkownika, który jest typem nazwa logowania użytkownika w sieci.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-135">Specifies a user principal name (UPN) identity, which is the logon name type of a user on a network.</span></span> <span data-ttu-id="7a5e0-136">Główna nazwa użytkownika zawiera nazwę obiektu użytkownika używane w usłudze Active Directory, a następnie na symbolu (@) i następnie zazwyczaj domeny nadrzędnej systemu nazw domen.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-136">The user principal name consists of the user object name used in Active Directory, followed by the at symbol (@) and then, typically, the Domain Name System parent domain.</span></span> <span data-ttu-id="7a5e0-137">Na przykład Jan w drzewie domeny Fabrikam.com może być nazwa główna użytkownika [ jeff@fabrikam.com ](mailto:jeffsmith@fabrikam.com).  Ten element zawiera atrybut `value` jest ciągiem i zawiera rzeczywistą nazwą podmiotu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-137">For example, Jeff in the Fabrikam.com domain tree might have the user principal name [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com).  This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="7a5e0-138">Ten element jest typu <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-138">This element is of type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7a5e0-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7a5e0-139">Parent Elements</span></span>  
  
|<span data-ttu-id="7a5e0-140">Element</span><span class="sxs-lookup"><span data-stu-id="7a5e0-140">Element</span></span>|<span data-ttu-id="7a5e0-141">Opis</span><span class="sxs-lookup"><span data-stu-id="7a5e0-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a5e0-142">\<niestandardowe ></span><span class="sxs-lookup"><span data-stu-id="7a5e0-142">\<custom></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|<span data-ttu-id="7a5e0-143">Określa program rozpoznawania nazw dla netPeerTcpBinding równorzędnej niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-143">Specifies a custom peer resolver for a netPeerTcpBinding.</span></span>|  
|[<span data-ttu-id="7a5e0-144">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="7a5e0-144">\<endpoint></span></span>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017)|<span data-ttu-id="7a5e0-145">Umożliwia skonfigurowanie różnych typów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-145">Configures different types of endpoints.</span></span>|  
|[<span data-ttu-id="7a5e0-146">\<Wystawca ></span><span class="sxs-lookup"><span data-stu-id="7a5e0-146">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|<span data-ttu-id="7a5e0-147">Określa zabezpieczeń tokenu usługi (STS) dla usługi federacyjnej.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-147">Specifies the Security Token Service (STS) for the federated service.</span></span>|  
|[<span data-ttu-id="7a5e0-148">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="7a5e0-148">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|<span data-ttu-id="7a5e0-149">Określa punktu końcowego metadanych dla zabezpieczeń tokenu usługi (STS) usługi federacyjnej.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-149">Specifies the metadata endpoint for the Security Token Service (STS) of a federated service.</span></span>|  
|[<span data-ttu-id="7a5e0-150">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="7a5e0-150">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="7a5e0-151">Definiuje parametry dla wystawionego tokenu do niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7a5e0-151">Defines parameters for an issued token in a custom binding.</span></span>|  
|[<span data-ttu-id="7a5e0-152">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="7a5e0-152">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="7a5e0-153">Określa lokalne zabezpieczenia tokenu usługi (STS).</span><span class="sxs-lookup"><span data-stu-id="7a5e0-153">Specifies a local Security Token Service (STS).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a5e0-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a5e0-154">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 [<span data-ttu-id="7a5e0-155">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="7a5e0-155">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="7a5e0-156">Punkty końcowe: Adresy powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="7a5e0-156">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
