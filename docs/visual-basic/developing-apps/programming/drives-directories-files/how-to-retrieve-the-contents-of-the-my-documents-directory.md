---
title: 'Instrukcje: Pobieranie zawartości katalogu Moje dokumenty w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: 6d4e0bc7d300b2553d5286600cc65b7c494359b9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964187"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>Instrukcje: Pobieranie zawartości katalogu Moje dokumenty w języku Visual Basic
<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Obiekt może służyć do odczytu z wielu **wszyscy użytkownicy** katalogi, takich jak **Moje dokumenty** lub **pulpitu**.  
  
### <a name="to-read-from-the-my-documents-folder"></a>Do odczytywania z folderu Moje dokumenty  
  
-   Użyj `ReadAllText` metodę w celu odczytania tekst z każdego pliku w określonym katalogu. Poniższy kod określa katalogów i plików, a następnie używa `ReadAllText` do ich czytania do parametrów o nazwie `patients`.  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
