---
title: <httpDigest>, element
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 914711e4d6c3dbb1ccc741af1b3abd6b8de716a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751049"
---
# <a name="httpdigest-element"></a><span data-ttu-id="6592c-102">\<httpDigest> Element</span><span class="sxs-lookup"><span data-stu-id="6592c-102">\<httpDigest> Element</span></span>
<span data-ttu-id="6592c-103">Określa szyfrowany typ poświadczenia używany podczas uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="6592c-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="6592c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6592c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6592c-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="6592c-105">\<behaviors></span></span>  
<span data-ttu-id="6592c-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="6592c-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="6592c-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="6592c-107">\<behavior></span></span>  
<span data-ttu-id="6592c-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="6592c-108">\<clientCredentials></span></span>  
<span data-ttu-id="6592c-109">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="6592c-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6592c-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="6592c-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6592c-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6592c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6592c-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6592c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6592c-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6592c-113">Attributes</span></span>  
  
|<span data-ttu-id="6592c-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6592c-114">Attribute</span></span>|<span data-ttu-id="6592c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6592c-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="6592c-116">Ustawia preferencje personifikacji, który klient komunikuje się z serwerem.</span><span class="sxs-lookup"><span data-stu-id="6592c-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="6592c-117">Tryb personifikacji, który klient wybiera nie są wymuszane na serwerze.</span><span class="sxs-lookup"><span data-stu-id="6592c-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="6592c-118">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="6592c-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6592c-119">— Identyfikator: Serwer można uzyskać tożsamości i uprawnień klienta, ale nie można spersonifikować klienta.</span><span class="sxs-lookup"><span data-stu-id="6592c-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="6592c-120">-Personifikacji: Serwer może personifikować klienta kontekstu zabezpieczeń w systemie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="6592c-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="6592c-121">-Delegowania: Serwer może personifikować klienta kontekstu zabezpieczeń w systemach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="6592c-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="6592c-122">-Anonimowe: Serwer nie może spersonifikować lub identyfikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="6592c-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="6592c-123">-Brak: Nie przypisano poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="6592c-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="6592c-124">Wartość domyślna to identyfikator.</span><span class="sxs-lookup"><span data-stu-id="6592c-124">The default is Identification.</span></span> <span data-ttu-id="6592c-125">Ten atrybut jest typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="6592c-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6592c-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6592c-126">Child Elements</span></span>  
 <span data-ttu-id="6592c-127">Brak</span><span class="sxs-lookup"><span data-stu-id="6592c-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6592c-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6592c-128">Parent Elements</span></span>  
  
|<span data-ttu-id="6592c-129">Element</span><span class="sxs-lookup"><span data-stu-id="6592c-129">Element</span></span>|<span data-ttu-id="6592c-130">Opis</span><span class="sxs-lookup"><span data-stu-id="6592c-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6592c-131">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="6592c-131">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="6592c-132">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="6592c-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6592c-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6592c-133">Remarks</span></span>  
 <span data-ttu-id="6592c-134">Podsumowanie jest skrót, określić przy użyciu algorytmu i zestaw danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="6592c-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="6592c-135">Wystawca uwierzytelnienia uwierzytelnionego zgody na algorytm i wymiany danych, używane jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="6592c-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="6592c-136">Klient może obliczenia skrótu i wysyłać je do usługi.</span><span class="sxs-lookup"><span data-stu-id="6592c-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="6592c-137">Ta usługa również oblicza skrót i porównuje wartości.</span><span class="sxs-lookup"><span data-stu-id="6592c-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="6592c-138">Dopasowanie weryfikuje klienta.</span><span class="sxs-lookup"><span data-stu-id="6592c-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="6592c-139">Ta funkcja wymaga włączenia w usłudze Active Directory, Windows i Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="6592c-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="6592c-140">Aby uzyskać więcej informacji, zobacz [uwierzytelnianie szyfrowane w usługach IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="6592c-140">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6592c-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6592c-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="6592c-142">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="6592c-142">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="6592c-143">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="6592c-143">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="6592c-144">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="6592c-144">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="6592c-145">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="6592c-145">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
