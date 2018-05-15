---
title: '&lt;add&gt; w &lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 2230b8d22a14c3df5eb3aa10872246febce015e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="0f174-102">&lt;add&gt; w &lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="0f174-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="0f174-103">Określa konto użytkownika dla procesów, które host usługi WCF i przyznano im dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="0f174-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="0f174-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="0f174-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f174-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f174-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f174-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0f174-106">Attributes and Elements</span></span>  
 <span data-ttu-id="0f174-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0f174-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f174-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0f174-108">Attributes</span></span>  
  
|<span data-ttu-id="0f174-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0f174-109">Attribute</span></span>|<span data-ttu-id="0f174-110">Opis</span><span class="sxs-lookup"><span data-stu-id="0f174-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0f174-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="0f174-111">securityIdentifier</span></span>|<span data-ttu-id="0f174-112">Ciąg określający unikatowy identyfikator używany do identyfikowania konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0f174-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="0f174-113">Wartości domyślne są LocalSystem, Administratorzy, NS, LS i IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="0f174-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f174-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0f174-114">Child Elements</span></span>  
 <span data-ttu-id="0f174-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="0f174-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0f174-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0f174-116">Parent Elements</span></span>  
  
|<span data-ttu-id="0f174-117">Element</span><span class="sxs-lookup"><span data-stu-id="0f174-117">Element</span></span>|<span data-ttu-id="0f174-118">Opis</span><span class="sxs-lookup"><span data-stu-id="0f174-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f174-119">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="0f174-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="0f174-120">Kolekcja elementów konfiguracji, które zawierają `securityIdentifier` atrybutu określ konta użytkowników dla procesów, które host usługi WCF i przyznano im dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="0f174-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0f174-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f174-121">Example</span></span>  
 <span data-ttu-id="0f174-122">W poniższym przykładzie konfiguracji dodaje identyfikatory pięć domyślnych dla kont użytkowników do tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0f174-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0f174-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f174-123">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
