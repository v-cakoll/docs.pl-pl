---
title: "Porady: instalowanie zestawu w globalnej pamięci podręcznej zestawów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98dd4d1e75fc37820a1b1f4eccfa48f978772687
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="239b8-102">Porady: instalowanie zestawu w globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="239b8-102">How to: Install an Assembly into the Global Assembly Cache</span></span>
<span data-ttu-id="239b8-103">Istnieją dwa sposoby instalacji zestawu o silnej nazwie w globalnej pamięci podręcznej zestawów (GAC):</span><span class="sxs-lookup"><span data-stu-id="239b8-103">There are two ways to install a strong-named assembly into the global assembly cache (GAC):</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="239b8-104">W pamięci podręcznej GAC można instalować tylko zestawy o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="239b8-104">Only strong-named assemblies can be installed into the GAC.</span></span> <span data-ttu-id="239b8-105">Aby uzyskać informacje o sposobie tworzenia zestawu z silną nazwą, zobacz [porady: podpisać zestaw o silnej nazwie](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="239b8-105">For information about how to create a strong-named assembly, see [How to: Sign an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
-   <span data-ttu-id="239b8-106">Przy użyciu [Instalatora Windows](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span><span class="sxs-lookup"><span data-stu-id="239b8-106">Using [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span></span>  
  
     <span data-ttu-id="239b8-107">Można to zrobić w programie Visual Studio 2012 i Visual Studio 2013, tworząc projekt programu InstallShield Limited Edition.</span><span class="sxs-lookup"><span data-stu-id="239b8-107">You do this in Visual Studio 2012 and Visual Studio 2013 by creating an InstallShield Limited Edition Project.</span></span>  
  
     <span data-ttu-id="239b8-108">Jest to zalecany i najpopularniejszy sposób dodawania zestawów do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="239b8-108">This is the recommended and most common way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="239b8-109">Instalator oferuje funkcję zliczania odwołań do zestawów znajdujących się w globalnej pamięci podręcznej zestawów, a także zapewnia inne korzyści.</span><span class="sxs-lookup"><span data-stu-id="239b8-109">The installer provides reference counting of assemblies in the global assembly cache, plus other benefits.</span></span>  
  
-   <span data-ttu-id="239b8-110">Przy użyciu [narzędzie Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="239b8-110">Using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
     <span data-ttu-id="239b8-111">Za pomocą narzędzia Gacutil.exe można dodawać zestawy o silnej nazwie do globalnej pamięci podręcznej zestawów i wyświetlać zawartość globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="239b8-111">You can use Gacutil.exe to add strong-named assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="239b8-112">Narzędzie Gacutil.exe jest przeznaczone tylko do celów deweloperskich i nie powinno być używane do instalowania zestawów produkcyjnych w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="239b8-112">Gacutil.exe is only for development purposes and should not be used to install production assemblies into the global assembly cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="239b8-113">We wcześniejszych wersjach programu .NET Framework rozszerzenie powłoki Shfusion.dll Windows włączone do zainstalowania zestawy, przeciągając je w Eksploratorze plików.</span><span class="sxs-lookup"><span data-stu-id="239b8-113">In earlier versions of the .NET Framework, the Shfusion.dll Windows shell extension enabled you to install assemblies by dragging them in File Explorer.</span></span> <span data-ttu-id="239b8-114">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="239b8-114">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a><span data-ttu-id="239b8-115">Aby użyć narzędzia Globalna pamięć podręczna zestawów (Gacutil.exe).</span><span class="sxs-lookup"><span data-stu-id="239b8-115">To use the Global Assembly Cache tool (Gacutil.exe)</span></span>  
  
1.  <span data-ttu-id="239b8-116">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="239b8-116">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="239b8-117">**gacutil -i** \< *nazwy zestawu*></span><span class="sxs-lookup"><span data-stu-id="239b8-117">**gacutil -i** \<*assembly name*></span></span>  
  
     <span data-ttu-id="239b8-118">W tym poleceniu *nazwy zestawu* jest nazwą zestawu do instalacji w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="239b8-118">In this command, *assembly name* is the name of the assembly to install in the global assembly cache.</span></span>  
  
 <span data-ttu-id="239b8-119">W poniższym przykładzie instalowana zestawu o nazwie pliku `hello.dll` w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="239b8-119">The following example installs an assembly with the file name `hello.dll` into the global assembly cache.</span></span>  
  
```  
gacutil -i hello.dll  
```  
  
 <span data-ttu-id="239b8-120">Aby uzyskać więcej informacji, zobacz [narzędzie Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="239b8-120">For more information, see [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
### <a name="to-use-an-installshield-limited-edition-project"></a><span data-ttu-id="239b8-121">Aby użyć projektu programu InstallShield Limited Edition</span><span class="sxs-lookup"><span data-stu-id="239b8-121">To use an InstallShield Limited Edition Project</span></span>  
  
1.  <span data-ttu-id="239b8-122">Dodawanie pakietu instalacji i wdrażania do rozwiązania Otwieranie menu skrótów do rozwiązania, a następnie wybierając **Dodaj**, **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="239b8-122">Add a setup and deployment package to your solution by opening the shortcut menu for your solution, and then choosing **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="239b8-123">W **Dodawanie nowego projektu** okna dialogowego, **zainstalowana** folderu, wybierz **inne typy projektów**, **instalacji i wdrażania**, **InstallShield Limited Edition**i nadaj nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="239b8-123">In the **Add New Project** dialog box, in the **Installed** folder, choose **Other Project Types**,  **Setup and Deployment**, **InstallShield Limited Edition**, and give your project a name.</span></span> <span data-ttu-id="239b8-124">(Jeśli zostanie wyświetlony monit, Pobierz, instalowania i aktywowania InstallShield.)</span><span class="sxs-lookup"><span data-stu-id="239b8-124">(If prompted, download, install, and activate InstallShield.)</span></span>  
  
3.  <span data-ttu-id="239b8-125">Wykonaj ogólne konfiguracji instalacji i wdrażania projektu przy użyciu Asystenta projektu w **Eksploratora rozwiązań**, lub wybierając podetapów numerowane czynności **Eksploratora rozwiązań**. Skonfiguruj ustawienia, jak w przypadku, jeśli nie dodawania zestawów w pamięci GAC.</span><span class="sxs-lookup"><span data-stu-id="239b8-125">Perform the general configuration of your setup and deployment project either by using the Project Assistant in **Solution Explorer**, or by choosing the substeps of the numbered steps in the **Solution Explorer**.Configure your setup as you would if you were not adding assemblies to the GAC.</span></span>  
  
4.  <span data-ttu-id="239b8-126">Aby rozpocząć proces dodawania zestawu w GAC, wybierz **pliki**, znajduje się w **Określ dane aplikacji** krok **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="239b8-126">To begin the process of adding an assembly to the GAC, choose **Files**, which is under the **Specify Application Data** step in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="239b8-127">W **folderów na komputerze docelowym** okienko, otwórz menu skrótów dla **komputera docelowego**, a następnie wybierz pozycję **Pokaż Folder wstępnie zdefiniowane**, **[ GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="239b8-127">In the **Destination computer's folders** pane, open the shortcut menu for **Destination Computer**, and then choose **Show Predefined Folder**, **[GlobalAssemblyCache]**.</span></span>  
  
6.  <span data-ttu-id="239b8-128">Dla każdego projektu w rozwiązaniu zawierającym zestaw, który chcesz zainstalować w globalnej pamięci podręcznej zestawów:</span><span class="sxs-lookup"><span data-stu-id="239b8-128">For each project in the solution that contains an assembly that you want to install in the global assembly cache:</span></span>  
  
    1.  <span data-ttu-id="239b8-129">W **źródła folderów na komputerze** okienku wybierz projekt.</span><span class="sxs-lookup"><span data-stu-id="239b8-129">In the **Source computer's folders** pane, choose the project.</span></span>  
  
    2.  <span data-ttu-id="239b8-130">W **folderów na komputerze docelowym** okienku wybierz **[GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="239b8-130">In the **Destination computer's folders** pane, choose **[GlobalAssemblyCache]**.</span></span>  
  
    3.  <span data-ttu-id="239b8-131">W **komputera pliki źródłowe** okienku wybierz **podstawowe dane wyjściowe z** *< nazwa_projektu >*.</span><span class="sxs-lookup"><span data-stu-id="239b8-131">In the **Source computer's files** pane, choose **Primary output from** *<project_name>*.</span></span>  
  
    4.  <span data-ttu-id="239b8-132">Przeciągnij plik w kroku c do **plików na komputerze docelowym** okienka (lub użyj **kopiowania** i **Wklej** poleceń menu skrótów pliku).</span><span class="sxs-lookup"><span data-stu-id="239b8-132">Drag the file in step c to the **Destination computer's files** pane (or use the **Copy** and **Paste** commands from the file's shortcut menu).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="239b8-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="239b8-133">See Also</span></span>  
 [<span data-ttu-id="239b8-134">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="239b8-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="239b8-135">Instrukcje: usuwanie zestawu z pamięci Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="239b8-135">How to: Remove an Assembly from the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [<span data-ttu-id="239b8-136">Gacutil.exe (narzędzie Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="239b8-136">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [<span data-ttu-id="239b8-137">Instrukcje: podpisywanie zestawu silną nazwą</span><span class="sxs-lookup"><span data-stu-id="239b8-137">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="239b8-138">Wdrożenia Instalatora Windows</span><span class="sxs-lookup"><span data-stu-id="239b8-138">Windows Installer Deployment</span></span>](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
