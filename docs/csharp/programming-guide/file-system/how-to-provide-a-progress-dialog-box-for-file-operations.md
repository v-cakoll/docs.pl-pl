---
title: 'Porady: dostarczanie okna dialogowego postępu dla operacji na plikach (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: e48fcee8dc4c85083a00a89c88027529ab1cc3aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Porady: dostarczanie okna dialogowego postępu dla operacji na plikach (Przewodnik programowania w języku C#)
Możesz podać standardowe okno dialogowe pokazuje postęp operacji na plikach w systemie Windows użycie <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> metody w <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Aby dodać odwołanie w Visual Studio  
  
1.  Na pasku menu wybierz **projektu**, **Dodaj odwołanie**.  
  
     **Menedżera odwołań** zostanie wyświetlone okno dialogowe.  
  
2.  W **zestawy** obszarze, wybierz**Framework** Jeśli nie jest już wybrana.  
  
3.  Na liście nazw wybierz **Microsoft.VisualBasic** pole wyboru, a następnie wybierz pozycję **OK** przycisk, aby zamknąć okno dialogowe.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kopiuje katalog który `sourcePath` określa do katalogu który `destinationPath` określa. Ten kod zawiera również standardowe okno dialogowe Wyświetla ilość szacowany pozostały czas przed zakończeniem operacji.  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [System plików i rejestr (C# przewodnik programowania w języku)](../../../csharp/programming-guide/file-system/index.md)
