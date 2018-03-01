---
title: -appconfig (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a3f2c1bc9d0d3fec0635d284f64138f0432f59ef
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-appconfig-c-compiler-options"></a><span data-ttu-id="837cd-102">-appconfig (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="837cd-102">-appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="837cd-103">**- Appconfig** — opcja kompilatora umożliwia aplikacji C# do określenia lokalizacji pliku konfiguracyjnego (app.config) aplikacji zestawu do środowisko uruchomieniowe języka wspólnego (CLR) w czasie powiązanie zestawu.</span><span class="sxs-lookup"><span data-stu-id="837cd-103">The **-appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="837cd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="837cd-104">Syntax</span></span>  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="837cd-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="837cd-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="837cd-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="837cd-106">Required.</span></span> <span data-ttu-id="837cd-107">Plik konfiguracji aplikacji, który zawiera ustawienia powiązania zestawu.</span><span class="sxs-lookup"><span data-stu-id="837cd-107">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="837cd-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="837cd-108">Remarks</span></span>  
 <span data-ttu-id="837cd-109">Użycie jednego **- appconfig** jest zaawansowanych scenariuszy, w których zestawu musi odwoływać się do zarówno wersji platformy .NET i .NET Framework dla programu Silverlight wersja zestawu odwołania w szczególności w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="837cd-109">One use of **-appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="837cd-110">Na przykład projektanta XAML zapisywane w systemie Windows Presentation Foundation (WPF) może być konieczne odwoływać zarówno WPF pulpitu, interfejs użytkownika projektanta i podzbiór WPF dołączonej do programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="837cd-110">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="837cd-111">Tego samego zestawu projektanta ma dostęp do obu zestawów.</span><span class="sxs-lookup"><span data-stu-id="837cd-111">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="837cd-112">Domyślnie wystąpi błąd kompilatora spowodować oddzielne odwołań, ponieważ powiązań zestawów będzie widział dwa zestawy jako równoważne.</span><span class="sxs-lookup"><span data-stu-id="837cd-112">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="837cd-113">**- Appconfig** — opcja kompilatora umożliwia określenie lokalizacji pliku app.config, które wyłączają domyślne zachowanie przy użyciu `<supportPortability>` tagów, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="837cd-113">The **-appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="837cd-114">Kompilator przekazuje lokalizację pliku do logiki powiązania zestawu CLR.</span><span class="sxs-lookup"><span data-stu-id="837cd-114">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="837cd-115">Jeśli używasz aparat kompilacji firmy Microsoft (MSBuild) do tworzenia aplikacji, możesz ustawić **- appconfig** — opcja kompilatora, dodając tag właściwości do pliku .csproj.</span><span class="sxs-lookup"><span data-stu-id="837cd-115">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **-appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="837cd-116">Aby użyć pliku app.config, który jest już ustawiony w projekcie, należy dodać tag właściwości `<UseAppConfigForCompiler>` do .csproj pliku i ustaw dla niego wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="837cd-116">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="837cd-117">Aby określić plik app.config różnych, należy dodać tag właściwości `<AppConfigForCompiler>` i ustaw jej wartość do lokalizacji pliku.</span><span class="sxs-lookup"><span data-stu-id="837cd-117">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="837cd-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="837cd-118">Example</span></span>  
 <span data-ttu-id="837cd-119">Poniższy przykład przedstawia plik app.config, który umożliwia aplikacjom odwołują się do wdrożenia programu .NET Framework i programu .NET Framework dla programu Silverlight implementacji zestawu .NET Framework, który istnieje w obu wdrożeniach.</span><span class="sxs-lookup"><span data-stu-id="837cd-119">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="837cd-120">**- Appconfig** — opcja kompilatora Określa lokalizację tego pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="837cd-120">The **-appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="837cd-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="837cd-121">See Also</span></span>  
 [<span data-ttu-id="837cd-122">\<supportPortability > — Element</span><span class="sxs-lookup"><span data-stu-id="837cd-122">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)  
 [<span data-ttu-id="837cd-123">Opcje kompilatora C# w porządku alfabetycznym</span><span class="sxs-lookup"><span data-stu-id="837cd-123">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
