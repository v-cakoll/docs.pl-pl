---
title: <add> z <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 1c6764b37b2aa5349b8ccf63e6b7c2bc580b69b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186605"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="b3643-102">\<Dodaj > z \<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="b3643-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="b3643-103">Określa konto użytkownika dla procesów, które prowadzą hosting usług WCF i przyznano im dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="b3643-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="b3643-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="b3643-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3643-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3643-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3643-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b3643-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b3643-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b3643-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3643-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b3643-108">Attributes</span></span>  
  
|<span data-ttu-id="b3643-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b3643-109">Attribute</span></span>|<span data-ttu-id="b3643-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b3643-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b3643-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="b3643-111">securityIdentifier</span></span>|<span data-ttu-id="b3643-112">Ciąg, który określa unikatowy identyfikator używany do identyfikowania konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b3643-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="b3643-113">Wartości domyślne to konto systemu lokalnego, Administratorzy, NS, LS i IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="b3643-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3643-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b3643-114">Child Elements</span></span>  
 <span data-ttu-id="b3643-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="b3643-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b3643-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b3643-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b3643-117">Element</span><span class="sxs-lookup"><span data-stu-id="b3643-117">Element</span></span>|<span data-ttu-id="b3643-118">Opis</span><span class="sxs-lookup"><span data-stu-id="b3643-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3643-119">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="b3643-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="b3643-120">Kolekcja elementów konfiguracji, które zawierają `securityIdentifier` atrybutu, aby określić konta użytkowników dla procesów, które prowadzą hosting usług WCF i przyznano im dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="b3643-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b3643-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3643-121">Example</span></span>  
 <span data-ttu-id="b3643-122">W poniższym przykładzie konfiguracji dodaje identyfikatory pięć domyślnych dla kont użytkowników do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b3643-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3643-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3643-123">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
