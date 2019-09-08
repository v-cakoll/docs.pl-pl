---
title: <httpDigest>, element
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 121df39c7e4ce4de5c1f0ef87921f6269d7cc1c0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785828"
---
# <a name="httpdigest-element"></a><span data-ttu-id="97e55-102">\<httpDigest, element ></span><span class="sxs-lookup"><span data-stu-id="97e55-102">\<httpDigest> Element</span></span>
<span data-ttu-id="97e55-103">Określa poświadczenia typu szyfrowanego używane podczas uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="97e55-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
<span data-ttu-id="97e55-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="97e55-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="97e55-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="97e55-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="97e55-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="97e55-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="97e55-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="97e55-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="97e55-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="97e55-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="97e55-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Obiekt clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="97e55-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="97e55-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<httpDigest >**</span><span class="sxs-lookup"><span data-stu-id="97e55-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97e55-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="97e55-111">Syntax</span></span>  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97e55-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="97e55-112">Attributes and Elements</span></span>  
 <span data-ttu-id="97e55-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="97e55-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97e55-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="97e55-114">Attributes</span></span>  
  
|<span data-ttu-id="97e55-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="97e55-115">Attribute</span></span>|<span data-ttu-id="97e55-116">Opis</span><span class="sxs-lookup"><span data-stu-id="97e55-116">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="97e55-117">Ustawia preferencje personifikacji, które klient komunikuje się z serwerem.</span><span class="sxs-lookup"><span data-stu-id="97e55-117">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="97e55-118">Tryb personifikacji wybierany przez klienta nie jest wymuszany na serwerze.</span><span class="sxs-lookup"><span data-stu-id="97e55-118">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="97e55-119">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="97e55-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="97e55-120">Identyfikatora Serwer może uzyskać tożsamość i uprawnienia klienta, ale nie może personifikować klienta.</span><span class="sxs-lookup"><span data-stu-id="97e55-120">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="97e55-121">Chodzi Serwer może personifikować kontekst zabezpieczeń klienta w systemie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="97e55-121">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="97e55-122">Wierz Serwer może personifikować kontekst zabezpieczeń klienta w systemach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="97e55-122">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="97e55-123">Anonimowe Serwer nie może personifikować lub zidentyfikować klienta.</span><span class="sxs-lookup"><span data-stu-id="97e55-123">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="97e55-124">Dawaj Nie przypisano poziomu personifikacji.</span><span class="sxs-lookup"><span data-stu-id="97e55-124">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="97e55-125">Wartość domyślna to Identification.</span><span class="sxs-lookup"><span data-stu-id="97e55-125">The default is Identification.</span></span> <span data-ttu-id="97e55-126">Ten atrybut jest typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="97e55-126">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97e55-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="97e55-127">Child Elements</span></span>  
 <span data-ttu-id="97e55-128">Brak</span><span class="sxs-lookup"><span data-stu-id="97e55-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97e55-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="97e55-129">Parent Elements</span></span>  
  
|<span data-ttu-id="97e55-130">Element</span><span class="sxs-lookup"><span data-stu-id="97e55-130">Element</span></span>|<span data-ttu-id="97e55-131">Opis</span><span class="sxs-lookup"><span data-stu-id="97e55-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97e55-132">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="97e55-132">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="97e55-133">Określa poświadczenia używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="97e55-133">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97e55-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97e55-134">Remarks</span></span>  
 <span data-ttu-id="97e55-135">Skrót jest skrótem określonym przy użyciu algorytmu i zestawu danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="97e55-135">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="97e55-136">Wystawcy uwierzytelnienie i uwierzytelnienie zgadzają się na algorytm i wymieniają dane wykorzystywane jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="97e55-136">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="97e55-137">Klient może obliczyć skrót i wysłać go do usługi.</span><span class="sxs-lookup"><span data-stu-id="97e55-137">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="97e55-138">Usługa oblicza również wartość skrótu i porównuje wartości.</span><span class="sxs-lookup"><span data-stu-id="97e55-138">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="97e55-139">Dopasowanie sprawdza poprawność klienta.</span><span class="sxs-lookup"><span data-stu-id="97e55-139">A match validates the client.</span></span>  
  
 <span data-ttu-id="97e55-140">Ta funkcja musi być włączona z Active Directory w systemie Windows i Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="97e55-140">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="97e55-141">Aby uzyskać więcej informacji, zobacz [uwierzytelnianie szyfrowane w usługach IIS 6,0](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="97e55-141">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97e55-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97e55-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="97e55-143">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="97e55-143">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="97e55-144">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="97e55-144">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="97e55-145">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="97e55-145">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="97e55-146">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="97e55-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
