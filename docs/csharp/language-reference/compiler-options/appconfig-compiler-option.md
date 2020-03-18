---
title: -appconfig (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 7a7e8e61f65704a2e99385a1be320048d950324c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69922518"
---
# <a name="-appconfig-c-compiler-options"></a>-appconfig (Opcje kompilatora C#)
Opcja kompilatora **-appconfig** umożliwia aplikacji C# określenie lokalizacji pliku konfiguracji aplikacji (app.config) zestawu do wspólnego języka wykonywania (CLR) w czasie wiązania zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Wymagany. Plik konfiguracji aplikacji, który zawiera ustawienia wiązania zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Jednym z użycia **-appconfig** jest zaawansowane scenariusze, w których zestaw ma odwoływać się zarówno do wersji .NET Framework i .NET Framework dla wersji Silverlight określonego zestawu referencyjnego w tym samym czasie. Na przykład projektant XAML napisany w programie Windows Presentation Foundation (WPF) może odwoływać się zarówno do pulpitu WPF, interfejsu użytkownika projektanta, jak i podzbioru Protokołu WPF dołączonego do programu Silverlight. Ten sam zestaw projektanta ma dostęp do obu zestawów. Domyślnie oddzielne odwołania powodują błąd kompilatora, ponieważ powiązanie zestawu widzi dwa zestawy jako równoważne.  
  
 Opcja **kompilatora -appconfig** umożliwia określenie lokalizacji pliku app.config, który wyłącza `<supportPortability>` domyślne zachowanie przy użyciu tagu, jak pokazano w poniższym przykładzie.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Kompilator przekazuje lokalizację pliku do logiki powiązania zestawu CLR.  
  
> [!NOTE]
> Jeśli używasz aparatu kompilacji firmy Microsoft (MSBuild) do tworzenia aplikacji, można ustawić opcję kompilatora **-appconfig,** dodając tag właściwości do pliku csproj. Aby użyć pliku app.config, który jest już ustawiony `<UseAppConfigForCompiler>` w projekcie, dodaj tag właściwości `true`do pliku csproj i ustaw jego wartość na . Aby określić inny plik app.config, `<AppConfigForCompiler>` dodaj znacznik właściwości i ustaw jego wartość na lokalizację pliku.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono plik app.config, który umożliwia aplikacji, aby mieć odwołania do implementacji .NET Framework i .NET Framework dla silverlight implementacji dowolnego zestawu .NET Framework, który istnieje w obu implementacjach. Opcja kompilatora **-appconfig** określa lokalizację tego pliku app.config.  
  
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

- [\<obsługaportowalność elementu>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [Opcje kompilatora C# w porządku alfabetycznym](./listed-alphabetically.md)
