---
title: Włączanie lub wyłączanie przekierowań automatycznie generowanych powiązań
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: d914310559403fba2f1fe8e4a60469ec3a867c24
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733441"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="64abf-102">Instrukcje: Włączanie i wyłączanie automatycznego przekierowania powiązań</span><span class="sxs-lookup"><span data-stu-id="64abf-102">How to: Enable and Disable Automatic Binding Redirection</span></span>

<span data-ttu-id="64abf-103">W przypadku kompilowania aplikacji w programie Visual Studio, które są przeznaczone dla .NET Framework 4.5.1 i nowszych wersji, przekierowania powiązań mogą być automatycznie dodawane do pliku konfiguracji aplikacji w celu zastąpienia zjednoczenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="64abf-103">When you compile apps in Visual Studio that target the .NET Framework 4.5.1 and later versions, binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="64abf-104">Przekierowania powiązań są dodawane, jeśli aplikacja lub jej składniki odwołują się do więcej niż jednej wersji tego samego zestawu, nawet jeśli przekierowania powiązań zostaną określone ręcznie w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="64abf-104">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="64abf-105">Funkcja automatycznego przekierowywania powiązań ma wpływ na aplikacje pulpitu i aplikacje sieci Web, które są przeznaczone dla .NET Framework 4.5.1 lub nowszej wersji, chociaż zachowanie jest nieco inne dla aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="64abf-105">The automatic binding redirection feature affects desktop apps and web apps that target the .NET Framework 4.5.1 or a later version, although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="64abf-106">Automatyczne przekierowywanie powiązań można włączyć, jeśli istnieją aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework, lub wyłączyć tę funkcję, jeśli chcesz ręcznie tworzyć przekierowania powiązań.</span><span class="sxs-lookup"><span data-stu-id="64abf-106">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to manually author binding redirects.</span></span>

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="64abf-107">Wyłączanie automatycznego przekierowywania powiązań w aplikacjach klasycznych</span><span class="sxs-lookup"><span data-stu-id="64abf-107">Disable automatic binding redirects in desktop apps</span></span>

<span data-ttu-id="64abf-108">Automatyczne przekierowania powiązań są domyślnie włączone dla aplikacji klasycznych systemu Windows, które są przeznaczone dla .NET Framework 4.5.1 i nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="64abf-108">Automatic binding redirects are enabled by default for Windows desktop apps that target the .NET Framework 4.5.1 and later versions.</span></span> <span data-ttu-id="64abf-109">Przekierowania powiązań są dodawane do pliku konfiguracji danych wyjściowych (**App. config**), gdy aplikacja jest kompilowana i przesłania nieujednolicenie zestawu, który może być w innym przypadku.</span><span class="sxs-lookup"><span data-stu-id="64abf-109">The binding redirects are added to the output configuration (**app.config**) file when the app is compiled and override the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="64abf-110">Plik źródłowy **App. config** nie jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="64abf-110">The source **app.config** file is not modified.</span></span> <span data-ttu-id="64abf-111">Tę funkcję można wyłączyć, modyfikując plik projektu dla aplikacji lub zaznaczając zaznaczenie pola wyboru we właściwościach projektu w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="64abf-111">You can disable this feature by modifying the project file for the app or by deselecting a checkbox in the project's properties in Visual Studio.</span></span>

### <a name="disable-through-project-properties"></a><span data-ttu-id="64abf-112">Wyłącz za poorednictwem właściwości projektu</span><span class="sxs-lookup"><span data-stu-id="64abf-112">Disable through project properties</span></span>

<span data-ttu-id="64abf-113">Jeśli masz program Visual Studio 2017 w wersji 15,7 lub nowszej, możesz łatwo wyłączyć automatycznie generowane przekierowania powiązań na stronach właściwości projektu.</span><span class="sxs-lookup"><span data-stu-id="64abf-113">If you have Visual Studio 2017 version 15.7 or later, you can easily disable autogenerated binding redirects in the project's property pages.</span></span>

