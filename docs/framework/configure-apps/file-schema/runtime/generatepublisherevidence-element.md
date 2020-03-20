---
title: <generatePublisherEvidence>, element
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: 24a5ea02992a5bce681b5bab4fb7f75505bd225d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154117"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="6e968-102">\<generatePublisherEvidence> Element</span><span class="sxs-lookup"><span data-stu-id="6e968-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="6e968-103">Określa, czy środowisko <xref:System.Security.Policy.Publisher> wykonawcze tworzy dowody zabezpieczeń dostępu do kodu (CAS).</span><span class="sxs-lookup"><span data-stu-id="6e968-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
<span data-ttu-id="6e968-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6e968-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6e968-105">&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="6e968-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="6e968-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**</span><span class="sxs-lookup"><span data-stu-id="6e968-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e968-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e968-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e968-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6e968-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6e968-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6e968-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e968-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6e968-110">Attributes</span></span>  
  
|<span data-ttu-id="6e968-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6e968-111">Attribute</span></span>|<span data-ttu-id="6e968-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6e968-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="6e968-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="6e968-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="6e968-114">Określa, czy środowisko <xref:System.Security.Policy.Publisher> wykonawcze tworzy dowody.</span><span class="sxs-lookup"><span data-stu-id="6e968-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6e968-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="6e968-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="6e968-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="6e968-116">Value</span></span>|<span data-ttu-id="6e968-117">Opis</span><span class="sxs-lookup"><span data-stu-id="6e968-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="6e968-118">Nie tworzy <xref:System.Security.Policy.Publisher> dowodów.</span><span class="sxs-lookup"><span data-stu-id="6e968-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="6e968-119">Tworzy <xref:System.Security.Policy.Publisher> dowody.</span><span class="sxs-lookup"><span data-stu-id="6e968-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="6e968-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="6e968-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e968-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6e968-121">Child Elements</span></span>  
 <span data-ttu-id="6e968-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="6e968-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e968-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6e968-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6e968-124">Element</span><span class="sxs-lookup"><span data-stu-id="6e968-124">Element</span></span>|<span data-ttu-id="6e968-125">Opis</span><span class="sxs-lookup"><span data-stu-id="6e968-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6e968-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6e968-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6e968-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6e968-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e968-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e968-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e968-129">W programie .NET Framework 4 i nowszych element ten nie ma wpływu na czasy ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="6e968-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="6e968-130">Aby uzyskać więcej informacji, zobacz sekcję "Uproszczenie zasad zabezpieczeń" w sekcji [Zmiany zabezpieczeń](../../../security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="6e968-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../security/security-changes.md).</span></span>  
  
 <span data-ttu-id="6e968-131">Środowisko wykonawcze języka wspólnego (CLR) próbuje zweryfikować authenticode <xref:System.Security.Policy.Publisher> podpisu w czasie ładowania, aby utworzyć dowody dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="6e968-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="6e968-132">Jednak domyślnie większość aplikacji nie <xref:System.Security.Policy.Publisher> potrzebuje dowodów.</span><span class="sxs-lookup"><span data-stu-id="6e968-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="6e968-133">Standardowe zasady CAS nie <xref:System.Security.Policy.PublisherMembershipCondition>opierają się na .</span><span class="sxs-lookup"><span data-stu-id="6e968-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="6e968-134">Należy unikać niepotrzebnych kosztów uruchamiania skojarzonych z weryfikacją podpisu wydawcy, chyba że aplikacja jest wykonywana <xref:System.Security.Permissions.PublisherIdentityPermission> na komputerze z niestandardowymi zasadami CAS lub zamierza zaspokoić wymagania w środowisku częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="6e968-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="6e968-135">(Wymagania dotyczące uprawnień tożsamości zawsze odnoszą sukces w środowisku pełnego zaufania).</span><span class="sxs-lookup"><span data-stu-id="6e968-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e968-136">Zaleca się, że `<generatePublisherEvidence>` usługi używają tego elementu w celu zwiększenia wydajności uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="6e968-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="6e968-137">Za pomocą tego elementu może również pomóc uniknąć opóźnień, które mogą spowodować limit czasu i anulowanie uruchamiania usługi.</span><span class="sxs-lookup"><span data-stu-id="6e968-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="6e968-138">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6e968-138">Configuration File</span></span>  
 <span data-ttu-id="6e968-139">Ten element może być używany tylko w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6e968-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e968-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="6e968-140">Example</span></span>  
 <span data-ttu-id="6e968-141">W poniższym przykładzie `<generatePublisherEvidence>` pokazano, jak użyć elementu, aby wyłączyć sprawdzanie zasad wydawcy CAS dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6e968-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e968-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e968-142">See also</span></span>

- [<span data-ttu-id="6e968-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="6e968-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6e968-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6e968-144">Configuration File Schema</span></span>](../index.md)
