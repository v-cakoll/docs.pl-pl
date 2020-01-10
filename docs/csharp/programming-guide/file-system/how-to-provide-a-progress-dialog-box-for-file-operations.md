---
title: Jak zapewnić okno dialogowe postępu dla operacji na plikach — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 30ab84054d26f5b32a3f042a8d35d5ef1211d928
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705135"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Jak zapewnić okno dialogowe postępu dla operacji na plikach (C# Przewodnik programowania)
Możesz podać standardowe okno dialogowe, które pokazuje postęp operacji na plikach w systemie Windows, jeśli używasz metody <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> w przestrzeni nazw <xref:Microsoft.VisualBasic?displayProperty=nameWithType>.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Aby dodać odwołanie w programie Visual Studio  
  
1. Na pasku menu wybierz **projekt**, **Dodaj odwołanie**.  
  
     Zostanie wyświetlone okno dialogowe **Menedżer odwołań** .  
  
2. W obszarze **zestawy** wybierz pozycję **Struktura** , jeśli nie została jeszcze wybrana.  
  
3. Na liście nazw zaznacz pole wyboru **Microsoft. VisualBasic** , a następnie wybierz przycisk **OK** , aby zamknąć okno dialogowe.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kopiuje katalog, który `sourcePath` określa do katalogu, który `destinationPath` określa. Ten kod udostępnia również standardowe okno dialogowe, które pokazuje szacowany czas pozostały do zakończenia operacji.  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a>Zobacz także

- [System plików i Rejestr (C# Przewodnik programowania)](./index.md)
