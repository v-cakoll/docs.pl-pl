---
title: 'Porady: instalowanie zestawu w globalnej pamięci podręcznej zestawów'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c3bd568cf504125bc99801815d08764417b42cd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469001"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="6d88d-102">Porady: instalowanie zestawu w globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="6d88d-102">How to: Install an Assembly into the Global Assembly Cache</span></span>
<span data-ttu-id="6d88d-103">Istnieją dwa sposoby instalacji zestawu o silnej nazwie w globalnej pamięci podręcznej zestawów (GAC):</span><span class="sxs-lookup"><span data-stu-id="6d88d-103">There are two ways to install a strong-named assembly into the global assembly cache (GAC):</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6d88d-104">W pamięci podręcznej GAC można instalować tylko zestawy o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="6d88d-104">Only strong-named assemblies can be installed into the GAC.</span></span> <span data-ttu-id="6d88d-105">Aby uzyskać informacje o sposobie tworzenia zestawu z silną nazwą, zobacz [porady: podpisywanie zestawu za pomocą silnej nazwy](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="6d88d-105">For information about how to create a strong-named assembly, see [How to: Sign an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
-   <span data-ttu-id="6d88d-106">Za pomocą [Instalatora Windows](/windows/desktop/Msi/windows-installer-portal).</span><span class="sxs-lookup"><span data-stu-id="6d88d-106">Using [Windows Installer](/windows/desktop/Msi/windows-installer-portal).</span></span>  
  
     <span data-ttu-id="6d88d-107">Można to zrobić w programie Visual Studio 2012 i Visual Studio 2013, tworząc projekt programu InstallShield Limited Edition.</span><span class="sxs-lookup"><span data-stu-id="6d88d-107">You do this in Visual Studio 2012 and Visual Studio 2013 by creating an InstallShield Limited Edition Project.</span></span>  
  
     <span data-ttu-id="6d88d-108">Jest to zalecany i najpopularniejszy sposób dodawania zestawów do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="6d88d-108">This is the recommended and most common way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="6d88d-109">Instalator oferuje funkcję zliczania odwołań do zestawów znajdujących się w globalnej pamięci podręcznej zestawów, a także zapewnia inne korzyści.</span><span class="sxs-lookup"><span data-stu-id="6d88d-109">The installer provides reference counting of assemblies in the global assembly cache, plus other benefits.</span></span>  
  
