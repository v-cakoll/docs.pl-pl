---
title: Konfigurowanie przekierowywania powiązań zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3424e7a412a79266d3bd9f20061ff4a0cd89115
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965757"
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="87eaf-102">Konfigurowanie przekierowywania powiązań zestawów</span><span class="sxs-lookup"><span data-stu-id="87eaf-102">Configuring Assembly Binding Redirection</span></span>
<span data-ttu-id="87eaf-103">Domyślnie aplikacje używają zestawu .NET Framework zestawów, które zostały dostarczone z wersją środowiska uruchomieniowego używaną do kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87eaf-103">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="87eaf-104">Możesz użyć **appliesTo** atrybutu na [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) elementu w pliku konfiguracji aplikacji do przekierowywania odwołań do powiązań zestawów do określonej wersji programu .NET Zestawy struktury.</span><span class="sxs-lookup"><span data-stu-id="87eaf-104">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="87eaf-105">Ten opcjonalny atrybut używa numeru wersji .NET Framework, aby wskazać, której wersji dotyczy.</span><span class="sxs-lookup"><span data-stu-id="87eaf-105">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="87eaf-106">Jeśli nie **appliesTo** atrybut jest określony, **\<assemblyBinding>** element ma zastosowanie do wszystkich wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87eaf-106">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="87eaf-107">Atrybut **AppliesTo** został wprowadzony w .NET Framework w wersji 1,1; jest on ignorowany przez .NET Framework w wersji 1,0.</span><span class="sxs-lookup"><span data-stu-id="87eaf-107">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="87eaf-108">Oznacza to, że wszystkie **\<assemblyBinding>** elementy są stosowane podczas korzystania z wersji programu .NET Framework 1.0, nawet jeśli **appliesTo** atrybut jest określony.</span><span class="sxs-lookup"><span data-stu-id="87eaf-108">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87eaf-109">Użyj atrybutu **AppliesTo** , aby ograniczyć przekierowywanie powiązań zestawu do określonej wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="87eaf-109">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="87eaf-110">Na przykład aby przekierować powiązanie zestawu dla zestawu .NET Framework w wersji 1,0, należy dołączyć następujący kod XML do pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87eaf-110">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="87eaf-111">**\<AssemblyBinding>** elementy są zależne od kolejności.</span><span class="sxs-lookup"><span data-stu-id="87eaf-111">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="87eaf-112">Najpierw należy wprowadzić informacje o przekierowaniu powiązań zestawów dla każdego zestawu .NET Framework w wersji 1,0, a następnie informacje o przekierowaniu powiązań zestawu dla wszystkich zestawów .NET Framework wersji 1,1.</span><span class="sxs-lookup"><span data-stu-id="87eaf-112">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="87eaf-113">Na koniec wprowadź informacje o przekierowaniu powiązań zestawów dla dowolnego przekierowania zestawu .NET Framework, który nie używa atrybutu **AppliesTo** i w związku z tym ma zastosowanie do wszystkich wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87eaf-113">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="87eaf-114">W przypadku konfliktu w przekierowaniu zostanie użyta pierwsza zgodna instrukcja przekierowania w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="87eaf-114">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="87eaf-115">Na przykład, aby przekierować jedno odwołanie do zestawu .NET Framework w wersji 1,0 i innego odwołania do zestawu .NET Framework wersja 1,1, należy użyć wzorca pokazanego w poniższym pseudokodzie.</span><span class="sxs-lookup"><span data-stu-id="87eaf-115">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">   
  <!-- .NET Framework version 1.0 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">   
  <!-- .NET Framework version 1.1 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="...">   
  <!-- Redirects meant for all versions of the .NET Framework. -->   
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="87eaf-116">Debugowanie błędów pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="87eaf-116">Debugging Configuration File Errors</span></span>  
 <span data-ttu-id="87eaf-117">Środowisko uruchomieniowe analizuje pliki konfiguracyjne raz podczas tworzenia domeny aplikacji i ładuje kod do tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87eaf-117">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="87eaf-118">Środowisko uruchomieniowe języka wspólnego obsługuje błędy w pliku konfiguracji, ignorując wpis.</span><span class="sxs-lookup"><span data-stu-id="87eaf-118">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="87eaf-119">Środowisko uruchomieniowe ignoruje cały plik konfiguracji, jeśli zawiera źle sformułowany kod XML.</span><span class="sxs-lookup"><span data-stu-id="87eaf-119">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="87eaf-120">Dla nieprawidłowego kodu XML są ignorowane tylko nieprawidłowe sekcje.</span><span class="sxs-lookup"><span data-stu-id="87eaf-120">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="87eaf-121">Można określić, czy plik konfiguracji jest używany przez określenie, czy występują przekierowania powiązań zestawu.</span><span class="sxs-lookup"><span data-stu-id="87eaf-121">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="87eaf-122">Użyj [podglądu dzienników powiązań zestawu (Fuslogvw. exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) , aby zobaczyć, które zestawy są ładowane.</span><span class="sxs-lookup"><span data-stu-id="87eaf-122">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="87eaf-123">Aby wyświetlić wszystkie powiązania zestawów, należy ustawić wpis dla **ForceLog** w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="87eaf-123">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87eaf-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87eaf-124">See also</span></span>

- [<span data-ttu-id="87eaf-125">Instrukcje: Włączanie i wyłączanie automatycznego przekierowywania powiązań</span><span class="sxs-lookup"><span data-stu-id="87eaf-125">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
