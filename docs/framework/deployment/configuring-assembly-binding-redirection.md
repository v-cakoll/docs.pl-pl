---
title: "Konfigurowanie przekierowywania powiązań zestawów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ff3f56b08aa3d6c7cb05bafd98d26f4700fa4e5a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="152f8-102">Konfigurowanie przekierowywania powiązań zestawów</span><span class="sxs-lookup"><span data-stu-id="152f8-102">Configuring Assembly Binding Redirection</span></span>
<span data-ttu-id="152f8-103">Domyślnie aplikacje używają zbiór zestawy .NET Framework, które zostały wydane z wersją środowiska uruchomieniowego umożliwia kompilowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="152f8-103">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="152f8-104">Można użyć **appliesTo** atrybutu [ \<assemblybinding — >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) elementu w pliku konfiguracyjnym aplikacji ma nastąpić przekierowanie powiązania odwołania do zestawów do określonej wersji programu .NET Zestawy struktury.</span><span class="sxs-lookup"><span data-stu-id="152f8-104">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="152f8-105">Ten opcjonalny atrybut używa numeru wersji .NET Framework w celu wskazania wersję, która dotyczy.</span><span class="sxs-lookup"><span data-stu-id="152f8-105">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="152f8-106">Jeśli nie **appliesTo** określono atrybut  **\<assemblybinding — >** element ma zastosowanie do wszystkich wersji platformy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="152f8-106">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="152f8-107">**AppliesTo** atrybutu została wprowadzona w programie .NET Framework w wersji 1.1; jest ignorowana przez program .NET Framework w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="152f8-107">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="152f8-108">Oznacza to, że wszystkie  **\<assemblybinding — >** elementy są stosowane, gdy przy użyciu platformy .NET Framework w wersji 1.0, nawet jeśli **appliesTo** jest określony atrybut.</span><span class="sxs-lookup"><span data-stu-id="152f8-108">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="152f8-109">Użyj **appliesTo** atrybutu, aby ograniczyć przekierowanie powiązań zestawów do określonej wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="152f8-109">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="152f8-110">Na przykład aby przekierować zestawu powiązania dla zestawu .NET Framework w wersji 1.0, można dołączyć następujący kod XML w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="152f8-110">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="152f8-111">**\<Assemblybinding — >** elementy są zależne od kolejności.</span><span class="sxs-lookup"><span data-stu-id="152f8-111">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="152f8-112">Wprowadź informacje przekierowania powiązania zestawu dla dowolne zestawy, .NET Framework w wersji 1.0 najpierw następuje informacji przekierowania powiązania zestawu dla dowolne zestawy, .NET Framework w wersji 1.1.</span><span class="sxs-lookup"><span data-stu-id="152f8-112">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="152f8-113">Na koniec wprowadź informacje dotyczące przekierowania powiązania zestawu dla przekierowania zestawu .NET Framework, które nie są używane **appliesTo** atrybut i dlatego ma zastosowanie do wszystkich wersji platformy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="152f8-113">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="152f8-114">W przypadku konfliktu przekierowania pierwszej instrukcji pasującego przekierowania w pliku konfiguracji jest używany.</span><span class="sxs-lookup"><span data-stu-id="152f8-114">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="152f8-115">Na przykład aby przekierować jedno odwołanie do zestawu .NET Framework w wersji 1.0 oraz inne odwołanie do zestawu .NET Framework w wersji 1.1, możesz użyć wzorzec pokazano w poniższych pseudocode.</span><span class="sxs-lookup"><span data-stu-id="152f8-115">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">   
<! — .NET Framework version 1.0 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">   
    <! — .NET Framework version 1.1 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="...">   
<!-- Redirects meant for all versions of the .NET Framework. -->   
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="152f8-116">Debugowanie błędów pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="152f8-116">Debugging Configuration File Errors</span></span>  
 <span data-ttu-id="152f8-117">Środowisko uruchomieniowe analizuje pliki konfiguracji raz po utworzeniu domeny aplikacji i ładuje kodu do tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="152f8-117">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="152f8-118">Środowisko uruchomieniowe języka wspólnego obsługuje błędy w pliku konfiguracji, pomijając wpis.</span><span class="sxs-lookup"><span data-stu-id="152f8-118">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="152f8-119">Środowisko uruchomieniowe ignoruje pliku całą konfigurację, jeśli zawiera on nieprawidłowo sformułowany kod XML.</span><span class="sxs-lookup"><span data-stu-id="152f8-119">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="152f8-120">Nieprawidłowy kod XML, aby uzyskać nieprawidłowe sekcje są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="152f8-120">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="152f8-121">Można określić, czy plik konfiguracji jest używana przez określenie, czy występują przekierowania powiązania zestawu.</span><span class="sxs-lookup"><span data-stu-id="152f8-121">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="152f8-122">Użyj [Podgląd dziennika powiązań zestawów (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) wyświetlić zestawy, które są ładowane.</span><span class="sxs-lookup"><span data-stu-id="152f8-122">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="152f8-123">Aby wyświetlić wszystkie powiązania przy użyciu zestawu, należy ustawić wpis dotyczący **ForceLog** w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="152f8-123">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="152f8-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="152f8-124">See Also</span></span>  
 [<span data-ttu-id="152f8-125">Porady: Włączanie i wyłączanie automatycznego przekierowania powiązań</span><span class="sxs-lookup"><span data-stu-id="152f8-125">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
