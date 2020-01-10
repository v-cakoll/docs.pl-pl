---
title: Konfigurowanie przekierowywania powiązań zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
ms.openlocfilehash: c7b9dcb99e08a1ef2844c5811897aa87ff86f866
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716553"
---
# <a name="configuring-assembly-binding-redirection"></a>Konfigurowanie przekierowywania powiązań zestawów
Domyślnie aplikacje używają zestawu .NET Framework zestawów, które zostały dostarczone z wersją środowiska uruchomieniowego używaną do kompilowania aplikacji. Możesz użyć **appliesTo** atrybutu na [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) elementu w pliku konfiguracji aplikacji do przekierowywania odwołań do powiązań zestawów do określonej wersji programu .NET Zestawy struktury. Ten opcjonalny atrybut używa numeru wersji .NET Framework, aby wskazać, której wersji dotyczy. Jeśli nie **appliesTo** atrybut jest określony, **\<assemblyBinding>** element ma zastosowanie do wszystkich wersji programu .NET Framework.  
  
 Atrybut **AppliesTo** został wprowadzony w .NET Framework w wersji 1,1; jest on ignorowany przez .NET Framework w wersji 1,0. Oznacza to, że wszystkie **\<assemblyBinding>** elementy są stosowane podczas korzystania z wersji programu .NET Framework 1.0, nawet jeśli **appliesTo** atrybut jest określony.  
  
> [!NOTE]
> Użyj atrybutu **AppliesTo** , aby ograniczyć przekierowywanie powiązań zestawu do określonej wersji środowiska uruchomieniowego.  
  
 Na przykład aby przekierować powiązanie zestawu dla zestawu .NET Framework w wersji 1,0, należy dołączyć następujący kod XML do pliku konfiguracji aplikacji.  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 **\<AssemblyBinding>** elementy są zależne od kolejności. Najpierw należy wprowadzić informacje o przekierowaniu powiązań zestawów dla każdego zestawu .NET Framework w wersji 1,0, a następnie informacje o przekierowaniu powiązań zestawu dla wszystkich zestawów .NET Framework wersji 1,1. Na koniec wprowadź informacje o przekierowaniu powiązań zestawów dla dowolnego przekierowania zestawu .NET Framework, który nie używa atrybutu **AppliesTo** i w związku z tym ma zastosowanie do wszystkich wersji .NET Framework. W przypadku konfliktu w przekierowaniu zostanie użyta pierwsza zgodna instrukcja przekierowania w pliku konfiguracji.  
  
 Na przykład, aby przekierować jedno odwołanie do zestawu .NET Framework w wersji 1,0 i innego odwołania do zestawu .NET Framework wersja 1,1, należy użyć wzorca pokazanego w poniższym pseudokodzie.  
  
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
  
## <a name="debugging-configuration-file-errors"></a>Debugowanie błędów pliku konfiguracji  
 Środowisko uruchomieniowe analizuje pliki konfiguracyjne raz podczas tworzenia domeny aplikacji i ładuje kod do tej domeny aplikacji. Środowisko uruchomieniowe języka wspólnego obsługuje błędy w pliku konfiguracji, ignorując wpis. Środowisko uruchomieniowe ignoruje cały plik konfiguracji, jeśli zawiera źle sformułowany kod XML. Dla nieprawidłowego kodu XML są ignorowane tylko nieprawidłowe sekcje.  
  
 Można określić, czy plik konfiguracji jest używany przez określenie, czy występują przekierowania powiązań zestawu. Użyj [podglądu dzienników powiązań zestawu (Fuslogvw. exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) , aby zobaczyć, które zestawy są ładowane. Aby wyświetlić wszystkie powiązania zestawów, należy ustawić wpis dla **ForceLog** w rejestrze.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: włączanie i wyłączanie automatycznego przekierowania powiązań](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
