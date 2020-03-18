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
# <a name="-appconfig-c-compiler-options"></a><span data-ttu-id="3ff8b-102">-appconfig (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="3ff8b-102">-appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="3ff8b-103">Opcja kompilatora **-appconfig** umożliwia aplikacji C# określenie lokalizacji pliku konfiguracji aplikacji (app.config) zestawu do wspólnego języka wykonywania (CLR) w czasie wiązania zestawu.</span><span class="sxs-lookup"><span data-stu-id="3ff8b-103">The **-appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ff8b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ff8b-104">Syntax</span></span>  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="3ff8b-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3ff8b-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="3ff8b-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="3ff8b-106">Required.</span></span> <span data-ttu-id="3ff8b-107">Plik konfiguracji aplikacji, który zawiera ustawienia wiązania zestawu.</span><span class="sxs-lookup"><span data-stu-id="3ff8b-107">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ff8b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ff8b-108">Remarks</span></span>  
 <span data-ttu-id="3ff8b-109">Jednym z użycia **-appconfig** jest zaawansowane scenariusze, w których zestaw ma odwoływać się zarówno do wersji .NET Framework i .NET Framework dla wersji Silverlight określonego zestawu referencyjnego w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="3ff8b-109">One use of **-appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="3ff8b-110">Na przykład projektant XAML napisany w programie Windows Presentation Foundation (WPF) może odwoływać się zarówno do pulpitu WPF, interfejsu użytkownika projektanta, jak i podzbioru Protokołu WPF dołączonego do programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="3ff8b-110">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="3ff8b-111">Ten sam zestaw projektanta ma dostęp do obu zestawów.</span><span class="sxs-lookup"><span data-stu-id="3ff8b-111">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="3ff8b-112">Domyślnie oddzielne odwołania powodują błąd kompilatora, ponieważ powiązanie zestawu widzi dwa zestawy jako równoważne.</span><span class="sxs-lookup"><span data-stu-id="3ff8b-112">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="3ff8b-113">Opcja **kompilatora -appconfig** umożliwia określenie lokalizacji pliku app.config, który wyłącza `<supportPortability>` domyślne zachowanie przy użyciu tagu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3ff8b-113">The **-appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="3ff8b-114">Kompilator przekazuje lokalizację pliku do logiki powiązania zestawu CLR.</span><span class="sxs-lookup"><span data-stu-id="3ff8b-114">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ff8b-115">Jeśli używasz aparatu kompilacji firmy Microsoft (MSBuild) do tworzenia aplikacji, można ustawić opcję kompilatora **-appconfig,** dodając tag właściwości do pliku csproj.</span><span class="sxs-lookup"><span data-stu-id="3ff8b-115">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **-appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="3ff8b-116">Aby użyć pliku app.config, który jest już ustawiony `<UseAppConfigForCompiler>` w projekcie, dodaj tag właściwości `true`do pliku csproj i ustaw jego wartość na .</span><span class="sxs-lookup"><span data-stu-id="3ff8b-116">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="3ff8b-117">Aby określić inny plik app.config, `<AppConfigForCompiler>` dodaj znacznik właściwości i ustaw jego wartość na lokalizację pliku.</span><span class="sxs-lookup"><span data-stu-id="3ff8b-117">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ff8b-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ff8b-118">Example</span></span>  
 <span data-ttu-id="3ff8b-119">W poniższym przykładzie przedstawiono plik app.config, który umożliwia aplikacji, aby mieć odwołania do implementacji .NET Framework i .NET Framework dla silverlight implementacji dowolnego zestawu .NET Framework, który istnieje w obu implementacjach.</span><span class="sxs-lookup"><span data-stu-id="3ff8b-119">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="3ff8b-120">Opcja kompilatora **-appconfig** określa lokalizację tego pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="3ff8b-120">The **-appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3ff8b-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ff8b-121">See also</span></span>

- [<span data-ttu-id="3ff8b-122">\<obsługaportowalność elementu></span><span class="sxs-lookup"><span data-stu-id="3ff8b-122">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [<span data-ttu-id="3ff8b-123">Opcje kompilatora C# w porządku alfabetycznym</span><span class="sxs-lookup"><span data-stu-id="3ff8b-123">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
