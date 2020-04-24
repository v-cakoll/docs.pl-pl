---
title: 'Porady: wywoływanie kompilatora wiersza polecenia'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 3b34ebba68c9c9b2a8335822d0ffaef2a9b06d7c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344258"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="b8756-102">Porady: wywoływanie kompilatora wiersza polecenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8756-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>

<span data-ttu-id="b8756-103">Kompilator wiersza polecenia można wywołać, wpisując nazwę pliku wykonywalnego w wierszu polecenia, znanego również jako monit MS-DOS.</span><span class="sxs-lookup"><span data-stu-id="b8756-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="b8756-104">Jeśli kompilujesz z domyślnego wiersza polecenia systemu Windows, musisz wpisać w pełni kwalifikowaną ścieżkę do pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="b8756-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="b8756-105">Aby zastąpić to zachowanie domyślne, można użyć wiersz polecenia dla deweloperów dla programu Visual Studio lub zmodyfikować zmienną środowiskową PATH.</span><span class="sxs-lookup"><span data-stu-id="b8756-105">To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable.</span></span> <span data-ttu-id="b8756-106">Oba umożliwiają kompilowanie z dowolnego katalogu przez wpisanie nazwy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="b8756-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a><span data-ttu-id="b8756-107">Aby wywołać kompilator przy użyciu wiersz polecenia dla deweloperów dla programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b8756-107">To invoke the compiler using the Developer Command Prompt for Visual Studio</span></span>

1. <span data-ttu-id="b8756-108">Otwórz folder programu Visual Studio Tools w grupie programów Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8756-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>

2. <span data-ttu-id="b8756-109">Możesz użyć wiersz polecenia dla deweloperów dla programu Visual Studio, aby uzyskać dostęp do kompilatora z dowolnego katalogu na komputerze, jeśli jest zainstalowany program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8756-109">You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>

3. <span data-ttu-id="b8756-110">Wywołaj wiersz polecenia dla deweloperów dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8756-110">Invoke the Developer Command Prompt for Visual Studio.</span></span>

4. <span data-ttu-id="b8756-111">W wierszu polecenia wpisz `vbc.exe` *sourceFileName* , a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="b8756-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>

    <span data-ttu-id="b8756-112">Na przykład jeśli kod źródłowy został zapisany w katalogu o nazwie `SourceFiles`, należy otworzyć wiersz polecenia i wpisać `cd SourceFiles` zmiany w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b8756-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="b8756-113">Jeśli katalog zawiera plik źródłowy o nazwie `Source.vb`, można go skompilować, wpisując. `vbc.exe Source.vb`</span><span class="sxs-lookup"><span data-stu-id="b8756-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="b8756-114">Aby ustawić zmienną środowiskową PATH na kompilator dla wiersza polecenia systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b8756-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>

1. <span data-ttu-id="b8756-115">Użyj funkcji wyszukiwania systemu Windows, aby znaleźć VBC. exe na dysku lokalnym.</span><span class="sxs-lookup"><span data-stu-id="b8756-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>

    <span data-ttu-id="b8756-116">Dokładna nazwa katalogu, w którym znajduje się kompilator, zależy od lokalizacji katalogu systemu Windows i zainstalowanej wersji programu ".NET Framework".</span><span class="sxs-lookup"><span data-stu-id="b8756-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="b8756-117">Jeśli masz zainstalowaną więcej niż jedną wersję ".NET Framework", musisz określić, która wersja ma być używana (zazwyczaj Najnowsza wersja).</span><span class="sxs-lookup"><span data-stu-id="b8756-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>

2. <span data-ttu-id="b8756-118">W menu **Start** kliknij prawym przyciskiem myszy pozycję **mój komputer**, a następnie kliknij polecenie **Właściwości** w menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="b8756-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>

3. <span data-ttu-id="b8756-119">Kliknij kartę **Zaawansowane** , a następnie kliknij pozycję **zmienne środowiskowe**.</span><span class="sxs-lookup"><span data-stu-id="b8756-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>

4. <span data-ttu-id="b8756-120">W okienku zmienne **systemowe** wybierz pozycję **ścieżka** z listy, a następnie kliknij pozycję **Edytuj**.</span><span class="sxs-lookup"><span data-stu-id="b8756-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>

5. <span data-ttu-id="b8756-121">W oknie dialogowym **Edycja zmiennej systemowej** przesuń punkt wstawiania do końca ciągu w polu **wartość zmiennej** i wpisz średnika (;) a następnie pełna nazwa katalogu znaleziona w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="b8756-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>

6. <span data-ttu-id="b8756-122">Kliknij przycisk **OK** , aby potwierdzić zmiany i zamknąć okna dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b8756-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>

     <span data-ttu-id="b8756-123">Po zmianie zmiennej środowiskowej PATH można uruchomić kompilator Visual Basic w wierszu polecenia systemu Windows z dowolnego katalogu na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b8756-123">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="b8756-124">Aby wywołać kompilator przy użyciu wiersza polecenia systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b8756-124">To invoke the compiler using the Windows Command Prompt</span></span>

1. <span data-ttu-id="b8756-125">W menu **Start** kliknij folder **akcesoria** , a następnie otwórz **wiersz polecenia systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="b8756-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>

2. <span data-ttu-id="b8756-126">W wierszu polecenia wpisz `vbc.exe` *sourceFileName* , a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="b8756-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>

     <span data-ttu-id="b8756-127">Na przykład jeśli kod źródłowy został zapisany w katalogu o nazwie `SourceFiles`, należy otworzyć wiersz polecenia i wpisać `cd SourceFiles` zmiany w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b8756-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="b8756-128">Jeśli katalog zawiera plik źródłowy o nazwie `Source.vb`, można go skompilować, wpisując. `vbc.exe Source.vb`</span><span class="sxs-lookup"><span data-stu-id="b8756-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8756-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8756-129">See also</span></span>

- [<span data-ttu-id="b8756-130">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b8756-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="b8756-131">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="b8756-131">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
