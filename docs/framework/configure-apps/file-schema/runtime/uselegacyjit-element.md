---
title: <useLegacyJit> Element
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
ms.openlocfilehash: a126b8c0050a8d1fd96a3d090f9b018a9faa07a7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968854"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="0ee4a-102">\<useLegacyJit> Element</span><span class="sxs-lookup"><span data-stu-id="0ee4a-102">\<useLegacyJit> Element</span></span>

<span data-ttu-id="0ee4a-103">Określa, czy środowisko uruchomieniowe języka wspólnego korzysta ze starszego 64-bitowego kompilatora JIT dla kompilacji just in Time.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<useLegacyJit>**  
  
## <a name="syntax"></a><span data-ttu-id="0ee4a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ee4a-104">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="0ee4a-105">Nazwa elementu `useLegacyJit` uwzględnia wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-105">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ee4a-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0ee4a-106">Attributes and elements</span></span>

<span data-ttu-id="0ee4a-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ee4a-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0ee4a-108">Attributes</span></span>  
  
| <span data-ttu-id="0ee4a-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0ee4a-109">Attribute</span></span> | <span data-ttu-id="0ee4a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="0ee4a-110">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="0ee4a-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-111">Required attribute.</span></span><br><br><span data-ttu-id="0ee4a-112">Określa, czy środowisko uruchomieniowe używa starszego 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-112">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="0ee4a-113">włączony atrybut</span><span class="sxs-lookup"><span data-stu-id="0ee4a-113">enabled attribute</span></span>  
  
| <span data-ttu-id="0ee4a-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="0ee4a-114">Value</span></span> | <span data-ttu-id="0ee4a-115">Opis</span><span class="sxs-lookup"><span data-stu-id="0ee4a-115">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="0ee4a-116">0</span><span class="sxs-lookup"><span data-stu-id="0ee4a-116">0</span></span>     | <span data-ttu-id="0ee4a-117">Środowisko uruchomieniowe języka wspólnego używa nowego kompilatora 64-bitowego JIT zawartego w .NET Framework 4,6 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-117">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="0ee4a-118">1</span><span class="sxs-lookup"><span data-stu-id="0ee4a-118">1</span></span>     | <span data-ttu-id="0ee4a-119">Środowisko uruchomieniowe języka wspólnego używa starszego 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-119">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="0ee4a-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0ee4a-120">Child elements</span></span>

<span data-ttu-id="0ee4a-121">Brak</span><span class="sxs-lookup"><span data-stu-id="0ee4a-121">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="0ee4a-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0ee4a-122">Parent elements</span></span>  
  
| <span data-ttu-id="0ee4a-123">Element</span><span class="sxs-lookup"><span data-stu-id="0ee4a-123">Element</span></span>         | <span data-ttu-id="0ee4a-124">Opis</span><span class="sxs-lookup"><span data-stu-id="0ee4a-124">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="0ee4a-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="0ee4a-126">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-126">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="0ee4a-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ee4a-127">Remarks</span></span>  

<span data-ttu-id="0ee4a-128">Począwszy od .NET Framework 4,6, środowisko uruchomieniowe języka wspólnego używa nowego kompilatora 64-bitowego dla kompilacji just-in-Time (JIT) domyślnie.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-128">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="0ee4a-129">W niektórych przypadkach może to skutkować różnicą w zachowaniu kodu aplikacji, który był skompilowany przez poprzednią wersję 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-129">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="0ee4a-130">Ustawiając `enabled` atrybut `<useLegacyJit>` elementu na `1` , można wyłączyć nowy kompilator 64-bitowy JIT, a zamiast tego skompilować aplikację przy użyciu starszego, 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-130">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ee4a-131">`<useLegacyJit>`Element ma wpływ tylko na 64-bitową kompilację JIT.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-131">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="0ee4a-132">Kompilacja z 32-bitowym kompilatorem JIT nie ma żadnych zmian.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-132">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="0ee4a-133">Zamiast korzystać z ustawienia pliku konfiguracji, można włączyć starszy 64-bitowy kompilator JIT na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="0ee4a-133">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="0ee4a-134">Ustawianie zmiennej środowiskowej</span><span class="sxs-lookup"><span data-stu-id="0ee4a-134">Setting an environment variable</span></span>

  <span data-ttu-id="0ee4a-135">Ustaw `COMPLUS_useLegacyJit` zmienną środowiskową na wartość `0` (Użyj nowego kompilatora 64-bitowego JIT) lub `1` (Użyj starszego, 64-bitowego kompilatora JIT):</span><span class="sxs-lookup"><span data-stu-id="0ee4a-135">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```env  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="0ee4a-136">Zmienna środowiskowa ma *zakres globalny*, co oznacza, że ma wpływ na wszystkie aplikacje działające na komputerze.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-136">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="0ee4a-137">Jeśli ta opcja jest ustawiona, może być zastąpiona przez ustawienie pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-137">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="0ee4a-138">W nazwie zmiennej środowiskowej nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-138">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="0ee4a-139">Dodawanie klucza rejestru</span><span class="sxs-lookup"><span data-stu-id="0ee4a-139">Adding a registry key</span></span>

  <span data-ttu-id="0ee4a-140">Można włączyć starszy kompilator 64-bitowy JIT, dodając `REG_DWORD` wartość do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` lub `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucz w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-140">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="0ee4a-141">Wartość jest nazywana `useLegacyJit` .</span><span class="sxs-lookup"><span data-stu-id="0ee4a-141">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="0ee4a-142">Jeśli wartość jest równa 0, używany jest nowy kompilator.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-142">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="0ee4a-143">Jeśli wartość wynosi 1, jest włączony starszy 64-bitowy kompilator JIT.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-143">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="0ee4a-144">W nazwie wartości rejestru nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-144">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="0ee4a-145">Dodanie wartości do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klucza ma wpływ na wszystkie aplikacje uruchomione na komputerze.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-145">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="0ee4a-146">Dodanie wartości do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucza ma wpływ na wszystkie aplikacje uruchamiane przez bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-146">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="0ee4a-147">Jeśli komputer jest skonfigurowany z wieloma kontami użytkowników, będzie to miało wpływ tylko na aplikacje uruchamiane przez bieżącego użytkownika, chyba że wartość zostanie dodana do kluczy rejestru dla innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-147">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="0ee4a-148">Dodanie `<useLegacyJit>` elementu do pliku konfiguracji zastępuje ustawienia rejestru, jeśli są obecne.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-148">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ee4a-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ee4a-149">Example</span></span>  

<span data-ttu-id="0ee4a-150">Następujący plik konfiguracji wyłącza kompilację z nowym 64-bitowym kompilatorem JIT, a zamiast tego używa starszego, 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="0ee4a-150">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ee4a-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ee4a-151">See also</span></span>

- [<span data-ttu-id="0ee4a-152">\<runtime>Postaci</span><span class="sxs-lookup"><span data-stu-id="0ee4a-152">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="0ee4a-153">\<configuration>Postaci</span><span class="sxs-lookup"><span data-stu-id="0ee4a-153">\<configuration> Element</span></span>](../configuration-element.md)
- [<span data-ttu-id="0ee4a-154">Środki zaradcze: nowy 64-bitowy kompilator JIT</span><span class="sxs-lookup"><span data-stu-id="0ee4a-154">Mitigation: New 64-bit JIT Compiler</span></span>](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
