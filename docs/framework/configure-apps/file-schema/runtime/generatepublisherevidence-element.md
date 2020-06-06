---
title: <generatePublisherEvidence> Element
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: c2ba4a7244b7849e28eac38fb34a2cdd0d1f1048
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "81645357"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="82cc2-102">\<generatePublisherEvidence> Element</span><span class="sxs-lookup"><span data-stu-id="82cc2-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="82cc2-103">Określa, czy środowisko uruchomieniowe tworzy <xref:System.Security.Policy.Publisher> dowód dla zabezpieczeń dostępu kodu (CAS).</span><span class="sxs-lookup"><span data-stu-id="82cc2-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**  
  
## <a name="syntax"></a><span data-ttu-id="82cc2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="82cc2-104">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82cc2-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="82cc2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="82cc2-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="82cc2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82cc2-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="82cc2-107">Attributes</span></span>  
  
|<span data-ttu-id="82cc2-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="82cc2-108">Attribute</span></span>|<span data-ttu-id="82cc2-109">Opis</span><span class="sxs-lookup"><span data-stu-id="82cc2-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="82cc2-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="82cc2-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="82cc2-111">Określa, czy środowisko uruchomieniowe tworzy <xref:System.Security.Policy.Publisher> dowód.</span><span class="sxs-lookup"><span data-stu-id="82cc2-111">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="82cc2-112">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="82cc2-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="82cc2-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="82cc2-113">Value</span></span>|<span data-ttu-id="82cc2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="82cc2-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="82cc2-115">Nie tworzy <xref:System.Security.Policy.Publisher> dowodów.</span><span class="sxs-lookup"><span data-stu-id="82cc2-115">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="82cc2-116">Tworzy <xref:System.Security.Policy.Publisher> dowód.</span><span class="sxs-lookup"><span data-stu-id="82cc2-116">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="82cc2-117">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="82cc2-117">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82cc2-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="82cc2-118">Child Elements</span></span>  
 <span data-ttu-id="82cc2-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="82cc2-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="82cc2-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="82cc2-120">Parent Elements</span></span>  
  
|<span data-ttu-id="82cc2-121">Element</span><span class="sxs-lookup"><span data-stu-id="82cc2-121">Element</span></span>|<span data-ttu-id="82cc2-122">Opis</span><span class="sxs-lookup"><span data-stu-id="82cc2-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="82cc2-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="82cc2-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="82cc2-124">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="82cc2-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82cc2-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82cc2-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82cc2-126">W .NET Framework 4 i nowszych ten element nie ma wpływu na czasy ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="82cc2-126">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="82cc2-127">Aby uzyskać więcej informacji, zobacz sekcję "uproszczenie zasad zabezpieczeń" w temacie [zmiany zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span><span class="sxs-lookup"><span data-stu-id="82cc2-127">For more information, see the "Security Policy Simplification" section in [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="82cc2-128">Środowisko uruchomieniowe języka wspólnego (CLR) próbuje zweryfikować podpis Authenticode w czasie ładowania, aby utworzyć <xref:System.Security.Policy.Publisher> dowód dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="82cc2-128">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="82cc2-129">Jednak domyślnie większość aplikacji nie potrzebuje <xref:System.Security.Policy.Publisher> dowodu.</span><span class="sxs-lookup"><span data-stu-id="82cc2-129">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="82cc2-130">Standardowe zasady CAS nie bazują na <xref:System.Security.Policy.PublisherMembershipCondition> .</span><span class="sxs-lookup"><span data-stu-id="82cc2-130">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="82cc2-131">Należy unikać niepotrzebnego kosztu uruchomienia związanego z weryfikacją podpisu wydawcy, chyba że aplikacja jest wykonywana na komputerze z niestandardowymi zasadami CAS lub nie spełnia wymagań dotyczących <xref:System.Security.Permissions.PublisherIdentityPermission> w środowisku częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="82cc2-131">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="82cc2-132">(Wymagania dotyczące uprawnień tożsamości zawsze powiodło się w środowisku pełnego zaufania).</span><span class="sxs-lookup"><span data-stu-id="82cc2-132">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82cc2-133">Zalecamy, aby usługi korzystały z `<generatePublisherEvidence>` elementu, aby zwiększyć wydajność uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="82cc2-133">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="82cc2-134">Za pomocą tego elementu można także uniknąć opóźnień, które mogą spowodować przekroczenie limitu czasu i anulowanie uruchamiania usługi.</span><span class="sxs-lookup"><span data-stu-id="82cc2-134">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="82cc2-135">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="82cc2-135">Configuration File</span></span>  
 <span data-ttu-id="82cc2-136">Tego elementu można używać tylko w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="82cc2-136">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82cc2-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="82cc2-137">Example</span></span>  
 <span data-ttu-id="82cc2-138">Poniższy przykład pokazuje, jak użyć elementu, `<generatePublisherEvidence>` Aby wyłączyć sprawdzanie zasad wydawcy CAS dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="82cc2-138">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="82cc2-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82cc2-139">See also</span></span>

- [<span data-ttu-id="82cc2-140">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="82cc2-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="82cc2-141">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="82cc2-141">Configuration File Schema</span></span>](../index.md)
