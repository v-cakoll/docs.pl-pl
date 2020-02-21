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
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a><span data-ttu-id="6f49b-102">Jak dodać możliwości przeglądarki sieci Web do aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6f49b-102">How to add web browser capabilities to a Windows Forms application</span></span>

<span data-ttu-id="6f49b-103">Za pomocą kontrolki <xref:System.Windows.Forms.WebBrowser> można dodać do aplikacji funkcje przeglądarki sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6f49b-103">With the <xref:System.Windows.Forms.WebBrowser> control, you can add Web browser functionality to your application.</span></span> <span data-ttu-id="6f49b-104">Domyślnie formant działa jak przeglądarka sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6f49b-104">The control works like a Web browser by default.</span></span> <span data-ttu-id="6f49b-105">Po załadowaniu początkowego adresu URL przez ustawienie właściwości <xref:System.Windows.Forms.WebBrowser.Url%2A> można nawigować przez kliknięcie hiperłączy lub za pomocą skrótów klawiaturowych, aby przejść do tyłu i do przodu przez historię przeglądania.</span><span class="sxs-lookup"><span data-stu-id="6f49b-105">After you load an initial URL by setting the <xref:System.Windows.Forms.WebBrowser.Url%2A> property, you can navigate by clicking hyperlinks or by using keyboard shortcuts to move backward and forward through navigation history.</span></span> <span data-ttu-id="6f49b-106">Domyślnie można uzyskać dostęp do dodatkowych funkcji przeglądarki za pomocą menu skrótów kliknij prawym przyciskiem myszy.</span><span class="sxs-lookup"><span data-stu-id="6f49b-106">By default, you can access additional browser functionality through the right-click shortcut menu.</span></span> <span data-ttu-id="6f49b-107">Możesz również otworzyć nowe dokumenty, upuszczając je na kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="6f49b-107">You can also open new documents by dropping them onto the control.</span></span> <span data-ttu-id="6f49b-108">Kontrolka <xref:System.Windows.Forms.WebBrowser> ma także kilka właściwości, metod i zdarzeń, których można użyć do implementowania funkcji interfejsu użytkownika podobnych do tych, które znajdują się w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="6f49b-108">The <xref:System.Windows.Forms.WebBrowser> control also has several properties, methods, and events that you can use to implement user interface features similar to those found in Internet Explorer.</span></span>

<span data-ttu-id="6f49b-109">Poniższy przykład kodu implementuje pasek adresu, typowe przyciski przeglądarki, menu **plik** , pasek stanu i pasek tytułu, który wyświetla bieżący tytuł strony.</span><span class="sxs-lookup"><span data-stu-id="6f49b-109">The following code example implements an address bar, typical browser buttons, a **File** menu, a status bar, and a title bar that displays the current page title.</span></span>

## <a name="example"></a><span data-ttu-id="6f49b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="6f49b-110">Example</span></span>

[!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]
  
## <a name="compile-the-code"></a><span data-ttu-id="6f49b-111">Skompilować kod</span><span class="sxs-lookup"><span data-stu-id="6f49b-111">Compile the code</span></span>

<span data-ttu-id="6f49b-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="6f49b-112">This example requires:</span></span>

- <span data-ttu-id="6f49b-113">Odwołania do zestawów `System`, `System.Drawing`i `System.Windows.Forms`.</span><span class="sxs-lookup"><span data-stu-id="6f49b-113">References to the `System`, `System.Drawing`, and `System.Windows.Forms` assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f49b-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f49b-114">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="6f49b-115">WebBrowser, kontrolka</span><span class="sxs-lookup"><span data-stu-id="6f49b-115">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
