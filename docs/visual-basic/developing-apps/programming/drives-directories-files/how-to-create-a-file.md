---
title: 'Instrukcje: Utwórz plik w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: a05e73a2096c82c9299e4483bbaf69e560fc2e45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038067"
---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="f8c3e-102">Instrukcje: Utwórz plik w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f8c3e-102">How to: Create a File in Visual Basic</span></span>
<span data-ttu-id="f8c3e-103">W tym przykładzie tworzy pusty plik tekstowy w określonej ścieżki przy użyciu <xref:System.IO.File.Create%2A> method in Class metoda <xref:System.IO.File> klasy.</span><span class="sxs-lookup"><span data-stu-id="f8c3e-103">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8c3e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8c3e-104">Example</span></span>  
 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f8c3e-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f8c3e-105">Compiling the Code</span></span>  
 <span data-ttu-id="f8c3e-106">Użyj `file` zmiennej można zapisać do pliku.</span><span class="sxs-lookup"><span data-stu-id="f8c3e-106">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f8c3e-107">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="f8c3e-107">Robust Programming</span></span>  
 <span data-ttu-id="f8c3e-108">Jeśli plik już istnieje, zostanie zastąpiona.</span><span class="sxs-lookup"><span data-stu-id="f8c3e-108">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="f8c3e-109">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="f8c3e-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="f8c3e-110">Nazwa ścieżki jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="f8c3e-110">The path name is malformed.</span></span> <span data-ttu-id="f8c3e-111">Na przykład zawiera niedozwolone znaki lub jest tylko spacją (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="f8c3e-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="f8c3e-112">Ścieżka jest tylko do odczytu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="f8c3e-112">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="f8c3e-113">Nazwa ścieżki jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="f8c3e-113">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="f8c3e-114">Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="f8c3e-114">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="f8c3e-115">Ścieżka jest nieprawidłowa (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="f8c3e-115">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="f8c3e-116">Ścieżka jest tylko dwukropek ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="f8c3e-116">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f8c3e-117">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="f8c3e-117">.NET Framework Security</span></span>  
 <span data-ttu-id="f8c3e-118">A <xref:System.Security.SecurityException> mogą być generowane w środowisku częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="f8c3e-118">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="f8c3e-119">Wywołanie <xref:System.IO.File.Create%2A> metoda wymaga <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="f8c3e-119">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="f8c3e-120"><xref:System.UnauthorizedAccessException> Jest generowany, jeśli użytkownik nie ma uprawnień do utworzenia pliku.</span><span class="sxs-lookup"><span data-stu-id="f8c3e-120">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8c3e-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8c3e-121">See also</span></span>

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [<span data-ttu-id="f8c3e-122">Używanie bibliotek pochodzących z częściowo zaufanego kodu</span><span class="sxs-lookup"><span data-stu-id="f8c3e-122">Using Libraries from Partially Trusted Code</span></span>](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [<span data-ttu-id="f8c3e-123">Podstawy zabezpieczeń dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="f8c3e-123">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
