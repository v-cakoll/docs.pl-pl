---
title: <httpDigest>, element
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 2ceefdd7fab82025e89ad08d8423d57524c2e4d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925564"
---
# <a name="httpdigest-element"></a><span data-ttu-id="733ee-102">\<httpDigest, element ></span><span class="sxs-lookup"><span data-stu-id="733ee-102">\<httpDigest> Element</span></span>
<span data-ttu-id="733ee-103">Określa poświadczenia typu szyfrowanego używane podczas uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="733ee-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="733ee-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="733ee-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="733ee-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="733ee-105">\<behaviors></span></span>  
<span data-ttu-id="733ee-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="733ee-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="733ee-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="733ee-107">\<behavior></span></span>  
<span data-ttu-id="733ee-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="733ee-108">\<clientCredentials></span></span>  
<span data-ttu-id="733ee-109">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="733ee-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="733ee-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="733ee-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="733ee-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="733ee-111">Attributes and Elements</span></span>  
 <span data-ttu-id="733ee-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="733ee-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="733ee-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="733ee-113">Attributes</span></span>  
  
|<span data-ttu-id="733ee-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="733ee-114">Attribute</span></span>|<span data-ttu-id="733ee-115">Opis</span><span class="sxs-lookup"><span data-stu-id="733ee-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="733ee-116">Ustawia preferencje personifikacji, które klient komunikuje się z serwerem.</span><span class="sxs-lookup"><span data-stu-id="733ee-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="733ee-117">Tryb personifikacji wybierany przez klienta nie jest wymuszany na serwerze.</span><span class="sxs-lookup"><span data-stu-id="733ee-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="733ee-118">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="733ee-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="733ee-119">Identyfikatora Serwer może uzyskać tożsamość i uprawnienia klienta, ale nie może personifikować klienta.</span><span class="sxs-lookup"><span data-stu-id="733ee-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="733ee-120">Chodzi Serwer może personifikować kontekst zabezpieczeń klienta w systemie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="733ee-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="733ee-121">Wierz Serwer może personifikować kontekst zabezpieczeń klienta w systemach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="733ee-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="733ee-122">Anonimowe Serwer nie może personifikować lub zidentyfikować klienta.</span><span class="sxs-lookup"><span data-stu-id="733ee-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="733ee-123">Dawaj Nie przypisano poziomu personifikacji.</span><span class="sxs-lookup"><span data-stu-id="733ee-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="733ee-124">Wartość domyślna to Identification.</span><span class="sxs-lookup"><span data-stu-id="733ee-124">The default is Identification.</span></span> <span data-ttu-id="733ee-125">Ten atrybut jest typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="733ee-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="733ee-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="733ee-126">Child Elements</span></span>  
 <span data-ttu-id="733ee-127">Brak</span><span class="sxs-lookup"><span data-stu-id="733ee-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="733ee-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="733ee-128">Parent Elements</span></span>  
  
|<span data-ttu-id="733ee-129">Element</span><span class="sxs-lookup"><span data-stu-id="733ee-129">Element</span></span>|<span data-ttu-id="733ee-130">Opis</span><span class="sxs-lookup"><span data-stu-id="733ee-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="733ee-131">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="733ee-131">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="733ee-132">Określa poświadczenia używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="733ee-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="733ee-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="733ee-133">Remarks</span></span>  
 <span data-ttu-id="733ee-134">Skrót jest skrótem określonym przy użyciu algorytmu i zestawu danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="733ee-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="733ee-135">Wystawcy uwierzytelnienie i uwierzytelnienie zgadzają się na algorytm i wymieniają dane wykorzystywane jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="733ee-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="733ee-136">Klient może obliczyć skrót i wysłać go do usługi.</span><span class="sxs-lookup"><span data-stu-id="733ee-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="733ee-137">Usługa oblicza również wartość skrótu i porównuje wartości.</span><span class="sxs-lookup"><span data-stu-id="733ee-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="733ee-138">Dopasowanie sprawdza poprawność klienta.</span><span class="sxs-lookup"><span data-stu-id="733ee-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="733ee-139">Ta funkcja musi być włączona z Active Directory w systemie Windows i Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="733ee-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="733ee-140">Aby uzyskać więcej informacji, zobacz [uwierzytelnianie szyfrowane w usługach IIS 6,0](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="733ee-140">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="733ee-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="733ee-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="733ee-142">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="733ee-142">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="733ee-143">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="733ee-143">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="733ee-144">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="733ee-144">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="733ee-145">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="733ee-145">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
