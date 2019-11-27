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
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>Porady: pobieranie zawartości katalogu Moje dokumenty w Visual Basic

Obiekt <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> może służyć do odczytu z wielu katalogów **użytkowników** , takich jak **Moje dokumenty** lub **pulpit**.  
  
### <a name="to-read-from-the-my-documents-folder"></a>Aby czytać z folderu Moje dokumenty  
  
- Użyj metody `ReadAllText`, aby odczytać tekst z każdego pliku w określonym katalogu. Poniższy kod określa katalog i plik, a następnie używa `ReadAllText` do odczytywania ich do ciągu o nazwie `patients`.  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
