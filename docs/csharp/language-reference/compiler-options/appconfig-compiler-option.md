---
title: -appconfig (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a3f2c1bc9d0d3fec0635d284f64138f0432f59ef
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-appconfig-c-compiler-options"></a>-appconfig (opcje kompilatora C#)
**- Appconfig** — opcja kompilatora umożliwia aplikacji C# do określenia lokalizacji pliku konfiguracyjnego (app.config) aplikacji zestawu do środowisko uruchomieniowe języka wspólnego (CLR) w czasie powiązanie zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Wymagany. Plik konfiguracji aplikacji, który zawiera ustawienia powiązania zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Użycie jednego **- appconfig** jest zaawansowanych scenariuszy, w których zestawu musi odwoływać się do zarówno wersji platformy .NET i .NET Framework dla programu Silverlight wersja zestawu odwołania w szczególności w tym samym czasie. Na przykład projektanta XAML zapisywane w systemie Windows Presentation Foundation (WPF) może być konieczne odwoływać zarówno WPF pulpitu, interfejs użytkownika projektanta i podzbiór WPF dołączonej do programu Silverlight. Tego samego zestawu projektanta ma dostęp do obu zestawów. Domyślnie wystąpi błąd kompilatora spowodować oddzielne odwołań, ponieważ powiązań zestawów będzie widział dwa zestawy jako równoważne.  
  
 **- Appconfig** — opcja kompilatora umożliwia określenie lokalizacji pliku app.config, które wyłączają domyślne zachowanie przy użyciu `<supportPortability>` tagów, jak pokazano w poniższym przykładzie.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Kompilator przekazuje lokalizację pliku do logiki powiązania zestawu CLR.  
  
> [!NOTE]
>  Jeśli używasz aparat kompilacji firmy Microsoft (MSBuild) do tworzenia aplikacji, możesz ustawić **- appconfig** — opcja kompilatora, dodając tag właściwości do pliku .csproj. Aby użyć pliku app.config, który jest już ustawiony w projekcie, należy dodać tag właściwości `<UseAppConfigForCompiler>` do .csproj pliku i ustaw dla niego wartość `true`. Aby określić plik app.config różnych, należy dodać tag właściwości `<AppConfigForCompiler>` i ustaw jej wartość do lokalizacji pliku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia plik app.config, który umożliwia aplikacjom odwołują się do wdrożenia programu .NET Framework i programu .NET Framework dla programu Silverlight implementacji zestawu .NET Framework, który istnieje w obu wdrożeniach. **- Appconfig** — opcja kompilatora Określa lokalizację tego pliku app.config.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [\<supportPortability > — Element](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)  
 [Opcje kompilatora C# w porządku alfabetycznym](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
