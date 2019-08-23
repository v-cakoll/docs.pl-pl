---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: c62f29c53d807cab397ff09c6163d924a71ea319
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926597"
---
# <a name="allowaccounts"></a><span data-ttu-id="9c544-101">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="9c544-101">\<allowAccounts></span></span>
<span data-ttu-id="9c544-102">Zawiera kolekcję elementów konfiguracji, które określają konta użytkowników dla procesów, które obsługują usługi Windows Communication Foundation (WCF) i uzyskują dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="9c544-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="9c544-103">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="9c544-103">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c544-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c544-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c544-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9c544-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9c544-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9c544-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c544-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9c544-107">Attributes</span></span>  
 <span data-ttu-id="9c544-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="9c544-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9c544-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9c544-109">Child Elements</span></span>  
  
|<span data-ttu-id="9c544-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9c544-110">Attribute</span></span>|<span data-ttu-id="9c544-111">Opis</span><span class="sxs-lookup"><span data-stu-id="9c544-111">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="9c544-112">\<add></span><span class="sxs-lookup"><span data-stu-id="9c544-112">\<add></span></span>](add-of-allowaccounts.md)|<span data-ttu-id="9c544-113">Dodaje konto użytkownika dla procesów, które obsługują usługi WCF i uzyskuje dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="9c544-113">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9c544-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9c544-114">Parent Elements</span></span>  
  
|<span data-ttu-id="9c544-115">Element</span><span class="sxs-lookup"><span data-stu-id="9c544-115">Element</span></span>|<span data-ttu-id="9c544-116">Opis</span><span class="sxs-lookup"><span data-stu-id="9c544-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c544-117">NET. pipe > lub [ \<](net-pipe.md) [ \<net. TCP >](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="9c544-117">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="9c544-118">Określa ustawienia konfiguracji dla potoku sieci lub usług współużytkowania TCP.</span><span class="sxs-lookup"><span data-stu-id="9c544-118">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c544-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c544-119">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
