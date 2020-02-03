---
title: Obsługa zdarzeń wejściowych użytkownika w kontrolkach
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
ms.openlocfilehash: 19adeb6c803c76cba4139841f58087487d523a50
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739420"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a><span data-ttu-id="b4bad-102">Porady: obsługa zdarzeń związanych z danymi użytkownika w kontrolkach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b4bad-102">How to: Handle User Input Events in Windows Forms Controls</span></span>
<span data-ttu-id="b4bad-103">W tym przykładzie pokazano, jak obsłużyć większość zdarzeń klawiatury, myszy, fokusu i walidacji, które mogą wystąpić w kontrolce Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b4bad-103">This example demonstrates how to handle most keyboard, mouse, focus, and validation events that can occur in a Windows Forms control.</span></span> <span data-ttu-id="b4bad-104">Pole tekstowe o nazwie `TextBoxInput` otrzymuje zdarzenia, gdy ma fokus, a informacje o każdym zdarzeniu są zapisywane w polu tekstowym o nazwie `TextBoxOutput` w kolejności, w jakiej zdarzenia zostały zgłoszone.</span><span class="sxs-lookup"><span data-stu-id="b4bad-104">The text box named `TextBoxInput` receives the events when it has focus, and information about each event is written in the text box named `TextBoxOutput` in the order in which the events are raised.</span></span> <span data-ttu-id="b4bad-105">Aplikacja zawiera również zestaw pól wyboru, których można użyć do filtrowania zdarzeń do raportowania.</span><span class="sxs-lookup"><span data-stu-id="b4bad-105">The application also includes a set of check boxes that can be used to filter which events to report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4bad-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4bad-106">Example</span></span>  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b4bad-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b4bad-107">Compiling the Code</span></span>  
 <span data-ttu-id="b4bad-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b4bad-108">This example requires:</span></span>  
  
- <span data-ttu-id="b4bad-109">Odwołania do zestawów system, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="b4bad-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4bad-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4bad-110">See also</span></span>

- [<span data-ttu-id="b4bad-111">Dane użytkownika w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b4bad-111">User Input in Windows Forms</span></span>](user-input-in-windows-forms.md)
