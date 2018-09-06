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
ms.openlocfilehash: 514895d11ba5a9c4ac47538f2d1a9c1d0e9d7995
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800449"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>Porady: dodawanie funkcji przeglądarki sieci Web do aplikacji systemu Windows
Za pomocą <xref:System.Windows.Forms.WebBrowser> kontrolki, można dodać funkcji przeglądarki sieci Web do aplikacji. Kontrolka działa jak przeglądarki sieci Web domyślnie. Po załadowaniu początkowy adres URL, ustawiając <xref:System.Windows.Forms.WebBrowser.Url%2A> właściwości, można przejść, klikając hiperłącza lub za pomocą skrótów klawiaturowych do tyłu i do przodu w historii nawigacji. Domyślnie możesz uzyskać dostęp przeglądarki dodatkowe funkcje, za pomocą menu skrótów kliknij prawym przyciskiem myszy. Można również otworzyć nowe dokumenty przez ich upuszczenie na formant. <xref:System.Windows.Forms.WebBrowser> Kontrolka ma również kilka właściwości, metody i zdarzenia, które można użyć, aby zaimplementować funkcje interfejsu użytkownika jest podobne do tych dostępnych w programie Internet Explorer.  
  
 Poniższy przykładowy kod implementuje paska adresu, przyciski przeglądarki typowe **pliku** menu, pasek stanu i pasek tytułu, który wyświetla bieżący tytuł strony.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołuje się do `System,``System.Drawing`, i `System.Windows.Forms` zestawów.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.WebBrowser>  
 [WebBrowser, kontrolka](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