1. <span data-ttu-id="64abf-114">Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="64abf-114">Right-click the project in **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="64abf-115">Na stronie **aplikacja** Usuń zaznaczenie opcji **automatycznie Generuj powiązania powiązań** .</span><span class="sxs-lookup"><span data-stu-id="64abf-115">On the **Application** page, uncheck the **Auto-generate binding redirects** option.</span></span>

3. <span data-ttu-id="64abf-116">Naciśnij **kombinację klawiszy CTRL**+**S** , aby zapisać zmiany.</span><span class="sxs-lookup"><span data-stu-id="64abf-116">Press **Ctrl**+**S** to save the change.</span></span>

### <a name="disable-manually-in-the-project-file"></a><span data-ttu-id="64abf-117">Wyłącz ręcznie w pliku projektu</span><span class="sxs-lookup"><span data-stu-id="64abf-117">Disable manually in the project file</span></span>

1. <span data-ttu-id="64abf-118">Otwórz plik projektu do edycji przy użyciu jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="64abf-118">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="64abf-119">W programie Visual Studio wybierz projekt w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Otwórz folder w Eksploratorze plików** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="64abf-119">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="64abf-120">W Eksploratorze plików Znajdź plik projektu (. csproj lub. vbproj) i otwórz go w Notatniku.</span><span class="sxs-lookup"><span data-stu-id="64abf-120">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="64abf-121">W programie Visual Studio w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zwolnij projekt**.</span><span class="sxs-lookup"><span data-stu-id="64abf-121">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="64abf-122">Ponownie kliknij prawym przyciskiem myszy niezaładowanego projektu, a następnie wybierz polecenie **Edytuj [ProjectName. csproj]** .</span><span class="sxs-lookup"><span data-stu-id="64abf-122">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="64abf-123">W pliku projektu znajdź następujący wpis właściwości:</span><span class="sxs-lookup"><span data-stu-id="64abf-123">In the project file, find the following property entry:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. <span data-ttu-id="64abf-124">Zmień `true` na `false`:</span><span class="sxs-lookup"><span data-stu-id="64abf-124">Change `true` to `false`:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a><span data-ttu-id="64abf-125">Ręcznie Włącz automatyczne przekierowania powiązań</span><span class="sxs-lookup"><span data-stu-id="64abf-125">Enable automatic binding redirects manually</span></span>

<span data-ttu-id="64abf-126">Automatyczne przekierowania powiązań można włączyć w istniejących aplikacjach przeznaczonych dla starszych wersji .NET Framework lub w przypadkach, gdy nie jest automatycznie wyświetlany monit o dodanie przekierowania.</span><span class="sxs-lookup"><span data-stu-id="64abf-126">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you're not automatically prompted to add a redirect.</span></span> <span data-ttu-id="64abf-127">Jeśli celem jest nowsza wersja struktury, ale nie zostanie automatycznie wyświetlony monit o dodanie przekierowania, prawdopodobnie otrzymasz dane wyjściowe kompilacji, które sugerują ponowne mapowanie zestawów.</span><span class="sxs-lookup"><span data-stu-id="64abf-127">If you're targeting a newer version of the framework but do not get automatically prompted to add a redirect, you'll likely get build output that suggests you remap assemblies.</span></span>

