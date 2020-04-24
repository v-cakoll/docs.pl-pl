---
title: 'Porady: zapisywanie tekstu do plików w katalogu Moje dokumenty'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: bc62f2bc63a2ea185b8ea4c8d271dd28d347d6f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334522"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="eb161-102">Porady: zapisywanie tekstu do plików w katalogu Moje dokumenty w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb161-102">How to: Write Text to Files in the My Documents Directory in Visual Basic</span></span>

<span data-ttu-id="eb161-103">`My.Computer.FileSystem.SpecialDirectories` Obiekt umożliwia dostęp do katalogów specjalnych, takich jak katalog **WebDocuments** .</span><span class="sxs-lookup"><span data-stu-id="eb161-103">The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="eb161-104">Procedura</span><span class="sxs-lookup"><span data-stu-id="eb161-104">Procedure</span></span>  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a><span data-ttu-id="eb161-105">Aby napisać nowe pliki tekstowe w katalogu Moje dokumenty</span><span class="sxs-lookup"><span data-stu-id="eb161-105">To write new text files in the My Documents directory</span></span>  
  
1. <span data-ttu-id="eb161-106">Użyj `My.Computer.FileSystem.SpecialDirectories.MyDocuments` właściwości, aby podać ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="eb161-106">Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.</span></span>  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2. <span data-ttu-id="eb161-107">Użyj metody `WriteAllText` , aby zapisać tekst do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="eb161-107">Use the `WriteAllText` method to write text to the specified file.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="eb161-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="eb161-108">Example</span></span>  

 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="eb161-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="eb161-109">Compiling the Code</span></span>  

 <span data-ttu-id="eb161-110">Zamień `test.txt` na nazwę pliku, do którego chcesz pisać.</span><span class="sxs-lookup"><span data-stu-id="eb161-110">Replace `test.txt` with the name of the file you want to write to.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="eb161-111">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="eb161-111">Robust Programming</span></span>  

 <span data-ttu-id="eb161-112">Ten kod ponownie generuje wszystkie wyjątki, które mogą wystąpić podczas zapisywania tekstu do pliku.</span><span class="sxs-lookup"><span data-stu-id="eb161-112">This code rethrows all the exceptions that may occur when writing text to the file.</span></span> <span data-ttu-id="eb161-113">Możliwe jest zmniejszenie prawdopodobieństwa wyjątków za pomocą kontrolek Windows Forms, takich jak [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) i składniki [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) , które ograniczają Opcje użytkownika do prawidłowych nazw plików.</span><span class="sxs-lookup"><span data-stu-id="eb161-113">You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) and the [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) components that limit the user choices to valid file names.</span></span> <span data-ttu-id="eb161-114">Korzystanie z tych kontrolek nie jest jednak foolproof.</span><span class="sxs-lookup"><span data-stu-id="eb161-114">Using these controls is not foolproof, however.</span></span> <span data-ttu-id="eb161-115">System plików można zmienić między czasem, gdy użytkownik wybierze plik i czas wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="eb161-115">The file system can change between the time the user selects a file and the time that the code executes.</span></span> <span data-ttu-id="eb161-116">Obsługa wyjątków jest w związku z tym niemal zawsze niepotrzebna podczas pracy z plikami.</span><span class="sxs-lookup"><span data-stu-id="eb161-116">Exception handling is therefore nearly always necessary when with working with files.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="eb161-117">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="eb161-117">.NET Framework Security</span></span>  

 <span data-ttu-id="eb161-118">Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek z powodu niewystarczających uprawnień.</span><span class="sxs-lookup"><span data-stu-id="eb161-118">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="eb161-119">Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="eb161-119">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="eb161-120">Ten przykład tworzy nowy plik.</span><span class="sxs-lookup"><span data-stu-id="eb161-120">This example creates a new file.</span></span> <span data-ttu-id="eb161-121">Jeśli aplikacja musi utworzyć plik, aplikacja musi mieć uprawnienie Tworzenie dla tego folderu.</span><span class="sxs-lookup"><span data-stu-id="eb161-121">If an application needs to create a file, that application needs Create permission for the folder.</span></span> <span data-ttu-id="eb161-122">Uprawnienia są ustawiane przy użyciu list kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="eb161-122">Permissions are set using access control lists.</span></span> <span data-ttu-id="eb161-123">Jeśli plik już istnieje, aplikacja wymaga tylko uprawnienia Zapis, ale ma mniejsze uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="eb161-123">If the file already exists, the application needs only Write permission, a lesser privilege.</span></span> <span data-ttu-id="eb161-124">Jeśli to możliwe, bezpieczniejsze jest tworzenie pliku podczas wdrażania i udzielanie uprawnień do odczytu tylko do jednego pliku, a nie do przyznawania uprawnień do tworzenia folderów.</span><span class="sxs-lookup"><span data-stu-id="eb161-124">Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder.</span></span> <span data-ttu-id="eb161-125">Ponadto bardziej bezpieczne jest zapisanie danych do folderów użytkowników niż folder główny lub folder **Program Files** .</span><span class="sxs-lookup"><span data-stu-id="eb161-125">Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder.</span></span> <span data-ttu-id="eb161-126">Aby uzyskać więcej informacji, zobacz [Omówienie technologii list ACL](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="eb161-126">For more information, see [ACL Technology Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb161-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb161-127">See also</span></span>

- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
