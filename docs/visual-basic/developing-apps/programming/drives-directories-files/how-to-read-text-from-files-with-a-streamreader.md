---
title: 'Porady: odczyt tekstu z plików za pomocą StreamReader'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: 572463d1f03d768fb133f2dac59b012051f053bb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334562"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a><span data-ttu-id="fb160-102">Porady: odczyt tekstu z plików za pomocą StreamReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb160-102">How to: Read Text from Files with a StreamReader (Visual Basic)</span></span>

<span data-ttu-id="fb160-103">Obiekt `My.Computer.FileSystem` zawiera metody umożliwiające otwarcie <xref:System.IO.TextReader> i <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="fb160-103">The `My.Computer.FileSystem` object provides methods to open a <xref:System.IO.TextReader> and a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="fb160-104">Te metody, `OpenTextFileWriter` i `OpenTextFileReader`, to metody zaawansowane, które nie są wyświetlane w technologii IntelliSense, chyba że wybierzesz kartę **wszystkie** .</span><span class="sxs-lookup"><span data-stu-id="fb160-104">These methods, `OpenTextFileWriter` and `OpenTextFileReader`, are advanced methods that do not appear in IntelliSense unless you select the **All** tab.</span></span>  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a><span data-ttu-id="fb160-105">Aby odczytać wiersz z pliku za pomocą czytnika tekstu</span><span class="sxs-lookup"><span data-stu-id="fb160-105">To read a line from a file with a text reader</span></span>  
  
- <span data-ttu-id="fb160-106">Użyj metody `OpenTextFileReader`, aby otworzyć <xref:System.IO.TextReader>, określając plik.</span><span class="sxs-lookup"><span data-stu-id="fb160-106">Use the `OpenTextFileReader` method to open the <xref:System.IO.TextReader>, specifying the file.</span></span> <span data-ttu-id="fb160-107">Ten przykład otwiera plik o nazwie `testfile.txt`, odczytuje z niego wiersz i wyświetla wiersz w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="fb160-107">This example opens the file named `testfile.txt`, reads a line from it, and displays the line in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="fb160-108">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="fb160-108">Robust Programming</span></span>  

 <span data-ttu-id="fb160-109">Odczytywany plik musi być plikiem tekstowym.</span><span class="sxs-lookup"><span data-stu-id="fb160-109">The file that is read must be a text file.</span></span>  
  
 <span data-ttu-id="fb160-110">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="fb160-110">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="fb160-111">Na przykład plik Form1. vb nie może być plikiem źródłowym Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fb160-111">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="fb160-112">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fb160-112">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="fb160-113">Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.</span><span class="sxs-lookup"><span data-stu-id="fb160-113">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fb160-114">Zabezpieczenia programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fb160-114">.NET Framework Security</span></span>  

 <span data-ttu-id="fb160-115">Aby odczytywać dane z pliku, zestaw wymaga poziomu uprawnień przyznanych przez klasę <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="fb160-115">To read from a file, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission> class.</span></span> <span data-ttu-id="fb160-116">Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek z powodu niewystarczających uprawnień.</span><span class="sxs-lookup"><span data-stu-id="fb160-116">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="fb160-117">Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="fb160-117">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span> <span data-ttu-id="fb160-118">Użytkownik musi również mieć dostęp do pliku.</span><span class="sxs-lookup"><span data-stu-id="fb160-118">The user also needs access to the file.</span></span> <span data-ttu-id="fb160-119">Aby uzyskać więcej informacji, zobacz [Omówienie technologii list ACL](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fb160-119">For more information, see [ACL Technology Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb160-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb160-120">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [<span data-ttu-id="fb160-121">SaveFileDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="fb160-121">SaveFileDialog Component</span></span>](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)
- [<span data-ttu-id="fb160-122">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="fb160-122">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
