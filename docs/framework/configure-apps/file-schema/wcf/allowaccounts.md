---
title: '&lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 097112a8b54467843554047882e55b62d7813c0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="939df-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="939df-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="939df-103">Zawiera kolekcję elementów konfiguracji, które określają użytkownika konta dla procesów hostujących usługi Windows Communication Foundation (WCF) i przyznano im dostęp do połączenia do udostępniania usługi.</span><span class="sxs-lookup"><span data-stu-id="939df-103">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="939df-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="939df-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="939df-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="939df-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="939df-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="939df-106">Attributes and Elements</span></span>  
 <span data-ttu-id="939df-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="939df-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="939df-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="939df-108">Attributes</span></span>  
 <span data-ttu-id="939df-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="939df-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="939df-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="939df-110">Child Elements</span></span>  
  
|<span data-ttu-id="939df-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="939df-111">Attribute</span></span>|<span data-ttu-id="939df-112">Opis</span><span class="sxs-lookup"><span data-stu-id="939df-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="939df-113">\<add></span><span class="sxs-lookup"><span data-stu-id="939df-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="939df-114">Dodaje konto użytkownika dla procesów, które host usługi WCF i przyznano im dostęp do połączenia z usługą udostępniania</span><span class="sxs-lookup"><span data-stu-id="939df-114">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="939df-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="939df-115">Parent Elements</span></span>  
  
|<span data-ttu-id="939df-116">Element</span><span class="sxs-lookup"><span data-stu-id="939df-116">Element</span></span>|<span data-ttu-id="939df-117">Opis</span><span class="sxs-lookup"><span data-stu-id="939df-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="939df-118">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) lub [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="939df-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="939df-119">Określa ustawienia konfiguracji dla potoku Net lub TCP usługi udostępniania.</span><span class="sxs-lookup"><span data-stu-id="939df-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="939df-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="939df-120">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
