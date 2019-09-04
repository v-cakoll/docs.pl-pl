---
title: <NetFx40_LegacySecurityPolicy> Element
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cd6f937811ae503dd4de7ff989510c4eb8b8933
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252448"
---
# <a name="netfx40_legacysecuritypolicy-element"></a><span data-ttu-id="b0cb4-102">\<NetFx40_LegacySecurityPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="b0cb4-102">\<NetFx40_LegacySecurityPolicy> Element</span></span>

<span data-ttu-id="b0cb4-103">Określa, czy środowisko uruchomieniowe korzysta ze starszych zasad zabezpieczeń dostępu kodu (CAS).</span><span class="sxs-lookup"><span data-stu-id="b0cb4-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>

<span data-ttu-id="b0cb4-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b0cb4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b0cb4-105">&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="b0cb4-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="b0cb4-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<NetFx40_LegacySecurityPolicy >**</span><span class="sxs-lookup"><span data-stu-id="b0cb4-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_LegacySecurityPolicy>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="b0cb4-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0cb4-107">Syntax</span></span>

```xml
<NetFx40_LegacySecurityPolicy
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b0cb4-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b0cb4-108">Attributes and Elements</span></span>

<span data-ttu-id="b0cb4-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b0cb4-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b0cb4-110">Attributes</span></span>

|<span data-ttu-id="b0cb4-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b0cb4-111">Attribute</span></span>|<span data-ttu-id="b0cb4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b0cb4-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="b0cb4-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="b0cb4-114">Określa, czy środowisko uruchomieniowe używa starszych zasad CAS.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-114">Specifies whether the runtime uses legacy CAS policy.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="b0cb4-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="b0cb4-115">enabled Attribute</span></span>

|<span data-ttu-id="b0cb4-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="b0cb4-116">Value</span></span>|<span data-ttu-id="b0cb4-117">Opis</span><span class="sxs-lookup"><span data-stu-id="b0cb4-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="b0cb4-118">Środowisko uruchomieniowe nie używa starszych zasad CAS.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-118">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="b0cb4-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="b0cb4-120">Środowisko uruchomieniowe używa starszych zasad CAS.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-120">The runtime uses legacy CAS policy.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b0cb4-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b0cb4-121">Child Elements</span></span>

<span data-ttu-id="b0cb4-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b0cb4-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b0cb4-123">Parent Elements</span></span>

|<span data-ttu-id="b0cb4-124">Element</span><span class="sxs-lookup"><span data-stu-id="b0cb4-124">Element</span></span>|<span data-ttu-id="b0cb4-125">Opis</span><span class="sxs-lookup"><span data-stu-id="b0cb4-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="b0cb4-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="b0cb4-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-127">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b0cb4-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0cb4-128">Remarks</span></span>

<span data-ttu-id="b0cb4-129">W .NET Framework wersja 3,5 i wcześniejsze wersje zasady CAS są zawsze włączone.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-129">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="b0cb4-130">W .NET Framework 4 należy włączyć zasady CAS.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-130">In the .NET Framework 4, CAS policy must be enabled.</span></span>

<span data-ttu-id="b0cb4-131">Zasady CAS są specyficzne dla wersji.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-131">CAS policy is version-specific.</span></span> <span data-ttu-id="b0cb4-132">Zasady niestandardowych urzędów certyfikacji, które istnieją we wcześniejszych wersjach .NET Framework muszą zostać określone w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-132">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the .NET Framework 4.</span></span>

<span data-ttu-id="b0cb4-133">Zastosowanie elementu do zestawu .NET Framework 4 nie wpływa na [kod przezroczysty dla bezpieczeństwa](../../../misc/security-transparent-code.md); nadal obowiązują reguły przezroczystości. `<NetFx40_LegacySecurityPolicy>`</span><span class="sxs-lookup"><span data-stu-id="b0cb4-133">Applying the `<NetFx40_LegacySecurityPolicy>` element to a .NET Framework 4 assembly does not affect [security-transparent code](../../../misc/security-transparent-code.md); the transparency rules still apply.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b0cb4-134">Zastosowanie elementu może spowodować znaczny wpływ na wydajność zestawów obrazów natywnych utworzonych przez [Generator obrazu natywnego (Ngen. exe)](../../../tools/ngen-exe-native-image-generator.md) , które nie są zainstalowane w [globalnej pamięci podręcznej zestawów.](../../../app-domains/gac.md) `<NetFx40_LegacySecurityPolicy>`</span><span class="sxs-lookup"><span data-stu-id="b0cb4-134">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../app-domains/gac.md).</span></span> <span data-ttu-id="b0cb4-135">Spadek wydajności jest spowodowany przez niezdolność środowiska uruchomieniowego do załadowania zestawów jako obrazów natywnych podczas stosowania atrybutu, co spowoduje ich załadowanie jako zestawów just in Time.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-135">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>

> [!NOTE]
> <span data-ttu-id="b0cb4-136">Jeśli określisz wersję docelową .NET Framework, która jest wcześniejsza niż .NET Framework 4 w ustawieniach projektu dla projektu programu Visual Studio, zostaną włączone zasady CAS, w tym wszelkie niestandardowe zasady dotyczące urzędów certyfikacji określone dla tej wersji.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-136">If you specify a target .NET Framework version that is earlier than the .NET Framework 4 in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="b0cb4-137">Nie będzie jednak można używać nowych typów i elementów członkowskich .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-137">However, you will not be able to use new .NET Framework 4 types and members.</span></span> <span data-ttu-id="b0cb4-138">Możesz również określić wcześniejszą wersję .NET Framework przy użyciu [ \<elementu > supportedRuntime](../startup/supportedruntime-element.md) w schemacie ustawień uruchamiania w [pliku konfiguracyjnym aplikacji](../../index.md).</span><span class="sxs-lookup"><span data-stu-id="b0cb4-138">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b0cb4-139">W składni pliku konfiguracji jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-139">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="b0cb4-140">Należy użyć składni podanej w sekcjach składnia i przykład.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-140">You should use the syntax as provided in the Syntax and Example sections.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="b0cb4-141">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b0cb4-141">Configuration File</span></span>

<span data-ttu-id="b0cb4-142">Tego elementu można używać tylko w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-142">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="b0cb4-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0cb4-143">Example</span></span>

<span data-ttu-id="b0cb4-144">Poniższy przykład pokazuje, jak włączyć zasady starszych urzędów certyfikacji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b0cb4-144">The following example shows how to enable legacy CAS policy for an application.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="b0cb4-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0cb4-145">See also</span></span>

- [<span data-ttu-id="b0cb4-146">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b0cb4-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b0cb4-147">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b0cb4-147">Configuration File Schema</span></span>](../index.md)
