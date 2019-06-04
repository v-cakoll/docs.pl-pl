---
title: <generatePublisherEvidence>, element
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a0861436ca727d63cdae58e3222826bf6414610
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489446"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="de05b-102">\<generatePublisherEvidence> Element</span><span class="sxs-lookup"><span data-stu-id="de05b-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="de05b-103">Określa, czy środowisko uruchomieniowe tworzy <xref:System.Security.Policy.Publisher> dowodów dla zabezpieczeń dostępu kodu (CAS).</span><span class="sxs-lookup"><span data-stu-id="de05b-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
 <span data-ttu-id="de05b-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="de05b-104">\<configuration></span></span>  
<span data-ttu-id="de05b-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="de05b-105">\<runtime></span></span>  
<span data-ttu-id="de05b-106">\<generatePublisherEvidence></span><span class="sxs-lookup"><span data-stu-id="de05b-106">\<generatePublisherEvidence></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de05b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="de05b-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de05b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="de05b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="de05b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="de05b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de05b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="de05b-110">Attributes</span></span>  
  
|<span data-ttu-id="de05b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="de05b-111">Attribute</span></span>|<span data-ttu-id="de05b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="de05b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="de05b-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="de05b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="de05b-114">Określa, czy środowisko uruchomieniowe tworzy <xref:System.Security.Policy.Publisher> dowodów.</span><span class="sxs-lookup"><span data-stu-id="de05b-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="de05b-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="de05b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="de05b-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="de05b-116">Value</span></span>|<span data-ttu-id="de05b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="de05b-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="de05b-118">Nie powoduje utworzenia <xref:System.Security.Policy.Publisher> dowodów.</span><span class="sxs-lookup"><span data-stu-id="de05b-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="de05b-119">Tworzy <xref:System.Security.Policy.Publisher> dowodów.</span><span class="sxs-lookup"><span data-stu-id="de05b-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="de05b-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="de05b-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de05b-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="de05b-121">Child Elements</span></span>  
 <span data-ttu-id="de05b-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="de05b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de05b-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="de05b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="de05b-124">Element</span><span class="sxs-lookup"><span data-stu-id="de05b-124">Element</span></span>|<span data-ttu-id="de05b-125">Opis</span><span class="sxs-lookup"><span data-stu-id="de05b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="de05b-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="de05b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="de05b-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="de05b-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de05b-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de05b-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de05b-129">W programie .NET Framework 4 i nowsze ten element nie ma wpływu na krótszy czas ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="de05b-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="de05b-130">Aby uzyskać więcej informacji, zobacz sekcję "Uproszczenia zasad zabezpieczeń" w [zmiany zabezpieczeń](../../../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="de05b-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="de05b-131">Środowisko uruchomieniowe języka wspólnego (CLR) próbuje zweryfikować podpisu Authenticode w czasie ładowania, aby utworzyć <xref:System.Security.Policy.Publisher> dowodu dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="de05b-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="de05b-132">Jednak domyślnie większość aplikacji nie ma potrzeby <xref:System.Security.Policy.Publisher> dowodów.</span><span class="sxs-lookup"><span data-stu-id="de05b-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="de05b-133">Standardowe zasady CAS nie zależą od <xref:System.Security.Policy.PublisherMembershipCondition>.</span><span class="sxs-lookup"><span data-stu-id="de05b-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="de05b-134">Należy unikać koszt uruchamiania niepotrzebnych związany z weryfikacji podpisu wydawcy, chyba że aplikacja wykonuje na komputerze za pomocą zasad niestandardowych urzędów certyfikacji lub zamierzający spełniają wymagania dla <xref:System.Security.Permissions.PublisherIdentityPermission> w środowisku częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="de05b-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="de05b-135">(Wymagania dotyczące uprawnień tożsamości zawsze powiedzie się w środowisku pełnego zaufania).</span><span class="sxs-lookup"><span data-stu-id="de05b-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de05b-136">Firma Microsoft zaleca, usługi, użyj `<generatePublisherEvidence>` element, aby zwiększyć wydajność uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="de05b-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="de05b-137">Przy użyciu tego elementu może również pomóc uniknąć opóźnień, które mogą powodować upływu limitu czasu i anulowania uruchomienia usługi.</span><span class="sxs-lookup"><span data-stu-id="de05b-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="de05b-138">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="de05b-138">Configuration File</span></span>  
 <span data-ttu-id="de05b-139">Ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de05b-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de05b-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="de05b-140">Example</span></span>  
 <span data-ttu-id="de05b-141">Poniższy przykład pokazuje, jak używać `<generatePublisherEvidence>` elementu, aby wyłączyć sprawdzanie urzędów certyfikacji zasad wydawcy dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de05b-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="de05b-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de05b-142">See also</span></span>

- [<span data-ttu-id="de05b-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="de05b-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="de05b-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="de05b-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
