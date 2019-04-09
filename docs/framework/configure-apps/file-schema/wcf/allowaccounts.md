---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: f9def3004b116afdc629de136cdfe0b0eb6e75c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102625"
---
# <a name="allowaccounts"></a><span data-ttu-id="fdd77-101">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="fdd77-101">\<allowAccounts></span></span>
<span data-ttu-id="fdd77-102">Zawiera kolekcję elementów konfiguracji, które określają użytkownika konta dla procesów hostujących usługi Windows Communication Foundation (WCF) i przyznano im dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="fdd77-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="fdd77-103">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="fdd77-103">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdd77-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fdd77-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdd77-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fdd77-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fdd77-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fdd77-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdd77-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fdd77-107">Attributes</span></span>  
 <span data-ttu-id="fdd77-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="fdd77-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fdd77-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fdd77-109">Child Elements</span></span>  
  
|<span data-ttu-id="fdd77-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fdd77-110">Attribute</span></span>|<span data-ttu-id="fdd77-111">Opis</span><span class="sxs-lookup"><span data-stu-id="fdd77-111">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="fdd77-112">\<add></span><span class="sxs-lookup"><span data-stu-id="fdd77-112">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="fdd77-113">Dodaje konto użytkownika dla procesów, które prowadzą hosting usług WCF i przyznano im dostęp do połączenia z usługą udostępniania</span><span class="sxs-lookup"><span data-stu-id="fdd77-113">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fdd77-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fdd77-114">Parent Elements</span></span>  
  
|<span data-ttu-id="fdd77-115">Element</span><span class="sxs-lookup"><span data-stu-id="fdd77-115">Element</span></span>|<span data-ttu-id="fdd77-116">Opis</span><span class="sxs-lookup"><span data-stu-id="fdd77-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fdd77-117">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) lub [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="fdd77-117">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="fdd77-118">Określa ustawienia konfiguracji dla Net potoku lub TCP usługi udostępniania.</span><span class="sxs-lookup"><span data-stu-id="fdd77-118">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fdd77-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdd77-119">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
