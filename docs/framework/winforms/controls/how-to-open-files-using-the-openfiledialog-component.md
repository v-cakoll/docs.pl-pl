---
title: 'Instrukcje: otwieranie plików za pomocą składnika OpenFileDialog'
ms.date: 02/11/2019
description: Dowiedz się, jak za pomocą składnika OpenFileDialog otworzyć okno dialogowe systemu Windows służące do przeglądania i wybierania plików.
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: d571885011b0f0c723c73a417f294f30f96952f4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904432"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>Instrukcje: otwieranie plików za pomocą OpenFileDialog

<xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType>Składnik otwiera okno dialogowe systemu Windows służące do przeglądania i wybierania plików. Aby otworzyć i odczytać wybrane pliki, można użyć <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> metody lub utworzyć wystąpienie <xref:System.IO.StreamReader?displayProperty=nameWithType> klasy. W poniższych przykładach pokazano oba podejścia.

W .NET Framework, aby uzyskać lub ustawić <xref:System.Windows.Forms.FileDialog.FileName%2A> Właściwość, wymaga poziomu uprawnień przyznany przez <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> klasę. Przykłady uruchamiają <xref:System.Security.Permissions.FileIOPermission> kontrolę uprawnień i mogą zgłosić wyjątek z powodu niewystarczających uprawnień, jeśli są uruchamiane w kontekście częściowego zaufania. Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../misc/code-access-security-basics.md).

Możesz tworzyć i uruchamiać te przykłady jako .NET Framework aplikacje z poziomu wiersza polecenia C# lub Visual Basic. Aby uzyskać więcej informacji, zobacz [Kompilowanie wiersza polecenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [Kompilowanie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

Począwszy od platformy .NET Core 3,0, można również kompilować i uruchamiać przykłady jako aplikacje platformy Windows .NET Core z folderu, który ma plik projektu programu .NET Core Windows Forms * \<folder name> . csproj* .

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>Przykład: odczytywanie pliku jako strumienia przy użyciu StreamReader  
  
Poniższy przykład używa <xref:System.Windows.Forms.Button> procedury obsługi zdarzeń kontrolki Windows Forms, <xref:System.Windows.Forms.Control.Click> Aby otworzyć <xref:System.Windows.Forms.OpenFileDialog> przy użyciu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody. Gdy użytkownik wybierze plik i wybierze **OK**, wystąpienie <xref:System.IO.StreamReader> klasy odczytuje plik i wyświetla jego zawartość w polu tekstowym formularza. Aby uzyskać więcej informacji na temat odczytywania strumieni plików, zobacz <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> i <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType> .  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>Przykład: otwiera plik z filtrowanego zaznaczenia za pomocą OpenFile

Poniższy przykład używa <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń kontrolki do otwierania <xref:System.Windows.Forms.OpenFileDialog> z filtrem, który pokazuje tylko pliki tekstowe. Gdy użytkownik wybierze plik tekstowy i wybierze **OK**, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> Metoda zostanie użyta do otwarcia pliku w Notatniku.

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.OpenFileDialog>
- [Składnik OpenFileDialog](openfiledialog-component-windows-forms.md)
