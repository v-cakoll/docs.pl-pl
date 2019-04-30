---
title: <NetFx40_LegacySecurityPolicy> Element
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20a0ca8560fcd5d7f9d171df3e3b4c3f42e78641
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674184"
---
# <a name="netfx40legacysecuritypolicy-element"></a><span data-ttu-id="886e7-102">\<NetFx40_LegacySecurityPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="886e7-102">\<NetFx40_LegacySecurityPolicy> Element</span></span>
<span data-ttu-id="886e7-103">Określa, czy środowisko wykonawcze używa starszego kodu zasady zabezpieczeń dostępu (CAS).</span><span class="sxs-lookup"><span data-stu-id="886e7-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>  
  
 <span data-ttu-id="886e7-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="886e7-104">\<configuration></span></span>  
<span data-ttu-id="886e7-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="886e7-105">\<runtime></span></span>  
<span data-ttu-id="886e7-106"><NetFx40_LegacySecurityPolicy></span><span class="sxs-lookup"><span data-stu-id="886e7-106"><NetFx40_LegacySecurityPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="886e7-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="886e7-107">Syntax</span></span>  
  
```xml  
<NetFx40_LegacySecurityPolicy  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="886e7-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="886e7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="886e7-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="886e7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="886e7-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="886e7-110">Attributes</span></span>  
  
|<span data-ttu-id="886e7-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="886e7-111">Attribute</span></span>|<span data-ttu-id="886e7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="886e7-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="886e7-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="886e7-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="886e7-114">Określa, czy środowisko wykonawcze używa starsza zasada CAS.</span><span class="sxs-lookup"><span data-stu-id="886e7-114">Specifies whether the runtime uses legacy CAS policy.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="886e7-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="886e7-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="886e7-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="886e7-116">Value</span></span>|<span data-ttu-id="886e7-117">Opis</span><span class="sxs-lookup"><span data-stu-id="886e7-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="886e7-118">Środowisko wykonawcze nie używa starsza zasada CAS.</span><span class="sxs-lookup"><span data-stu-id="886e7-118">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="886e7-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="886e7-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="886e7-120">Środowisko wykonawcze używa starsza zasada CAS.</span><span class="sxs-lookup"><span data-stu-id="886e7-120">The runtime uses legacy CAS policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="886e7-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="886e7-121">Child Elements</span></span>  
 <span data-ttu-id="886e7-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="886e7-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="886e7-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="886e7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="886e7-124">Element</span><span class="sxs-lookup"><span data-stu-id="886e7-124">Element</span></span>|<span data-ttu-id="886e7-125">Opis</span><span class="sxs-lookup"><span data-stu-id="886e7-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="886e7-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="886e7-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="886e7-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="886e7-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="886e7-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="886e7-128">Remarks</span></span>  
 <span data-ttu-id="886e7-129">W .NET Framework w wersji 3.5 i wcześniejszymi wersjami urzędy certyfikacji zasad jest zawsze w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="886e7-129">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="886e7-130">W [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], musi być włączone zasady CAS.</span><span class="sxs-lookup"><span data-stu-id="886e7-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], CAS policy must be enabled.</span></span>  
  
 <span data-ttu-id="886e7-131">Urzędy certyfikacji zasad jest specyficzny dla wersji.</span><span class="sxs-lookup"><span data-stu-id="886e7-131">CAS policy is version-specific.</span></span> <span data-ttu-id="886e7-132">Zasady niestandardowe urzędów certyfikacji, które istnieją we wcześniejszych wersjach programu .NET Framework musi obowiązywać w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="886e7-132">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>  
  
 <span data-ttu-id="886e7-133">Stosowanie `<NetFx40_LegacySecurityPolicy>` elementu [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] zestawu nie ma wpływu na [kod o przezroczystym poziomie bezpieczeństwa](../../../../../docs/framework/misc/security-transparent-code.md); nadal mają zastosowanie zasady przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="886e7-133">Applying the `<NetFx40_LegacySecurityPolicy>` element to a [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] assembly does not affect [security-transparent code](../../../../../docs/framework/misc/security-transparent-code.md); the transparency rules still apply.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="886e7-134">Stosowanie `<NetFx40_LegacySecurityPolicy>` elementu może spowodować istotnie poprawiającą wydajność dla zestawów obrazu natywnego, utworzone przez [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) nie są zainstalowane w [globalnej pamięci podręcznej zestawów ](../../../../../docs/framework/app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="886e7-134">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../../../docs/framework/app-domains/gac.md).</span></span> <span data-ttu-id="886e7-135">Spadek wydajności jest spowodowany brakiem możliwości środowiska uruchomieniowego ładować zestawy jako obrazy natywne, jeśli ten atrybut jest stosowany, co spowoduje ich załadowanych zespołów jako just-in-time.</span><span class="sxs-lookup"><span data-stu-id="886e7-135">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="886e7-136">Jeśli określisz docelowego .NET Framework w wersji starszej niż [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] w ustawieniach projektu dla projektu programu Visual Studio, urzędy certyfikacji zasady zostaną włączone, łącznie z urzędami certyfikacji zasad niestandardowych określony dla danej wersji.</span><span class="sxs-lookup"><span data-stu-id="886e7-136">If you specify a target .NET Framework version that is earlier than the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="886e7-137">Jednak nie będzie mógł używać nowego [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] typów i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="886e7-137">However, you will not be able to use new [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] types and members.</span></span> <span data-ttu-id="886e7-138">Można również określić przy użyciu wcześniejszej wersji programu .NET Framework [ \<supportedRuntime > element](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) w schemat ustawień uruchamiania w swojej [pliku konfiguracji aplikacji](../../../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="886e7-138">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../../../../docs/framework/configure-apps/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="886e7-139">Składni plików konfiguracji jest uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="886e7-139">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="886e7-140">Należy użyć składni, zgodnie z postanowieniami w sekcjach składnię i przykład.</span><span class="sxs-lookup"><span data-stu-id="886e7-140">You should use the syntax as provided in the Syntax and Example sections.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="886e7-141">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="886e7-141">Configuration File</span></span>  
 <span data-ttu-id="886e7-142">Ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="886e7-142">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="886e7-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="886e7-143">Example</span></span>  
 <span data-ttu-id="886e7-144">Poniższy przykład przedstawia sposób Włącz starszą zasadę dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="886e7-144">The following example shows how to enable legacy CAS policy for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="886e7-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="886e7-145">See also</span></span>

- [<span data-ttu-id="886e7-146">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="886e7-146">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="886e7-147">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="886e7-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
