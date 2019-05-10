---
title: 'Instrukcje: dodawanie funkcji przeglądarki sieci Web do aplikacji Windows Forms'
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
ms.openlocfilehash: c091d9473bb7c3540453cb5763052f45f61b61f0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624005"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a><span data-ttu-id="c7617-102">Instrukcje: dodawanie funkcji przeglądarki sieci Web do aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7617-102">How to: Add Web Browser Capabilities to a Windows Forms Application</span></span>
<span data-ttu-id="c7617-103">Za pomocą <xref:System.Windows.Forms.WebBrowser> kontrolki, można dodać funkcji przeglądarki sieci Web do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7617-103">With the <xref:System.Windows.Forms.WebBrowser> control, you can add Web browser functionality to your application.</span></span> <span data-ttu-id="c7617-104">Kontrolka działa jak przeglądarki sieci Web domyślnie.</span><span class="sxs-lookup"><span data-stu-id="c7617-104">The control works like a Web browser by default.</span></span> <span data-ttu-id="c7617-105">Po załadowaniu początkowy adres URL, ustawiając <xref:System.Windows.Forms.WebBrowser.Url%2A> właściwości, można przejść, klikając hiperłącza lub za pomocą skrótów klawiaturowych do tyłu i do przodu w historii nawigacji.</span><span class="sxs-lookup"><span data-stu-id="c7617-105">After you load an initial URL by setting the <xref:System.Windows.Forms.WebBrowser.Url%2A> property, you can navigate by clicking hyperlinks or by using keyboard shortcuts to move backward and forward through navigation history.</span></span> <span data-ttu-id="c7617-106">Domyślnie możesz uzyskać dostęp przeglądarki dodatkowe funkcje, za pomocą menu skrótów kliknij prawym przyciskiem myszy.</span><span class="sxs-lookup"><span data-stu-id="c7617-106">By default, you can access additional browser functionality through the right-click shortcut menu.</span></span> <span data-ttu-id="c7617-107">Można również otworzyć nowe dokumenty przez ich upuszczenie na formant.</span><span class="sxs-lookup"><span data-stu-id="c7617-107">You can also open new documents by dropping them onto the control.</span></span> <span data-ttu-id="c7617-108"><xref:System.Windows.Forms.WebBrowser> Kontrolka ma również kilka właściwości, metody i zdarzenia, które można użyć, aby zaimplementować funkcje interfejsu użytkownika jest podobne do tych dostępnych w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="c7617-108">The <xref:System.Windows.Forms.WebBrowser> control also has several properties, methods, and events that you can use to implement user interface features similar to those found in Internet Explorer.</span></span>  
  
 <span data-ttu-id="c7617-109">Poniższy przykładowy kod implementuje paska adresu, przyciski przeglądarki typowe **pliku** menu, pasek stanu i pasek tytułu, który wyświetla bieżący tytuł strony.</span><span class="sxs-lookup"><span data-stu-id="c7617-109">The following code example implements an address bar, typical browser buttons, a **File** menu, a status bar, and a title bar that displays the current page title.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7617-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="c7617-110">Example</span></span>  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c7617-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c7617-111">Compiling the Code</span></span>  
 <span data-ttu-id="c7617-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="c7617-112">This example requires:</span></span>  
  
- <span data-ttu-id="c7617-113">Odwołuje się do `System`, `System.Drawing`, i `System.Windows.Forms` zestawów.</span><span class="sxs-lookup"><span data-stu-id="c7617-113">References to the `System`, `System.Drawing`, and `System.Windows.Forms` assemblies.</span></span>  
  
 <span data-ttu-id="c7617-114">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c7617-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="c7617-115">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="c7617-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7617-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7617-116">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="c7617-117">WebBrowser, kontrolka</span><span class="sxs-lookup"><span data-stu-id="c7617-117">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
