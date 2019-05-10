---
title: 'Instrukcje: Odczytywanie tekstu z plików za pomocą StreamReader (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: 5631b402743a7be19428d15f55fbaa78b5b90668
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623360"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a><span data-ttu-id="b10d1-102">Instrukcje: Odczytywanie tekstu z plików za pomocą StreamReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b10d1-102">How to: Read Text from Files with a StreamReader (Visual Basic)</span></span>
<span data-ttu-id="b10d1-103">`My.Computer.FileSystem` Obiektu udostępnia metody, aby otworzyć <xref:System.IO.TextReader> i <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="b10d1-103">The `My.Computer.FileSystem` object provides methods to open a <xref:System.IO.TextReader> and a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="b10d1-104">Te metody `OpenTextFileWriter` i `OpenTextFileReader`, są zaawansowane metody, które nie są wyświetlane w IntelliSense dopiero po wybraniu **wszystkich** kartę.</span><span class="sxs-lookup"><span data-stu-id="b10d1-104">These methods, `OpenTextFileWriter` and `OpenTextFileReader`, are advanced methods that do not appear in IntelliSense unless you select the **All** tab.</span></span>  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a><span data-ttu-id="b10d1-105">Aby odczytywać plik wiersz z czytnika tekstu</span><span class="sxs-lookup"><span data-stu-id="b10d1-105">To read a line from a file with a text reader</span></span>  
  
- <span data-ttu-id="b10d1-106">Użyj `OpenTextFileReader` metodę, aby otworzyć <xref:System.IO.TextReader>, określenie pliku.</span><span class="sxs-lookup"><span data-stu-id="b10d1-106">Use the `OpenTextFileReader` method to open the <xref:System.IO.TextReader>, specifying the file.</span></span> <span data-ttu-id="b10d1-107">W tym przykładzie otwiera plik o nazwie `testfile.txt`, odczytuje wiersz z niego i wyświetla wiersz w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b10d1-107">This example opens the file named `testfile.txt`, reads a line from it, and displays the line in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b10d1-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="b10d1-108">Robust Programming</span></span>  
 <span data-ttu-id="b10d1-109">Plik, który jest wczytywany musi być plikiem tekstowym.</span><span class="sxs-lookup"><span data-stu-id="b10d1-109">The file that is read must be a text file.</span></span>  
  
 <span data-ttu-id="b10d1-110">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="b10d1-110">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="b10d1-111">Na przykład plik Form1.vb może nie być plik źródłowy w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b10d1-111">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="b10d1-112">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b10d1-112">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="b10d1-113">Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.</span><span class="sxs-lookup"><span data-stu-id="b10d1-113">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b10d1-114">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="b10d1-114">.NET Framework Security</span></span>  
 <span data-ttu-id="b10d1-115">Aby odczytać z pliku, zestaw wymaga poziom uprawnień przyznanych przez <xref:System.Security.Permissions.FileIOPermission> klasy.</span><span class="sxs-lookup"><span data-stu-id="b10d1-115">To read from a file, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission> class.</span></span> <span data-ttu-id="b10d1-116">Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek ze względu na niewystarczające uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="b10d1-116">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="b10d1-117">Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="b10d1-117">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span> <span data-ttu-id="b10d1-118">Użytkownik musi również dostępu do pliku.</span><span class="sxs-lookup"><span data-stu-id="b10d1-118">The user also needs access to the file.</span></span> <span data-ttu-id="b10d1-119">Aby uzyskać więcej informacji, zobacz [Przegląd technologii ACL](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b10d1-119">For more information, see [ACL Technology Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b10d1-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b10d1-120">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [<span data-ttu-id="b10d1-121">SaveFileDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="b10d1-121">SaveFileDialog Component</span></span>](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)
- [<span data-ttu-id="b10d1-122">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="b10d1-122">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
