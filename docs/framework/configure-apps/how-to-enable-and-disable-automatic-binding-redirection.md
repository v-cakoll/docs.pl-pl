---
title: "Porady: włączanie i wyłączanie automatycznego przekierowania powiązań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 83b004934c303c95bdc4e6edb6031a86e2b1a6ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="c9717-102">Porady: włączanie i wyłączanie automatycznego przekierowania powiązań</span><span class="sxs-lookup"><span data-stu-id="c9717-102">How to: Enable and Disable Automatic Binding Redirection</span></span>
<span data-ttu-id="c9717-103">Począwszy od [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], podczas kompilowania aplikacji przeznaczonych [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], przekierowania powiązań mogą być automatycznie dodawane do pliku konfiguracji aplikacji, aby zastąpić ujednolicenie zestawu.</span><span class="sxs-lookup"><span data-stu-id="c9717-103">Starting with [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], when you compile apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="c9717-104">Przekierowania powiązań są dodawane, jeśli aplikacja lub jej składniki odwołują się do więcej niż jednej wersji tego samego zestawu, nawet jeśli przekierowania powiązań zostaną określone ręcznie w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c9717-104">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="c9717-105">Funkcja przekierowania powiązania automatyczne wpływa na tradycyjnych aplikacji klasycznych i aplikacji sieci web przeznaczonych [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], chociaż to zachowanie różni się nieznacznie dla aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="c9717-105">The automatic binding redirection feature affects traditional desktop apps and web apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="c9717-106">Można włączyć automatyczne przekierowywanie połączeń, jeśli są używane aplikacje, których platformami docelowymi są poprzednie wersje programu .NET Framework, ale można też wyłączyć tę funkcję, aby używać tworzonych ręcznie przekierowań powiązań.</span><span class="sxs-lookup"><span data-stu-id="c9717-106">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to keep manually authored binding redirects.</span></span>  
  
