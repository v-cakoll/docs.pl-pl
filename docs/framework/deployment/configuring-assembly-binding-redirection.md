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
ms.workload: dotnet
ms.openlocfilehash: b53673d1ddb1de7fed087b4c5cb125e50f11b918
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-assembly-binding-redirection"></a>Konfigurowanie przekierowywania powiązań zestawów
Domyślnie aplikacje używają zbiór zestawy .NET Framework, które zostały wydane z wersją środowiska uruchomieniowego umożliwia kompilowanie aplikacji. Można użyć **appliesTo** atrybutu [ \<assemblybinding — >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) elementu w pliku konfiguracyjnym aplikacji ma nastąpić przekierowanie powiązania odwołania do zestawów do określonej wersji programu .NET Zestawy struktury. Ten opcjonalny atrybut używa numeru wersji .NET Framework w celu wskazania wersję, która dotyczy. Jeśli nie **appliesTo** określono atrybut  **\<assemblybinding — >** element ma zastosowanie do wszystkich wersji platformy .NET Framework.  
  
 **AppliesTo** atrybutu została wprowadzona w programie .NET Framework w wersji 1.1; jest ignorowana przez program .NET Framework w wersji 1.0. Oznacza to, że wszystkie  **\<assemblybinding — >** elementy są stosowane, gdy przy użyciu platformy .NET Framework w wersji 1.0, nawet jeśli **appliesTo** jest określony atrybut.  
  
> [!NOTE]
>  Użyj **appliesTo** atrybutu, aby ograniczyć przekierowanie powiązań zestawów do określonej wersji środowiska uruchomieniowego.  
  
 Na przykład aby przekierować zestawu powiązania dla zestawu .NET Framework w wersji 1.0, można dołączyć następujący kod XML w pliku konfiguracyjnym aplikacji.  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
  **\<Assemblybinding — >** elementy są zależne od kolejności. Wprowadź informacje przekierowania powiązania zestawu dla dowolne zestawy, .NET Framework w wersji 1.0 najpierw następuje informacji przekierowania powiązania zestawu dla dowolne zestawy, .NET Framework w wersji 1.1. Na koniec wprowadź informacje dotyczące przekierowania powiązania zestawu dla przekierowania zestawu .NET Framework, które nie są używane **appliesTo** atrybut i dlatego ma zastosowanie do wszystkich wersji platformy .NET Framework. W przypadku konfliktu przekierowania pierwszej instrukcji pasującego przekierowania w pliku konfiguracji jest używany.  
  
 Na przykład aby przekierować jedno odwołanie do zestawu .NET Framework w wersji 1.0 oraz inne odwołanie do zestawu .NET Framework w wersji 1.1, możesz użyć wzorzec pokazano w poniższych pseudocode.  
  
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
  
## <a name="debugging-configuration-file-errors"></a>Debugowanie błędów pliku konfiguracji  
 Środowisko uruchomieniowe analizuje pliki konfiguracji raz po utworzeniu domeny aplikacji i ładuje kodu do tej domeny aplikacji. Środowisko uruchomieniowe języka wspólnego obsługuje błędy w pliku konfiguracji, pomijając wpis. Środowisko uruchomieniowe ignoruje pliku całą konfigurację, jeśli zawiera on nieprawidłowo sformułowany kod XML. Nieprawidłowy kod XML, aby uzyskać nieprawidłowe sekcje są ignorowane.  
  
 Można określić, czy plik konfiguracji jest używana przez określenie, czy występują przekierowania powiązania zestawu. Użyj [Podgląd dziennika powiązań zestawów (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) wyświetlić zestawy, które są ładowane. Aby wyświetlić wszystkie powiązania przy użyciu zestawu, należy ustawić wpis dotyczący **ForceLog** w rejestrze.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: włączanie i wyłączanie automatycznego przekierowania powiązań](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
