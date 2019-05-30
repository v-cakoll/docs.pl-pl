---
title: Włączanie lub wyłączanie wygenerowany automatycznie przekierowania powiązań
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: b6c9c3508c53e8a68a3f7e1cb12b6b6c95600e7b
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380106"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="566b5-102">Instrukcje: Włączanie i wyłączanie automatycznego przekierowania powiązań</span><span class="sxs-lookup"><span data-stu-id="566b5-102">How to: Enable and Disable Automatic Binding Redirection</span></span>

<span data-ttu-id="566b5-103">Podczas kompilowania aplikacji w programie Visual Studio przeznaczonych dla platformy .NET Framework 4.5.1 i nowszych wersjach, przekierowania powiązań mogą automatycznie dodawane do pliku konfiguracji aplikacji w celu zastąpienia ujednolicenia zestawów.</span><span class="sxs-lookup"><span data-stu-id="566b5-103">When you compile apps in Visual Studio that target the .NET Framework 4.5.1 and later versions, binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="566b5-104">Przekierowania powiązań są dodawane, jeśli aplikacja lub jej składniki odwołują się do więcej niż jednej wersji tego samego zestawu, nawet jeśli przekierowania powiązań zostaną określone ręcznie w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="566b5-104">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="566b5-105">Funkcja automatycznego przekierowywania powiązań ma wpływ na aplikacje pulpitu i aplikacje sieci web przeznaczonych dla platformy .NET Framework 4.5.1 lub nowszej, chociaż zachowanie jest nieco inne w przypadku aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="566b5-105">The automatic binding redirection feature affects desktop apps and web apps that target the .NET Framework 4.5.1 or a later version, although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="566b5-106">Można włączyć automatyczne przekierowywanie powiązań, jeśli masz istniejące aplikacje w tym docelowymi są poprzednie wersje programu .NET Framework lub wyłączyć tę funkcję, jeśli chcesz ręcznie tworzyć przekierowania powiązań.</span><span class="sxs-lookup"><span data-stu-id="566b5-106">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to manually author binding redirects.</span></span>

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="566b5-107">Wyłączyć automatyczne przekierowywanie powiązań w aplikacjach klasycznych</span><span class="sxs-lookup"><span data-stu-id="566b5-107">Disable automatic binding redirects in desktop apps</span></span>

<span data-ttu-id="566b5-108">Automatyczne przekierowania powiązań są domyślnie włączone dla aplikacji komputerowych Windows przeznaczonych dla środowiska .NET Framework 4.5.1 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="566b5-108">Automatic binding redirects are enabled by default for Windows desktop apps that target the .NET Framework 4.5.1 and later versions.</span></span> <span data-ttu-id="566b5-109">Przekierowania powiązań są dodawane do konfiguracji danych wyjściowych (**app.config**) plik, gdy aplikacja jest kompilowana i zastąpienia ujednolicenia zestawów, które mogłoby mieć miejsce.</span><span class="sxs-lookup"><span data-stu-id="566b5-109">The binding redirects are added to the output configuration (**app.config**) file when the app is compiled and override the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="566b5-110">Źródło **app.config** plik nie został zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="566b5-110">The source **app.config** file is not modified.</span></span> <span data-ttu-id="566b5-111">Tę funkcję można wyłączyć, modyfikując plik projektu dla aplikacji lub usunięcie zaznaczenia pola wyboru w oknie właściwości projektu w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="566b5-111">You can disable this feature by modifying the project file for the app or by deselecting a checkbox in the project's properties in Visual Studio.</span></span>

### <a name="disable-through-project-properties"></a><span data-ttu-id="566b5-112">Wyłączyć za pomocą właściwości projektu</span><span class="sxs-lookup"><span data-stu-id="566b5-112">Disable through project properties</span></span>

<span data-ttu-id="566b5-113">Jeśli masz program Visual Studio 2017 w wersji 15.7 lub nowszej, łatwo można wyłączyć przekierowania powiązań automatycznie wygenerowana na stronach właściwości projektu.</span><span class="sxs-lookup"><span data-stu-id="566b5-113">If you have Visual Studio 2017 version 15.7 or later, you can easily disable autogenerated binding redirects in the project's property pages.</span></span>

