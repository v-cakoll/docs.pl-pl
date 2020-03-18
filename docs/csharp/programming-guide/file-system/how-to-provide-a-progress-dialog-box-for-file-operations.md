---
title: Jak udostępnić okno dialogowe postępu dla operacji plików - Przewodnik po programowaniu c#
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 30ab84054d26f5b32a3f042a8d35d5ef1211d928
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705135"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Jak udostępnić okno dialogowe postępu dla operacji plików (Przewodnik programowania C#)
Można podać standardowe okno dialogowe, które pokazuje postęp <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> operacji na <xref:Microsoft.VisualBasic?displayProperty=nameWithType> plikach w systemie Windows, jeśli używasz metody w obszarze nazw.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Aby dodać odwołanie w programie Visual Studio  
  
1. Na pasku menu wybierz pozycję **Projekt**, **Dodaj odwołanie**.  
  
     Pojawi się okno **dialogowe Menedżera odwołań.**  
  
2. W obszarze **Zestawy** wybierz **pozycję Framework,** jeśli nie jest ona jeszcze wybrana.  
  
3. Na liście nazw zaznacz pole wyboru **Microsoft.VisualBasic,** a następnie wybierz przycisk **OK,** aby zamknąć okno dialogowe.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kopiuje `sourcePath` katalog, który `destinationPath` określa się do katalogu, który określa. Ten kod zawiera również standardowe okno dialogowe, które pokazuje szacowany czas pozostały do zakończenia operacji.  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a>Zobacz też

- [System plików i rejestr (Przewodnik programowania w języku C#)](./index.md)
