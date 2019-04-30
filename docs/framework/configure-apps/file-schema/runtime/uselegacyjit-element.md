---
title: <useLegacyJit>, element
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a467599084f01b1a48c95c5e25fb1f869156dffa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673891"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="34b2f-102">\<useLegacyJit> Element</span><span class="sxs-lookup"><span data-stu-id="34b2f-102">\<useLegacyJit> Element</span></span>

<span data-ttu-id="34b2f-103">Określa, czy środowisko uruchomieniowe języka wspólnego używa starszej wersji 64-bitowy kompilator JIT dla kompilacji just in time.</span><span class="sxs-lookup"><span data-stu-id="34b2f-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
<span data-ttu-id="34b2f-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="34b2f-104">\<configuration></span></span>  
<span data-ttu-id="34b2f-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="34b2f-105">\<runtime></span></span>  
<span data-ttu-id="34b2f-106">\<useLegacyJit></span><span class="sxs-lookup"><span data-stu-id="34b2f-106">\<useLegacyJit></span></span>
  
## <a name="syntax"></a><span data-ttu-id="34b2f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="34b2f-107">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="34b2f-108">Nazwa elementu `useLegacyJit` jest uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="34b2f-108">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34b2f-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="34b2f-109">Attributes and elements</span></span>

<span data-ttu-id="34b2f-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="34b2f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34b2f-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="34b2f-111">Attributes</span></span>  
  
| <span data-ttu-id="34b2f-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="34b2f-112">Attribute</span></span> | <span data-ttu-id="34b2f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="34b2f-113">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="34b2f-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="34b2f-114">Required attribute.</span></span><br><br><span data-ttu-id="34b2f-115">Określa, czy środowisko wykonawcze używa starszej wersji 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="34b2f-115">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="34b2f-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="34b2f-116">enabled attribute</span></span>  
  
| <span data-ttu-id="34b2f-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="34b2f-117">Value</span></span> | <span data-ttu-id="34b2f-118">Opis</span><span class="sxs-lookup"><span data-stu-id="34b2f-118">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="34b2f-119">0</span><span class="sxs-lookup"><span data-stu-id="34b2f-119">0</span></span>     | <span data-ttu-id="34b2f-120">Środowisko uruchomieniowe języka wspólnego używa nowego 64-bitowy kompilator JIT zawarte w .NET Framework 4.6 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="34b2f-120">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="34b2f-121">1</span><span class="sxs-lookup"><span data-stu-id="34b2f-121">1</span></span>     | <span data-ttu-id="34b2f-122">Środowisko uruchomieniowe języka wspólnego używa starszej 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="34b2f-122">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="34b2f-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="34b2f-123">Child elements</span></span>

<span data-ttu-id="34b2f-124">Brak</span><span class="sxs-lookup"><span data-stu-id="34b2f-124">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="34b2f-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="34b2f-125">Parent elements</span></span>  
  
| <span data-ttu-id="34b2f-126">Element</span><span class="sxs-lookup"><span data-stu-id="34b2f-126">Element</span></span>         | <span data-ttu-id="34b2f-127">Opis</span><span class="sxs-lookup"><span data-stu-id="34b2f-127">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="34b2f-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34b2f-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="34b2f-129">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="34b2f-129">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="34b2f-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34b2f-130">Remarks</span></span>  

