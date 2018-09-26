---
title: 'Porady: włączanie i wyłączanie automatycznego przekierowania powiązań'
ms.date: 09/12/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 9b9c9cbdb89ccf67942dcccee37ea410c6fa39a5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208675"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="b196c-102">Porady: włączanie i wyłączanie automatycznego przekierowania powiązań</span><span class="sxs-lookup"><span data-stu-id="b196c-102">How to: Enable and Disable Automatic Binding Redirection</span></span>

<span data-ttu-id="b196c-103">Podczas kompilowania aplikacji w programie Visual Studio, których platformą docelową [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] i nowsze wersje, przekierowania powiązań mogą być automatycznie dodawane do pliku konfiguracyjnego aplikacji w celu zastąpienia ujednolicenia zestawów.</span><span class="sxs-lookup"><span data-stu-id="b196c-103">When you compile apps in Visual Studio that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions, binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="b196c-104">Przekierowania powiązań są dodawane, jeśli aplikacja lub jej składniki odwołują się do więcej niż jednej wersji tego samego zestawu, nawet jeśli przekierowania powiązań zostaną określone ręcznie w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b196c-104">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="b196c-105">Funkcja automatycznego przekierowywania powiązań dotyczy tradycyjnych aplikacji komputerowych i aplikacji sieci web, których platformą docelową [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] lub nowszej, chociaż zachowanie jest nieco inne w przypadku aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="b196c-105">The automatic binding redirection feature affects traditional desktop apps and web apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] or a later version, although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="b196c-106">Można włączyć automatyczne przekierowywanie połączeń, jeśli są używane aplikacje, których platformami docelowymi są poprzednie wersje programu .NET Framework, ale można też wyłączyć tę funkcję, aby używać tworzonych ręcznie przekierowań powiązań.</span><span class="sxs-lookup"><span data-stu-id="b196c-106">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to keep manually authored binding redirects.</span></span>

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="b196c-107">Wyłączyć automatyczne przekierowywanie powiązań w aplikacjach klasycznych</span><span class="sxs-lookup"><span data-stu-id="b196c-107">Disable automatic binding redirects in desktop apps</span></span>

