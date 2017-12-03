---
title: '&lt;add&gt; w &lt;allowAccounts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09ab06bb94249e79743335da1a360f6b668b1d86
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="dff49-102">&lt;add&gt; w &lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="dff49-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="dff49-103">Określa konta użytkownika dla procesów obsługujących [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług i przyznano im dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="dff49-103">Specifies a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="dff49-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="dff49-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dff49-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dff49-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dff49-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dff49-106">Attributes and Elements</span></span>  
 <span data-ttu-id="dff49-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dff49-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dff49-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dff49-108">Attributes</span></span>  
  
|<span data-ttu-id="dff49-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dff49-109">Attribute</span></span>|<span data-ttu-id="dff49-110">Opis</span><span class="sxs-lookup"><span data-stu-id="dff49-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dff49-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="dff49-111">securityIdentifier</span></span>|<span data-ttu-id="dff49-112">Ciąg określający unikatowy identyfikator używany do identyfikowania konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dff49-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="dff49-113">Wartości domyślne są LocalSystem, Administratorzy, NS, LS i IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="dff49-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dff49-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dff49-114">Child Elements</span></span>  
 <span data-ttu-id="dff49-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="dff49-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dff49-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dff49-116">Parent Elements</span></span>  
  
|<span data-ttu-id="dff49-117">Element</span><span class="sxs-lookup"><span data-stu-id="dff49-117">Element</span></span>|<span data-ttu-id="dff49-118">Opis</span><span class="sxs-lookup"><span data-stu-id="dff49-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dff49-119">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="dff49-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="dff49-120">Kolekcja elementów konfiguracji, które zawierają `securityIdentifier` atrybutu, aby określić konta użytkowników dla procesów obsługujących [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług i przyznano im dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="dff49-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dff49-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="dff49-121">Example</span></span>  
 <span data-ttu-id="dff49-122">W poniższym przykładzie konfiguracji dodaje identyfikatory pięć domyślnych dla kont użytkowników do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="dff49-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
```xml  
<allowAccounts>  
   // LocalSystem account  
   <add securityIdentifier="S-1-5-18"/>  
   // LocalService account  
   <add securityIdentifier="S-1-5-19"/>  
   // Administrators account  
   <add securityIdentifier="S-1-5-20"/>  
   // Network Service account  
   <add securityIdentifier="S-1-5-32-544" />  
   // IIS_IUSRS account (Vista only)  
   <add securityIdentifier="S-1-5-32-568"/>  
</allowAccounts>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dff49-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dff49-123">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
