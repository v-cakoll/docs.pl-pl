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
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398511"
---
# <a name="-appconfig-c-compiler-options"></a><span data-ttu-id="2cc3c-102">-appconfig (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="2cc3c-102">-appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="2cc3c-103">**- Appconfig** — opcja kompilatora umożliwia określanie lokalizacji zestawu pliku konfiguracji aplikacji (app.config) do środowisko uruchomieniowe języka wspólnego (CLR) w czasie powiązania zestawu aplikacji C#.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-103">The **-appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cc3c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2cc3c-104">Syntax</span></span>  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="2cc3c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2cc3c-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="2cc3c-106">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-106">Required.</span></span> <span data-ttu-id="2cc3c-107">Plik konfiguracyjny aplikacji zawierający ustawienia powiązania zestawu.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-107">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cc3c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2cc3c-108">Remarks</span></span>  
 <span data-ttu-id="2cc3c-109">Jednym z zastosowań **- appconfig** jest zaawansowane scenariusze, w których zestaw musi odwoływać się do wersji programu .NET Framework i .NET Framework dla Silverlight wersję szczególnym odniesieniem zespołu, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-109">One use of **-appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="2cc3c-110">Na przykład projektant XAML, napisany w Windows Presentation Foundation (WPF) może być można odwoływać się do obu pulpicie WPF dla interfejsu użytkownika projektanta i podzbiór WPF, który jest dołączony do programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-110">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="2cc3c-111">Tego samego zestawu projektanta ma dostęp do obu zestawów.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-111">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="2cc3c-112">Domyślnie oddzielne odwołania spowodują błąd kompilatora, ponieważ powiązanie zestawu widzi dwa zestawy jako równoważne.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-112">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="2cc3c-113">**- Appconfig** — opcja kompilatora umożliwia określenie lokalizacji pliku app.config, który wyłącza domyślne zachowanie za pomocą `<supportPortability>` tag, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-113">The **-appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="2cc3c-114">Kompilator przekazuje lokalizację pliku do logiki związanej z zestawem środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-114">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2cc3c-115">Jeśli używasz aparatu Microsoft Build Engine (MSBuild) do budowania aplikacji, możesz ustawić **- appconfig** — opcja kompilatora, dodając tag właściwości do pliku csproj.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-115">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **-appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="2cc3c-116">Aby użyć pliku app.config, który jest już ustawiony w projekcie, należy dodać tag właściwości `<UseAppConfigForCompiler>` do pliku csproj pliku i ustawić jej wartość na `true`.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-116">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="2cc3c-117">Aby określić plik app.config różnych, Dodaj tag właściwość `<AppConfigForCompiler>` i ustawić jej wartość na lokalizację pliku.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-117">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cc3c-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="2cc3c-118">Example</span></span>  
 <span data-ttu-id="2cc3c-119">Poniższy przykład przedstawia plik app.config, który umożliwia aplikacjom odwołanie się do wdrożenia programu .NET Framework i .NET Framework do wdrożenia dodatku Silverlight dowolnego zestawu .NET Framework, która znajduje się w obu implementacjach.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-119">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="2cc3c-120">**- Appconfig** — opcja kompilatora Określa lokalizację tego pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-120">The **-appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2cc3c-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2cc3c-121">See Also</span></span>  

- [<span data-ttu-id="2cc3c-122">\<supportportability — > Element</span><span class="sxs-lookup"><span data-stu-id="2cc3c-122">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)  
- [<span data-ttu-id="2cc3c-123">Opcje kompilatora C# w porządku alfabetycznym</span><span class="sxs-lookup"><span data-stu-id="2cc3c-123">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
