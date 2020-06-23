---
title: 'Instrukcje: otwieranie plików za pomocą składnika OpenFileDialog'
ms.date: 02/11/2019
description: Dowiedz się, jak za pomocą składnika OpenFileDialog otworzyć okno dialogowe systemu Windows służące do przeglądania i wybierania plików.
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: d571885011b0f0c723c73a417f294f30f96952f4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904432"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a><span data-ttu-id="8b6bf-103">Instrukcje: otwieranie plików za pomocą OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="8b6bf-103">How to: Open files with the OpenFileDialog</span></span>

<span data-ttu-id="8b6bf-104"><xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType>Składnik otwiera okno dialogowe systemu Windows służące do przeglądania i wybierania plików.</span><span class="sxs-lookup"><span data-stu-id="8b6bf-104">The <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> component opens the Windows dialog box for browsing and selecting files.</span></span> <span data-ttu-id="8b6bf-105">Aby otworzyć i odczytać wybrane pliki, można użyć <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> metody lub utworzyć wystąpienie <xref:System.IO.StreamReader?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="8b6bf-105">To open and read the selected files, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> method, or create an instance of the <xref:System.IO.StreamReader?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="8b6bf-106">W poniższych przykładach pokazano oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="8b6bf-106">The following examples show both approaches.</span></span>

<span data-ttu-id="8b6bf-107">W .NET Framework, aby uzyskać lub ustawić <xref:System.Windows.Forms.FileDialog.FileName%2A> Właściwość, wymaga poziomu uprawnień przyznany przez <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> klasę.</span><span class="sxs-lookup"><span data-stu-id="8b6bf-107">In .NET Framework, to get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="8b6bf-108">Przykłady uruchamiają <xref:System.Security.Permissions.FileIOPermission> kontrolę uprawnień i mogą zgłosić wyjątek z powodu niewystarczających uprawnień, jeśli są uruchamiane w kontekście częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="8b6bf-108">The examples run a <xref:System.Security.Permissions.FileIOPermission> permission check, and can throw an exception due to insufficient privileges if run in a partial-trust context.</span></span> <span data-ttu-id="8b6bf-109">Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="8b6bf-109">For more information, see [Code access security basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="8b6bf-110">Możesz tworzyć i uruchamiać te przykłady jako .NET Framework aplikacje z poziomu wiersza polecenia C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8b6bf-110">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="8b6bf-111">Aby uzyskać więcej informacji, zobacz [Kompilowanie wiersza polecenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [Kompilowanie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="8b6bf-111">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>

<span data-ttu-id="8b6bf-112">Począwszy od platformy .NET Core 3,0, można również kompilować i uruchamiać przykłady jako aplikacje platformy Windows .NET Core z folderu, który ma plik projektu programu .NET Core Windows Forms \* \<folder name> . csproj\* .</span><span class="sxs-lookup"><span data-stu-id="8b6bf-112">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span>

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a><span data-ttu-id="8b6bf-113">Przykład: odczytywanie pliku jako strumienia przy użyciu StreamReader</span><span class="sxs-lookup"><span data-stu-id="8b6bf-113">Example: Read a file as a stream with StreamReader</span></span>  
  
<span data-ttu-id="8b6bf-114">Poniższy przykład używa <xref:System.Windows.Forms.Button> procedury obsługi zdarzeń kontrolki Windows Forms, <xref:System.Windows.Forms.Control.Click> Aby otworzyć <xref:System.Windows.Forms.OpenFileDialog> przy użyciu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8b6bf-114">The following example uses the Windows Forms <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="8b6bf-115">Gdy użytkownik wybierze plik i wybierze **OK**, wystąpienie <xref:System.IO.StreamReader> klasy odczytuje plik i wyświetla jego zawartość w polu tekstowym formularza.</span><span class="sxs-lookup"><span data-stu-id="8b6bf-115">After the user chooses a file and selects **OK**, an instance of the <xref:System.IO.StreamReader> class reads the file and displays its contents in the form's text box.</span></span> <span data-ttu-id="8b6bf-116">Aby uzyskać więcej informacji na temat odczytywania strumieni plików, zobacz <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> i <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8b6bf-116">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span></span>  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a><span data-ttu-id="8b6bf-117">Przykład: otwiera plik z filtrowanego zaznaczenia za pomocą OpenFile</span><span class="sxs-lookup"><span data-stu-id="8b6bf-117">Example: Open a file from a filtered selection with OpenFile</span></span>

<span data-ttu-id="8b6bf-118">Poniższy przykład używa <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń kontrolki do otwierania <xref:System.Windows.Forms.OpenFileDialog> z filtrem, który pokazuje tylko pliki tekstowe.</span><span class="sxs-lookup"><span data-stu-id="8b6bf-118">The following example uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with a filter that shows only text files.</span></span> <span data-ttu-id="8b6bf-119">Gdy użytkownik wybierze plik tekstowy i wybierze **OK**, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> Metoda zostanie użyta do otwarcia pliku w Notatniku.</span><span class="sxs-lookup"><span data-stu-id="8b6bf-119">After the user chooses a text file and selects **OK**, the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is used to open the file in Notepad.</span></span>

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="8b6bf-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b6bf-120">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="8b6bf-121">Składnik OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="8b6bf-121">OpenFileDialog component</span></span>](openfiledialog-component-windows-forms.md)
