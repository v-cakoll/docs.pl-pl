---
title: <windows><clientCredentials> elementu
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 61ca99213f0b83a5af5df0184a8c1de405366288
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399121"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="fb987-102">\<> systemu Windows \<obiektu ClientCredentials ></span><span class="sxs-lookup"><span data-stu-id="fb987-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="fb987-103">Określa ustawienia poświadczeń systemu Windows, które mają być używane do reprezentowania klienta.</span><span class="sxs-lookup"><span data-stu-id="fb987-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
<span data-ttu-id="fb987-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fb987-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fb987-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fb987-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fb987-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fb987-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="fb987-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fb987-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="fb987-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fb987-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="fb987-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Obiekt clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="fb987-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="fb987-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> systemu Windows**</span><span class="sxs-lookup"><span data-stu-id="fb987-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb987-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb987-111">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb987-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fb987-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fb987-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fb987-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb987-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fb987-114">Attributes</span></span>  
  
|<span data-ttu-id="fb987-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fb987-115">Attribute</span></span>|<span data-ttu-id="fb987-116">Opis</span><span class="sxs-lookup"><span data-stu-id="fb987-116">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="fb987-117">Ustawia preferencje personifikacji, które klient komunikuje się z serwerem.</span><span class="sxs-lookup"><span data-stu-id="fb987-117">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="fb987-118">Tryb personifikacji wybierany przez klienta nie jest wymuszany na serwerze.</span><span class="sxs-lookup"><span data-stu-id="fb987-118">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="fb987-119">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="fb987-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fb987-120">Identyfikatora Serwer może uzyskać tożsamość i uprawnienia klienta, ale nie może personifikować klienta.</span><span class="sxs-lookup"><span data-stu-id="fb987-120">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="fb987-121">Chodzi Serwer może personifikować kontekst zabezpieczeń klienta w systemie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="fb987-121">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="fb987-122">Wierz Serwer może personifikować kontekst zabezpieczeń klienta w systemach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="fb987-122">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="fb987-123">Anonimowe Serwer nie może personifikować lub zidentyfikować klienta.</span><span class="sxs-lookup"><span data-stu-id="fb987-123">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="fb987-124">Dawaj Nie przypisano poziomu personifikacji.</span><span class="sxs-lookup"><span data-stu-id="fb987-124">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="fb987-125">Wartość domyślna to Identification.</span><span class="sxs-lookup"><span data-stu-id="fb987-125">The default is Identification.</span></span> <span data-ttu-id="fb987-126">Ten atrybut jest typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="fb987-126">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="fb987-127">Ustawienie tej właściwości `true` umożliwia uwierzytelnianie w przypadku, gdy protokół Kerberos jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="fb987-127">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="fb987-128">Ustawienie tej właściwości `false` powoduje, że Windows Communication Foundation (WCF), aby najlepszym wysiłku zgłosić wyjątek, jeśli jest używany protokół NTLM.</span><span class="sxs-lookup"><span data-stu-id="fb987-128">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="fb987-129">Należy pamiętać, że ustawienie tej `false` właściwości na nie zapobiega wysyłaniu poświadczeń NTLM za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="fb987-129">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb987-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fb987-130">Child Elements</span></span>  
 <span data-ttu-id="fb987-131">Brak.</span><span class="sxs-lookup"><span data-stu-id="fb987-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb987-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fb987-132">Parent Elements</span></span>  
  
|<span data-ttu-id="fb987-133">Element</span><span class="sxs-lookup"><span data-stu-id="fb987-133">Element</span></span>|<span data-ttu-id="fb987-134">Opis</span><span class="sxs-lookup"><span data-stu-id="fb987-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb987-135">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="fb987-135">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="fb987-136">Określa poświadczenia używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="fb987-136">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb987-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb987-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="fb987-138">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="fb987-138">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="fb987-139">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="fb987-139">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="fb987-140">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="fb987-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