1. <span data-ttu-id="566b5-114">Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="566b5-114">Right-click the project in **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="566b5-115">Na **aplikacji** strony, usuń zaznaczenie pola wyboru **automatycznego generowania przekierowania powiązań** opcji.</span><span class="sxs-lookup"><span data-stu-id="566b5-115">On the **Application** page, uncheck the **Auto-generate binding redirects** option.</span></span>

3. <span data-ttu-id="566b5-116">Naciśnij klawisz **Ctrl**+**S** można zapisać zmiany.</span><span class="sxs-lookup"><span data-stu-id="566b5-116">Press **Ctrl**+**S** to save the change.</span></span>

### <a name="disable-manually-in-the-project-file"></a><span data-ttu-id="566b5-117">Wyłącz ręcznie w pliku projektu</span><span class="sxs-lookup"><span data-stu-id="566b5-117">Disable manually in the project file</span></span>

1. <span data-ttu-id="566b5-118">Otwórz plik projektu do edycji przy użyciu jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="566b5-118">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="566b5-119">W programie Visual Studio wybierz projekt w **Eksploratora rozwiązań**, a następnie wybierz **Otwórz Folder w Eksploratorze plików** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="566b5-119">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="566b5-120">W Eksploratorze plików Znajdź plik projektu (.csproj lub .vbproj), a następnie otwórz go w Notatniku.</span><span class="sxs-lookup"><span data-stu-id="566b5-120">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="566b5-121">W programie Visual Studio w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zwolnij projekt**.</span><span class="sxs-lookup"><span data-stu-id="566b5-121">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="566b5-122">Ponownie kliknij prawym przyciskiem myszy zwolnionego projektu, a następnie wybierz **Edytuj [projectname.csproj]** .</span><span class="sxs-lookup"><span data-stu-id="566b5-122">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="566b5-123">W pliku projektu znajdź następujący wpis właściwości:</span><span class="sxs-lookup"><span data-stu-id="566b5-123">In the project file, find the following property entry:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. <span data-ttu-id="566b5-124">Zmiana `true` do `false`:</span><span class="sxs-lookup"><span data-stu-id="566b5-124">Change `true` to `false`:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a><span data-ttu-id="566b5-125">Ręcznie Włącz automatyczne przekierowania powiązań</span><span class="sxs-lookup"><span data-stu-id="566b5-125">Enable automatic binding redirects manually</span></span>

<span data-ttu-id="566b5-126">Automatyczne przekierowania powiązań w istniejących aplikacjach można włączyć w tym docelowymi są starsze wersje programu .NET Framework lub w przypadkach, gdy zostanie wyświetlony automatycznie monit dodane przekierowanie.</span><span class="sxs-lookup"><span data-stu-id="566b5-126">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you're not automatically prompted to add a redirect.</span></span> <span data-ttu-id="566b5-127">Jeśli elementem docelowym nowszą wersję platformy, ale nie są wyświetlane automatycznie monity można dodać przekierowania, prawdopodobnie otrzymasz dane wyjściowe kompilacji, który sugeruje, że należy ponownie zamapować zestawów.</span><span class="sxs-lookup"><span data-stu-id="566b5-127">If you're targeting a newer version of the framework but do not get automatically prompted to add a redirect, you'll likely get build output that suggests you remap assemblies.</span></span>

