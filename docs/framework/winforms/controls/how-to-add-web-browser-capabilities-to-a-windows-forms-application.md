---
title: Dodawanie funkcji przeglądarki sieci Web do aplikacji
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
ms.openlocfilehash: 7cb789121f4aa9a1e7cef54f992d0697ce6dfc62
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543576"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>Jak dodać możliwości przeglądarki sieci Web do aplikacji Windows Forms

Za pomocą kontrolki <xref:System.Windows.Forms.WebBrowser> można dodać do aplikacji funkcje przeglądarki sieci Web. Domyślnie formant działa jak przeglądarka sieci Web. Po załadowaniu początkowego adresu URL przez ustawienie właściwości <xref:System.Windows.Forms.WebBrowser.Url%2A> można nawigować przez kliknięcie hiperłączy lub za pomocą skrótów klawiaturowych, aby przejść do tyłu i do przodu przez historię przeglądania. Domyślnie można uzyskać dostęp do dodatkowych funkcji przeglądarki za pomocą menu skrótów kliknij prawym przyciskiem myszy. Możesz również otworzyć nowe dokumenty, upuszczając je na kontrolkę. Kontrolka <xref:System.Windows.Forms.WebBrowser> ma także kilka właściwości, metod i zdarzeń, których można użyć do implementowania funkcji interfejsu użytkownika podobnych do tych, które znajdują się w programie Internet Explorer.

Poniższy przykład kodu implementuje pasek adresu, typowe przyciski przeglądarki, menu **plik** , pasek stanu i pasek tytułu, który wyświetla bieżący tytuł strony.

## <a name="example"></a>Przykład

[!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]
  
## <a name="compile-the-code"></a>Skompilować kod

Ten przykład wymaga:

- Odwołania do zestawów `System`, `System.Drawing`i `System.Windows.Forms`.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.WebBrowser>
- [WebBrowser, kontrolka](webbrowser-control-windows-forms.md)
