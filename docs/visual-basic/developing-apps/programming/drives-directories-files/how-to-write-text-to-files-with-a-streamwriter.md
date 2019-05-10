---
title: 'Instrukcje: Zapisywanie tekstu do plików za pomocą StreamWriter w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 3b4f74836b32fea0e5c24fd4500581f17e39cd4c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623130"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="1ff3b-102">Instrukcje: Zapisywanie tekstu do plików za pomocą StreamWriter w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ff3b-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>
<span data-ttu-id="1ff3b-103">W tym przykładzie otwiera <xref:System.IO.StreamWriter> obiekt z `My.Computer.FileSystem.OpenTextFileWriter` metody i używa go zapisać ciąg do pliku tekstowego z <xref:System.IO.TextWriter.WriteLine%2A> metody <xref:System.IO.StreamWriter> klasy.</span><span class="sxs-lookup"><span data-stu-id="1ff3b-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ff3b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ff3b-104">Example</span></span>  
 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1ff3b-105">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="1ff3b-105">Robust Programming</span></span>  
 <span data-ttu-id="1ff3b-106">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="1ff3b-106">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="1ff3b-107">Plik istnieje i jest tylko do odczytu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="1ff3b-107">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="1ff3b-108">Dysk jest pełny (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="1ff3b-108">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="1ff3b-109">Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="1ff3b-109">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1ff3b-110">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="1ff3b-110">.NET Framework Security</span></span>  
 <span data-ttu-id="1ff3b-111">W tym przykładzie tworzy nowy plik, jeśli go jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="1ff3b-111">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="1ff3b-112">Jeśli aplikacja musi utworzyć plik, ta aplikacja musi mieć `Create` dostępu do folderu.</span><span class="sxs-lookup"><span data-stu-id="1ff3b-112">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="1ff3b-113">Jeśli plik już istnieje, aplikacja potrzebuje tylko `Write` dostępu, mniejsze uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="1ff3b-113">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="1ff3b-114">Jeśli to możliwe, bezpieczniej jest tworzyć plik podczas wdrożenia i udzielić `Read` dostępu do pojedynczego pliku, zamiast `Create` dostępu do folderu.</span><span class="sxs-lookup"><span data-stu-id="1ff3b-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ff3b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ff3b-115">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [<span data-ttu-id="1ff3b-116">Instrukcje: Odczyt z plików tekstowych</span><span class="sxs-lookup"><span data-stu-id="1ff3b-116">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
- [<span data-ttu-id="1ff3b-117">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="1ff3b-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
