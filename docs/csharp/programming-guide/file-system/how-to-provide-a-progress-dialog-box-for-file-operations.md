---
title: 'Instrukcje: Dostarczanie okna dialogowego postępu dla operacji na plikach — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: ab268c30af6b5eefe84ade852c679535c1e48068
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597271"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Instrukcje: Dostarczanie okna dialogowego postępu dla operacji na plikach (C# Programming Guide)
Można zapewnić standardowe okno dialogowe, które wyświetla postęp w operacjach plików w Windows, jeśli używasz <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in Class metoda <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Aby dodać odwołanie w Visual Studio  
  
1.  Na pasku menu wybierz **projektu**, **Dodaj odwołanie**.  
  
     **Menadżer odwołań** pojawi się okno dialogowe.  
  
2.  W **zestawy** obszaru, wybierz **Framework** Jeśli nie została jeszcze wybrana.  
  
3.  Na liście nazw, wybierz **Microsoft.VisualBasic** pole wyboru, a następnie wybierz **OK** przycisk, aby zamknąć okno dialogowe.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kopiuje katalog który `sourcePath` określa do katalogu, `destinationPath` określa. Ten kod zapewnia standardowe okno dialogowe, pokazuje szacowany pozostały czas przed zakończeniem operacji.  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a>Zobacz także

- [System plików i rejestr (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md)
