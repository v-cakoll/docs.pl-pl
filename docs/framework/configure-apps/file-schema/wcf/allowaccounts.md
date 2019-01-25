---
title: '&lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: c1c4630e6191dbbe02688a4e4a9db9e18b8d36d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508421"
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="709d8-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="709d8-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="709d8-103">Zawiera kolekcję elementów konfiguracji, które określają użytkownika konta dla procesów hostujących usługi Windows Communication Foundation (WCF) i przyznano im dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="709d8-103">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="709d8-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="709d8-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="709d8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="709d8-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="709d8-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="709d8-106">Attributes and Elements</span></span>  
 <span data-ttu-id="709d8-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="709d8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="709d8-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="709d8-108">Attributes</span></span>  
 <span data-ttu-id="709d8-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="709d8-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="709d8-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="709d8-110">Child Elements</span></span>  
  
|<span data-ttu-id="709d8-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="709d8-111">Attribute</span></span>|<span data-ttu-id="709d8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="709d8-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="709d8-113">\<add></span><span class="sxs-lookup"><span data-stu-id="709d8-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="709d8-114">Dodaje konto użytkownika dla procesów, które prowadzą hosting usług WCF i przyznano im dostęp do połączenia z usługą udostępniania</span><span class="sxs-lookup"><span data-stu-id="709d8-114">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="709d8-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="709d8-115">Parent Elements</span></span>  
  
|<span data-ttu-id="709d8-116">Element</span><span class="sxs-lookup"><span data-stu-id="709d8-116">Element</span></span>|<span data-ttu-id="709d8-117">Opis</span><span class="sxs-lookup"><span data-stu-id="709d8-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="709d8-118">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) lub [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="709d8-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="709d8-119">Określa ustawienia konfiguracji dla Net potoku lub TCP usługi udostępniania.</span><span class="sxs-lookup"><span data-stu-id="709d8-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="709d8-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="709d8-120">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