<span data-ttu-id="34b2f-131">Począwszy od programu .NET Framework 4.6, środowisko uruchomieniowe języka wspólnego nowy, 64-bitowego kompilatora dla kompilacji just in Time (JIT) domyślnie używa.</span><span class="sxs-lookup"><span data-stu-id="34b2f-131">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="34b2f-132">W niektórych przypadkach może to spowodować różnice w zachowaniu w kodzie aplikacji, która została skompilowana JIT w poprzedniej wersji 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="34b2f-132">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="34b2f-133">Ustawiając `enabled` atrybutu `<useLegacyJit>` elementu `1`, można wyłączyć nowego 64-bitowy kompilator JIT i zamiast tego Kompilowanie aplikacji za pomocą starszej wersji 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="34b2f-133">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34b2f-134">`<useLegacyJit>` Elementu dotyczy tylko kompilacja JIT w 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="34b2f-134">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="34b2f-135">Kompilacja z 32-bitowy kompilator JIT pozostaje bez zmian.</span><span class="sxs-lookup"><span data-stu-id="34b2f-135">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="34b2f-136">Zamiast korzystać z ustawień pliku konfiguracji, należy włączyć starszej wersji 64-bitowy kompilator JIT, które na dwa inne sposoby:</span><span class="sxs-lookup"><span data-stu-id="34b2f-136">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="34b2f-137">Ustawienie zmiennej środowiskowej</span><span class="sxs-lookup"><span data-stu-id="34b2f-137">Setting an environment variable</span></span>

  <span data-ttu-id="34b2f-138">Ustaw `COMPLUS_useLegacyJit` zmiennej środowiskowej, aby albo `0` (Użyj nowego 64-bitowy kompilator JIT) lub `1` (Użyj starszych 64-bitowy kompilator JIT):</span><span class="sxs-lookup"><span data-stu-id="34b2f-138">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="34b2f-139">Zmienna środowiskowa została *zakresu globalnego*, co oznacza, że ma to wpływ na wszystkie aplikacje są uruchamiane na maszynie.</span><span class="sxs-lookup"><span data-stu-id="34b2f-139">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="34b2f-140">Jeśli ustawiona, jego może zostać przesłonięta przez ustawienie pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34b2f-140">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="34b2f-141">Zmienna środowiskowa nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="34b2f-141">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="34b2f-142">Dodawanie klucza rejestru</span><span class="sxs-lookup"><span data-stu-id="34b2f-142">Adding a registry key</span></span>

  <span data-ttu-id="34b2f-143">Włącz starsze 64-bitowy kompilator JIT, dodając `REG_DWORD` wartość albo `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` lub `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucza w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="34b2f-143">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="34b2f-144">Wartość o nazwie `useLegacyJit`.</span><span class="sxs-lookup"><span data-stu-id="34b2f-144">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="34b2f-145">Jeśli wartość wynosi 0, jest używany nowy kompilator.</span><span class="sxs-lookup"><span data-stu-id="34b2f-145">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="34b2f-146">Jeśli wartość wynosi 1, starszego 64-bitowy kompilator JIT jest włączona.</span><span class="sxs-lookup"><span data-stu-id="34b2f-146">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="34b2f-147">Nazwa wartości rejestru nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="34b2f-147">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="34b2f-148">Dodaj wartość do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klucza ma wpływ na wszystkie aplikacje uruchomione na komputerze.</span><span class="sxs-lookup"><span data-stu-id="34b2f-148">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="34b2f-149">Dodaj wartość do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucza ma wpływ na wszystkie aplikacje uruchomione przez bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="34b2f-149">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="34b2f-150">Jeśli maszyna jest skonfigurowana z wieloma kontami użytkowników, tylko aplikacje uruchomione przez bieżącego użytkownika jest narażony, chyba, że wartość jest dodawana do kluczy rejestru, jak również do innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="34b2f-150">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="34b2f-151">Dodawanie `<useLegacyJit>` element do pliku konfiguracji zastępuje ustawienia rejestru, jeśli są one obecne.</span><span class="sxs-lookup"><span data-stu-id="34b2f-151">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34b2f-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="34b2f-152">Example</span></span>  

<span data-ttu-id="34b2f-153">Następujący plik konfiguracji powoduje wyłączenie kompilacji za pomocą nowego 64-bitowy kompilator JIT i zamiast tego używa starszej wersji 64-bitowego kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="34b2f-153">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="34b2f-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34b2f-154">See also</span></span>

- [<span data-ttu-id="34b2f-155">\<środowisko uruchomieniowe > Element</span><span class="sxs-lookup"><span data-stu-id="34b2f-155">\<runtime> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)
- [<span data-ttu-id="34b2f-156">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="34b2f-156">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
- [<span data-ttu-id="34b2f-157">Środki zaradcze: Nowy kompilator JIT 64-bitowych</span><span class="sxs-lookup"><span data-stu-id="34b2f-157">Mitigation: New 64-bit JIT Compiler</span></span>](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
