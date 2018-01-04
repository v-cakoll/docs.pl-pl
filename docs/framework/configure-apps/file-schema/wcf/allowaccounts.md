---
title: '&lt;allowAccounts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a1716aa77808b2a9f8f3ca903dabf81b21b8f709
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="ca988-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="ca988-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="ca988-103">Zawiera kolekcję elementów konfiguracyjnych określających konta użytkowników dla procesów obsługujących [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usług i przyznano im dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="ca988-103">Contains a collection of configuration elements that specify user accounts for processes that host [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="ca988-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="ca988-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca988-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca988-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca988-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ca988-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ca988-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ca988-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca988-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ca988-108">Attributes</span></span>  
 <span data-ttu-id="ca988-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="ca988-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ca988-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ca988-110">Child Elements</span></span>  
  
|<span data-ttu-id="ca988-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ca988-111">Attribute</span></span>|<span data-ttu-id="ca988-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ca988-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="ca988-113">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="ca988-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="ca988-114">Dodaje konto użytkownika dla procesów obsługujących [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług i przyznano im dostęp do połączenia z usługą udostępniania</span><span class="sxs-lookup"><span data-stu-id="ca988-114">Adds a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca988-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ca988-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ca988-116">Element</span><span class="sxs-lookup"><span data-stu-id="ca988-116">Element</span></span>|<span data-ttu-id="ca988-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ca988-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca988-118">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) lub [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="ca988-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="ca988-119">Określa ustawienia konfiguracji dla potoku Net lub TCP usługi udostępniania.</span><span class="sxs-lookup"><span data-stu-id="ca988-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca988-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca988-120">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
