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
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014521"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>Instrukcje: Uruchamianie aplikacji i wysyłanie do niej uderzeń w klawisze (Visual Basic)
W tym przykładzie użyto `Shell` działać do uruchomienia aplikacji Kalkulator, a następnie mnoży dwie liczby, wysyłając naciśnięcia klawiszy `My.Computer.Keyboard.SendKeys` metody.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 A <xref:System.ArgumentException> wyjątek jest zgłaszany, jeśli nie można odnaleźć aplikacji za pomocą identyfikatora żądany proces.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Wywołanie `Shell` funkcja wymaga pełnego zaufania (<xref:System.Security.SecurityException> klasy).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
