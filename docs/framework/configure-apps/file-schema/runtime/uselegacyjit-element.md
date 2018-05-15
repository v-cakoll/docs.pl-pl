---
title: '&lt;useLegacyJit&gt; — Element'
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd0ae1a44b41ddcae2149bcf685871a37dd01b06
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltuselegacyjitgt-element"></a><span data-ttu-id="83288-102">&lt;useLegacyJit&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="83288-102">&lt;useLegacyJit&gt; Element</span></span>

<span data-ttu-id="83288-103">Określa, czy środowisko uruchomieniowe języka wspólnego używa starszej wersji kompilatora JIT 64-bitowej w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="83288-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
<span data-ttu-id="83288-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="83288-104">\<configuration></span></span>  
<span data-ttu-id="83288-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="83288-105">\<runtime></span></span>  
<span data-ttu-id="83288-106">\<useLegacyJit ></span><span class="sxs-lookup"><span data-stu-id="83288-106">\<useLegacyJit></span></span>
  
## <a name="syntax"></a><span data-ttu-id="83288-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="83288-107">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="83288-108">Nazwa elementu `useLegacyJit` jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="83288-108">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83288-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="83288-109">Attributes and elements</span></span>

<span data-ttu-id="83288-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="83288-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83288-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="83288-111">Attributes</span></span>  
  
| <span data-ttu-id="83288-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="83288-112">Attribute</span></span> | <span data-ttu-id="83288-113">Opis</span><span class="sxs-lookup"><span data-stu-id="83288-113">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="83288-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="83288-114">Required attribute.</span></span><br><br><span data-ttu-id="83288-115">Określa, czy środowisko uruchomieniowe używa starszej wersji kompilatora JIT 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="83288-115">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="83288-116">Atrybut enabled</span><span class="sxs-lookup"><span data-stu-id="83288-116">enabled attribute</span></span>  
  
| <span data-ttu-id="83288-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="83288-117">Value</span></span> | <span data-ttu-id="83288-118">Opis</span><span class="sxs-lookup"><span data-stu-id="83288-118">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="83288-119">0</span><span class="sxs-lookup"><span data-stu-id="83288-119">0</span></span>     | <span data-ttu-id="83288-120">Środowisko uruchomieniowe języka wspólnego używa nowego 64-bitowym przy użyciu kompilatora JIT uwzględnione w programie .NET Framework 4.6 i nowszymi wersjami.</span><span class="sxs-lookup"><span data-stu-id="83288-120">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="83288-121">1</span><span class="sxs-lookup"><span data-stu-id="83288-121">1</span></span>     | <span data-ttu-id="83288-122">Środowisko uruchomieniowe języka wspólnego używa starszego kompilatora JIT 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="83288-122">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="83288-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="83288-123">Child elements</span></span>

<span data-ttu-id="83288-124">Brak</span><span class="sxs-lookup"><span data-stu-id="83288-124">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="83288-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="83288-125">Parent elements</span></span>  
  
| <span data-ttu-id="83288-126">Element</span><span class="sxs-lookup"><span data-stu-id="83288-126">Element</span></span>         | <span data-ttu-id="83288-127">Opis</span><span class="sxs-lookup"><span data-stu-id="83288-127">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="83288-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="83288-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="83288-129">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="83288-129">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="83288-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83288-130">Remarks</span></span>  

