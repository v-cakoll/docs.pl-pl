---
title: 'Porady: pobieranie zawartości katalogu Moje dokumenty w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: 1d0536c65949dab7d431f3a4cb7b3293bddb7008
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583230"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="16557-102">Porady: pobieranie zawartości katalogu Moje dokumenty w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16557-102">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="16557-103"><xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Obiekt może służyć do odczytu z wielu **wszyscy użytkownicy** katalogi, takich jak **Moje dokumenty** lub **pulpitu**.</span><span class="sxs-lookup"><span data-stu-id="16557-103">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="16557-104">Można odczytać z folderu Moje dokumenty</span><span class="sxs-lookup"><span data-stu-id="16557-104">To read from the My Documents folder</span></span>  
  
-   <span data-ttu-id="16557-105">Użyj `ReadAllText` metody można odczytać tekstu z poszczególnych plików w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="16557-105">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="16557-106">Poniższy kod określa katalogów i plików, a następnie używa `ReadAllText` je odczytać w ciągu o nazwie `patients`.</span><span class="sxs-lookup"><span data-stu-id="16557-106">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="16557-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16557-107">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