1. <span data-ttu-id="64abf-128">Otwórz plik projektu do edycji przy użyciu jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="64abf-128">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="64abf-129">W programie Visual Studio wybierz projekt w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Otwórz folder w Eksploratorze plików** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="64abf-129">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="64abf-130">W Eksploratorze plików Znajdź plik projektu (. csproj lub. vbproj) i otwórz go w Notatniku.</span><span class="sxs-lookup"><span data-stu-id="64abf-130">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="64abf-131">W programie Visual Studio w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zwolnij projekt**.</span><span class="sxs-lookup"><span data-stu-id="64abf-131">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="64abf-132">Ponownie kliknij prawym przyciskiem myszy niezaładowanego projektu, a następnie wybierz polecenie **Edytuj [ProjectName. csproj]** .</span><span class="sxs-lookup"><span data-stu-id="64abf-132">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="64abf-133">Dodaj następujący element do pierwszej grupy właściwości konfiguracji (w obszarze \<> tagu właściwości):</span><span class="sxs-lookup"><span data-stu-id="64abf-133">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   <span data-ttu-id="64abf-134">Poniżej przedstawiono przykładowy plik projektu z wstawionym elementem:</span><span class="sxs-lookup"><span data-stu-id="64abf-134">The following shows an example project file with the element inserted:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
     <PropertyGroup>
       <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
       <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
       <ProjectGuid>{123334}</ProjectGuid>
       ...
       <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
     </PropertyGroup>
     ...
   </Project>
   ```

3. <span data-ttu-id="64abf-135">Skompiluj aplikację.</span><span class="sxs-lookup"><span data-stu-id="64abf-135">Compile your app.</span></span>

## <a name="enable-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="64abf-136">Włączanie automatycznego przekierowywania powiązań w aplikacjach sieci Web</span><span class="sxs-lookup"><span data-stu-id="64abf-136">Enable automatic binding redirects in web apps</span></span>

<span data-ttu-id="64abf-137">Automatyczne przekierowania powiązań są w przypadku aplikacji internetowych implementowane w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="64abf-137">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="64abf-138">Ponieważ plik konfiguracji źródłowej (**Web. config**) musi zostać zmodyfikowany dla aplikacji sieci Web, przekierowania powiązań nie są automatycznie dodawane do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="64abf-138">Because the source configuration (**web.config**) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="64abf-139">Jednak program Visual Studio powiadamia o konfliktach powiązań, więc można dodać przekierowania powiązań, aby rozwiązać konflikty.</span><span class="sxs-lookup"><span data-stu-id="64abf-139">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="64abf-140">Ponieważ zawsze jest wyświetlany monit o dodanie przekierowań powiązań, nie trzeba jawnie wyłączać tej funkcji dla aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="64abf-140">Because you're always prompted to add binding redirects, you don't need to explicitly disable this feature for a web app.</span></span>

<span data-ttu-id="64abf-141">Aby dodać przekierowania powiązań do pliku **Web. config** :</span><span class="sxs-lookup"><span data-stu-id="64abf-141">To add binding redirects to a **web.config** file:</span></span>

1. <span data-ttu-id="64abf-142">W programie Visual Studio skompiluj aplikację i sprawdź, czy występują ostrzeżenia kompilacji.</span><span class="sxs-lookup"><span data-stu-id="64abf-142">In Visual Studio, compile the app, and check for build warnings.</span></span>

   <span data-ttu-id="64abf-143">![Ostrzeżenie kompilacji dla konfliktów odwołań do zestawu](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="64abf-143">![Build warning for assembly reference conflicts](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>

2. <span data-ttu-id="64abf-144">Jeśli występują konflikty powiązań zestawów, zostanie wyświetlone ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="64abf-144">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="64abf-145">Kliknij dwukrotnie ostrzeżenie lub wybierz ostrzeżenie i naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="64abf-145">Double-click the warning, or select the warning and press **Enter**.</span></span>

   <span data-ttu-id="64abf-146">Zostanie wyświetlone okno dialogowe, które umożliwia automatyczne dodanie niezbędnych przekierowań powiązań do źródłowego pliku **Web. config** .</span><span class="sxs-lookup"><span data-stu-id="64abf-146">A dialog box that enables you to automatically add the necessary binding redirects to the source **web.config** file appears.</span></span>

   <span data-ttu-id="64abf-147">![Okno dialogowe uprawnień przekierowywania powiązań](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="64abf-147">![Binding redirect permission dialog](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>

## <a name="see-also"></a><span data-ttu-id="64abf-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64abf-148">See also</span></span>

- [<span data-ttu-id="64abf-149">\<bindingRedirect> Element</span><span class="sxs-lookup"><span data-stu-id="64abf-149">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="64abf-150">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="64abf-150">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
