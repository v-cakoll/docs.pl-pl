---
title: "&lt;generatePublisherEvidence&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c7f7debed03526dbd7a5b2e24ff8a370921fe020
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltgeneratepublisherevidencegt-element"></a><span data-ttu-id="17da2-102">&lt;generatePublisherEvidence&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="17da2-102">&lt;generatePublisherEvidence&gt; Element</span></span>
<span data-ttu-id="17da2-103">Określa, czy środowisko uruchomieniowe utworzy <xref:System.Security.Policy.Publisher> dowodów zabezpieczeń dostępu kodu (CAS).</span><span class="sxs-lookup"><span data-stu-id="17da2-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
 <span data-ttu-id="17da2-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="17da2-104">\<configuration></span></span>  
<span data-ttu-id="17da2-105">\<Runtime ></span><span class="sxs-lookup"><span data-stu-id="17da2-105">\<runtime></span></span>  
<span data-ttu-id="17da2-106">\<generatePublisherEvidence ></span><span class="sxs-lookup"><span data-stu-id="17da2-106">\<generatePublisherEvidence></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17da2-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="17da2-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17da2-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="17da2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="17da2-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="17da2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17da2-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="17da2-110">Attributes</span></span>  
  
|<span data-ttu-id="17da2-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="17da2-111">Attribute</span></span>|<span data-ttu-id="17da2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="17da2-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="17da2-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="17da2-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="17da2-114">Określa, czy środowisko uruchomieniowe utworzy <xref:System.Security.Policy.Publisher> dowód.</span><span class="sxs-lookup"><span data-stu-id="17da2-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="17da2-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="17da2-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="17da2-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="17da2-116">Value</span></span>|<span data-ttu-id="17da2-117">Opis</span><span class="sxs-lookup"><span data-stu-id="17da2-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="17da2-118">Nie tworzy <xref:System.Security.Policy.Publisher> dowód.</span><span class="sxs-lookup"><span data-stu-id="17da2-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="17da2-119">Tworzy <xref:System.Security.Policy.Publisher> dowód.</span><span class="sxs-lookup"><span data-stu-id="17da2-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="17da2-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="17da2-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17da2-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="17da2-121">Child Elements</span></span>  
 <span data-ttu-id="17da2-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="17da2-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="17da2-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="17da2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="17da2-124">Element</span><span class="sxs-lookup"><span data-stu-id="17da2-124">Element</span></span>|<span data-ttu-id="17da2-125">Opis</span><span class="sxs-lookup"><span data-stu-id="17da2-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="17da2-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="17da2-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="17da2-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="17da2-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17da2-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17da2-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17da2-129">W [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] i później, ten element nie ma wpływu na czas ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="17da2-129">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="17da2-130">Aby uzyskać więcej informacji, zobacz sekcję "Uproszczenia zasad zabezpieczeń" w [zmiany zabezpieczeń](../../../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="17da2-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="17da2-131">Środowisko uruchomieniowe języka wspólnego (CLR) próbuje zweryfikować podpisu Authenticode w czasie ładowania, aby utworzyć <xref:System.Security.Policy.Publisher> dowody dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="17da2-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="17da2-132">Domyślnie większość aplikacji muszą jednak <xref:System.Security.Policy.Publisher> dowód.</span><span class="sxs-lookup"><span data-stu-id="17da2-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="17da2-133">Standardowe zasady CAS nie bazuje na <xref:System.Security.Policy.PublisherMembershipCondition>.</span><span class="sxs-lookup"><span data-stu-id="17da2-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="17da2-134">Należy unikać koszt uruchamiania niepotrzebnych związany z weryfikowanie podpisu wydawcy, chyba że aplikacja wykonuje na komputerze z niestandardowych zasad CAS lub mają zostać do zaspokojenia potrzeb <xref:System.Security.Permissions.PublisherIdentityPermission> w środowisku z częściowym zaufaniem.</span><span class="sxs-lookup"><span data-stu-id="17da2-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="17da2-135">(Wymagania dotyczące uprawnień tożsamości zawsze powiedzie się w pełni zaufanym środowisku).</span><span class="sxs-lookup"><span data-stu-id="17da2-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17da2-136">Zaleca się, że usługi użyj `<generatePublisherEvidence>` elementu, aby poprawić wydajność uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="17da2-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="17da2-137">Za pomocą tego elementu może również pomóc uniknąć opóźnienia, które mogą spowodować limit czasu i anulowania uruchomienia usługi.</span><span class="sxs-lookup"><span data-stu-id="17da2-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="17da2-138">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="17da2-138">Configuration File</span></span>  
 <span data-ttu-id="17da2-139">Ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17da2-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17da2-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="17da2-140">Example</span></span>  
 <span data-ttu-id="17da2-141">Poniższy przykład przedstawia użycie `<generatePublisherEvidence>` element, aby wyłączyć sprawdzanie urzędów certyfikacji zasad wydawcy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17da2-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="17da2-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17da2-142">See Also</span></span>  
 [<span data-ttu-id="17da2-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="17da2-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="17da2-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="17da2-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
