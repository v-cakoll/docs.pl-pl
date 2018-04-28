---
title: 'Porady: wywoływanie kompilatora wiersza polecenia (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 20239045426e466ba58427bb9794ea7e55b3aa4c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="7c117-102">Porady: wywoływanie kompilatora wiersza polecenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c117-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>
<span data-ttu-id="7c117-103">Można wywołać kompilatora wiersza polecenia, wpisując nazwę jego pliku wykonywalnego do wiersza polecenia, znanej także jako polecenia systemu MS-DOS.</span><span class="sxs-lookup"><span data-stu-id="7c117-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="7c117-104">Jeśli kompilacja z domyślnego wiersza polecenia systemu Windows, należy wpisać w pełni kwalifikowana ścieżka do pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="7c117-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="7c117-105">Aby zmienić to zachowanie domyślne, możesz Użyj wiersz polecenia programu Visual Studio lub zmodyfikuj zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="7c117-105">To override this default behavior, you can either use the Visual Studio Command Prompt, or modify the PATH environment variable.</span></span> <span data-ttu-id="7c117-106">Umożliwiają zarówno skompilować z dowolnego katalogu, wpisując nazwę kompilatora.</span><span class="sxs-lookup"><span data-stu-id="7c117-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-visual-studio-command-prompt"></a><span data-ttu-id="7c117-107">Aby wywołać kompilatora przy użyciu wiersza polecenia programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7c117-107">To invoke the compiler using the Visual Studio Command Prompt</span></span>  
  
1.  <span data-ttu-id="7c117-108">Otwórz folder programu Visual Studio Tools w obrębie grupy programu Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7c117-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>  
  
2.  <span data-ttu-id="7c117-109">Wiersz polecenia programu Visual Studio służy do uzyskania dostępu przez kompilator z dowolnego katalogu na komputerze, po zainstalowaniu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7c117-109">You can use the Visual Studio Command Prompt to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>  
  
3.  <span data-ttu-id="7c117-110">Należy wywołać wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7c117-110">Invoke the Visual Studio Command Prompt.</span></span>  
  
4.  <span data-ttu-id="7c117-111">W wierszu polecenia wpisz `vbc.exe` *sourceFileName* , a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="7c117-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="7c117-112">Na przykład, jeśli kod źródłowy jest przechowywany w katalogu o nazwie `SourceFiles`, czy Otwórz wiersz polecenia i wpisz `cd SourceFiles` zmiany do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="7c117-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="7c117-113">Jeśli katalog zawiera plik źródłowy o nazwie `Source.vb`, można go skompilować, wpisując `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="7c117-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="7c117-114">Aby ustawić wartość zmiennej środowiskowej PATH kompilatora wiersza polecenia systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7c117-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="7c117-115">Użyj funkcji wyszukiwania systemu Windows można znaleźć Vbc.exe na lokalnym dysku twardym.</span><span class="sxs-lookup"><span data-stu-id="7c117-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>  
  
     <span data-ttu-id="7c117-116">Dokładną nazwę katalogu, w którym znajduje się kompilator zależy od lokalizacji katalogu systemu Windows i wersji ".NET Framework" zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="7c117-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="7c117-117">Jeśli masz więcej niż jedną wersję ".NET Framework" zainstalowany, należy określić wersji do użycia (zwykle najnowsza wersja).</span><span class="sxs-lookup"><span data-stu-id="7c117-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>  
  
2.  <span data-ttu-id="7c117-118">Z sieci **Start** Menu, kliknij prawym przyciskiem myszy **Mój komputer**, a następnie kliknij przycisk **właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="7c117-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="7c117-119">Kliknij przycisk **zaawansowane** , a następnie kliknij pozycję **zmiennych środowiskowych**.</span><span class="sxs-lookup"><span data-stu-id="7c117-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="7c117-120">W **systemu** zmienne okienku wybierz **ścieżki** na liście i kliknij przycisk **Edytuj**.</span><span class="sxs-lookup"><span data-stu-id="7c117-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>  
  
5.  <span data-ttu-id="7c117-121">W **edycji systemu** okna dialogowego zmiennej, umieść punkt wstawiania na końcu ciągu w **wartość zmiennej** i wpisz średnikiem (;) następuje nazwa katalogu pełna w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="7c117-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>  
  
6.  <span data-ttu-id="7c117-122">Kliknij przycisk **OK** aby potwierdzić zmiany i zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="7c117-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>  
  
     <span data-ttu-id="7c117-123">Po zmianie zmiennej środowiskowej PATH, można uruchomić kompilator Visual Basic w wierszu polecenia systemu Windows z dowolnego katalogu na komputerze.</span><span class="sxs-lookup"><span data-stu-id="7c117-123">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="7c117-124">Aby wywołać kompilatora przy użyciu wiersza polecenia systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7c117-124">To invoke the compiler using the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="7c117-125">Z **Start** menu, kliknij polecenie **Akcesoria** folder, a następnie otwórz **wiersza polecenia systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="7c117-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="7c117-126">W wierszu polecenia wpisz `vbc.exe` *sourceFileName* , a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="7c117-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="7c117-127">Na przykład, jeśli kod źródłowy jest przechowywany w katalogu o nazwie `SourceFiles`, czy Otwórz wiersz polecenia i wpisz `cd SourceFiles` zmiany do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="7c117-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="7c117-128">Jeśli katalog zawiera plik źródłowy o nazwie `Source.vb`, można go skompilować, wpisując `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="7c117-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c117-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c117-129">See Also</span></span>  
 [<span data-ttu-id="7c117-130">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7c117-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="7c117-131">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="7c117-131">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
