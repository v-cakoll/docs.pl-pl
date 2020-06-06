---
title: <add> dla <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 02654b8ab198a2b161b3044c1f3aa452761a6a4c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398377"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="8d07b-102">\<add> dla \<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="8d07b-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="8d07b-103">Określa konto użytkownika dla procesów, które obsługują usługi WCF i ma dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="8d07b-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowAccounts>**](allowaccounts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="8d07b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d07b-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d07b-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8d07b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8d07b-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8d07b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d07b-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8d07b-107">Attributes</span></span>  
  
|<span data-ttu-id="8d07b-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8d07b-108">Attribute</span></span>|<span data-ttu-id="8d07b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8d07b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d07b-110">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="8d07b-110">securityIdentifier</span></span>|<span data-ttu-id="8d07b-111">Ciąg określający unikatowy identyfikator używany do identyfikowania konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8d07b-111">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="8d07b-112">Wartości domyślne to LocalSystem, Administratorzy, NS, LS i IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="8d07b-112">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d07b-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8d07b-113">Child Elements</span></span>  
 <span data-ttu-id="8d07b-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="8d07b-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d07b-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8d07b-115">Parent Elements</span></span>  
  
|<span data-ttu-id="8d07b-116">Element</span><span class="sxs-lookup"><span data-stu-id="8d07b-116">Element</span></span>|<span data-ttu-id="8d07b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="8d07b-117">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="8d07b-118">Kolekcja elementów konfiguracji, które zawierają atrybut służący `securityIdentifier` do określania kont użytkowników dla procesów, które obsługują usługi WCF i mają dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="8d07b-118">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8d07b-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d07b-119">Example</span></span>  
 <span data-ttu-id="8d07b-120">Poniższy przykład konfiguracji dodaje pięć domyślnych identyfikatorów kont użytkowników do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8d07b-120">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d07b-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d07b-121">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
