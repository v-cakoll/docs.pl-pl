---
title: 'Instrukcje: Pobieranie zawartości katalogu Moje dokumenty w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: fe98d3e92726dc6c4ed576ef989d968852c846d6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770298"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="4a1fb-102">Instrukcje: Pobieranie zawartości katalogu Moje dokumenty w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a1fb-102">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="4a1fb-103"><xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Obiekt może służyć do odczytu z wielu **wszyscy użytkownicy** katalogi, takich jak **Moje dokumenty** lub **pulpitu**.</span><span class="sxs-lookup"><span data-stu-id="4a1fb-103">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="4a1fb-104">Do odczytywania z folderu Moje dokumenty</span><span class="sxs-lookup"><span data-stu-id="4a1fb-104">To read from the My Documents folder</span></span>  
  
-   <span data-ttu-id="4a1fb-105">Użyj `ReadAllText` metodę w celu odczytania tekst z każdego pliku w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4a1fb-105">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="4a1fb-106">Poniższy kod określa katalogów i plików, a następnie używa `ReadAllText` do ich czytania do parametrów o nazwie `patients`.</span><span class="sxs-lookup"><span data-stu-id="4a1fb-106">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="4a1fb-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a1fb-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
