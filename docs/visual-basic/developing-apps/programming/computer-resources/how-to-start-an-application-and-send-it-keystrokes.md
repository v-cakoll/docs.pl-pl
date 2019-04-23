---
title: 'Instrukcje: Uruchamianie aplikacji i wysyłanie do niej uderzeń w klawisze (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 9519fd85177d5d2adf97b54652c19330954edadf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976394"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a><span data-ttu-id="9f7c2-102">Instrukcje: Uruchamianie aplikacji i wysyłanie do niej uderzeń w klawisze (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f7c2-102">How to: Start an Application and Send it Keystrokes (Visual Basic)</span></span>
<span data-ttu-id="9f7c2-103">W tym przykładzie użyto `Shell` działać do uruchomienia aplikacji Kalkulator, a następnie mnoży dwie liczby, wysyłając naciśnięcia klawiszy `My.Computer.Keyboard.SendKeys` metody.</span><span class="sxs-lookup"><span data-stu-id="9f7c2-103">This example uses the `Shell` function to start the calculator application and then multiplies two numbers by sending keystrokes using the `My.Computer.Keyboard.SendKeys` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f7c2-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9f7c2-104">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]  
  
## <a name="robust-programming"></a><span data-ttu-id="9f7c2-105">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="9f7c2-105">Robust Programming</span></span>  
 <span data-ttu-id="9f7c2-106">A <xref:System.ArgumentException> wyjątek jest zgłaszany, jeśli nie można odnaleźć aplikacji za pomocą identyfikatora żądany proces.</span><span class="sxs-lookup"><span data-stu-id="9f7c2-106">A <xref:System.ArgumentException> exception is raised if an application with the requested process identifier cannot be found.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9f7c2-107">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="9f7c2-107">.NET Framework Security</span></span>  
 <span data-ttu-id="9f7c2-108">Wywołanie `Shell` funkcja wymaga pełnego zaufania (<xref:System.Security.SecurityException> klasy).</span><span class="sxs-lookup"><span data-stu-id="9f7c2-108">The call to the `Shell` function requires full trust (<xref:System.Security.SecurityException> class).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f7c2-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f7c2-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
