---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: fd3121146577122446ba82528fc6e46dadbf5033
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255552"
---
# <a name="allowaccounts"></a><span data-ttu-id="a1a1b-101">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="a1a1b-101">\<allowAccounts></span></span>
<span data-ttu-id="a1a1b-102">Zawiera kolekcję elementów konfiguracji, które określają użytkownika konta dla procesów hostujących usługi Windows Communication Foundation (WCF) i przyznano im dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="a1a1b-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="a1a1b-103">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="a1a1b-103">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1a1b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1a1b-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1a1b-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a1a1b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a1a1b-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a1a1b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1a1b-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a1a1b-107">Attributes</span></span>  
 <span data-ttu-id="a1a1b-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="a1a1b-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a1a1b-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a1a1b-109">Child Elements</span></span>  
  
|<span data-ttu-id="a1a1b-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a1a1b-110">Attribute</span></span>|<span data-ttu-id="a1a1b-111">Opis</span><span class="sxs-lookup"><span data-stu-id="a1a1b-111">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="a1a1b-112">\<add></span><span class="sxs-lookup"><span data-stu-id="a1a1b-112">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="a1a1b-113">Dodaje konto użytkownika dla procesów, które prowadzą hosting usług WCF i przyznano im dostęp do połączenia z usługą udostępniania</span><span class="sxs-lookup"><span data-stu-id="a1a1b-113">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a1a1b-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a1a1b-114">Parent Elements</span></span>  
  
|<span data-ttu-id="a1a1b-115">Element</span><span class="sxs-lookup"><span data-stu-id="a1a1b-115">Element</span></span>|<span data-ttu-id="a1a1b-116">Opis</span><span class="sxs-lookup"><span data-stu-id="a1a1b-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1a1b-117">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) lub [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="a1a1b-117">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="a1a1b-118">Określa ustawienia konfiguracji dla Net potoku lub TCP usługi udostępniania.</span><span class="sxs-lookup"><span data-stu-id="a1a1b-118">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a1a1b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1a1b-119">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
