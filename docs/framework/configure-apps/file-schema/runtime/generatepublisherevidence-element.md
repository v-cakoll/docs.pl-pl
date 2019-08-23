---
title: <generatePublisherEvidence>, element
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5314fe5927abf2d3855acb45c763507ab6cb3c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920749"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="16508-102">\<generatePublisherEvidence> Element</span><span class="sxs-lookup"><span data-stu-id="16508-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="16508-103">Określa, czy środowisko uruchomieniowe tworzy <xref:System.Security.Policy.Publisher> dowód dla zabezpieczeń dostępu kodu (CAS).</span><span class="sxs-lookup"><span data-stu-id="16508-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
 <span data-ttu-id="16508-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="16508-104">\<configuration></span></span>  
<span data-ttu-id="16508-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="16508-105">\<runtime></span></span>  
<span data-ttu-id="16508-106">\<generatePublisherEvidence></span><span class="sxs-lookup"><span data-stu-id="16508-106">\<generatePublisherEvidence></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16508-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="16508-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16508-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="16508-108">Attributes and Elements</span></span>  
 <span data-ttu-id="16508-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="16508-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16508-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="16508-110">Attributes</span></span>  
  
|<span data-ttu-id="16508-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="16508-111">Attribute</span></span>|<span data-ttu-id="16508-112">Opis</span><span class="sxs-lookup"><span data-stu-id="16508-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="16508-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="16508-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="16508-114">Określa, czy środowisko uruchomieniowe tworzy <xref:System.Security.Policy.Publisher> dowód.</span><span class="sxs-lookup"><span data-stu-id="16508-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="16508-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="16508-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="16508-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="16508-116">Value</span></span>|<span data-ttu-id="16508-117">Opis</span><span class="sxs-lookup"><span data-stu-id="16508-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="16508-118">Nie tworzy <xref:System.Security.Policy.Publisher> dowodów.</span><span class="sxs-lookup"><span data-stu-id="16508-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="16508-119">Tworzy <xref:System.Security.Policy.Publisher> dowód.</span><span class="sxs-lookup"><span data-stu-id="16508-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="16508-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="16508-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16508-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="16508-121">Child Elements</span></span>  
 <span data-ttu-id="16508-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="16508-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16508-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="16508-123">Parent Elements</span></span>  
  
|<span data-ttu-id="16508-124">Element</span><span class="sxs-lookup"><span data-stu-id="16508-124">Element</span></span>|<span data-ttu-id="16508-125">Opis</span><span class="sxs-lookup"><span data-stu-id="16508-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="16508-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16508-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="16508-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="16508-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16508-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="16508-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16508-129">W .NET Framework 4 i nowszych ten element nie ma wpływu na czasy ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="16508-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="16508-130">Aby uzyskać więcej informacji, zobacz sekcję "uproszczenie zasad zabezpieczeń" w temacie [zmiany zabezpieczeń](../../../security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="16508-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../security/security-changes.md).</span></span>  
  
 <span data-ttu-id="16508-131">Środowisko uruchomieniowe języka wspólnego (CLR) próbuje zweryfikować podpis Authenticode w czasie ładowania, aby <xref:System.Security.Policy.Publisher> utworzyć dowód dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="16508-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="16508-132">Jednak domyślnie większość aplikacji nie potrzebuje <xref:System.Security.Policy.Publisher> dowodu.</span><span class="sxs-lookup"><span data-stu-id="16508-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="16508-133">Standardowe zasady CAS nie bazują na <xref:System.Security.Policy.PublisherMembershipCondition>.</span><span class="sxs-lookup"><span data-stu-id="16508-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="16508-134">Należy unikać niepotrzebnego kosztu uruchomienia związanego z weryfikacją podpisu wydawcy, chyba że aplikacja jest wykonywana na komputerze z niestandardowymi zasadami CAS lub nie spełnia wymagań dotyczących <xref:System.Security.Permissions.PublisherIdentityPermission> w środowisku częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="16508-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="16508-135">(Wymagania dotyczące uprawnień tożsamości zawsze powiodło się w środowisku pełnego zaufania).</span><span class="sxs-lookup"><span data-stu-id="16508-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16508-136">Zalecamy, aby usługi korzystały `<generatePublisherEvidence>` z elementu, aby zwiększyć wydajność uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="16508-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="16508-137">Za pomocą tego elementu można także uniknąć opóźnień, które mogą spowodować przekroczenie limitu czasu i anulowanie uruchamiania usługi.</span><span class="sxs-lookup"><span data-stu-id="16508-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="16508-138">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="16508-138">Configuration File</span></span>  
 <span data-ttu-id="16508-139">Tego elementu można używać tylko w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16508-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16508-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="16508-140">Example</span></span>  
 <span data-ttu-id="16508-141">Poniższy przykład pokazuje, jak użyć elementu, `<generatePublisherEvidence>` aby wyłączyć sprawdzanie zasad wydawcy CAS dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16508-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="16508-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16508-142">See also</span></span>

- [<span data-ttu-id="16508-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="16508-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="16508-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="16508-144">Configuration File Schema</span></span>](../index.md)
