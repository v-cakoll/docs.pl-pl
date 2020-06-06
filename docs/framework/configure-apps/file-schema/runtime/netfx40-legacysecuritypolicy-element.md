---
title: <NetFx40_LegacySecurityPolicy>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
ms.openlocfilehash: d5192eb56bb8b640544bdc52a0bb9d8a5277efef
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116252"
---
# <a name="netfx40_legacysecuritypolicy-element"></a><span data-ttu-id="48170-102">\<NetFx40_LegacySecurityPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="48170-102">\<NetFx40_LegacySecurityPolicy> Element</span></span>

<span data-ttu-id="48170-103">Określa, czy środowisko uruchomieniowe korzysta ze starszych zasad zabezpieczeń dostępu kodu (CAS).</span><span class="sxs-lookup"><span data-stu-id="48170-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_LegacySecurityPolicy>**  

## <a name="syntax"></a><span data-ttu-id="48170-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="48170-104">Syntax</span></span>

```xml
<NetFx40_LegacySecurityPolicy
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="48170-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="48170-105">Attributes and Elements</span></span>

<span data-ttu-id="48170-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="48170-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="48170-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="48170-107">Attributes</span></span>

|<span data-ttu-id="48170-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="48170-108">Attribute</span></span>|<span data-ttu-id="48170-109">Opis</span><span class="sxs-lookup"><span data-stu-id="48170-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="48170-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="48170-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="48170-111">Określa, czy środowisko uruchomieniowe używa starszych zasad CAS.</span><span class="sxs-lookup"><span data-stu-id="48170-111">Specifies whether the runtime uses legacy CAS policy.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="48170-112">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="48170-112">enabled Attribute</span></span>

|<span data-ttu-id="48170-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="48170-113">Value</span></span>|<span data-ttu-id="48170-114">Opis</span><span class="sxs-lookup"><span data-stu-id="48170-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="48170-115">Środowisko uruchomieniowe nie używa starszych zasad CAS.</span><span class="sxs-lookup"><span data-stu-id="48170-115">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="48170-116">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="48170-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="48170-117">Środowisko uruchomieniowe używa starszych zasad CAS.</span><span class="sxs-lookup"><span data-stu-id="48170-117">The runtime uses legacy CAS policy.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="48170-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="48170-118">Child Elements</span></span>

<span data-ttu-id="48170-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="48170-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="48170-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="48170-120">Parent Elements</span></span>

|<span data-ttu-id="48170-121">Element</span><span class="sxs-lookup"><span data-stu-id="48170-121">Element</span></span>|<span data-ttu-id="48170-122">Opis</span><span class="sxs-lookup"><span data-stu-id="48170-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="48170-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48170-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="48170-124">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="48170-124">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="48170-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="48170-125">Remarks</span></span>

<span data-ttu-id="48170-126">W .NET Framework wersja 3,5 i wcześniejsze wersje zasady CAS są zawsze włączone.</span><span class="sxs-lookup"><span data-stu-id="48170-126">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="48170-127">W .NET Framework 4 należy włączyć zasady CAS.</span><span class="sxs-lookup"><span data-stu-id="48170-127">In the .NET Framework 4, CAS policy must be enabled.</span></span>

<span data-ttu-id="48170-128">Zasady CAS są specyficzne dla wersji.</span><span class="sxs-lookup"><span data-stu-id="48170-128">CAS policy is version-specific.</span></span> <span data-ttu-id="48170-129">Zasady niestandardowych urzędów certyfikacji, które istnieją we wcześniejszych wersjach .NET Framework muszą zostać określone w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="48170-129">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the .NET Framework 4.</span></span>

<span data-ttu-id="48170-130">Zastosowanie `<NetFx40_LegacySecurityPolicy>` elementu do zestawu .NET Framework 4 nie wpływa na [kod przezroczysty dla bezpieczeństwa](../../../misc/security-transparent-code.md); nadal obowiązują reguły przezroczystości.</span><span class="sxs-lookup"><span data-stu-id="48170-130">Applying the `<NetFx40_LegacySecurityPolicy>` element to a .NET Framework 4 assembly does not affect [security-transparent code](../../../misc/security-transparent-code.md); the transparency rules still apply.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="48170-131">Zastosowanie `<NetFx40_LegacySecurityPolicy>` elementu może spowodować znaczny wpływ na wydajność zestawów obrazów natywnych utworzonych przez [Generator obrazu natywnego (Ngen. exe)](../../../tools/ngen-exe-native-image-generator.md) , które nie są zainstalowane w [globalnej pamięci podręcznej zestawów](../../../app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="48170-131">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../app-domains/gac.md).</span></span> <span data-ttu-id="48170-132">Spadek wydajności jest spowodowany przez niezdolność środowiska uruchomieniowego do załadowania zestawów jako obrazów natywnych podczas stosowania atrybutu, co spowoduje ich załadowanie jako zestawów just in Time.</span><span class="sxs-lookup"><span data-stu-id="48170-132">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>

> [!NOTE]
> <span data-ttu-id="48170-133">Jeśli określisz wersję docelową .NET Framework, która jest wcześniejsza niż .NET Framework 4 w ustawieniach projektu dla projektu programu Visual Studio, zostaną włączone zasady CAS, w tym wszelkie niestandardowe zasady dotyczące urzędów certyfikacji określone dla tej wersji.</span><span class="sxs-lookup"><span data-stu-id="48170-133">If you specify a target .NET Framework version that is earlier than the .NET Framework 4 in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="48170-134">Nie będzie jednak można używać nowych typów i elementów członkowskich .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="48170-134">However, you will not be able to use new .NET Framework 4 types and members.</span></span> <span data-ttu-id="48170-135">Możesz również określić wcześniejszą wersję .NET Framework za pomocą [ \<supportedRuntime> elementu](../startup/supportedruntime-element.md) w schemacie ustawienia uruchamiania w [pliku konfiguracyjnym aplikacji](../../index.md).</span><span class="sxs-lookup"><span data-stu-id="48170-135">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="48170-136">W składni pliku konfiguracji jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="48170-136">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="48170-137">Należy użyć składni podanej w sekcjach składnia i przykład.</span><span class="sxs-lookup"><span data-stu-id="48170-137">You should use the syntax as provided in the Syntax and Example sections.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="48170-138">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="48170-138">Configuration File</span></span>

<span data-ttu-id="48170-139">Tego elementu można używać tylko w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="48170-139">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="48170-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="48170-140">Example</span></span>

<span data-ttu-id="48170-141">Poniższy przykład pokazuje, jak włączyć zasady starszych urzędów certyfikacji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="48170-141">The following example shows how to enable legacy CAS policy for an application.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="48170-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48170-142">See also</span></span>

- [<span data-ttu-id="48170-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="48170-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="48170-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="48170-144">Configuration File Schema</span></span>](../index.md)