<span data-ttu-id="83288-131">Począwszy od programu .NET Framework 4.6, środowisko uruchomieniowe języka wspólnego nowy kompilator 64-bitowy dla kompilacji just in Time (JIT) domyślnie używa.</span><span class="sxs-lookup"><span data-stu-id="83288-131">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="83288-132">W niektórych przypadkach może to spowodować różnice w zachowaniu z kodu aplikacji, który został skompilowany JIT w poprzedniej wersji kompilatora JIT 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="83288-132">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="83288-133">Przez ustawienie `enabled` atrybutu `<useLegacyJit>` elementu `1`, można wyłączyć kompilator JIT 64-bitowe i zamiast tego Kompilowanie aplikacji za pomocą starszego kompilatora JIT 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="83288-133">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="83288-134">`<useLegacyJit>` Elementu dotyczy tylko kompilacji JIT 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="83288-134">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="83288-135">Kompilacja z kompilatorem JIT 32-bitowych nie mają wpływu.</span><span class="sxs-lookup"><span data-stu-id="83288-135">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="83288-136">Zamiast pliku ustawień konfiguracji, można włączyć starszej wersji 64-bitowej przy użyciu kompilatora JIT dwa inne sposoby:</span><span class="sxs-lookup"><span data-stu-id="83288-136">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="83288-137">Ustawienie zmiennej środowiskowej</span><span class="sxs-lookup"><span data-stu-id="83288-137">Setting an environment variable</span></span>

  <span data-ttu-id="83288-138">Ustaw `COMPLUS_useLegacyJit` albo zmienną środowiskową `0` (Użyj kompilator JIT 64-bitowe) lub `1` (należy użyć starszego kompilatora JIT 64-bitowe):</span><span class="sxs-lookup"><span data-stu-id="83288-138">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="83288-139">Zmienna środowiskowa ma *globalne*, co oznacza, że ma to wpływ na wszystkie aplikacje uruchamiane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="83288-139">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="83288-140">Jeśli ustawiona, jej mogą zostać zastąpione przez ustawienie pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83288-140">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="83288-141">Nazwa zmiennej środowiskowej nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="83288-141">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="83288-142">Dodawanie klucza rejestru</span><span class="sxs-lookup"><span data-stu-id="83288-142">Adding a registry key</span></span>

  <span data-ttu-id="83288-143">Można włączyć starszego kompilatora JIT 64-bitowych, dodając `REG_DWORD` wartość jednej `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` lub `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucza w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="83288-143">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="83288-144">Wartość jest o nazwie `useLegacyJit`.</span><span class="sxs-lookup"><span data-stu-id="83288-144">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="83288-145">Jeśli wartość wynosi 0, jest używany nowy kompilator.</span><span class="sxs-lookup"><span data-stu-id="83288-145">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="83288-146">Jeśli wartość wynosi 1, starszego kompilatora JIT 64-bitowych jest włączone.</span><span class="sxs-lookup"><span data-stu-id="83288-146">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="83288-147">Nazwa wartości rejestru nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="83288-147">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="83288-148">Dodaj wartość do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klucz ma wpływ na wszystkie aplikacje uruchomione na maszynie.</span><span class="sxs-lookup"><span data-stu-id="83288-148">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="83288-149">Dodaj wartość do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucz ma wpływ na wszystkie aplikacje uruchamiane przez bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="83288-149">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="83288-150">Jeśli maszyna jest skonfigurowana z wieloma kontami użytkowników, tylko aplikacje uruchamiane przez bieżącego użytkownika jest narażony, chyba że wartość jest dodawana do kluczy rejestru, jak również innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="83288-150">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="83288-151">Dodawanie `<useLegacyJit>` elementu do pliku konfiguracji zastępuje ustawienia rejestru, jeśli są one obecne.</span><span class="sxs-lookup"><span data-stu-id="83288-151">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83288-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="83288-152">Example</span></span>  

<span data-ttu-id="83288-153">Następującego pliku konfiguracji powoduje wyłączenie kompilacji przez kompilator JIT 64-bitowe i zamiast tego używa starszej wersji kompilatora JIT 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="83288-153">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="83288-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83288-154">See also</span></span>

<span data-ttu-id="83288-155">[\<środowisko uruchomieniowe > — Element](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="83288-155">[\<runtime> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) </span></span>  
<span data-ttu-id="83288-156">[\<Konfiguracja > — Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="83288-156">[\<configuration> Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
[<span data-ttu-id="83288-157">Środki zaradcze: Nowy kompilator JIT 64-bitowych</span><span class="sxs-lookup"><span data-stu-id="83288-157">Mitigation: New 64-bit JIT Compiler</span></span>](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