<span data-ttu-id="b196c-108">Automatyczne przekierowania powiązań są domyślnie włączone dla tradycyjnych aplikacji komputerowych, których platformą docelową [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="b196c-108">Automatic binding redirects are enabled by default for traditional desktop apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions.</span></span> <span data-ttu-id="b196c-109">Przekierowania powiązań są dodawane do wyjściowego pliku konfiguracji (app.config), gdy aplikacja jest kompilowana, co powoduje zastąpienie ujednolicenia zestawów, które mogłoby mieć miejsce.</span><span class="sxs-lookup"><span data-stu-id="b196c-109">The binding redirects are added to the output configuration (app.config) file when the app is compiled and overrides the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="b196c-110">Źródłowy plik app.config nie jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="b196c-110">The source app.config file is not modified.</span></span> <span data-ttu-id="b196c-111">Tę funkcję można wyłączyć, modyfikując plik projektu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b196c-111">You can disable this feature by modifying the project file for the app.</span></span>

1. <span data-ttu-id="b196c-112">Otwórz plik projektu do edycji przy użyciu jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="b196c-112">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="b196c-113">W programie Visual Studio wybierz projekt w **Eksploratora rozwiązań**, a następnie wybierz **Otwórz Folder w Eksploratorze plików** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="b196c-113">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="b196c-114">W Eksploratorze plików Znajdź plik projektu (.csproj lub .vbproj), a następnie otwórz go w Notatniku.</span><span class="sxs-lookup"><span data-stu-id="b196c-114">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="b196c-115">W programie Visual Studio w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zwolnij projekt**.</span><span class="sxs-lookup"><span data-stu-id="b196c-115">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="b196c-116">Ponownie kliknij prawym przyciskiem myszy zwolnionego projektu, a następnie wybierz **Edytuj [projectname.csproj]**.</span><span class="sxs-lookup"><span data-stu-id="b196c-116">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="b196c-117">W pliku projektu znajdź następujący wpis właściwości:</span><span class="sxs-lookup"><span data-stu-id="b196c-117">In the project file, find the following property entry:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. <span data-ttu-id="b196c-118">Zmiana `true` do `false`:</span><span class="sxs-lookup"><span data-stu-id="b196c-118">Change `true` to `false`:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a><span data-ttu-id="b196c-119">Ręcznie Włącz automatyczne przekierowania powiązań</span><span class="sxs-lookup"><span data-stu-id="b196c-119">Enable automatic binding redirects manually</span></span>

<span data-ttu-id="b196c-120">Automatyczne przekierowania powiązań w istniejących aplikacjach można włączyć w tym docelowymi są starsze wersje programu .NET Framework lub w przypadkach, gdy zostanie wyświetlony automatycznie monit dodane przekierowanie.</span><span class="sxs-lookup"><span data-stu-id="b196c-120">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you're not automatically prompted to add a redirect.</span></span> <span data-ttu-id="b196c-121">Jeśli elementem docelowym nowszą wersję platformy, ale nie są wyświetlane automatycznie monity można dodać przekierowania, prawdopodobnie otrzymasz dane wyjściowe kompilacji, który sugeruje, że należy ponownie zamapować zestawów.</span><span class="sxs-lookup"><span data-stu-id="b196c-121">If you're targeting a newer version of the framework but do not get automatically prompted to add a redirect, you'll likely get build output that suggests you remap assemblies.</span></span>

1. <span data-ttu-id="b196c-122">Otwórz plik projektu do edycji przy użyciu jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="b196c-122">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="b196c-123">W programie Visual Studio wybierz projekt w **Eksploratora rozwiązań**, a następnie wybierz **Otwórz Folder w Eksploratorze plików** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="b196c-123">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="b196c-124">W Eksploratorze plików Znajdź plik projektu (.csproj lub .vbproj), a następnie otwórz go w Notatniku.</span><span class="sxs-lookup"><span data-stu-id="b196c-124">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="b196c-125">W programie Visual Studio w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zwolnij projekt**.</span><span class="sxs-lookup"><span data-stu-id="b196c-125">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="b196c-126">Ponownie kliknij prawym przyciskiem myszy zwolnionego projektu, a następnie wybierz **Edytuj [projectname.csproj]**.</span><span class="sxs-lookup"><span data-stu-id="b196c-126">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="b196c-127">Dodaj następujący element do pierwszej grupy właściwości konfiguracji (w obszarze \<PropertyGroup > tag):</span><span class="sxs-lookup"><span data-stu-id="b196c-127">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   <span data-ttu-id="b196c-128">Poniżej przedstawiono przykładowy plik projektu z elementem wstawione:</span><span class="sxs-lookup"><span data-stu-id="b196c-128">The following shows an example project file with the element inserted:</span></span>

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

3. <span data-ttu-id="b196c-129">Skompiluj aplikację.</span><span class="sxs-lookup"><span data-stu-id="b196c-129">Compile your app.</span></span>

## <a name="enable-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="b196c-130">Włącz automatyczne przekierowania powiązań w aplikacjach sieci web</span><span class="sxs-lookup"><span data-stu-id="b196c-130">Enable automatic binding redirects in web apps</span></span>

<span data-ttu-id="b196c-131">Automatyczne przekierowania powiązań są w przypadku aplikacji internetowych implementowane w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="b196c-131">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="b196c-132">Ponieważ źródłowy plik konfiguracji (web.config) musi zostać zmodyfikowany dla aplikacji internetowych, przekierowania powiązań nie są automatycznie dodawane do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b196c-132">Because the source configuration (web.config) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="b196c-133">Jednak program Visual Studio powiadamia o konfliktach powiązań, więc można dodać przekierowania powiązań, aby rozwiązać konflikty.</span><span class="sxs-lookup"><span data-stu-id="b196c-133">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="b196c-134">Ponieważ zawsze monit o dodanie przekierowań powiązań, nie trzeba jawnie wyłączać tej funkcji dla aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="b196c-134">Because you're always prompted to add binding redirects, you don't need to explicitly disable this feature for a web app.</span></span>

<span data-ttu-id="b196c-135">Aby dodać przekierowania powiązań do pliku web.config:</span><span class="sxs-lookup"><span data-stu-id="b196c-135">To add binding redirects to a web.config file:</span></span>

1. <span data-ttu-id="b196c-136">W programie Visual Studio skompiluj aplikację i sprawdź, czy występują ostrzeżenia kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b196c-136">In Visual Studio, compile the app, and check for build warnings.</span></span>

   <span data-ttu-id="b196c-137">![Ostrzeżenie w przypadku konfliktów odwołanie do zestawu kompilacji](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="b196c-137">![Build warning for assembly reference conflicts](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>

2. <span data-ttu-id="b196c-138">Jeśli występują konflikty powiązań zestawów, zostanie wyświetlone ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="b196c-138">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="b196c-139">Kliknij dwukrotnie ostrzeżenie, lub Wybierz ostrzeżenie i naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="b196c-139">Double-click the warning, or select the warning and press **Enter**.</span></span>

   <span data-ttu-id="b196c-140">Zostanie wyświetlone okno dialogowe umożliwiające automatyczne dodanie niezbędnych przekierowań powiązań do źródłowego pliku web.config.</span><span class="sxs-lookup"><span data-stu-id="b196c-140">A dialog box that enables you to automatically add the necessary binding redirects to the source web.config file appears.</span></span>

   <span data-ttu-id="b196c-141">![Okno dialogowe uprawnienia przekierowania powiązania](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="b196c-141">![Binding redirect permission dialog](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>

## <a name="see-also"></a><span data-ttu-id="b196c-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b196c-142">See also</span></span>

- [<span data-ttu-id="b196c-143">\<bindingRedirect > Element</span><span class="sxs-lookup"><span data-stu-id="b196c-143">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="b196c-144">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="b196c-144">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
