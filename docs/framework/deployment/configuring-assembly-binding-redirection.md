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
# <a name="configuring-assembly-binding-redirection"></a>Konfigurowanie przekierowywania powiązań zestawów
Domyślnie aplikacje używają zestawu zestawów .NET Framework dostarczanych z wersją środowiska wykonawczego używaną do kompilowania aplikacji. Można użyć **atrybutu appliesTo** w [ \<elementze zestawuBinowanie>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) w pliku konfiguracji aplikacji w celu przekierowania odwołań do wiązania zestawu do określonej wersji zestawów .NET Framework. Ten atrybut opcjonalny używa numeru wersji programu .NET Framework, aby wskazać, której wersji dotyczy. Jeśli nie **appliesTo** atrybut jest określony, ** \<assemblyBinding>** element ma zastosowanie do wszystkich wersji programu .NET Framework.  
  
 Atrybut **appliesTo** został wprowadzony w wersji programu .NET Framework w wersji 1.1; jest ignorowana przez program .NET Framework w wersji 1.0. Oznacza to, ** \<** że wszystkie elementy>wiązania zestawu są stosowane podczas korzystania z programu .NET Framework w wersji 1.0, nawet jeśli atrybut **appliesTo** jest określony.  
  
> [!NOTE]
> Użyj **atrybutu appliesTo,** aby ograniczyć przekierowanie powiązania zestawu do określonej wersji środowiska wykonawczego.  
  
 Na przykład, aby przekierować powiązanie zestawu dla zestawu .NET Framework w wersji 1.0, należy dołączyć następujący kod XML w pliku konfiguracji aplikacji.  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 ** \<Elementy>zestawu** są zależne od kolejności. Najpierw należy wprowadzić informacje o przekierowywaniu powiązania zestawu dla wszystkich zestawów .NET Framework w wersji 1.0, a następnie informacje o przekierowywaniu powiązania zestawu dla dowolnych zestawów .NET Framework w wersji 1.1. Na koniec wprowadź informacje o przekierowywaniu powiązania zestawu dla dowolnego przekierowania zestawu .NET Framework, który nie używa atrybutu **appliesTo** i dlatego ma zastosowanie do wszystkich wersji programu .NET Framework. W przypadku konfliktu w przekierowaniu używana jest pierwsza pasująca instrukcja przekierowania w pliku konfiguracyjnym.  
  
 Na przykład, aby przekierować jedno odwołanie do zestawu .NET Framework w wersji 1.0 i inne odwołanie do zestawu .NET Framework w wersji 1.1, należy użyć wzorca pokazanego w poniższym pseudokodem.  
  
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
 Środowisko wykonawcze analizuje pliki konfiguracyjne raz podczas tworzenia domeny aplikacji i ładuje kod do tej domeny aplikacji. Środowisko wykonawcze języka wspólnego obsługuje błędy w pliku konfiguracji, ignorując wpis. Środowisko wykonawcze ignoruje cały plik konfiguracyjny, jeśli zawiera zniekształcony kod XML. W przypadku nieprawidłowego kodu XML tylko nieprawidłowe sekcje są ignorowane.  
  
 Można określić, czy plik konfiguracji jest używany przez określenie, czy występują przekierowania powiązania zestawu. Użyj [podglądu dziennika wiązania zestawu (Fuslogvw.exe),](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) aby zobaczyć, które zestawy są ładowane. Aby wyświetlić wszystkie powiązania zestawu, należy ustawić wpis **dla ForceLog** w rejestrze.  
  
## <a name="see-also"></a>Zobacz też

- [Porady: włączanie i wyłączanie automatycznego przekierowania powiązań](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
