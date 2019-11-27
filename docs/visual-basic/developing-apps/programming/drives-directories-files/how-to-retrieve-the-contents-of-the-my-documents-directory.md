---
title: 'Porady: pobieranie zawartości katalogu Moje dokumenty'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: cf4470020507c581999b9d72602ddb6e3e76ed74
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334537"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="42b31-102">Porady: pobieranie zawartości katalogu Moje dokumenty w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42b31-102">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>

<span data-ttu-id="42b31-103">Obiekt <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> może służyć do odczytu z wielu katalogów **użytkowników** , takich jak **Moje dokumenty** lub **pulpit**.</span><span class="sxs-lookup"><span data-stu-id="42b31-103">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="42b31-104">Aby czytać z folderu Moje dokumenty</span><span class="sxs-lookup"><span data-stu-id="42b31-104">To read from the My Documents folder</span></span>  
  
- <span data-ttu-id="42b31-105">Użyj metody `ReadAllText`, aby odczytać tekst z każdego pliku w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="42b31-105">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="42b31-106">Poniższy kod określa katalog i plik, a następnie używa `ReadAllText` do odczytywania ich do ciągu o nazwie `patients`.</span><span class="sxs-lookup"><span data-stu-id="42b31-106">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="42b31-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42b31-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
