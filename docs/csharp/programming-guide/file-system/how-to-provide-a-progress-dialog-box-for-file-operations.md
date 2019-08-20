---
title: 'Instrukcje: Udostępnianie okna dialogowego postępu dla operacji na plikach — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 028e779f3cd8a17f162a79791b0c84abae14cf44
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590047"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Instrukcje: Udostępnianie okna dialogowego postępu dla operacji na plikach (C# Przewodnik programowania)
Możesz podać standardowe okno dialogowe, które pokazuje postęp operacji na plikach w systemie Windows, jeśli używasz <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> metody <xref:Microsoft.VisualBasic?displayProperty=nameWithType> z przestrzeni nazw.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Aby dodać odwołanie w programie Visual Studio  
  
1. Na pasku menu wybierz **projekt**, **Dodaj odwołanie**.  
  
     Zostanie wyświetlone okno dialogowe **Menedżer odwołań** .  
  
2. W obszarze **zestawy** wybierz pozycję **Struktura** , jeśli nie została jeszcze wybrana.  
  
3. Na liście nazw zaznacz pole wyboru **Microsoft. VisualBasic** , a następnie wybierz przycisk **OK** , aby zamknąć okno dialogowe.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kopiuje katalog `sourcePath` określany w katalogu, który `destinationPath` określa. Ten kod udostępnia również standardowe okno dialogowe, które pokazuje szacowany czas pozostały do zakończenia operacji.  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a>Zobacz także

- [System plików i Rejestr (C# Przewodnik programowania)](./index.md)
