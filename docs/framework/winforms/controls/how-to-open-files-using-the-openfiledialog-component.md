---
title: 'Jak: Otwieranie plików za pomocą składnika OpenFileDialog'
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: ca69de19ab1b9ae387002898145fe99e35a7b6b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182130"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a><span data-ttu-id="c1b86-102">Jak: Otwieranie plików za pomocą OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="c1b86-102">How to: Open files with the OpenFileDialog</span></span>

<span data-ttu-id="c1b86-103">Składnik <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> otwiera okno dialogowe systemu Windows do przeglądania i wybierania plików.</span><span class="sxs-lookup"><span data-stu-id="c1b86-103">The <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> component opens the Windows dialog box for browsing and selecting files.</span></span> <span data-ttu-id="c1b86-104">Aby otworzyć i odczytać wybrane pliki, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> można użyć metody lub <xref:System.IO.StreamReader?displayProperty=nameWithType> utworzyć wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="c1b86-104">To open and read the selected files, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> method, or create an instance of the <xref:System.IO.StreamReader?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="c1b86-105">Poniższe przykłady pokazują oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="c1b86-105">The following examples show both approaches.</span></span>

<span data-ttu-id="c1b86-106">W .NET Framework, aby <xref:System.Windows.Forms.FileDialog.FileName%2A> uzyskać lub ustawić właściwość <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> wymaga poziomu uprawnień przyznane przez klasę.</span><span class="sxs-lookup"><span data-stu-id="c1b86-106">In .NET Framework, to get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="c1b86-107">Przykłady uruchomić <xref:System.Security.Permissions.FileIOPermission> sprawdzanie uprawnień i można zgłosić wyjątek z powodu niewystarczających uprawnień, jeśli są uruchamiane w kontekście częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="c1b86-107">The examples run a <xref:System.Security.Permissions.FileIOPermission> permission check, and can throw an exception due to insufficient privileges if run in a partial-trust context.</span></span> <span data-ttu-id="c1b86-108">Aby uzyskać więcej informacji, zobacz [Podstawy zabezpieczeń dostępu do kodu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="c1b86-108">For more information, see [Code access security basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="c1b86-109">Można skompilować i uruchomić te przykłady jako aplikacje .NET Framework z wiersza polecenia C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c1b86-109">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="c1b86-110">Aby uzyskać więcej informacji, zobacz [Tworzenie wiersza polecenia za pomocą pliku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [Kompilacja z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="c1b86-110">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>

<span data-ttu-id="c1b86-111">Począwszy od programu .NET Core 3.0, można również tworzyć i uruchamiać przykłady jako aplikacje windows .NET Core z folderu o nazwie folderu .NET Core Windows Forms \* \<>.csproj\* pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="c1b86-111">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span>

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a><span data-ttu-id="c1b86-112">Przykład: Odczyt pliku jako strumienia za pomocą streamreadera</span><span class="sxs-lookup"><span data-stu-id="c1b86-112">Example: Read a file as a stream with StreamReader</span></span>  
  
<span data-ttu-id="c1b86-113">W poniższym przykładzie <xref:System.Windows.Forms.Button> użyto <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń <xref:System.Windows.Forms.OpenFileDialog> formantu Windows Forms, aby otworzyć <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę with.</span><span class="sxs-lookup"><span data-stu-id="c1b86-113">The following example uses the Windows Forms <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="c1b86-114">Gdy użytkownik wybierze plik i wybierze przycisk <xref:System.IO.StreamReader> **OK,** wystąpienie klasy odczytuje plik i wyświetla jego zawartość w polu tekstowym formularza.</span><span class="sxs-lookup"><span data-stu-id="c1b86-114">After the user chooses a file and selects **OK**, an instance of the <xref:System.IO.StreamReader> class reads the file and displays its contents in the form's text box.</span></span> <span data-ttu-id="c1b86-115">Aby uzyskać więcej informacji na temat <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>odczytu ze strumieni plików, zobacz i .</span><span class="sxs-lookup"><span data-stu-id="c1b86-115">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span></span>  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a><span data-ttu-id="c1b86-116">Przykład: Otwieranie pliku z filtrowanego zaznaczenia za pomocą pliku OpenFile</span><span class="sxs-lookup"><span data-stu-id="c1b86-116">Example: Open a file from a filtered selection with OpenFile</span></span>

<span data-ttu-id="c1b86-117">W poniższym <xref:System.Windows.Forms.Button> przykładzie użyto programu obsługi <xref:System.Windows.Forms.Control.Click> zdarzeń formantu, aby otworzyć <xref:System.Windows.Forms.OpenFileDialog> z filtrem, który pokazuje tylko pliki tekstowe.</span><span class="sxs-lookup"><span data-stu-id="c1b86-117">The following example uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with a filter that shows only text files.</span></span> <span data-ttu-id="c1b86-118">Gdy użytkownik wybierze plik tekstowy i <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> wybierze **przycisk OK,** metoda ta jest używana do otwierania pliku w Notatniku.</span><span class="sxs-lookup"><span data-stu-id="c1b86-118">After the user chooses a text file and selects **OK**, the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is used to open the file in Notepad.</span></span>

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="c1b86-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1b86-119">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="c1b86-120">Składnik OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="c1b86-120">OpenFileDialog component</span></span>](openfiledialog-component-windows-forms.md)
