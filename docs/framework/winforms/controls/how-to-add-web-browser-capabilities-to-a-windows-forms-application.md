---
title: 'Porady: dodawanie funkcji przeglądarki sieci Web do aplikacji systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
ms.openlocfilehash: d106736a288283c58bdc8020cd54b88859454fba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526852"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>Porady: dodawanie funkcji przeglądarki sieci Web do aplikacji systemu Windows
Z <xref:System.Windows.Forms.WebBrowser> sterowania, można dodać funkcji przeglądarki sieci Web do aplikacji. Formant działa jak przeglądarki sieci Web domyślnie. Po załadowaniu początkowy adres URL przez ustawienie <xref:System.Windows.Forms.WebBrowser.Url%2A> właściwości, można przejść, klikając hiperłącza lub za pomocą skróty klawiaturowe do tyłu i przekazywać je do historii nawigacji. Domyślnie można uzyskać dostępu do funkcjonalności przeglądarki dodatkowe za pośrednictwem menu skrótów kliknij prawym przyciskiem myszy. Można również otworzyć nowych dokumentów, przeciągając je w formancie. <xref:System.Windows.Forms.WebBrowser> Formant ma również kilka właściwości, metod i zdarzeń, które służy do implementowania funkcji interfejsu użytkownika podobne do tych znaleziono w programie Internet Explorer.  
  
 Poniższy przykład kodu implementuje paska adresu, przyciski typowe przeglądarki, **pliku** menu, paska stanu i pasek tytułu, który wyświetla bieżący tytuł strony.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołuje się do `System,``System.Drawing`, i `System.Windows.Forms` zestawów.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.WebBrowser>  
 [WebBrowser, kontrolka](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
