---
title: 'Instrukcje: Otwieranie plików za pomocą składnika OpenFileDialog'
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: 7f4e96f1714a182647665f12e29d38f2b8037478
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913461"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a><span data-ttu-id="5827c-102">Instrukcje: Pliki otwarte z OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="5827c-102">How to: Open files with the OpenFileDialog</span></span> 

<span data-ttu-id="5827c-103"><xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> Składnika otwiera okno dialogowe Windows do przeglądania i zaznaczania plików.</span><span class="sxs-lookup"><span data-stu-id="5827c-103">The <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> component opens the Windows dialog box for browsing and selecting files.</span></span> <span data-ttu-id="5827c-104">Aby otworzyć i odczytać wybranych plików, można użyć <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> metodę, lub Utwórz wystąpienie obiektu <xref:System.IO.StreamReader?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="5827c-104">To open and read the selected files, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> method, or create an instance of the <xref:System.IO.StreamReader?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="5827c-105">W poniższych przykładach pokazano oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="5827c-105">The following examples show both approaches.</span></span> 

<span data-ttu-id="5827c-106">W programie .NET Framework do pobierania lub ustawiania <xref:System.Windows.Forms.FileDialog.FileName%2A> właściwości wymaga poziomu uprawnień przyznanych przez <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="5827c-106">In .NET Framework, to get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="5827c-107">Uruchamianie przykładów <xref:System.Security.Permissions.FileIOPermission> uprawnień Sprawdź i może zgłosić wyjątek ze względu na niewystarczające uprawnienia, jeśli są uruchamiane w kontekście częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="5827c-107">The examples run a <xref:System.Security.Permissions.FileIOPermission> permission check, and can throw an exception due to insufficient privileges if run in a partial-trust context.</span></span> <span data-ttu-id="5827c-108">Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="5827c-108">For more information, see [Code access security basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="5827c-109">Można skompilować i uruchomić te przykłady jako aplikacji .NET Framework z C# lub wiersza polecenia programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5827c-109">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="5827c-110">Aby uzyskać więcej informacji, zobacz [za pomocą wiersza polecenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [kompilacji z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="5827c-110">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span> 

<span data-ttu-id="5827c-111">Począwszy od programu .NET Core 3.0 można również skompilować i uruchomić przykłady jako Windows aplikacje platformy .NET Core z folderu, który ma .NET Core Windows form  *\<nazwę folderu > .csproj* pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="5827c-111">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span> 

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a><span data-ttu-id="5827c-112">Przykład: Odczytywanie pliku jako strumienia za pomocą StreamReader</span><span class="sxs-lookup"><span data-stu-id="5827c-112">Example: Read a file as a stream with StreamReader</span></span>  
  
<span data-ttu-id="5827c-113">W poniższym przykładzie użyto formularze Windows <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń, aby otworzyć <xref:System.Windows.Forms.OpenFileDialog> z <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5827c-113">The following example uses the Windows Forms <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="5827c-114">Po użytkownik wybierze plik i wybierze **OK**, wystąpienie <xref:System.IO.StreamReader> klasy odczytuje plik i wyświetla jego zawartość w polu tekstowym w formularzu.</span><span class="sxs-lookup"><span data-stu-id="5827c-114">After the user chooses a file and selects **OK**, an instance of the <xref:System.IO.StreamReader> class reads the file and displays its contents in the form's text box.</span></span> <span data-ttu-id="5827c-115">Aby uzyskać więcej informacji na temat odczytywania ze strumieni plików Zobacz <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> i <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5827c-115">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span></span>  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a><span data-ttu-id="5827c-116">Przykład: Otwórz plik z filtrowanych zaznaczenia z OpenFile</span><span class="sxs-lookup"><span data-stu-id="5827c-116">Example: Open a file from a filtered selection with OpenFile</span></span> 

<span data-ttu-id="5827c-117">W poniższym przykładzie użyto <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń, aby otworzyć <xref:System.Windows.Forms.OpenFileDialog> za pomocą filtru, który pokazuje tylko pliki tekstowe.</span><span class="sxs-lookup"><span data-stu-id="5827c-117">The following example uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with a filter that shows only text files.</span></span> <span data-ttu-id="5827c-118">Gdy użytkownik wybierze plik tekstowy, a wybiera **OK**, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda służy do otwierania tego pliku w Notatniku.</span><span class="sxs-lookup"><span data-stu-id="5827c-118">After the user chooses a text file and selects **OK**, the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is used to open the file in Notepad.</span></span>

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="5827c-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5827c-119">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="5827c-120">Openfiledialog — składnik</span><span class="sxs-lookup"><span data-stu-id="5827c-120">OpenFileDialog component</span></span>](openfiledialog-component-windows-forms.md)