-   <span data-ttu-id="6d88d-110">Za pomocą [narzędzia Globalna pamięć podręczna zestawów (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="6d88d-110">Using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
     <span data-ttu-id="6d88d-111">Za pomocą narzędzia Gacutil.exe można dodawać zestawy o silnej nazwie do globalnej pamięci podręcznej zestawów i wyświetlać zawartość globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="6d88d-111">You can use Gacutil.exe to add strong-named assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d88d-112">Narzędzie Gacutil.exe jest przeznaczone tylko do celów deweloperskich i nie powinno być używane do instalowania zestawów produkcyjnych w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="6d88d-112">Gacutil.exe is only for development purposes and should not be used to install production assemblies into the global assembly cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d88d-113">We wcześniejszych wersjach programu .NET Framework rozszerzenie powłoki Windows Shfusion.dll umożliwia instalowanie zestawów, przeciągając je w Eksploratorze plików.</span><span class="sxs-lookup"><span data-stu-id="6d88d-113">In earlier versions of the .NET Framework, the Shfusion.dll Windows shell extension enabled you to install assemblies by dragging them in File Explorer.</span></span> <span data-ttu-id="6d88d-114">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], biblioteka Shfusion.dll jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="6d88d-114">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a><span data-ttu-id="6d88d-115">Aby użyć narzędzia Globalna pamięć podręczna zestawów (Gacutil.exe).</span><span class="sxs-lookup"><span data-stu-id="6d88d-115">To use the Global Assembly Cache tool (Gacutil.exe)</span></span>  
  
1.  <span data-ttu-id="6d88d-116">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="6d88d-116">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="6d88d-117">**gacutil -i** \< *nazwy zestawu*></span><span class="sxs-lookup"><span data-stu-id="6d88d-117">**gacutil -i** \<*assembly name*></span></span>  
  
     <span data-ttu-id="6d88d-118">W tym poleceniu *nazwy zestawu* to nazwa zestawu, aby zainstalować w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6d88d-118">In this command, *assembly name* is the name of the assembly to install in the global assembly cache.</span></span>  
  
 <span data-ttu-id="6d88d-119">Poniższy przykład instaluje zestaw o nazwie pliku `hello.dll` w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6d88d-119">The following example installs an assembly with the file name `hello.dll` into the global assembly cache.</span></span>  
  
```  
gacutil -i hello.dll  
```  
  
 <span data-ttu-id="6d88d-120">Aby uzyskać więcej informacji, zobacz [narzędzia Globalna pamięć podręczna zestawów (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="6d88d-120">For more information, see [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
### <a name="to-use-an-installshield-limited-edition-project"></a><span data-ttu-id="6d88d-121">Aby użyć projektu programu InstallShield Limited Edition</span><span class="sxs-lookup"><span data-stu-id="6d88d-121">To use an InstallShield Limited Edition Project</span></span>  
  
1.  <span data-ttu-id="6d88d-122">Dodaj do rozwiązania pakiet instalacji i wdrożenia, otwierając menu skrótów dla danego rozwiązania, a następnie wybierając **Dodaj**, **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="6d88d-122">Add a setup and deployment package to your solution by opening the shortcut menu for your solution, and then choosing **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="6d88d-123">W **Dodaj nowy projekt** dialogowym **zainstalowane** folderu, wybierz **inne typy projektów**, **instalacja i wdrożenie**, **InstallShield Limited Edition**, a następnie nadaj projektowi nazwę.</span><span class="sxs-lookup"><span data-stu-id="6d88d-123">In the **Add New Project** dialog box, in the **Installed** folder, choose **Other Project Types**,  **Setup and Deployment**, **InstallShield Limited Edition**, and give your project a name.</span></span> <span data-ttu-id="6d88d-124">(Jeśli zostanie wyświetlony monit, pobierania, instalowania i aktywowania InstallShield.)</span><span class="sxs-lookup"><span data-stu-id="6d88d-124">(If prompted, download, install, and activate InstallShield.)</span></span>  
  
3.  <span data-ttu-id="6d88d-125">Wykonaj ogólną konfigurację projektu instalacji i wdrożenia przy użyciu Asystenta projektu w **Eksploratora rozwiązań**, lub wybierając podkroki ponumerowanych kroków w **Eksploratora rozwiązań**. Skonfiguruj ustawienia, jak gdyby były nie dodaje zestawy w pamięci GAC.</span><span class="sxs-lookup"><span data-stu-id="6d88d-125">Perform the general configuration of your setup and deployment project either by using the Project Assistant in **Solution Explorer**, or by choosing the substeps of the numbered steps in the **Solution Explorer**.Configure your setup as you would if you were not adding assemblies to the GAC.</span></span>  
  
4.  <span data-ttu-id="6d88d-126">Aby rozpocząć proces dodawania zestawu do globalnej pamięci podręcznej zestawów, wybierz pozycję **pliki**, czyli w ramach **Określ dane aplikacji** krok w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="6d88d-126">To begin the process of adding an assembly to the GAC, choose **Files**, which is under the **Specify Application Data** step in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="6d88d-127">W **foldery komputera docelowego** okienko, otwórz menu skrótów dla **komputera docelowego**, a następnie wybierz **Pokaż wstępnie zdefiniowany Folder**, **[ GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="6d88d-127">In the **Destination computer's folders** pane, open the shortcut menu for **Destination Computer**, and then choose **Show Predefined Folder**, **[GlobalAssemblyCache]**.</span></span>  
  
6.  <span data-ttu-id="6d88d-128">Dla każdego projektu w rozwiązaniu zawierającym zestaw, który chcesz zainstalować w globalnej pamięci podręcznej zestawów:</span><span class="sxs-lookup"><span data-stu-id="6d88d-128">For each project in the solution that contains an assembly that you want to install in the global assembly cache:</span></span>  
  
    1.  <span data-ttu-id="6d88d-129">W **foldery komputera źródłowego** okienku, wybierz projekt.</span><span class="sxs-lookup"><span data-stu-id="6d88d-129">In the **Source computer's folders** pane, choose the project.</span></span>  
  
    2.  <span data-ttu-id="6d88d-130">W **foldery komputera docelowego** okienku wybierz **[GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="6d88d-130">In the **Destination computer's folders** pane, choose **[GlobalAssemblyCache]**.</span></span>  
  
    3.  <span data-ttu-id="6d88d-131">W **komputera pliki źródłowe** okienku wybierz **podstawowe wyjście z** *< project_name >*.</span><span class="sxs-lookup"><span data-stu-id="6d88d-131">In the **Source computer's files** pane, choose **Primary output from** *<project_name>*.</span></span>  
  
    4.  <span data-ttu-id="6d88d-132">Przeciągnij plik z kroku c do **plikach na komputerze docelowym** okienko (lub użyj **kopiowania** i **Wklej** poleceń w menu skrótów pliku).</span><span class="sxs-lookup"><span data-stu-id="6d88d-132">Drag the file in step c to the **Destination computer's files** pane (or use the **Copy** and **Paste** commands from the file's shortcut menu).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d88d-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d88d-133">See Also</span></span>  
 [<span data-ttu-id="6d88d-134">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="6d88d-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="6d88d-135">Instrukcje: usuwanie zestawu z pamięci Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="6d88d-135">How to: Remove an Assembly from the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [<span data-ttu-id="6d88d-136">Gacutil.exe (narzędzie Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="6d88d-136">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [<span data-ttu-id="6d88d-137">Instrukcje: podpisywanie zestawu silną nazwą</span><span class="sxs-lookup"><span data-stu-id="6d88d-137">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="6d88d-138">Wdrażanie za pomocą Instalatora Windows</span><span class="sxs-lookup"><span data-stu-id="6d88d-138">Windows Installer Deployment</span></span>](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
