---
title: 'Porady: zapisywanie tekstu do plików w katalogu Moje dokumenty w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: 894458ad6d69b8bb2836518b90723703733208b6
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264522"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="42a3d-102">Porady: zapisywanie tekstu do plików w katalogu Moje dokumenty w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42a3d-102">How to: Write Text to Files in the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="42a3d-103">`My.Computer.FileSystem.SpecialDirectories` Obiekt umożliwia dostęp do specjalnych katalogi, takich jak **Moje dokumenty** katalogu.</span><span class="sxs-lookup"><span data-stu-id="42a3d-103">The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="42a3d-104">Procedura</span><span class="sxs-lookup"><span data-stu-id="42a3d-104">Procedure</span></span>  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a><span data-ttu-id="42a3d-105">Aby zapisać nowych plików tekstowych w katalogu Moje dokumenty</span><span class="sxs-lookup"><span data-stu-id="42a3d-105">To write new text files in the My Documents directory</span></span>  
  
1.  <span data-ttu-id="42a3d-106">Użyj `My.Computer.FileSystem.SpecialDirectories.MyDocuments` właściwość, aby podać ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="42a3d-106">Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.</span></span>  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  <span data-ttu-id="42a3d-107">Użyj `WriteAllText` metodę, aby wpisać tekst w określonym pliku.</span><span class="sxs-lookup"><span data-stu-id="42a3d-107">Use the `WriteAllText` method to write text to the specified file.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="42a3d-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="42a3d-108">Example</span></span>  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="42a3d-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="42a3d-109">Compiling the Code</span></span>  
 <span data-ttu-id="42a3d-110">Zastąp `test.txt` nazwę pliku, o których mają zostać zapisane.</span><span class="sxs-lookup"><span data-stu-id="42a3d-110">Replace `test.txt` with the name of the file you want to write to.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="42a3d-111">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="42a3d-111">Robust Programming</span></span>  
 <span data-ttu-id="42a3d-112">Ten kod ponownie zgłasza wyjątki, które mogą wystąpić podczas zapisywania w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="42a3d-112">This code rethrows all the exceptions that may occur when writing text to the file.</span></span> <span data-ttu-id="42a3d-113">Można zmniejszyć prawdopodobieństwo wyjątków za pomocą kontrolek formularzy Windows Forms, takich jak [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) i [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) składników, które ograniczyć wybór użytkownika z nazwami plików prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="42a3d-113">You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) and the [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) components that limit the user choices to valid file names.</span></span> <span data-ttu-id="42a3d-114">Za pomocą tych kontrolek nie jest niezawodne, jednak.</span><span class="sxs-lookup"><span data-stu-id="42a3d-114">Using these controls is not foolproof, however.</span></span> <span data-ttu-id="42a3d-115">System plików można przełączać się między czasie użytkownik wybierze plik i czas, jaki kod jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="42a3d-115">The file system can change between the time the user selects a file and the time that the code executes.</span></span> <span data-ttu-id="42a3d-116">Obsługa wyjątków jest niemal zawsze z pracy z plikami.</span><span class="sxs-lookup"><span data-stu-id="42a3d-116">Exception handling is therefore nearly always necessary when with working with files.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="42a3d-117">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="42a3d-117">.NET Framework Security</span></span>  
 <span data-ttu-id="42a3d-118">Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek ze względu na niewystarczające uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="42a3d-118">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="42a3d-119">Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="42a3d-119">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="42a3d-120">Ten przykład tworzy nowy plik.</span><span class="sxs-lookup"><span data-stu-id="42a3d-120">This example creates a new file.</span></span> <span data-ttu-id="42a3d-121">Jeśli aplikacja musi utworzyć plik, ta aplikacja musi mieć uprawnienia do tworzenia folderu.</span><span class="sxs-lookup"><span data-stu-id="42a3d-121">If an application needs to create a file, that application needs Create permission for the folder.</span></span> <span data-ttu-id="42a3d-122">Uprawnienia są ustawiane przy użyciu list kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="42a3d-122">Permissions are set using access control lists.</span></span> <span data-ttu-id="42a3d-123">Jeśli plik już istnieje, aplikacja musi uprawnienie, mniejsze uprawnienia tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="42a3d-123">If the file already exists, the application needs only Write permission, a lesser privilege.</span></span> <span data-ttu-id="42a3d-124">W przypadku, gdy jest to możliwe, bezpieczniej jest tworzyć plik podczas wdrożenia i udzielić uprawnień do odczytu do pojedynczego pliku, a nie do przyznawania uprawnień Tworzenie folderu.</span><span class="sxs-lookup"><span data-stu-id="42a3d-124">Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder.</span></span> <span data-ttu-id="42a3d-125">Ponadto jest bardziej bezpieczne, można zapisać danych do folderów użytkowników niż do folderu głównego lub **Program Files** folderu.</span><span class="sxs-lookup"><span data-stu-id="42a3d-125">Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder.</span></span> <span data-ttu-id="42a3d-126">Aby uzyskać więcej informacji, zobacz [Przegląd technologii ACL](https://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).</span><span class="sxs-lookup"><span data-stu-id="42a3d-126">For more information, see [ACL Technology Overview](https://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42a3d-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42a3d-127">See Also</span></span>  
 <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
