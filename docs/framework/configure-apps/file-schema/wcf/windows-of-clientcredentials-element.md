---
title: '&lt;windows&gt; w &lt;clientCredentials&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5cf2740b0218286178e62262723bb060dc2d3817
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltwindowsgt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="193b8-102">&lt;windows&gt; w &lt;clientCredentials&gt;, element</span><span class="sxs-lookup"><span data-stu-id="193b8-102">&lt;windows&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="193b8-103">Określa ustawienia dla poświadczenia systemu Windows do użycia do reprezentacji klienta.</span><span class="sxs-lookup"><span data-stu-id="193b8-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="193b8-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="193b8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="193b8-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="193b8-105">\<behaviors></span></span>  
<span data-ttu-id="193b8-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="193b8-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="193b8-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="193b8-107">\<behavior></span></span>  
<span data-ttu-id="193b8-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="193b8-108">\<clientCredentials></span></span>  
<span data-ttu-id="193b8-109">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="193b8-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="193b8-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="193b8-110">Syntax</span></span>  
  
```xml  
<windows   
    allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"  
        allowNtlm="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="193b8-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="193b8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="193b8-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="193b8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="193b8-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="193b8-113">Attributes</span></span>  
  
|<span data-ttu-id="193b8-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="193b8-114">Attribute</span></span>|<span data-ttu-id="193b8-115">Opis</span><span class="sxs-lookup"><span data-stu-id="193b8-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="193b8-116">Ustawia preferencje personifikacji, który klient komunikuje się z serwerem.</span><span class="sxs-lookup"><span data-stu-id="193b8-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="193b8-117">Tryb personifikacji, w którym klient wybiera nie są wymuszane na serwerze.</span><span class="sxs-lookup"><span data-stu-id="193b8-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="193b8-118">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="193b8-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="193b8-119">— Identyfikator: Serwera można uzyskać tożsamości i uprawnienia klienta, ale nie można spersonifikować klienta.</span><span class="sxs-lookup"><span data-stu-id="193b8-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="193b8-120">-Personifikacji: Serwer może personifikować klienta kontekstu zabezpieczeń w systemie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="193b8-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="193b8-121">-Delegowania: Serwer może personifikować klienta kontekstu zabezpieczeń w systemach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="193b8-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="193b8-122">-Anonimowe: Serwer nie może Cię personifikacji lub identyfikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="193b8-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="193b8-123">-Brak: Poziom personifikacji nie jest przypisany.</span><span class="sxs-lookup"><span data-stu-id="193b8-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="193b8-124">Wartość domyślna to identyfikator.</span><span class="sxs-lookup"><span data-stu-id="193b8-124">The default is Identification.</span></span> <span data-ttu-id="193b8-125">Ten atrybut jest typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="193b8-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="193b8-126">Ustawienie tej właściwości na `true` umożliwia uwierzytelnianie do poziomu starszej wersji NTLM Jeśli protokołu Kerberos nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="193b8-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="193b8-127">Ustawienie tej właściwości na `false` powoduje, że [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] dokonanie optymalnych zostać zgłoszony wyjątek, jeśli używane jest uwierzytelnianie NTLM.</span><span class="sxs-lookup"><span data-stu-id="193b8-127">Setting this property to `false` causes [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="193b8-128">Należy pamiętać, że ustawienie tej właściwości na `false` może uniemożliwia poświadczeń NTLM są przesyłane przez sieć.</span><span class="sxs-lookup"><span data-stu-id="193b8-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="193b8-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="193b8-129">Child Elements</span></span>  
 <span data-ttu-id="193b8-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="193b8-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="193b8-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="193b8-131">Parent Elements</span></span>  
  
|<span data-ttu-id="193b8-132">Element</span><span class="sxs-lookup"><span data-stu-id="193b8-132">Element</span></span>|<span data-ttu-id="193b8-133">Opis</span><span class="sxs-lookup"><span data-stu-id="193b8-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="193b8-134">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="193b8-134">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="193b8-135">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="193b8-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="193b8-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="193b8-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WindowsClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 [<span data-ttu-id="193b8-137">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="193b8-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="193b8-138">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="193b8-138">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="193b8-139">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="193b8-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
