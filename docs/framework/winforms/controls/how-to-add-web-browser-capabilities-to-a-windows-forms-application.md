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
ms.openlocfilehash: 5feecd975700745541103e81fd09bfc5e788c729
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747227"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>Porady: dodawanie funkcji przeglądarki sieci Web do aplikacji Windows Forms
Za pomocą kontrolki <xref:System.Windows.Forms.WebBrowser> można dodać do aplikacji funkcje przeglądarki sieci Web. Domyślnie formant działa jak przeglądarka sieci Web. Po załadowaniu początkowego adresu URL przez ustawienie właściwości <xref:System.Windows.Forms.WebBrowser.Url%2A> można nawigować przez kliknięcie hiperłączy lub za pomocą skrótów klawiaturowych, aby przejść do tyłu i do przodu przez historię przeglądania. Domyślnie można uzyskać dostęp do dodatkowych funkcji przeglądarki za pomocą menu skrótów kliknij prawym przyciskiem myszy. Możesz również otworzyć nowe dokumenty, upuszczając je na kontrolkę. Kontrolka <xref:System.Windows.Forms.WebBrowser> ma także kilka właściwości, metod i zdarzeń, których można użyć do implementowania funkcji interfejsu użytkownika podobnych do tych, które znajdują się w programie Internet Explorer.  
  
 Poniższy przykład kodu implementuje pasek adresu, typowe przyciski przeglądarki, menu **plik** , pasek stanu i pasek tytułu, który wyświetla bieżący tytuł strony.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów `System`, `System.Drawing`i `System.Windows.Forms`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.WebBrowser>
- [WebBrowser, kontrolka](webbrowser-control-windows-forms.md)
