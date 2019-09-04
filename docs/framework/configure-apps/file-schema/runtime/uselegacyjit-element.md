---
title: <useLegacyJit>, element
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b783a82b1ef964de308532ef544bbfab2397400
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252226"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="dc481-102">\<useLegacyJit> Element</span><span class="sxs-lookup"><span data-stu-id="dc481-102">\<useLegacyJit> Element</span></span>

<span data-ttu-id="dc481-103">Określa, czy środowisko uruchomieniowe języka wspólnego korzysta ze starszego 64-bitowego kompilatora JIT dla kompilacji just in Time.</span><span class="sxs-lookup"><span data-stu-id="dc481-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
<span data-ttu-id="dc481-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dc481-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dc481-105">&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="dc481-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="dc481-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<useLegacyJit>**</span><span class="sxs-lookup"><span data-stu-id="dc481-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<useLegacyJit>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc481-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc481-107">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="dc481-108">Nazwa `useLegacyJit` elementu uwzględnia wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="dc481-108">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc481-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dc481-109">Attributes and elements</span></span>

<span data-ttu-id="dc481-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dc481-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc481-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dc481-111">Attributes</span></span>  
  
| <span data-ttu-id="dc481-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dc481-112">Attribute</span></span> | <span data-ttu-id="dc481-113">Opis</span><span class="sxs-lookup"><span data-stu-id="dc481-113">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="dc481-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="dc481-114">Required attribute.</span></span><br><br><span data-ttu-id="dc481-115">Określa, czy środowisko uruchomieniowe używa starszego 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="dc481-115">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="dc481-116">włączony atrybut</span><span class="sxs-lookup"><span data-stu-id="dc481-116">enabled attribute</span></span>  
  
| <span data-ttu-id="dc481-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="dc481-117">Value</span></span> | <span data-ttu-id="dc481-118">Opis</span><span class="sxs-lookup"><span data-stu-id="dc481-118">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="dc481-119">0</span><span class="sxs-lookup"><span data-stu-id="dc481-119">0</span></span>     | <span data-ttu-id="dc481-120">Środowisko uruchomieniowe języka wspólnego używa nowego kompilatora 64-bitowego JIT zawartego w .NET Framework 4,6 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="dc481-120">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="dc481-121">1</span><span class="sxs-lookup"><span data-stu-id="dc481-121">1</span></span>     | <span data-ttu-id="dc481-122">Środowisko uruchomieniowe języka wspólnego używa starszego 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="dc481-122">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="dc481-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dc481-123">Child elements</span></span>

<span data-ttu-id="dc481-124">Brak</span><span class="sxs-lookup"><span data-stu-id="dc481-124">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="dc481-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dc481-125">Parent elements</span></span>  
  
| <span data-ttu-id="dc481-126">Element</span><span class="sxs-lookup"><span data-stu-id="dc481-126">Element</span></span>         | <span data-ttu-id="dc481-127">Opis</span><span class="sxs-lookup"><span data-stu-id="dc481-127">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="dc481-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc481-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="dc481-129">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="dc481-129">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="dc481-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc481-130">Remarks</span></span>  