## <a name="disabling-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="c9717-107">Wyłączanie automatycznego powiązanie przekierowuje w aplikacjach klasycznych</span><span class="sxs-lookup"><span data-stu-id="c9717-107">Disabling automatic binding redirects in desktop apps</span></span>  
 <span data-ttu-id="c9717-108">Przekierowania powiązania automatyczne są domyślnie włączone dla tradycyjnej aplikacji klasycznych, które odnoszą się do [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="c9717-108">Automatic binding redirects are enabled by default for traditional desktop apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions.</span></span> <span data-ttu-id="c9717-109">Przekierowania powiązań są dodawane do wyjściowego pliku konfiguracji (app.config), gdy aplikacja jest kompilowana, co powoduje zastąpienie ujednolicenia zestawów, które mogłoby mieć miejsce.</span><span class="sxs-lookup"><span data-stu-id="c9717-109">The binding redirects are added to the output configuration (app.config) file when the app is compiled and overrides the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="c9717-110">Źródłowy plik app.config nie jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="c9717-110">The source app.config file is not modified.</span></span> <span data-ttu-id="c9717-111">Tę funkcję można wyłączyć, modyfikując plik projektu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c9717-111">You can disable this feature by modifying the project file for the app.</span></span>  
  
#### <a name="to-disable-automatic-binding-redirects"></a><span data-ttu-id="c9717-112">Aby wyłączyć automatyczne przekierowywanie powiązań</span><span class="sxs-lookup"><span data-stu-id="c9717-112">To disable automatic binding redirects</span></span>  
  
1.  <span data-ttu-id="c9717-113">W programie Visual Studio, wybierz projekt **Eksploratora rozwiązań**, a następnie wybierz pozycję **Otwórz Folder w Eksploratorze plików** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="c9717-113">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="c9717-114">W Eksploratorze plików znajdź plik projektu (csproj lub vbproj) i otwórz go w Notatniku.</span><span class="sxs-lookup"><span data-stu-id="c9717-114">In File Explorer, find the project (.csproj or .vbproj) file, and open it in Notepad.</span></span>  
  
3.  <span data-ttu-id="c9717-115">W pliku projektu znajdź następujący wpis właściwości:</span><span class="sxs-lookup"><span data-stu-id="c9717-115">In the project file, find the following property entry:</span></span>  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
4.  <span data-ttu-id="c9717-116">Zmień `true` do `false`:</span><span class="sxs-lookup"><span data-stu-id="c9717-116">Change `true` to `false`:</span></span>  
  
     `<AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>`  
  
## <a name="enabling-automatic-binding-redirects-manually"></a><span data-ttu-id="c9717-117">Włączanie automatycznego powiązanie przekierowuje ręcznie</span><span class="sxs-lookup"><span data-stu-id="c9717-117">Enabling automatic binding redirects manually</span></span>  
 <span data-ttu-id="c9717-118">Można włączyć tego docelowego starsze wersje programu .NET Framework lub w przypadkach, gdy monit nie jest automatycznie dodać przekierowanie przekierowania powiązania automatyczne w istniejących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c9717-118">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you are not automatically prompted to add a redirect.</span></span> <span data-ttu-id="c9717-119">Jeśli przeznaczona dla nowszej wersji platformy, ale nie będzie automatycznie monitowany dodać przekierowanie, prawdopodobnie otrzymasz dane wyjściowe kompilacji, które sugeruje się, że można ponownie zamapować zestawów.</span><span class="sxs-lookup"><span data-stu-id="c9717-119">If you are targeting a newer version of the framework but do not get automatically prompted to add a redirect, you will likely get   build output that suggests you remap assemblies.</span></span>  
  
#### <a name="to-manually-add-an-automatic-binding-redirect-property"></a><span data-ttu-id="c9717-120">Aby ręcznie dodać właściwość przekierowania powiązania automatyczne</span><span class="sxs-lookup"><span data-stu-id="c9717-120">To manually add an automatic binding redirect property</span></span>  
  
1.  <span data-ttu-id="c9717-121">W programie Visual Studio, wybierz projekt **Eksploratora rozwiązań**, a następnie wybierz pozycję **Otwórz Folder w Eksploratorze plików** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="c9717-121">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="c9717-122">W Eksploratorze plików znajdź plik projektu (csproj lub vbproj) i otwórz go w Notatniku.</span><span class="sxs-lookup"><span data-stu-id="c9717-122">In File Explorer, find the project (.csproj or .vbproj) file, and open it in Notepad.</span></span>  
  
3.  <span data-ttu-id="c9717-123">Dodaj następujący element do pierwszej grupy właściwości konfiguracji (w obszarze \<PropertyGroup > tagu):</span><span class="sxs-lookup"><span data-stu-id="c9717-123">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
     <span data-ttu-id="c9717-124">Poniżej przedstawiono przykładowy plik projektu z wstawiony element.</span><span class="sxs-lookup"><span data-stu-id="c9717-124">The following shows an example project file with the element inserted.</span></span>  
  
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
  
4.  <span data-ttu-id="c9717-125">Skompiluj aplikację.</span><span class="sxs-lookup"><span data-stu-id="c9717-125">Compile your app.</span></span>  
  
## <a name="enabling-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="c9717-126">Włączanie automatycznego przekierowywania powiązań w aplikacjach sieci web</span><span class="sxs-lookup"><span data-stu-id="c9717-126">Enabling automatic binding redirects in web apps</span></span>  
 <span data-ttu-id="c9717-127">Automatyczne przekierowania powiązań są w przypadku aplikacji sieci web implementowane w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="c9717-127">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="c9717-128">Ponieważ źródłowy plik konfiguracji (web.config) musi zostać zmodyfikowany dla aplikacji sieci web, przekierowania powiązań nie są automatycznie dodawane do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c9717-128">Because the source configuration (web.config) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="c9717-129">Jednak program Visual Studio powiadamia o konfliktach powiązań, więc można dodać przekierowania powiązań, aby rozwiązać konflikty.</span><span class="sxs-lookup"><span data-stu-id="c9717-129">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="c9717-130">Zawsze jest wyświetlany monit o dodanie przekierowań powiązań, więc nie trzeba jawnie wyłączać tej funkcji dla aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="c9717-130">Because you are always prompted to add binding redirects, you do not need to explicitly disable this feature for a web app.</span></span>  
  
#### <a name="to-add-binding-redirects-to-a-webconfig-file"></a><span data-ttu-id="c9717-131">Aby dodać przekierowania powiązań do pliku web.config</span><span class="sxs-lookup"><span data-stu-id="c9717-131">To add binding redirects to a web.config file</span></span>  
  
1.  <span data-ttu-id="c9717-132">W programie Visual Studio skompiluj aplikację i sprawdź, czy występują ostrzeżenia kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c9717-132">In Visual Studio, compile the app, and check for build warnings.</span></span>  
  
     <span data-ttu-id="c9717-133">![Ostrzeżenie dotyczące konflikty odwołań zestawu kompilacji](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="c9717-133">![Build warning for assembly reference conflicts](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>  
  
2.  <span data-ttu-id="c9717-134">Jeśli występują konflikty powiązań zestawów, zostanie wyświetlone ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="c9717-134">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="c9717-135">Kliknij dwukrotnie ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="c9717-135">Double-click the warning.</span></span> <span data-ttu-id="c9717-136">(Klawiatury: Wybierz to ostrzeżenie i naciśnij klawisz **Enter**.)</span><span class="sxs-lookup"><span data-stu-id="c9717-136">(Keyboard: Select the warning and press **Enter**.)</span></span>  
  
     <span data-ttu-id="c9717-137">Zostanie wyświetlone okno dialogowe umożliwiające automatyczne dodanie niezbędnych przekierowań powiązań do źródłowego pliku web.config.</span><span class="sxs-lookup"><span data-stu-id="c9717-137">A dialog box that enables you to automatically add the necessary binding redirects to the source web.config file appears.</span></span>  
  
     <span data-ttu-id="c9717-138">![Okno dialogowe uprawnienia przekierowania powiązania](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="c9717-138">![Binding redirect permission dialog](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9717-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9717-139">See Also</span></span>  
 [<span data-ttu-id="c9717-140">\<w parametrze bindingRedirect > — Element</span><span class="sxs-lookup"><span data-stu-id="c9717-140">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [<span data-ttu-id="c9717-141">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="c9717-141">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
