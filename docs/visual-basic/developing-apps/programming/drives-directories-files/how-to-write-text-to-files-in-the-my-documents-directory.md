---
title: "Porady: zapisywanie tekstu do plików w katalogu Moje dokumenty w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4c8970994f3ac4e34dfdf4af3e28100e2d009855
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="1d771-102">Porady: zapisywanie tekstu do plików w katalogu Moje dokumenty w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1d771-102">How to: Write Text to Files in the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="1d771-103">`My.Computer.FileSystem.SpecialDirectories` Obiekt umożliwia dostęp do specjalnych katalogi, takich jak **Moje dokumenty** katalogu.</span><span class="sxs-lookup"><span data-stu-id="1d771-103">The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="1d771-104">Procedura</span><span class="sxs-lookup"><span data-stu-id="1d771-104">Procedure</span></span>  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a><span data-ttu-id="1d771-105">Aby zapisać nowe pliki tekstowe w katalogu Moje dokumenty</span><span class="sxs-lookup"><span data-stu-id="1d771-105">To write new text files in the My Documents directory</span></span>  
  
1.  <span data-ttu-id="1d771-106">Użyj `My.Computer.FileSystem.SpecialDirectories.MyDocuments` właściwość, aby podać ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="1d771-106">Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.</span></span>  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  <span data-ttu-id="1d771-107">Użyj `WriteAllText` metodę zapisywanie tekstu do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="1d771-107">Use the `WriteAllText` method to write text to the specified file.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="1d771-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d771-108">Example</span></span>  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1d771-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1d771-109">Compiling the Code</span></span>  
 <span data-ttu-id="1d771-110">Zastąp `test.txt` z nazwą pliku, który chcesz zapisać.</span><span class="sxs-lookup"><span data-stu-id="1d771-110">Replace `test.txt` with the name of the file you want to write to.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1d771-111">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="1d771-111">Robust Programming</span></span>  
 <span data-ttu-id="1d771-112">Ten kod ponownie zgłasza wszystkie wyjątki, które mogą wystąpić podczas zapisywania do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="1d771-112">This code rethrows all the exceptions that may occur when writing text to the file.</span></span> <span data-ttu-id="1d771-113">Można zmniejszyć prawdopodobieństwo wyjątków za pomocą formantów formularzy systemu Windows, takich jak [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) i [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) składników, które ograniczyć wybór użytkownika prawidłowe nazwy.</span><span class="sxs-lookup"><span data-stu-id="1d771-113">You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) and the [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) components that limit the user choices to valid file names.</span></span> <span data-ttu-id="1d771-114">Za pomocą tych kontrolek nie jest niezawodna, jednak.</span><span class="sxs-lookup"><span data-stu-id="1d771-114">Using these controls is not foolproof, however.</span></span> <span data-ttu-id="1d771-115">System plików, można zmienić między czasem użytkownik wybierze pliku i czasu, która wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="1d771-115">The file system can change between the time the user selects a file and the time that the code executes.</span></span> <span data-ttu-id="1d771-116">Obsługa wyjątków jest niemal zawsze gdy o pracy z plikami.</span><span class="sxs-lookup"><span data-stu-id="1d771-116">Exception handling is therefore nearly always necessary when with working with files.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1d771-117">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="1d771-117">.NET Framework Security</span></span>  
 <span data-ttu-id="1d771-118">Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek, ze względu na niewystarczające uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="1d771-118">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="1d771-119">Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](https://msdn.microsoft.com/library/33tceax8).</span><span class="sxs-lookup"><span data-stu-id="1d771-119">For more information, see [Code Access Security Basics](https://msdn.microsoft.com/library/33tceax8).</span></span>  
  
 <span data-ttu-id="1d771-120">W tym przykładzie tworzy nowy plik.</span><span class="sxs-lookup"><span data-stu-id="1d771-120">This example creates a new file.</span></span> <span data-ttu-id="1d771-121">Jeśli aplikacja musi utworzyć plik, tego aplikacja wymaga uprawnień tworzenia folderu.</span><span class="sxs-lookup"><span data-stu-id="1d771-121">If an application needs to create a file, that application needs Create permission for the folder.</span></span> <span data-ttu-id="1d771-122">Uprawnienia są ustawiane przy użyciu list kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="1d771-122">Permissions are set using access control lists.</span></span> <span data-ttu-id="1d771-123">Jeśli plik już istnieje, aplikacja musi uprawnienie, niższego poziomu uprawnień tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="1d771-123">If the file already exists, the application needs only Write permission, a lesser privilege.</span></span> <span data-ttu-id="1d771-124">Jeśli to możliwe, jest bardziej bezpieczne tworzenie pliku podczas wdrażania i przyznać uprawnienia odczytu do jednego pliku, a nie do przyznawania uprawnień tworzenia folderu.</span><span class="sxs-lookup"><span data-stu-id="1d771-124">Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder.</span></span> <span data-ttu-id="1d771-125">Ponadto jest bardziej bezpieczne można zapisać danych do folderów użytkownika niż do folderu głównego lub **Program Files** folderu.</span><span class="sxs-lookup"><span data-stu-id="1d771-125">Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder.</span></span> <span data-ttu-id="1d771-126">Aby uzyskać więcej informacji, zobacz [omówienie technologii ACL](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045).</span><span class="sxs-lookup"><span data-stu-id="1d771-126">For more information, see [ACL Technology Overview](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d771-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d771-127">See Also</span></span>  
 <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