<span data-ttu-id="dc481-131">Począwszy od .NET Framework 4,6, środowisko uruchomieniowe języka wspólnego używa nowego kompilatora 64-bitowego dla kompilacji just-in-Time (JIT) domyślnie.</span><span class="sxs-lookup"><span data-stu-id="dc481-131">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="dc481-132">W niektórych przypadkach może to skutkować różnicą w zachowaniu kodu aplikacji, który był skompilowany przez poprzednią wersję 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="dc481-132">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="dc481-133">Ustawiając `enabled` atrybut `<useLegacyJit>` elementu na`1`, można wyłączyć nowy kompilator 64-bitowy JIT, a zamiast tego skompilować aplikację przy użyciu starszego, 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="dc481-133">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc481-134">`<useLegacyJit>` Element ma wpływ tylko na 64-bitową kompilację JIT.</span><span class="sxs-lookup"><span data-stu-id="dc481-134">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="dc481-135">Kompilacja z 32-bitowym kompilatorem JIT nie ma żadnych zmian.</span><span class="sxs-lookup"><span data-stu-id="dc481-135">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="dc481-136">Zamiast korzystać z ustawienia pliku konfiguracji, można włączyć starszy 64-bitowy kompilator JIT na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="dc481-136">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="dc481-137">Ustawianie zmiennej środowiskowej</span><span class="sxs-lookup"><span data-stu-id="dc481-137">Setting an environment variable</span></span>

  <span data-ttu-id="dc481-138">Ustaw zmienną `0` `1` środowiskową na wartość (Użyj nowego kompilatora 64-bitowego JIT) lub (Użyj starszego, 64-bitowego kompilatora JIT): `COMPLUS_useLegacyJit`</span><span class="sxs-lookup"><span data-stu-id="dc481-138">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="dc481-139">Zmienna środowiskowa ma *zakres globalny*, co oznacza, że ma wpływ na wszystkie aplikacje działające na komputerze.</span><span class="sxs-lookup"><span data-stu-id="dc481-139">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="dc481-140">Jeśli ta opcja jest ustawiona, może być zastąpiona przez ustawienie pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc481-140">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="dc481-141">W nazwie zmiennej środowiskowej nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="dc481-141">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="dc481-142">Dodawanie klucza rejestru</span><span class="sxs-lookup"><span data-stu-id="dc481-142">Adding a registry key</span></span>

  <span data-ttu-id="dc481-143">Można włączyć starszy kompilator 64-bitowy JIT, dodając `REG_DWORD` wartość do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` lub `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucz w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="dc481-143">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="dc481-144">Wartość jest nazywana `useLegacyJit`.</span><span class="sxs-lookup"><span data-stu-id="dc481-144">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="dc481-145">Jeśli wartość jest równa 0, używany jest nowy kompilator.</span><span class="sxs-lookup"><span data-stu-id="dc481-145">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="dc481-146">Jeśli wartość wynosi 1, jest włączony starszy 64-bitowy kompilator JIT.</span><span class="sxs-lookup"><span data-stu-id="dc481-146">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="dc481-147">W nazwie wartości rejestru nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="dc481-147">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="dc481-148">Dodanie wartości do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klucza ma wpływ na wszystkie aplikacje uruchomione na komputerze.</span><span class="sxs-lookup"><span data-stu-id="dc481-148">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="dc481-149">Dodanie wartości do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucza ma wpływ na wszystkie aplikacje uruchamiane przez bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dc481-149">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="dc481-150">Jeśli komputer jest skonfigurowany z wieloma kontami użytkowników, będzie to miało wpływ tylko na aplikacje uruchamiane przez bieżącego użytkownika, chyba że wartość zostanie dodana do kluczy rejestru dla innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="dc481-150">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="dc481-151">`<useLegacyJit>` Dodanie elementu do pliku konfiguracji zastępuje ustawienia rejestru, jeśli są obecne.</span><span class="sxs-lookup"><span data-stu-id="dc481-151">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc481-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc481-152">Example</span></span>  

<span data-ttu-id="dc481-153">Następujący plik konfiguracji wyłącza kompilację z nowym 64-bitowym kompilatorem JIT, a zamiast tego używa starszego, 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="dc481-153">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc481-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc481-154">See also</span></span>

- [<span data-ttu-id="dc481-155">\<Element > środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="dc481-155">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="dc481-156">\<> elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="dc481-156">\<configuration> Element</span></span>](../configuration-element.md)
- [<span data-ttu-id="dc481-157">Środki zaradcze Nowy 64-bitowy kompilator JIT</span><span class="sxs-lookup"><span data-stu-id="dc481-157">Mitigation: New 64-bit JIT Compiler</span></span>](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
