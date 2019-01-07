---
title: Konfigurowanie przekierowywania powiązań zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 37ff2b42ec338d31242a2391cea002fbe582c6dd
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029583"
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="65f21-102">Konfigurowanie przekierowywania powiązań zestawów</span><span class="sxs-lookup"><span data-stu-id="65f21-102">Configuring Assembly Binding Redirection</span></span>
<span data-ttu-id="65f21-103">Domyślnie aplikacje używają zbiór zestawów .NET Framework, które są dostarczane z wersji środowiska uruchomieniowego, które umożliwiają kompilowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="65f21-103">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="65f21-104">Możesz użyć **appliesTo** atrybutu na [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) elementu w pliku konfiguracji aplikacji do przekierowywania odwołań do powiązań zestawów do określonej wersji programu .NET Zestawy struktury.</span><span class="sxs-lookup"><span data-stu-id="65f21-104">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="65f21-105">Ten atrybut opcjonalny używa numeru wersji .NET Framework w celu wskazania, której wersji ma zastosowanie do.</span><span class="sxs-lookup"><span data-stu-id="65f21-105">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="65f21-106">Jeśli nie **appliesTo** atrybut jest określony,  **\<assemblyBinding >** element ma zastosowanie do wszystkich wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65f21-106">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="65f21-107">**AppliesTo** atrybut wprowadzono w programie .NET Framework w wersji 1.1; jest ignorowana przez program .NET Framework w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="65f21-107">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="65f21-108">Oznacza to, że wszystkie  **\<assemblyBinding >** elementy są stosowane podczas korzystania z wersji programu .NET Framework 1.0, nawet jeśli **appliesTo** atrybut jest określony.</span><span class="sxs-lookup"><span data-stu-id="65f21-108">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65f21-109">Użyj **appliesTo** atrybutu, aby ograniczyć przekierowanie powiązań zestawów do określonej wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="65f21-109">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="65f21-110">Na przykład aby przekierować powiązanie zestawu dla zestawu .NET Framework w wersji 1.0, należy dołączyć następujący kod XML w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="65f21-110">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="65f21-111">**\<AssemblyBinding >** elementy są zależne od kolejności.</span><span class="sxs-lookup"><span data-stu-id="65f21-111">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="65f21-112">Należy wprowadzić informacje o przekierowaniach powiązań zestawów dla dowolnego środowiska .NET Framework w wersji 1.0 zestawów najpierw następuje informacje o przekierowaniach powiązań zestawów dla dowolne zestawy, .NET Framework w wersji 1.1.</span><span class="sxs-lookup"><span data-stu-id="65f21-112">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="65f21-113">Na koniec wprowadź informacje o przekierowaniach powiązań zestawów dla przekierowania z zestawu .NET Framework, która nie korzysta z **appliesTo** atrybut i dlatego ma zastosowanie do wszystkich wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65f21-113">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="65f21-114">W przypadku konfliktu przekierowania jest używana pierwsza pasująca instrukcja przekierowania w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="65f21-114">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="65f21-115">Na przykład aby przekierować jedno odwołanie do zestawu .NET Framework w wersji 1.0, a inne odwołanie do zestawu .NET Framework w wersji 1.1, możesz użyć wzoru pokazanego w poniższym pseudokodzie.</span><span class="sxs-lookup"><span data-stu-id="65f21-115">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
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
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="65f21-116">Debugowanie błędów pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="65f21-116">Debugging Configuration File Errors</span></span>  
 <span data-ttu-id="65f21-117">Środowisko uruchomieniowe analizuje pliki konfiguracji raz, gdy domeny aplikacji, zostanie utworzona i ładuje kodu do tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="65f21-117">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="65f21-118">Środowisko uruchomieniowe języka wspólnego obsługuje błędy w pliku konfiguracji, ignorując wpis.</span><span class="sxs-lookup"><span data-stu-id="65f21-118">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="65f21-119">Środowisko wykonawcze ignoruje plik całą konfigurację, jeśli zawiera on nieprawidłowo sformułowany kod XML.</span><span class="sxs-lookup"><span data-stu-id="65f21-119">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="65f21-120">Nieprawidłowy kod XML, aby uzyskać tylko nieprawidłowe sekcje są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="65f21-120">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="65f21-121">Można określić, czy plik konfiguracji jest on używany przez określenie, czy występują przekierowania powiązań zestawu.</span><span class="sxs-lookup"><span data-stu-id="65f21-121">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="65f21-122">Użyj [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) Aby wyświetlić zestawy, które są ładowane.</span><span class="sxs-lookup"><span data-stu-id="65f21-122">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="65f21-123">Aby wyświetlić wszystkie powiązania zestawów, należy ustawić wpis dla **ForceLog** w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="65f21-123">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f21-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65f21-124">See Also</span></span>  
- [<span data-ttu-id="65f21-125">Instrukcje: Włączanie i wyłączanie automatycznego przekierowania powiązań</span><span class="sxs-lookup"><span data-stu-id="65f21-125">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
