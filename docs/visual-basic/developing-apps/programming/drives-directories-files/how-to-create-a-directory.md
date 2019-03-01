---
title: 'Instrukcje: Utwórz katalog w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: a7ba9ea1e7762b0a4a6660339c331fa6cdeb7858
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976905"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a><span data-ttu-id="600a0-102">Instrukcje: Utwórz katalog w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="600a0-102">How to: Create a Directory in Visual Basic</span></span>
<span data-ttu-id="600a0-103">Użyj `CreateDirectory` metody `My.Computer.FileSystem` obiekt do tworzenia katalogów.</span><span class="sxs-lookup"><span data-stu-id="600a0-103">Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.</span></span>  
  
 <span data-ttu-id="600a0-104">Jeśli katalog już istnieje, jest zgłaszany żaden wyjątek.</span><span class="sxs-lookup"><span data-stu-id="600a0-104">If the directory already exists, no exception is thrown.</span></span>  
  
### <a name="to-create-a-directory"></a><span data-ttu-id="600a0-105">Aby utworzyć katalog</span><span class="sxs-lookup"><span data-stu-id="600a0-105">To create a directory</span></span>  
  
-   <span data-ttu-id="600a0-106">Użyj `CreateDirectory` metody, podając pełną ścieżkę lokalizacji, w którym można utworzyć katalogu.</span><span class="sxs-lookup"><span data-stu-id="600a0-106">Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created.</span></span> <span data-ttu-id="600a0-107">W tym przykładzie tworzy katalog `NewDirectory` w `C:\Documents and Settings\All Users\Documents`.</span><span class="sxs-lookup"><span data-stu-id="600a0-107">This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="600a0-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="600a0-108">Robust Programming</span></span>  
 <span data-ttu-id="600a0-109">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="600a0-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="600a0-110">Nazwa katalogu jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="600a0-110">The directory name is malformed.</span></span> <span data-ttu-id="600a0-111">Na przykład zawiera niedozwolone znaki lub jest tylko spacją (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="600a0-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="600a0-112">Katalog, który ma zostać utworzony w katalogu nadrzędnym jest tylko do odczytu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="600a0-112">The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="600a0-113">Nazwa katalogu jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="600a0-113">The directory name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="600a0-114">Nazwa katalogu jest zbyt długa (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="600a0-114">The directory name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="600a0-115">Nazwa katalogu jest dwukropek ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="600a0-115">The directory name is a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="600a0-116">Użytkownik nie ma uprawnień do tworzenia katalogu (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="600a0-116">The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="600a0-117">Użytkownik nie ma uprawnienia w sytuacjach częściowego zaufania (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="600a0-117">The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="600a0-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="600a0-118">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [<span data-ttu-id="600a0-119">Tworzenie, usuwanie i przenoszenie plików i katalogów</span><span class="sxs-lookup"><span data-stu-id="600a0-119">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
