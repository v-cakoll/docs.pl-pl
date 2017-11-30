---
title: "Porady: pobieranie zawartości katalogu Moje dokumenty w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3456984a697439a8c2ab7fb88f9f0f32d10cb0e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="4ccdd-102">Porady: pobieranie zawartości katalogu Moje dokumenty w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4ccdd-102">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="4ccdd-103"><xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Obiekt może służyć do odczytu z wielu **wszyscy użytkownicy** katalogi, takich jak **Moje dokumenty** lub **pulpitu**.</span><span class="sxs-lookup"><span data-stu-id="4ccdd-103">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="4ccdd-104">Można odczytać z folderu Moje dokumenty</span><span class="sxs-lookup"><span data-stu-id="4ccdd-104">To read from the My Documents folder</span></span>  
  
-   <span data-ttu-id="4ccdd-105">Użyj `ReadAllText` metody można odczytać tekstu z poszczególnych plików w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4ccdd-105">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="4ccdd-106">Poniższy kod określa katalogów i plików, a następnie używa `ReadAllText` je odczytać w ciągu o nazwie `patients`.</span><span class="sxs-lookup"><span data-stu-id="4ccdd-106">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4ccdd-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ccdd-107">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
