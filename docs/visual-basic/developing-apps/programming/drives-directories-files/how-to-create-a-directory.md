---
title: 'Porady: tworzenie katalogu w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2e4cd94113d77b2f4ff8127c80174107966ef360
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-directory-in-visual-basic"></a><span data-ttu-id="fd43b-102">Porady: tworzenie katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fd43b-102">How to: Create a Directory in Visual Basic</span></span>
<span data-ttu-id="fd43b-103">Użyj `CreateDirectory` metody `My.Computer.FileSystem` obiekt do tworzenia katalogów.</span><span class="sxs-lookup"><span data-stu-id="fd43b-103">Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.</span></span>  
  
 <span data-ttu-id="fd43b-104">Jeśli katalog już istnieje, nie jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="fd43b-104">If the directory already exists, no exception is thrown.</span></span>  
  
### <a name="to-create-a-directory"></a><span data-ttu-id="fd43b-105">Aby utworzyć katalog</span><span class="sxs-lookup"><span data-stu-id="fd43b-105">To create a directory</span></span>  
  
-   <span data-ttu-id="fd43b-106">Użyj `CreateDirectory` metody określić pełną ścieżkę lokalizacji, w którym ma zostać utworzony katalog.</span><span class="sxs-lookup"><span data-stu-id="fd43b-106">Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created.</span></span> <span data-ttu-id="fd43b-107">To przykładowe polecenie tworzy katalog `NewDirectory` w `C:\Documents and Settings\All Users\Documents`.</span><span class="sxs-lookup"><span data-stu-id="fd43b-107">This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="fd43b-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="fd43b-108">Robust Programming</span></span>  
 <span data-ttu-id="fd43b-109">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="fd43b-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="fd43b-110">Nazwa katalogu jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="fd43b-110">The directory name is malformed.</span></span> <span data-ttu-id="fd43b-111">Na przykład zawiera niedozwolone znaki lub jest tylko znak odstępu (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="fd43b-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="fd43b-112">Katalog ma zostać utworzony w katalogu nadrzędnym jest tylko do odczytu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="fd43b-112">The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="fd43b-113">Nazwa katalogu jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="fd43b-113">The directory name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="fd43b-114">Nazwa katalogu jest zbyt długa (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="fd43b-114">The directory name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="fd43b-115">Nazwa katalogu jest dwukropka ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="fd43b-115">The directory name is a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="fd43b-116">Użytkownik nie ma uprawnień do tworzenia katalogu (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="fd43b-116">The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="fd43b-117">Użytkownik nie ma uprawnień w przypadku zaufania częściowego (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="fd43b-117">The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd43b-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd43b-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>  
 [<span data-ttu-id="fd43b-119">Tworzenie, usuwanie i przenoszenie plików i katalogów</span><span class="sxs-lookup"><span data-stu-id="fd43b-119">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
