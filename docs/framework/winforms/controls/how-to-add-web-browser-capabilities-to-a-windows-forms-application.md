---
title: Dodawanie funkcji przeglądarki sieci Web do aplikacji
description: Dowiedz się, jak dodać możliwości przeglądarki sieci Web do aplikacji Windows Forms z kontrolką WebBrowser.
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
ms.openlocfilehash: a5a33961ac8301bda86bb5f34e65ac159308987f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174552"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>Jak dodać możliwości przeglądarki sieci Web do aplikacji Windows Forms

Za pomocą <xref:System.Windows.Forms.WebBrowser> kontrolki możesz dodać do aplikacji funkcje przeglądarki sieci Web. Domyślnie formant działa jak przeglądarka sieci Web. Po załadowaniu początkowego adresu URL przez ustawienie <xref:System.Windows.Forms.WebBrowser.Url%2A> właściwości można nawigować przez kliknięcie hiperłączy lub za pomocą skrótów klawiaturowych, aby przejść do tyłu i do przodu przez historię przeglądania. Domyślnie można uzyskać dostęp do dodatkowych funkcji przeglądarki za pomocą menu skrótów kliknij prawym przyciskiem myszy. Możesz również otworzyć nowe dokumenty, upuszczając je na kontrolkę. <xref:System.Windows.Forms.WebBrowser>Kontrolka ma także kilka właściwości, metod i zdarzeń, których można użyć do implementowania funkcji interfejsu użytkownika podobnych do tych, które znajdują się w programie Internet Explorer.

Poniższy przykład kodu implementuje pasek adresu, typowe przyciski przeglądarki, menu **plik** , pasek stanu i pasek tytułu, który wyświetla bieżący tytuł strony.

## <a name="example"></a>Przykład

[!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]
  
## <a name="compile-the-code"></a>Kompiluj kod

Ten przykład wymaga:

- Odwołania do `System` zestawów, `System.Drawing` i `System.Windows.Forms` .

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.WebBrowser>
- [WebBrowser, kontrolka](webbrowser-control-windows-forms.md)
