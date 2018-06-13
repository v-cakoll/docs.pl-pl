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
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>Porady: pobieranie zawartości katalogu Moje dokumenty w Visual Basic
<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Obiekt może służyć do odczytu z wielu **wszyscy użytkownicy** katalogi, takich jak **Moje dokumenty** lub **pulpitu**.  
  
### <a name="to-read-from-the-my-documents-folder"></a>Można odczytać z folderu Moje dokumenty  
  
-   Użyj `ReadAllText` metody można odczytać tekstu z poszczególnych plików w określonym katalogu. Poniższy kod określa katalogów i plików, a następnie używa `ReadAllText` je odczytać w ciągu o nazwie `patients`.  
  
     [!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
