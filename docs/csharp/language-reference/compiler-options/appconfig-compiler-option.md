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
# <a name="-appconfig-c-compiler-options"></a><span data-ttu-id="44c63-102">-AppConfig (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="44c63-102">-appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="44c63-103">Opcja kompilatora **-AppConfig** umożliwia C# aplikacji określenie lokalizacji pliku konfiguracji aplikacji (App. config) zestawu w środowisku uruchomieniowym języka wspólnego (CLR) w czasie powiązania zestawu.</span><span class="sxs-lookup"><span data-stu-id="44c63-103">The **-appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44c63-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="44c63-104">Syntax</span></span>  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="44c63-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="44c63-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="44c63-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="44c63-106">Required.</span></span> <span data-ttu-id="44c63-107">Plik konfiguracji aplikacji, który zawiera ustawienia powiązania zestawu.</span><span class="sxs-lookup"><span data-stu-id="44c63-107">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44c63-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44c63-108">Remarks</span></span>  
 <span data-ttu-id="44c63-109">Jednym z zastosowań **-AppConfig** jest zaawansowane scenariusze, w których zestaw musi odwoływać się zarówno do wersji .NET Framework, jak i .NET Framework dla wersji Silverlight określonego zestawu odwołania w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="44c63-109">One use of **-appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="44c63-110">Na przykład Projektant XAML zapisany w Windows Presentation Foundation (WPF) może potrzebować odwoływać się zarówno do pulpitu WPF, interfejsu użytkownika projektanta, jak i podzbioru WPF, który jest dołączony do Silverlight.</span><span class="sxs-lookup"><span data-stu-id="44c63-110">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="44c63-111">Ten sam zestaw projektanta ma dostęp do obu zestawów.</span><span class="sxs-lookup"><span data-stu-id="44c63-111">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="44c63-112">Domyślnie oddzielne odwołania powodują wystąpienie błędu kompilatora, ponieważ powiązanie zestawu widzi dwa zestawy jako równoważne.</span><span class="sxs-lookup"><span data-stu-id="44c63-112">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="44c63-113">Opcja kompilatora **-AppConfig** umożliwia określenie lokalizacji pliku App. config, który wyłącza zachowanie domyślne przy użyciu `<supportPortability>` znacznika, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="44c63-113">The **-appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="44c63-114">Kompilator przekazuje lokalizację pliku do logiki powiązania zestawu środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="44c63-114">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="44c63-115">Jeśli używasz Microsoft Build Engine (MSBuild) do kompilowania aplikacji, możesz ustawić opcję kompilatora **-AppConfig** przez dodanie znacznika właściwości do pliku. csproj.</span><span class="sxs-lookup"><span data-stu-id="44c63-115">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **-appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="44c63-116">Aby użyć pliku App. config, który jest już ustawiony w projekcie, Dodaj tag `<UseAppConfigForCompiler>` właściwości do pliku. csproj i ustaw jego wartość na. `true`</span><span class="sxs-lookup"><span data-stu-id="44c63-116">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="44c63-117">Aby określić inny plik App. config, Dodaj tag `<AppConfigForCompiler>` właściwości i ustaw jego wartość na lokalizację pliku.</span><span class="sxs-lookup"><span data-stu-id="44c63-117">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44c63-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="44c63-118">Example</span></span>  
 <span data-ttu-id="44c63-119">W poniższym przykładzie przedstawiono plik App. config, który umożliwia aplikacjom odwołującą się do implementacji .NET Framework i .NET Framework dla implementacji Silverlight dowolnego zestawu .NET Framework, który istnieje w obu implementacjach.</span><span class="sxs-lookup"><span data-stu-id="44c63-119">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="44c63-120">Opcja kompilatora **-AppConfig** określa lokalizację pliku App. config.</span><span class="sxs-lookup"><span data-stu-id="44c63-120">The **-appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44c63-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44c63-121">See also</span></span>

- [<span data-ttu-id="44c63-122">\<Tag supportportability, element ></span><span class="sxs-lookup"><span data-stu-id="44c63-122">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [<span data-ttu-id="44c63-123">Opcje kompilatora C# w porządku alfabetycznym</span><span class="sxs-lookup"><span data-stu-id="44c63-123">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
