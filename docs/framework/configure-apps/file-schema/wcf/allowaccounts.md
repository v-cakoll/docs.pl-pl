---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 74b9d51b7400469c96fc9c8b36e4b0fb1d46969b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398403"
---
# \<allowAccounts>
<span data-ttu-id="0add4-101">Zawiera kolekcję elementów konfiguracji, które określają konta użytkowników dla procesów, które obsługują usługi Windows Communication Foundation (WCF) i uzyskują dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="0add4-101">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**  
  
## <a name="syntax"></a><span data-ttu-id="0add4-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="0add4-102">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0add4-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0add4-103">Attributes and Elements</span></span>  
 <span data-ttu-id="0add4-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0add4-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0add4-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0add4-105">Attributes</span></span>  
 <span data-ttu-id="0add4-106">Brak.</span><span class="sxs-lookup"><span data-stu-id="0add4-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0add4-107">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0add4-107">Child Elements</span></span>  
  
|<span data-ttu-id="0add4-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0add4-108">Attribute</span></span>|<span data-ttu-id="0add4-109">Opis</span><span class="sxs-lookup"><span data-stu-id="0add4-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-allowaccounts.md)|<span data-ttu-id="0add4-110">Dodaje konto użytkownika dla procesów, które obsługują usługi WCF i uzyskuje dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="0add4-110">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0add4-111">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0add4-111">Parent Elements</span></span>  
  
|<span data-ttu-id="0add4-112">Element</span><span class="sxs-lookup"><span data-stu-id="0add4-112">Element</span></span>|<span data-ttu-id="0add4-113">Opis</span><span class="sxs-lookup"><span data-stu-id="0add4-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0add4-114">[\<net.pipe>](net-pipe.md)oraz[\<net.tcp>](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="0add4-114">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="0add4-115">Określa ustawienia konfiguracji dla potoku sieci lub usług współużytkowania TCP.</span><span class="sxs-lookup"><span data-stu-id="0add4-115">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0add4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0add4-116">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
