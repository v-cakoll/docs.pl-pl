---
title: '&lt;generatePublisherEvidence&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33d4c023b7a649fd2aa3d9d52a90bb7111c59743
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683037"
---
# <a name="ltgeneratepublisherevidencegt-element"></a><span data-ttu-id="45794-102">&lt;generatePublisherEvidence&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="45794-102">&lt;generatePublisherEvidence&gt; Element</span></span>
<span data-ttu-id="45794-103">Określa, czy środowisko uruchomieniowe tworzy <xref:System.Security.Policy.Publisher> dowodów dla zabezpieczeń dostępu kodu (CAS).</span><span class="sxs-lookup"><span data-stu-id="45794-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
 <span data-ttu-id="45794-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="45794-104">\<configuration></span></span>  
<span data-ttu-id="45794-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="45794-105">\<runtime></span></span>  
<span data-ttu-id="45794-106">\<generatePublisherEvidence></span><span class="sxs-lookup"><span data-stu-id="45794-106">\<generatePublisherEvidence></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45794-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="45794-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45794-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="45794-108">Attributes and Elements</span></span>  
 <span data-ttu-id="45794-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="45794-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45794-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="45794-110">Attributes</span></span>  
  
|<span data-ttu-id="45794-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="45794-111">Attribute</span></span>|<span data-ttu-id="45794-112">Opis</span><span class="sxs-lookup"><span data-stu-id="45794-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="45794-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="45794-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="45794-114">Określa, czy środowisko uruchomieniowe tworzy <xref:System.Security.Policy.Publisher> dowodów.</span><span class="sxs-lookup"><span data-stu-id="45794-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="45794-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="45794-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="45794-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="45794-116">Value</span></span>|<span data-ttu-id="45794-117">Opis</span><span class="sxs-lookup"><span data-stu-id="45794-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="45794-118">Nie powoduje utworzenia <xref:System.Security.Policy.Publisher> dowodów.</span><span class="sxs-lookup"><span data-stu-id="45794-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="45794-119">Tworzy <xref:System.Security.Policy.Publisher> dowodów.</span><span class="sxs-lookup"><span data-stu-id="45794-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="45794-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="45794-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45794-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="45794-121">Child Elements</span></span>  
 <span data-ttu-id="45794-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="45794-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45794-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="45794-123">Parent Elements</span></span>  
  
|<span data-ttu-id="45794-124">Element</span><span class="sxs-lookup"><span data-stu-id="45794-124">Element</span></span>|<span data-ttu-id="45794-125">Opis</span><span class="sxs-lookup"><span data-stu-id="45794-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="45794-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="45794-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="45794-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="45794-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45794-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45794-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45794-129">W [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] i nowszym, ten element nie ma wpływu na krótszy czas ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="45794-129">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="45794-130">Aby uzyskać więcej informacji, zobacz sekcję "Uproszczenia zasad zabezpieczeń" w [zmiany zabezpieczeń](../../../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="45794-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="45794-131">Środowisko uruchomieniowe języka wspólnego (CLR) próbuje zweryfikować podpisu Authenticode w czasie ładowania, aby utworzyć <xref:System.Security.Policy.Publisher> dowodu dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="45794-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="45794-132">Jednak domyślnie większość aplikacji nie ma potrzeby <xref:System.Security.Policy.Publisher> dowodów.</span><span class="sxs-lookup"><span data-stu-id="45794-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="45794-133">Standardowe zasady CAS nie zależą od <xref:System.Security.Policy.PublisherMembershipCondition>.</span><span class="sxs-lookup"><span data-stu-id="45794-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="45794-134">Należy unikać koszt uruchamiania niepotrzebnych związany z weryfikacji podpisu wydawcy, chyba że aplikacja wykonuje na komputerze za pomocą zasad niestandardowych urzędów certyfikacji lub zamierzający spełniają wymagania dla <xref:System.Security.Permissions.PublisherIdentityPermission> w środowisku częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="45794-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="45794-135">(Wymagania dotyczące uprawnień tożsamości zawsze powiedzie się w środowisku pełnego zaufania).</span><span class="sxs-lookup"><span data-stu-id="45794-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45794-136">Firma Microsoft zaleca, usługi, użyj `<generatePublisherEvidence>` element, aby zwiększyć wydajność uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="45794-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="45794-137">Przy użyciu tego elementu może również pomóc uniknąć opóźnień, które mogą powodować upływu limitu czasu i anulowania uruchomienia usługi.</span><span class="sxs-lookup"><span data-stu-id="45794-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="45794-138">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="45794-138">Configuration File</span></span>  
 <span data-ttu-id="45794-139">Ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45794-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45794-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="45794-140">Example</span></span>  
 <span data-ttu-id="45794-141">Poniższy przykład pokazuje, jak używać `<generatePublisherEvidence>` elementu, aby wyłączyć sprawdzanie urzędów certyfikacji zasad wydawcy dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45794-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45794-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45794-142">See also</span></span>
- [<span data-ttu-id="45794-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="45794-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="45794-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="45794-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
