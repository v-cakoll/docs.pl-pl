---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 74b9d51b7400469c96fc9c8b36e4b0fb1d46969b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398403"
---
# <a name="allowaccounts"></a><span data-ttu-id="4dadc-101">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="4dadc-101">\<allowAccounts></span></span>
<span data-ttu-id="4dadc-102">Zawiera kolekcję elementów konfiguracji, które określają konta użytkowników dla procesów, które obsługują usługi Windows Communication Foundation (WCF) i uzyskują dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="4dadc-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
<span data-ttu-id="4dadc-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4dadc-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4dadc-104">&nbsp;&nbsp;[ **\<> System. serviceModel. Activation**](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="4dadc-104">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="4dadc-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> net. pipe**](net-pipe.md)</span><span class="sxs-lookup"><span data-stu-id="4dadc-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)</span></span>\
<span data-ttu-id="4dadc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<allowAccounts >**</span><span class="sxs-lookup"><span data-stu-id="4dadc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dadc-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="4dadc-107">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4dadc-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4dadc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4dadc-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4dadc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4dadc-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4dadc-110">Attributes</span></span>  
 <span data-ttu-id="4dadc-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="4dadc-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4dadc-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4dadc-112">Child Elements</span></span>  
  
|<span data-ttu-id="4dadc-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4dadc-113">Attribute</span></span>|<span data-ttu-id="4dadc-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4dadc-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="4dadc-115">\<add></span><span class="sxs-lookup"><span data-stu-id="4dadc-115">\<add></span></span>](add-of-allowaccounts.md)|<span data-ttu-id="4dadc-116">Dodaje konto użytkownika dla procesów, które obsługują usługi WCF i uzyskuje dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="4dadc-116">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4dadc-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4dadc-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4dadc-118">Element</span><span class="sxs-lookup"><span data-stu-id="4dadc-118">Element</span></span>|<span data-ttu-id="4dadc-119">Opis</span><span class="sxs-lookup"><span data-stu-id="4dadc-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4dadc-120">NET. pipe > lub [ \<](net-pipe.md) [ \<net. TCP >](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="4dadc-120">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="4dadc-121">Określa ustawienia konfiguracji dla potoku sieci lub usług współużytkowania TCP.</span><span class="sxs-lookup"><span data-stu-id="4dadc-121">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4dadc-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4dadc-122">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
