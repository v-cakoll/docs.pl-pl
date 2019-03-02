---
title: 'Instrukcje: Otwieranie plików za pomocą składnika OpenFileDialog'
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: f297b557e86c13c00a57a2033ba4cd61753b3d0b
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202655"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>Instrukcje: Pliki otwarte z OpenFileDialog 

<xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> Składnika otwiera okno dialogowe Windows do przeglądania i zaznaczania plików. Aby otworzyć i odczytać wybranych plików, można użyć <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> metodę, lub Utwórz wystąpienie obiektu <xref:System.IO.StreamReader?displayProperty=nameWithType> klasy. W poniższych przykładach pokazano oba podejścia. 

W programie .NET Framework do pobierania lub ustawiania <xref:System.Windows.Forms.FileDialog.FileName%2A> właściwości wymaga poziomu uprawnień przyznanych przez <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> klasy. Uruchamianie przykładów <xref:System.Security.Permissions.FileIOPermission> uprawnień Sprawdź i może zgłosić wyjątek ze względu na niewystarczające uprawnienia, jeśli są uruchamiane w kontekście częściowego zaufania. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../docs/framework/misc/code-access-security-basics.md).

Można skompilować i uruchomić te przykłady jako aplikacji .NET Framework z C# lub wiersza polecenia programu Visual Basic. Aby uzyskać więcej informacji, zobacz [za pomocą wiersza polecenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [kompilacji z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md). 

Począwszy od programu .NET Core 3.0 można również skompilować i uruchomić przykłady jako Windows aplikacje platformy .NET Core z folderu, który ma .NET Core Windows form  *\<nazwę folderu > .csproj* pliku projektu. 

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>Przykład: Odczytywanie pliku jako strumienia za pomocą StreamReader  
  
W poniższym przykładzie użyto formularze Windows <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń, aby otworzyć <xref:System.Windows.Forms.OpenFileDialog> z <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody. Po użytkownik wybierze plik i wybierze **OK**, wystąpienie <xref:System.IO.StreamReader> klasy odczytuje plik i wyświetla jego zawartość w polu tekstowym w formularzu. Aby uzyskać więcej informacji na temat odczytywania ze strumieni plików Zobacz <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> i <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.  

 [!code-csharp[OpenFileDialog#1](../../../../samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](../../../../samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>Przykład: Otwórz plik z filtrowanych zaznaczenia z OpenFile 

W poniższym przykładzie użyto <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń, aby otworzyć <xref:System.Windows.Forms.OpenFileDialog> za pomocą filtru, który pokazuje tylko pliki tekstowe. Gdy użytkownik wybierze plik tekstowy, a wybiera **OK**, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda służy do otwierania tego pliku w Notatniku.

 [!code-csharp[OpenFileDialog#2](../../../../samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](../../../../samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.OpenFileDialog>
- [Openfiledialog — składnik](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
