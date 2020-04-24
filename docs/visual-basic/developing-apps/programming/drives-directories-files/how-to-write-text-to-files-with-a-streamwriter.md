---
title: 'Porady: zapisywanie tekstu do plików za pomocą StreamWriter'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 869e29263abcdd8525b2c372c7bb466e3e21fc65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334497"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="909b2-102">Porady: zapisywanie tekstu do plików za pomocą StreamWriter w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="909b2-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>

<span data-ttu-id="909b2-103"><xref:System.IO.StreamWriter> Ten przykład otwiera obiekt `My.Computer.FileSystem.OpenTextFileWriter` z metodą i używa go do pisania ciągu do pliku tekstowego z <xref:System.IO.TextWriter.WriteLine%2A> metodą <xref:System.IO.StreamWriter> klasy.</span><span class="sxs-lookup"><span data-stu-id="909b2-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="909b2-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="909b2-104">Example</span></span>  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a><span data-ttu-id="909b2-105">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="909b2-105">Robust Programming</span></span>  

 <span data-ttu-id="909b2-106">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="909b2-106">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="909b2-107">Plik istnieje i jest tylko do odczytu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="909b2-107">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="909b2-108">Dysk jest pełny (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="909b2-108">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="909b2-109">Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="909b2-109">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="909b2-110">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="909b2-110">.NET Framework Security</span></span>  

 <span data-ttu-id="909b2-111">Ten przykład tworzy nowy plik, jeśli plik jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="909b2-111">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="909b2-112">Jeśli aplikacja musi utworzyć plik, aplikacja musi `Create` mieć dostęp do tego folderu.</span><span class="sxs-lookup"><span data-stu-id="909b2-112">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="909b2-113">Jeśli plik już istnieje, aplikacja wymaga tylko `Write` dostępu, ale ma mniejsze uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="909b2-113">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="909b2-114">Jeśli to możliwe, bezpieczniejsze jest tworzenie pliku podczas wdrażania i udzielanie `Read` dostępu do pojedynczego pliku, a nie `Create` dostęp do folderu.</span><span class="sxs-lookup"><span data-stu-id="909b2-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="909b2-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="909b2-115">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [<span data-ttu-id="909b2-116">Instrukcje: odczyt z plików tekstowych</span><span class="sxs-lookup"><span data-stu-id="909b2-116">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
- [<span data-ttu-id="909b2-117">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="909b2-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
