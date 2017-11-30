---
title: 'Porady: tworzenie pliku w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96e6785086f8c97f983c6dcd6fd713c01e34e258
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="41ece-102">Porady: tworzenie pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="41ece-102">How to: Create a File in Visual Basic</span></span>
<span data-ttu-id="41ece-103">Pusty plik tekstowy w tym przykładzie jest tworzona przy użyciu określonej ścieżki <xref:System.IO.File.Create%2A> metoda <xref:System.IO.File> klasy.</span><span class="sxs-lookup"><span data-stu-id="41ece-103">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41ece-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="41ece-104">Example</span></span>  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="41ece-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="41ece-105">Compiling the Code</span></span>  
 <span data-ttu-id="41ece-106">Użyj `file` zmienną do zapisu w pliku.</span><span class="sxs-lookup"><span data-stu-id="41ece-106">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="41ece-107">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="41ece-107">Robust Programming</span></span>  
 <span data-ttu-id="41ece-108">Jeśli plik już istnieje, zostanie zastąpiony.</span><span class="sxs-lookup"><span data-stu-id="41ece-108">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="41ece-109">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="41ece-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="41ece-110">Nazwa ścieżki jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="41ece-110">The path name is malformed.</span></span> <span data-ttu-id="41ece-111">Na przykład zawiera niedozwolone znaki lub jest tylko znak odstępu (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="41ece-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="41ece-112">Ścieżka jest tylko do odczytu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="41ece-112">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="41ece-113">Nazwa ścieżki jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="41ece-113">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="41ece-114">Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="41ece-114">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="41ece-115">Ścieżka jest nieprawidłowa (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="41ece-115">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="41ece-116">Ścieżka jest tylko dwukropka ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="41ece-116">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="41ece-117">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="41ece-117">.NET Framework Security</span></span>  
 <span data-ttu-id="41ece-118">A <xref:System.Security.SecurityException> może zostać zgłoszony w częściowo zaufanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="41ece-118">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="41ece-119">Wywołanie <xref:System.IO.File.Create%2A> metoda wymaga <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="41ece-119">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="41ece-120"><xref:System.UnauthorizedAccessException> Jest generowany, jeśli użytkownik nie ma uprawnień do tworzenia pliku.</span><span class="sxs-lookup"><span data-stu-id="41ece-120">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41ece-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41ece-121">See Also</span></span>  
 <xref:System.IO>  
 <xref:System.IO.File.Create%2A>  
 [<span data-ttu-id="41ece-122">Używanie bibliotek pochodzących z częściowo zaufanego kodu</span><span class="sxs-lookup"><span data-stu-id="41ece-122">Using Libraries from Partially Trusted Code</span></span>](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)  
 [<span data-ttu-id="41ece-123">Podstawy zabezpieczeń dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="41ece-123">Code Access Security Basics</span></span>](https://msdn.microsoft.com/library/33tceax8)
