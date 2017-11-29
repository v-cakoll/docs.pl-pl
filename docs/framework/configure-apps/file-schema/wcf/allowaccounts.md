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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8e1cf4c4428814361a56b5fd06dcce9e1512c836
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="b92b8-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="b92b8-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="b92b8-103">Zawiera kolekcję elementów konfiguracyjnych określających konta użytkowników dla procesów obsługujących [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usług i przyznano im dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="b92b8-103">Contains a collection of configuration elements that specify user accounts for processes that host [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="b92b8-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="b92b8-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b92b8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b92b8-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b92b8-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b92b8-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b92b8-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b92b8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b92b8-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b92b8-108">Attributes</span></span>  
 <span data-ttu-id="b92b8-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="b92b8-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b92b8-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b92b8-110">Child Elements</span></span>  
  
|<span data-ttu-id="b92b8-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b92b8-111">Attribute</span></span>|<span data-ttu-id="b92b8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b92b8-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="b92b8-113">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="b92b8-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="b92b8-114">Dodaje konto użytkownika dla procesów obsługujących [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług i przyznano im dostęp do połączenia z usługą udostępniania</span><span class="sxs-lookup"><span data-stu-id="b92b8-114">Adds a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b92b8-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b92b8-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b92b8-116">Element</span><span class="sxs-lookup"><span data-stu-id="b92b8-116">Element</span></span>|<span data-ttu-id="b92b8-117">Opis</span><span class="sxs-lookup"><span data-stu-id="b92b8-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b92b8-118">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) lub [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="b92b8-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="b92b8-119">Określa ustawienia konfiguracji dla potoku Net lub TCP usługi udostępniania.</span><span class="sxs-lookup"><span data-stu-id="b92b8-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b92b8-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b92b8-120">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
