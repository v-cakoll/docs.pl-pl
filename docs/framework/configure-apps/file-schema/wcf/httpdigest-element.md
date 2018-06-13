---
title: '&lt;httpDigest&gt;, element'
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 8ea4597dbfc704f669a514b0d6c5976c80c5c3a6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748896"
---
# <a name="lthttpdigestgt-element"></a><span data-ttu-id="5a763-102">&lt;httpDigest&gt;, element</span><span class="sxs-lookup"><span data-stu-id="5a763-102">&lt;httpDigest&gt; Element</span></span>
<span data-ttu-id="5a763-103">Określa szyfrowany typ poświadczenia używany podczas uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="5a763-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="5a763-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5a763-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5a763-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="5a763-105">\<behaviors></span></span>  
<span data-ttu-id="5a763-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="5a763-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="5a763-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="5a763-107">\<behavior></span></span>  
<span data-ttu-id="5a763-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="5a763-108">\<clientCredentials></span></span>  
<span data-ttu-id="5a763-109">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="5a763-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a763-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a763-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a763-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5a763-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5a763-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5a763-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a763-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5a763-113">Attributes</span></span>  
  
|<span data-ttu-id="5a763-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5a763-114">Attribute</span></span>|<span data-ttu-id="5a763-115">Opis</span><span class="sxs-lookup"><span data-stu-id="5a763-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="5a763-116">Ustawia preferencje personifikacji, który klient komunikuje się z serwerem.</span><span class="sxs-lookup"><span data-stu-id="5a763-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="5a763-117">Tryb personifikacji, w którym klient wybiera nie są wymuszane na serwerze.</span><span class="sxs-lookup"><span data-stu-id="5a763-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="5a763-118">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="5a763-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5a763-119">— Identyfikator: Serwera można uzyskać tożsamości i uprawnienia klienta, ale nie można spersonifikować klienta.</span><span class="sxs-lookup"><span data-stu-id="5a763-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="5a763-120">-Personifikacji: Serwer może personifikować klienta kontekstu zabezpieczeń w systemie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="5a763-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="5a763-121">-Delegowania: Serwer może personifikować klienta kontekstu zabezpieczeń w systemach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="5a763-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="5a763-122">-Anonimowe: Serwer nie może Cię personifikacji lub identyfikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="5a763-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="5a763-123">-Brak: Poziom personifikacji nie jest przypisany.</span><span class="sxs-lookup"><span data-stu-id="5a763-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="5a763-124">Wartość domyślna to identyfikator.</span><span class="sxs-lookup"><span data-stu-id="5a763-124">The default is Identification.</span></span> <span data-ttu-id="5a763-125">Ten atrybut jest typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="5a763-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a763-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5a763-126">Child Elements</span></span>  
 <span data-ttu-id="5a763-127">Brak</span><span class="sxs-lookup"><span data-stu-id="5a763-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a763-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5a763-128">Parent Elements</span></span>  
  
|<span data-ttu-id="5a763-129">Element</span><span class="sxs-lookup"><span data-stu-id="5a763-129">Element</span></span>|<span data-ttu-id="5a763-130">Opis</span><span class="sxs-lookup"><span data-stu-id="5a763-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a763-131">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="5a763-131">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="5a763-132">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="5a763-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a763-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a763-133">Remarks</span></span>  
 <span data-ttu-id="5a763-134">Skrót jest skrót ustalić przy użyciu algorytmu i zestaw danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="5a763-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="5a763-135">Wystawca uwierzytelnienia uwierzytelniony uzgodnić algorytm i wymiany danych używane jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="5a763-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="5a763-136">Klienta można obliczyć skrótu i wysłać go do usługi.</span><span class="sxs-lookup"><span data-stu-id="5a763-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="5a763-137">Usługa również oblicza skrót i porównuje wartości.</span><span class="sxs-lookup"><span data-stu-id="5a763-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="5a763-138">Dopasowanie weryfikuje klienta.</span><span class="sxs-lookup"><span data-stu-id="5a763-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="5a763-139">Ta funkcja musi być włączona w usłudze Active Directory w systemach Windows i usługi Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="5a763-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="5a763-140">Aby uzyskać więcej informacji, zobacz [uwierzytelnianie szyfrowane w usługach IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="5a763-140">For more information, see [Digest Authentication in IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a763-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a763-141">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>  
 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>  
 <xref:System.ServiceModel.Security.HttpDigestClientCredential>  
 [<span data-ttu-id="5a763-142">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="5a763-142">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="5a763-143">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="5a763-143">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="5a763-144">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="5a763-144">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="5a763-145">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="5a763-145">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
