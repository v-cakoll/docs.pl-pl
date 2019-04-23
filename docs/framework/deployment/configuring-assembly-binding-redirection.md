---
title: Konfigurowanie przekierowywania powiązań zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5df468b87c62f454f6a42fa7a80d92e5ec199fd1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151544"
---
# <a name="configuring-assembly-binding-redirection"></a>Konfigurowanie przekierowywania powiązań zestawów
Domyślnie aplikacje używają zbiór zestawów .NET Framework, które są dostarczane z wersji środowiska uruchomieniowego, które umożliwiają kompilowanie aplikacji. Możesz użyć **appliesTo** atrybutu na [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) elementu w pliku konfiguracji aplikacji do przekierowywania odwołań do powiązań zestawów do określonej wersji programu .NET Zestawy struktury. Ten atrybut opcjonalny używa numeru wersji .NET Framework w celu wskazania, której wersji ma zastosowanie do. Jeśli nie **appliesTo** atrybut jest określony,  **\<assemblyBinding >** element ma zastosowanie do wszystkich wersji programu .NET Framework.  
  
 **AppliesTo** atrybut wprowadzono w programie .NET Framework w wersji 1.1; jest ignorowana przez program .NET Framework w wersji 1.0. Oznacza to, że wszystkie  **\<assemblyBinding >** elementy są stosowane podczas korzystania z wersji programu .NET Framework 1.0, nawet jeśli **appliesTo** atrybut jest określony.  
  
> [!NOTE]
>  Użyj **appliesTo** atrybutu, aby ograniczyć przekierowanie powiązań zestawów do określonej wersji środowiska uruchomieniowego.  
  
 Na przykład aby przekierować powiązanie zestawu dla zestawu .NET Framework w wersji 1.0, należy dołączyć następujący kod XML w pliku konfiguracyjnym aplikacji.  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
  **\<AssemblyBinding >** elementy są zależne od kolejności. Należy wprowadzić informacje o przekierowaniach powiązań zestawów dla dowolnego środowiska .NET Framework w wersji 1.0 zestawów najpierw następuje informacje o przekierowaniach powiązań zestawów dla dowolne zestawy, .NET Framework w wersji 1.1. Na koniec wprowadź informacje o przekierowaniach powiązań zestawów dla przekierowania z zestawu .NET Framework, która nie korzysta z **appliesTo** atrybut i dlatego ma zastosowanie do wszystkich wersji programu .NET Framework. W przypadku konfliktu przekierowania jest używana pierwsza pasująca instrukcja przekierowania w pliku konfiguracji.  
  
 Na przykład aby przekierować jedno odwołanie do zestawu .NET Framework w wersji 1.0, a inne odwołanie do zestawu .NET Framework w wersji 1.1, możesz użyć wzoru pokazanego w poniższym pseudokodzie.  
  
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
 Środowisko uruchomieniowe analizuje pliki konfiguracji raz, gdy domeny aplikacji, zostanie utworzona i ładuje kodu do tej domeny aplikacji. Środowisko uruchomieniowe języka wspólnego obsługuje błędy w pliku konfiguracji, ignorując wpis. Środowisko wykonawcze ignoruje plik całą konfigurację, jeśli zawiera on nieprawidłowo sformułowany kod XML. Nieprawidłowy kod XML, aby uzyskać tylko nieprawidłowe sekcje są ignorowane.  
  
 Można określić, czy plik konfiguracji jest on używany przez określenie, czy występują przekierowania powiązań zestawu. Użyj [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) Aby wyświetlić zestawy, które są ładowane. Aby wyświetlić wszystkie powiązania zestawów, należy ustawić wpis dla **ForceLog** w rejestrze.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Włączanie i wyłączanie automatycznego przekierowania powiązań](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
