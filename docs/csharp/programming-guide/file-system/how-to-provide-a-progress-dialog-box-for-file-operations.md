---
title: 'Porady: dostarczanie okna dialogowego postępu dla operacji na plikach (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: f80bbc94579c58210769800ad8bf74bc60878af5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44200818"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Porady: dostarczanie okna dialogowego postępu dla operacji na plikach (Przewodnik programowania w języku C#)
Można zapewnić standardowe okno dialogowe, które wyświetla postęp w operacjach plików w Windows, jeśli używasz <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in Class metoda <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Aby dodać odwołanie w Visual Studio  
  
1.  Na pasku menu wybierz **projektu**, **Dodaj odwołanie**.  
  
     **Menadżer odwołań** pojawi się okno dialogowe.  
  
2.  W **zestawy** obszaru, wybierz**Framework** Jeśli nie została jeszcze wybrana.  
  
3.  Na liście nazw, wybierz **Microsoft.VisualBasic** pole wyboru, a następnie wybierz **OK** przycisk, aby zamknąć okno dialogowe.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kopiuje katalog który `sourcePath` określa do katalogu, `destinationPath` określa. Ten kod zapewnia standardowe okno dialogowe, pokazuje szacowany pozostały czas przed zakończeniem operacji.  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [System plików i rejestr (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md)