1. <span data-ttu-id="566b5-128">Otwórz plik projektu do edycji przy użyciu jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="566b5-128">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="566b5-129">W programie Visual Studio wybierz projekt w **Eksploratora rozwiązań**, a następnie wybierz **Otwórz Folder w Eksploratorze plików** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="566b5-129">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="566b5-130">W Eksploratorze plików Znajdź plik projektu (.csproj lub .vbproj), a następnie otwórz go w Notatniku.</span><span class="sxs-lookup"><span data-stu-id="566b5-130">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="566b5-131">W programie Visual Studio w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zwolnij projekt**.</span><span class="sxs-lookup"><span data-stu-id="566b5-131">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="566b5-132">Ponownie kliknij prawym przyciskiem myszy zwolnionego projektu, a następnie wybierz **Edytuj [projectname.csproj]** .</span><span class="sxs-lookup"><span data-stu-id="566b5-132">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="566b5-133">Dodaj następujący element do pierwszej grupy właściwości konfiguracji (w obszarze \<PropertyGroup > tag):</span><span class="sxs-lookup"><span data-stu-id="566b5-133">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   <span data-ttu-id="566b5-134">Poniżej przedstawiono przykładowy plik projektu z elementem wstawione:</span><span class="sxs-lookup"><span data-stu-id="566b5-134">The following shows an example project file with the element inserted:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
       <PropertyGroup>
         <Configuration Condition=" '$(Configuration)' == ''     ">Debug</Configuration>
         <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
         <ProjectGuid>{123334}</ProjectGuid>
         ...
         <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
       </PropertyGroup>
     ...
   </Project>
   ```

3. <span data-ttu-id="566b5-135">Skompiluj aplikację.</span><span class="sxs-lookup"><span data-stu-id="566b5-135">Compile your app.</span></span>

## <a name="enable-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="566b5-136">Włącz automatyczne przekierowania powiązań w aplikacjach sieci web</span><span class="sxs-lookup"><span data-stu-id="566b5-136">Enable automatic binding redirects in web apps</span></span>

<span data-ttu-id="566b5-137">Automatyczne przekierowania powiązań są w przypadku aplikacji internetowych implementowane w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="566b5-137">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="566b5-138">Ponieważ konfiguracja źródła (**web.config**) plik musi zostać zmodyfikowany dla aplikacji sieci web, przekierowania powiązań nie są automatycznie dodawane do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="566b5-138">Because the source configuration (**web.config**) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="566b5-139">Jednak program Visual Studio powiadamia o konfliktach powiązań, więc można dodać przekierowania powiązań, aby rozwiązać konflikty.</span><span class="sxs-lookup"><span data-stu-id="566b5-139">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="566b5-140">Ponieważ zawsze monit o dodanie przekierowań powiązań, nie trzeba jawnie wyłączać tej funkcji dla aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="566b5-140">Because you're always prompted to add binding redirects, you don't need to explicitly disable this feature for a web app.</span></span>

<span data-ttu-id="566b5-141">Aby dodać przekierowania powiązań do **web.config** pliku:</span><span class="sxs-lookup"><span data-stu-id="566b5-141">To add binding redirects to a **web.config** file:</span></span>

1. <span data-ttu-id="566b5-142">W programie Visual Studio skompiluj aplikację i sprawdź, czy występują ostrzeżenia kompilacji.</span><span class="sxs-lookup"><span data-stu-id="566b5-142">In Visual Studio, compile the app, and check for build warnings.</span></span>

   <span data-ttu-id="566b5-143">![Ostrzeżenie w przypadku konfliktów odwołanie do zestawu kompilacji](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="566b5-143">![Build warning for assembly reference conflicts](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>

2. <span data-ttu-id="566b5-144">Jeśli występują konflikty powiązań zestawów, zostanie wyświetlone ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="566b5-144">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="566b5-145">Kliknij dwukrotnie ostrzeżenie, lub Wybierz ostrzeżenie i naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="566b5-145">Double-click the warning, or select the warning and press **Enter**.</span></span>

   <span data-ttu-id="566b5-146">Okno dialogowe, która umożliwia automatyczne dodawanie powiązania niezbędne przekierowuje do źródła **web.config** pojawia się w pliku.</span><span class="sxs-lookup"><span data-stu-id="566b5-146">A dialog box that enables you to automatically add the necessary binding redirects to the source **web.config** file appears.</span></span>

   <span data-ttu-id="566b5-147">![Okno dialogowe uprawnienia przekierowania powiązania](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="566b5-147">![Binding redirect permission dialog](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>

## <a name="see-also"></a><span data-ttu-id="566b5-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="566b5-148">See also</span></span>

- [<span data-ttu-id="566b5-149">\<bindingRedirect> Element</span><span class="sxs-lookup"><span data-stu-id="566b5-149">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="566b5-150">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="566b5-150">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
