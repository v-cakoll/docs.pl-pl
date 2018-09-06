---
title: -appconfig (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 33f79967c34736f2175e0bb6e2b5b88d211545c2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881239"
---
# <a name="-appconfig-c-compiler-options"></a>-appconfig (opcje kompilatora C#)
**- Appconfig** — opcja kompilatora umożliwia określanie lokalizacji zestawu pliku konfiguracji aplikacji (app.config) do środowisko uruchomieniowe języka wspólnego (CLR) w czasie powiązania zestawu aplikacji C#.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Wymagane. Plik konfiguracyjny aplikacji zawierający ustawienia powiązania zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Jednym z zastosowań **- appconfig** jest zaawansowane scenariusze, w których zestaw musi odwoływać się do wersji programu .NET Framework i .NET Framework dla Silverlight wersję szczególnym odniesieniem zespołu, w tym samym czasie. Na przykład projektant XAML, napisany w Windows Presentation Foundation (WPF) może być można odwoływać się do obu pulpicie WPF dla interfejsu użytkownika projektanta i podzbiór WPF, który jest dołączony do programu Silverlight. Tego samego zestawu projektanta ma dostęp do obu zestawów. Domyślnie oddzielne odwołania spowodują błąd kompilatora, ponieważ powiązanie zestawu widzi dwa zestawy jako równoważne.  
  
 **- Appconfig** — opcja kompilatora umożliwia określenie lokalizacji pliku app.config, który wyłącza domyślne zachowanie za pomocą `<supportPortability>` tag, jak pokazano w poniższym przykładzie.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Kompilator przekazuje lokalizację pliku do logiki związanej z zestawem środowiska CLR.  
  
> [!NOTE]
>  Jeśli używasz aparatu Microsoft Build Engine (MSBuild) do budowania aplikacji, możesz ustawić **- appconfig** — opcja kompilatora, dodając tag właściwości do pliku csproj. Aby użyć pliku app.config, który jest już ustawiony w projekcie, należy dodać tag właściwości `<UseAppConfigForCompiler>` do pliku csproj pliku i ustawić jej wartość na `true`. Aby określić plik app.config różnych, Dodaj tag właściwość `<AppConfigForCompiler>` i ustawić jej wartość na lokalizację pliku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia plik app.config, który umożliwia aplikacjom odwołanie się do wdrożenia programu .NET Framework i .NET Framework do wdrożenia dodatku Silverlight dowolnego zestawu .NET Framework, która znajduje się w obu implementacjach. **- Appconfig** — opcja kompilatora Określa lokalizację tego pliku app.config.  
  
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

- [\<supportportability — > Element](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)  
- [Opcje kompilatora C# w porządku alfabetycznym](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
