---
title: <windows><clientCredentials> elementu
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: e9f0ed9879cc42ea25b83e6b626139a40a593112
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940306"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="e4234-102">\<> systemu Windows \<obiektu ClientCredentials ></span><span class="sxs-lookup"><span data-stu-id="e4234-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="e4234-103">Określa ustawienia poświadczeń systemu Windows, które mają być używane do reprezentowania klienta.</span><span class="sxs-lookup"><span data-stu-id="e4234-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="e4234-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e4234-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e4234-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="e4234-105">\<behaviors></span></span>  
<span data-ttu-id="e4234-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="e4234-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="e4234-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="e4234-107">\<behavior></span></span>  
<span data-ttu-id="e4234-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="e4234-108">\<clientCredentials></span></span>  
<span data-ttu-id="e4234-109">\<windows></span><span class="sxs-lookup"><span data-stu-id="e4234-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4234-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4234-110">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4234-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e4234-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e4234-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e4234-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4234-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e4234-113">Attributes</span></span>  
  
|<span data-ttu-id="e4234-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e4234-114">Attribute</span></span>|<span data-ttu-id="e4234-115">Opis</span><span class="sxs-lookup"><span data-stu-id="e4234-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="e4234-116">Ustawia preferencje personifikacji, które klient komunikuje się z serwerem.</span><span class="sxs-lookup"><span data-stu-id="e4234-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="e4234-117">Tryb personifikacji wybierany przez klienta nie jest wymuszany na serwerze.</span><span class="sxs-lookup"><span data-stu-id="e4234-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="e4234-118">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="e4234-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e4234-119">Identyfikatora Serwer może uzyskać tożsamość i uprawnienia klienta, ale nie może personifikować klienta.</span><span class="sxs-lookup"><span data-stu-id="e4234-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="e4234-120">Chodzi Serwer może personifikować kontekst zabezpieczeń klienta w systemie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="e4234-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="e4234-121">Wierz Serwer może personifikować kontekst zabezpieczeń klienta w systemach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="e4234-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="e4234-122">Anonimowe Serwer nie może personifikować lub zidentyfikować klienta.</span><span class="sxs-lookup"><span data-stu-id="e4234-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="e4234-123">Dawaj Nie przypisano poziomu personifikacji.</span><span class="sxs-lookup"><span data-stu-id="e4234-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="e4234-124">Wartość domyślna to Identification.</span><span class="sxs-lookup"><span data-stu-id="e4234-124">The default is Identification.</span></span> <span data-ttu-id="e4234-125">Ten atrybut jest typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="e4234-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="e4234-126">Ustawienie tej właściwości `true` umożliwia uwierzytelnianie w przypadku, gdy protokół Kerberos jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="e4234-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="e4234-127">Ustawienie tej właściwości `false` powoduje, że Windows Communication Foundation (WCF), aby najlepszym wysiłku zgłosić wyjątek, jeśli jest używany protokół NTLM.</span><span class="sxs-lookup"><span data-stu-id="e4234-127">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="e4234-128">Należy pamiętać, że ustawienie tej `false` właściwości na nie zapobiega wysyłaniu poświadczeń NTLM za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="e4234-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4234-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e4234-129">Child Elements</span></span>  
 <span data-ttu-id="e4234-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="e4234-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4234-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e4234-131">Parent Elements</span></span>  
  
|<span data-ttu-id="e4234-132">Element</span><span class="sxs-lookup"><span data-stu-id="e4234-132">Element</span></span>|<span data-ttu-id="e4234-133">Opis</span><span class="sxs-lookup"><span data-stu-id="e4234-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4234-134">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="e4234-134">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="e4234-135">Określa poświadczenia używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="e4234-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4234-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4234-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="e4234-137">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="e4234-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="e4234-138">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="e4234-138">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="e4234-139">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="e4234-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
