---
title: Konfigurowanie przekierowywania powiązań zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
ms.openlocfilehash: 5b24d99aa23358272eecd042c40001413965d7f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181683"
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="a45cc-102">Konfigurowanie przekierowywania powiązań zestawów</span><span class="sxs-lookup"><span data-stu-id="a45cc-102">Configuring Assembly Binding Redirection</span></span>
<span data-ttu-id="a45cc-103">Domyślnie aplikacje używają zestawu zestawów .NET Framework dostarczanych z wersją środowiska wykonawczego używaną do kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a45cc-103">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="a45cc-104">Można użyć **atrybutu appliesTo** w [ \<elementze zestawuBinowanie>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) w pliku konfiguracji aplikacji w celu przekierowania odwołań do wiązania zestawu do określonej wersji zestawów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a45cc-104">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="a45cc-105">Ten atrybut opcjonalny używa numeru wersji programu .NET Framework, aby wskazać, której wersji dotyczy.</span><span class="sxs-lookup"><span data-stu-id="a45cc-105">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="a45cc-106">Jeśli nie **appliesTo** atrybut jest określony, \*\* \<assemblyBinding>\*\* element ma zastosowanie do wszystkich wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a45cc-106">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="a45cc-107">Atrybut **appliesTo** został wprowadzony w wersji programu .NET Framework w wersji 1.1; jest ignorowana przez program .NET Framework w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="a45cc-107">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="a45cc-108">Oznacza to, \*\* \<\*\* że wszystkie elementy>wiązania zestawu są stosowane podczas korzystania z programu .NET Framework w wersji 1.0, nawet jeśli atrybut **appliesTo** jest określony.</span><span class="sxs-lookup"><span data-stu-id="a45cc-108">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a45cc-109">Użyj **atrybutu appliesTo,** aby ograniczyć przekierowanie powiązania zestawu do określonej wersji środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="a45cc-109">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="a45cc-110">Na przykład, aby przekierować powiązanie zestawu dla zestawu .NET Framework w wersji 1.0, należy dołączyć następujący kod XML w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a45cc-110">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="a45cc-111">\*\* \<Elementy>zestawu\*\* są zależne od kolejności.</span><span class="sxs-lookup"><span data-stu-id="a45cc-111">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="a45cc-112">Najpierw należy wprowadzić informacje o przekierowywaniu powiązania zestawu dla wszystkich zestawów .NET Framework w wersji 1.0, a następnie informacje o przekierowywaniu powiązania zestawu dla dowolnych zestawów .NET Framework w wersji 1.1.</span><span class="sxs-lookup"><span data-stu-id="a45cc-112">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="a45cc-113">Na koniec wprowadź informacje o przekierowywaniu powiązania zestawu dla dowolnego przekierowania zestawu .NET Framework, który nie używa atrybutu **appliesTo** i dlatego ma zastosowanie do wszystkich wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a45cc-113">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="a45cc-114">W przypadku konfliktu w przekierowaniu używana jest pierwsza pasująca instrukcja przekierowania w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="a45cc-114">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="a45cc-115">Na przykład, aby przekierować jedno odwołanie do zestawu .NET Framework w wersji 1.0 i inne odwołanie do zestawu .NET Framework w wersji 1.1, należy użyć wzorca pokazanego w poniższym pseudokodem.</span><span class="sxs-lookup"><span data-stu-id="a45cc-115">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
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
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="a45cc-116">Debugowanie błędów pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a45cc-116">Debugging Configuration File Errors</span></span>  
 <span data-ttu-id="a45cc-117">Środowisko wykonawcze analizuje pliki konfiguracyjne raz podczas tworzenia domeny aplikacji i ładuje kod do tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a45cc-117">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="a45cc-118">Środowisko wykonawcze języka wspólnego obsługuje błędy w pliku konfiguracji, ignorując wpis.</span><span class="sxs-lookup"><span data-stu-id="a45cc-118">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="a45cc-119">Środowisko wykonawcze ignoruje cały plik konfiguracyjny, jeśli zawiera zniekształcony kod XML.</span><span class="sxs-lookup"><span data-stu-id="a45cc-119">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="a45cc-120">W przypadku nieprawidłowego kodu XML tylko nieprawidłowe sekcje są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a45cc-120">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="a45cc-121">Można określić, czy plik konfiguracji jest używany przez określenie, czy występują przekierowania powiązania zestawu.</span><span class="sxs-lookup"><span data-stu-id="a45cc-121">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="a45cc-122">Użyj [podglądu dziennika wiązania zestawu (Fuslogvw.exe),](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) aby zobaczyć, które zestawy są ładowane.</span><span class="sxs-lookup"><span data-stu-id="a45cc-122">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="a45cc-123">Aby wyświetlić wszystkie powiązania zestawu, należy ustawić wpis **dla ForceLog** w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="a45cc-123">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a45cc-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a45cc-124">See also</span></span>

- [<span data-ttu-id="a45cc-125">Porady: włączanie i wyłączanie automatycznego przekierowania powiązań</span><span class="sxs-lookup"><span data-stu-id="a45cc-125">How to: Enable and Disable Automatic Binding Redirection</span></span>](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
