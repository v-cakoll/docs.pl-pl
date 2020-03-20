---
title: 'Jak: Otwieranie plików za pomocą składnika OpenFileDialog'
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: ca69de19ab1b9ae387002898145fe99e35a7b6b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182130"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>Jak: Otwieranie plików za pomocą OpenFileDialog

Składnik <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> otwiera okno dialogowe systemu Windows do przeglądania i wybierania plików. Aby otworzyć i odczytać wybrane pliki, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> można użyć metody lub <xref:System.IO.StreamReader?displayProperty=nameWithType> utworzyć wystąpienie klasy. Poniższe przykłady pokazują oba podejścia.

W .NET Framework, aby <xref:System.Windows.Forms.FileDialog.FileName%2A> uzyskać lub ustawić właściwość <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> wymaga poziomu uprawnień przyznane przez klasę. Przykłady uruchomić <xref:System.Security.Permissions.FileIOPermission> sprawdzanie uprawnień i można zgłosić wyjątek z powodu niewystarczających uprawnień, jeśli są uruchamiane w kontekście częściowego zaufania. Aby uzyskać więcej informacji, zobacz [Podstawy zabezpieczeń dostępu do kodu](../../misc/code-access-security-basics.md).

Można skompilować i uruchomić te przykłady jako aplikacje .NET Framework z wiersza polecenia C# lub Visual Basic. Aby uzyskać więcej informacji, zobacz [Tworzenie wiersza polecenia za pomocą pliku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [Kompilacja z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

Począwszy od programu .NET Core 3.0, można również tworzyć i uruchamiać przykłady jako aplikacje windows .NET Core z folderu o nazwie folderu .NET Core Windows Forms * \<>.csproj* pliku projektu.

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>Przykład: Odczyt pliku jako strumienia za pomocą streamreadera  
  
W poniższym przykładzie <xref:System.Windows.Forms.Button> użyto <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń <xref:System.Windows.Forms.OpenFileDialog> formantu Windows Forms, aby otworzyć <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę with. Gdy użytkownik wybierze plik i wybierze przycisk <xref:System.IO.StreamReader> **OK,** wystąpienie klasy odczytuje plik i wyświetla jego zawartość w polu tekstowym formularza. Aby uzyskać więcej informacji na temat <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>odczytu ze strumieni plików, zobacz i .  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>Przykład: Otwieranie pliku z filtrowanego zaznaczenia za pomocą pliku OpenFile

W poniższym <xref:System.Windows.Forms.Button> przykładzie użyto programu obsługi <xref:System.Windows.Forms.Control.Click> zdarzeń formantu, aby otworzyć <xref:System.Windows.Forms.OpenFileDialog> z filtrem, który pokazuje tylko pliki tekstowe. Gdy użytkownik wybierze plik tekstowy i <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> wybierze **przycisk OK,** metoda ta jest używana do otwierania pliku w Notatniku.

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.OpenFileDialog>
- [Składnik OpenFileDialog](openfiledialog-component-windows-forms.md)
