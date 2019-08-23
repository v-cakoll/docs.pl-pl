---
title: -AppConfig (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 7a7e8e61f65704a2e99385a1be320048d950324c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922518"
---
# <a name="-appconfig-c-compiler-options"></a>-AppConfig (C# opcje kompilatora)
Opcja kompilatora **-AppConfig** umożliwia C# aplikacji określenie lokalizacji pliku konfiguracji aplikacji (App. config) zestawu w środowisku uruchomieniowym języka wspólnego (CLR) w czasie powiązania zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Wymagana. Plik konfiguracji aplikacji, który zawiera ustawienia powiązania zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Jednym z zastosowań **-AppConfig** jest zaawansowane scenariusze, w których zestaw musi odwoływać się zarówno do wersji .NET Framework, jak i .NET Framework dla wersji Silverlight określonego zestawu odwołania w tym samym czasie. Na przykład Projektant XAML zapisany w Windows Presentation Foundation (WPF) może potrzebować odwoływać się zarówno do pulpitu WPF, interfejsu użytkownika projektanta, jak i podzbioru WPF, który jest dołączony do Silverlight. Ten sam zestaw projektanta ma dostęp do obu zestawów. Domyślnie oddzielne odwołania powodują wystąpienie błędu kompilatora, ponieważ powiązanie zestawu widzi dwa zestawy jako równoważne.  
  
 Opcja kompilatora **-AppConfig** umożliwia określenie lokalizacji pliku App. config, który wyłącza zachowanie domyślne przy użyciu `<supportPortability>` znacznika, jak pokazano w poniższym przykładzie.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Kompilator przekazuje lokalizację pliku do logiki powiązania zestawu środowiska CLR.  
  
> [!NOTE]
> Jeśli używasz Microsoft Build Engine (MSBuild) do kompilowania aplikacji, możesz ustawić opcję kompilatora **-AppConfig** przez dodanie znacznika właściwości do pliku. csproj. Aby użyć pliku App. config, który jest już ustawiony w projekcie, Dodaj tag `<UseAppConfigForCompiler>` właściwości do pliku. csproj i ustaw jego wartość na. `true` Aby określić inny plik App. config, Dodaj tag `<AppConfigForCompiler>` właściwości i ustaw jego wartość na lokalizację pliku.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono plik App. config, który umożliwia aplikacjom odwołującą się do implementacji .NET Framework i .NET Framework dla implementacji Silverlight dowolnego zestawu .NET Framework, który istnieje w obu implementacjach. Opcja kompilatora **-AppConfig** określa lokalizację pliku App. config.  
  
```xml  
<configuration>  
      <runtime>  
      <assemblyBinding>  
            <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
            <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
      </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [\<Tag supportportability, element >](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [Opcje kompilatora C# w porządku alfabetycznym](./listed-alphabetically.md)
