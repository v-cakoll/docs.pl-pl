---
title: 'Instrukcje: Wywoływanie kompilatora wiersza polecenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 67cad0df3f10ff1fa1f6a58546fe150232fe1283
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032074"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="2dfce-102">Instrukcje: Wywoływanie kompilatora wiersza polecenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2dfce-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>
<span data-ttu-id="2dfce-103">Można wywołać kompilatora wiersza polecenia, wpisując nazwę jego pliku wykonywalnego do wiersza polecenia, znany także jako wiersz systemu MS-DOS.</span><span class="sxs-lookup"><span data-stu-id="2dfce-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="2dfce-104">Jeśli kompilujesz w wierszu polecenia Windows domyślnej, należy wpisać w pełni kwalifikowana ścieżka do pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="2dfce-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="2dfce-105">Aby zastąpić to zachowanie domyślne, można użyć wiersza polecenia dewelopera dla programu Visual Studio lub zmodyfikować zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="2dfce-105">To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable.</span></span> <span data-ttu-id="2dfce-106">Obie umożliwiają kompilowanie z dowolnego katalogu, po prostu wpisując nazwę kompilatora.</span><span class="sxs-lookup"><span data-stu-id="2dfce-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a><span data-ttu-id="2dfce-107">Aby wywołać kompilatora przy użyciu wiersza polecenia dla deweloperów programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2dfce-107">To invoke the compiler using the Developer Command Prompt for Visual Studio</span></span>  
  
1. <span data-ttu-id="2dfce-108">Otwórz folder programu Visual Studio Tools w obrębie grupy programu Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2dfce-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>  
  
2. <span data-ttu-id="2dfce-109">Jeśli zainstalowano program Visual Studio, można użyć wiersza polecenia dewelopera dla programu Visual Studio dostęp do kompilatora z dowolnego katalogu na komputerze.</span><span class="sxs-lookup"><span data-stu-id="2dfce-109">You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>  
  
3. <span data-ttu-id="2dfce-110">Wywołaj wiersz polecenia programisty dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2dfce-110">Invoke the Developer Command Prompt for Visual Studio.</span></span>  
  
4. <span data-ttu-id="2dfce-111">W wierszu polecenia wpisz polecenie `vbc.exe` *sourceFileName* i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="2dfce-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="2dfce-112">Na przykład, jeśli kod źródłowy jest przechowywany w katalogu o nazwie `SourceFiles`, czy otworzyć wiersz polecenia i wpisz `cd SourceFiles` zmiany do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="2dfce-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="2dfce-113">Jeśli katalog zawiera plik źródłowy o nazwie `Source.vb`, można go skompilować, wpisując `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="2dfce-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="2dfce-114">Aby ustawić zmiennej środowiskowej PATH kompilatora wiersza polecenia dla Windows</span><span class="sxs-lookup"><span data-stu-id="2dfce-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>  
  
1. <span data-ttu-id="2dfce-115">Użyj funkcji Windows Search, aby znaleźć Vbc.exe na dysku lokalnym.</span><span class="sxs-lookup"><span data-stu-id="2dfce-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>  
  
     <span data-ttu-id="2dfce-116">Dokładną nazwę katalogu, w którym znajduje się kompilator zależy od tego, lokalizację katalogu Windows i wersji "Systemu.NET Framework".</span><span class="sxs-lookup"><span data-stu-id="2dfce-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="2dfce-117">Jeśli masz więcej niż jedna wersja "Systemu.NET Framework", musisz określić wyborze wersji do użycia (zwykle najnowszą).</span><span class="sxs-lookup"><span data-stu-id="2dfce-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>  
  
2. <span data-ttu-id="2dfce-118">Z usługi **Start** Menu, kliknij prawym przyciskiem myszy **Mój komputer**, a następnie kliknij przycisk **właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="2dfce-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>  
  
3. <span data-ttu-id="2dfce-119">Kliknij przycisk **zaawansowane** kartę, a następnie kliknij przycisk **zmienne środowiskowe**.</span><span class="sxs-lookup"><span data-stu-id="2dfce-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4. <span data-ttu-id="2dfce-120">W **systemu** Okienko zmiennych, wybierz opcję **ścieżki** z listy i kliknij przycisk **Edytuj**.</span><span class="sxs-lookup"><span data-stu-id="2dfce-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>  
  
5. <span data-ttu-id="2dfce-121">W **edycji systemu** okno dialogowe zmiennej, przesuń punkt wstawiania do końca ciągu w **wartość zmiennej** pola, a następnie wpisz je średnikiem (;) następuje nazwa pełny katalog, w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="2dfce-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>  
  
6. <span data-ttu-id="2dfce-122">Kliknij przycisk **OK** aby potwierdzić zmiany i zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="2dfce-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>  
  
     <span data-ttu-id="2dfce-123">Po zmianie zmiennej środowiskowej PATH, można uruchomić kompilator Visual Basic w wierszu polecenia Windows z dowolnego katalogu na komputerze.</span><span class="sxs-lookup"><span data-stu-id="2dfce-123">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="2dfce-124">Aby wywołać kompilatora przy użyciu wiersza polecenia Windows</span><span class="sxs-lookup"><span data-stu-id="2dfce-124">To invoke the compiler using the Windows Command Prompt</span></span>  
  
1. <span data-ttu-id="2dfce-125">Z **Start** menu, kliknij pozycję **Akcesoria** folder, a następnie otwórz **wiersza polecenia Windows**.</span><span class="sxs-lookup"><span data-stu-id="2dfce-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>  
  
2. <span data-ttu-id="2dfce-126">W wierszu polecenia wpisz polecenie `vbc.exe` *sourceFileName* i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="2dfce-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="2dfce-127">Na przykład, jeśli kod źródłowy jest przechowywany w katalogu o nazwie `SourceFiles`, czy otworzyć wiersz polecenia i wpisz `cd SourceFiles` zmiany do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="2dfce-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="2dfce-128">Jeśli katalog zawiera plik źródłowy o nazwie `Source.vb`, można go skompilować, wpisując `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="2dfce-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dfce-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2dfce-129">See also</span></span>

- [<span data-ttu-id="2dfce-130">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2dfce-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="2dfce-131">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="2dfce-131">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
