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
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a><span data-ttu-id="f50ed-103">Jak dodać możliwości przeglądarki sieci Web do aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f50ed-103">How to add web browser capabilities to a Windows Forms application</span></span>

<span data-ttu-id="f50ed-104">Za pomocą <xref:System.Windows.Forms.WebBrowser> kontrolki możesz dodać do aplikacji funkcje przeglądarki sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f50ed-104">With the <xref:System.Windows.Forms.WebBrowser> control, you can add Web browser functionality to your application.</span></span> <span data-ttu-id="f50ed-105">Domyślnie formant działa jak przeglądarka sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f50ed-105">The control works like a Web browser by default.</span></span> <span data-ttu-id="f50ed-106">Po załadowaniu początkowego adresu URL przez ustawienie <xref:System.Windows.Forms.WebBrowser.Url%2A> właściwości można nawigować przez kliknięcie hiperłączy lub za pomocą skrótów klawiaturowych, aby przejść do tyłu i do przodu przez historię przeglądania.</span><span class="sxs-lookup"><span data-stu-id="f50ed-106">After you load an initial URL by setting the <xref:System.Windows.Forms.WebBrowser.Url%2A> property, you can navigate by clicking hyperlinks or by using keyboard shortcuts to move backward and forward through navigation history.</span></span> <span data-ttu-id="f50ed-107">Domyślnie można uzyskać dostęp do dodatkowych funkcji przeglądarki za pomocą menu skrótów kliknij prawym przyciskiem myszy.</span><span class="sxs-lookup"><span data-stu-id="f50ed-107">By default, you can access additional browser functionality through the right-click shortcut menu.</span></span> <span data-ttu-id="f50ed-108">Możesz również otworzyć nowe dokumenty, upuszczając je na kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="f50ed-108">You can also open new documents by dropping them onto the control.</span></span> <span data-ttu-id="f50ed-109"><xref:System.Windows.Forms.WebBrowser>Kontrolka ma także kilka właściwości, metod i zdarzeń, których można użyć do implementowania funkcji interfejsu użytkownika podobnych do tych, które znajdują się w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f50ed-109">The <xref:System.Windows.Forms.WebBrowser> control also has several properties, methods, and events that you can use to implement user interface features similar to those found in Internet Explorer.</span></span>

<span data-ttu-id="f50ed-110">Poniższy przykład kodu implementuje pasek adresu, typowe przyciski przeglądarki, menu **plik** , pasek stanu i pasek tytułu, który wyświetla bieżący tytuł strony.</span><span class="sxs-lookup"><span data-stu-id="f50ed-110">The following code example implements an address bar, typical browser buttons, a **File** menu, a status bar, and a title bar that displays the current page title.</span></span>

## <a name="example"></a><span data-ttu-id="f50ed-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="f50ed-111">Example</span></span>

[!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]
  
## <a name="compile-the-code"></a><span data-ttu-id="f50ed-112">Kompiluj kod</span><span class="sxs-lookup"><span data-stu-id="f50ed-112">Compile the code</span></span>

<span data-ttu-id="f50ed-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="f50ed-113">This example requires:</span></span>

- <span data-ttu-id="f50ed-114">Odwołania do `System` zestawów, `System.Drawing` i `System.Windows.Forms` .</span><span class="sxs-lookup"><span data-stu-id="f50ed-114">References to the `System`, `System.Drawing`, and `System.Windows.Forms` assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="f50ed-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f50ed-115">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="f50ed-116">WebBrowser, kontrolka</span><span class="sxs-lookup"><span data-stu-id="f50ed-116">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
