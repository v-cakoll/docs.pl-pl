---
title: <windows><clientCredentials>elementu
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 61ca99213f0b83a5af5df0184a8c1de405366288
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399121"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="25c3b-102">\<windows>\<clientCredentials>elementu</span><span class="sxs-lookup"><span data-stu-id="25c3b-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="25c3b-103">Określa ustawienia poświadczeń systemu Windows, które mają być używane do reprezentowania klienta.</span><span class="sxs-lookup"><span data-stu-id="25c3b-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**  
  
## <a name="syntax"></a><span data-ttu-id="25c3b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25c3b-104">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25c3b-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="25c3b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="25c3b-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="25c3b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25c3b-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="25c3b-107">Attributes</span></span>  
  
|<span data-ttu-id="25c3b-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="25c3b-108">Attribute</span></span>|<span data-ttu-id="25c3b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="25c3b-109">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="25c3b-110">Ustawia preferencje personifikacji, które klient komunikuje się z serwerem.</span><span class="sxs-lookup"><span data-stu-id="25c3b-110">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="25c3b-111">Tryb personifikacji wybierany przez klienta nie jest wymuszany na serwerze.</span><span class="sxs-lookup"><span data-stu-id="25c3b-111">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="25c3b-112">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="25c3b-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="25c3b-113">-Identyfikacja: serwer może uzyskać tożsamość i uprawnienia klienta, ale nie może personifikować klienta.</span><span class="sxs-lookup"><span data-stu-id="25c3b-113">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="25c3b-114">-Personifikacja: serwer może personifikować kontekst zabezpieczeń klienta w systemie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="25c3b-114">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="25c3b-115">-Delegowanie: serwer może personifikować kontekst zabezpieczeń klienta w systemach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="25c3b-115">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="25c3b-116">-Anonymous: serwer nie może personifikować lub zidentyfikować klienta.</span><span class="sxs-lookup"><span data-stu-id="25c3b-116">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="25c3b-117">-Brak: nie przypisano poziomu personifikacji.</span><span class="sxs-lookup"><span data-stu-id="25c3b-117">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="25c3b-118">Wartość domyślna to Identification.</span><span class="sxs-lookup"><span data-stu-id="25c3b-118">The default is Identification.</span></span> <span data-ttu-id="25c3b-119">Ten atrybut jest typu <xref:System.Security.Principal.TokenImpersonationLevel> .</span><span class="sxs-lookup"><span data-stu-id="25c3b-119">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="25c3b-120">Ustawienie tej właściwości umożliwia `true` uwierzytelnianie w przypadku, gdy protokół Kerberos jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="25c3b-120">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="25c3b-121">Ustawienie tej właściwości `false` powoduje, że Windows Communication Foundation (WCF), aby najlepszym wysiłku zgłosić wyjątek, jeśli jest używany protokół NTLM.</span><span class="sxs-lookup"><span data-stu-id="25c3b-121">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="25c3b-122">Należy pamiętać, że ustawienie tej właściwości na `false` nie zapobiega wysyłaniu poświadczeń NTLM za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="25c3b-122">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25c3b-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="25c3b-123">Child Elements</span></span>  
 <span data-ttu-id="25c3b-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="25c3b-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="25c3b-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="25c3b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="25c3b-126">Element</span><span class="sxs-lookup"><span data-stu-id="25c3b-126">Element</span></span>|<span data-ttu-id="25c3b-127">Opis</span><span class="sxs-lookup"><span data-stu-id="25c3b-127">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="25c3b-128">Określa poświadczenia używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="25c3b-128">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25c3b-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25c3b-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="25c3b-130">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="25c3b-130">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="25c3b-131">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="25c3b-131">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="25c3b-132">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="25c3b-132">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
