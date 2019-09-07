---
title: <add> dla <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 02654b8ab198a2b161b3044c1f3aa452761a6a4c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398377"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="f8e38-102">\<Dodawanie > \<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="f8e38-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="f8e38-103">Określa konto użytkownika dla procesów, które obsługują usługi WCF i ma dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="f8e38-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
<span data-ttu-id="f8e38-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f8e38-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f8e38-105">&nbsp;&nbsp;[ **\<> System. serviceModel. Activation**](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="f8e38-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="f8e38-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> net. pipe**](net-pipe.md)</span><span class="sxs-lookup"><span data-stu-id="f8e38-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)</span></span>\
<span data-ttu-id="f8e38-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<allowAccounts >** ](allowaccounts.md)</span><span class="sxs-lookup"><span data-stu-id="f8e38-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowAccounts>**](allowaccounts.md)</span></span>\
<span data-ttu-id="f8e38-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="f8e38-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8e38-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8e38-109">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8e38-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f8e38-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f8e38-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f8e38-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8e38-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f8e38-112">Attributes</span></span>  
  
|<span data-ttu-id="f8e38-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f8e38-113">Attribute</span></span>|<span data-ttu-id="f8e38-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f8e38-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f8e38-115">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="f8e38-115">securityIdentifier</span></span>|<span data-ttu-id="f8e38-116">Ciąg określający unikatowy identyfikator używany do identyfikowania konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f8e38-116">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="f8e38-117">Wartości domyślne to LocalSystem, Administratorzy, NS, LS i IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="f8e38-117">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8e38-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f8e38-118">Child Elements</span></span>  
 <span data-ttu-id="f8e38-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="f8e38-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f8e38-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f8e38-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f8e38-121">Element</span><span class="sxs-lookup"><span data-stu-id="f8e38-121">Element</span></span>|<span data-ttu-id="f8e38-122">Opis</span><span class="sxs-lookup"><span data-stu-id="f8e38-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8e38-123">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="f8e38-123">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="f8e38-124">Kolekcja elementów konfiguracji, które zawierają `securityIdentifier` atrybut służący do określania kont użytkowników dla procesów, które obsługują usługi WCF i mają dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="f8e38-124">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f8e38-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8e38-125">Example</span></span>  
 <span data-ttu-id="f8e38-126">Poniższy przykład konfiguracji dodaje pięć domyślnych identyfikatorów kont użytkowników do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f8e38-126">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
```xml  
<allowAccounts>
  <!-- LocalSystem account -->
  <add securityIdentifier="S-1-5-18" />
  <!-- LocalService account -->
  <add securityIdentifier="S-1-5-19" />
  <!-- Administrators account -->
  <add securityIdentifier="S-1-5-20" />
  <!-- Network Service account -->
  <add securityIdentifier="S-1-5-32-544" />
  <!-- IIS_IUSRS account (Vista only) -->
  <add securityIdentifier="S-1-5-32-568" />
</allowAccounts>
```  
  
## <a name="see-also"></a><span data-ttu-id="f8e38-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8e38-127">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
