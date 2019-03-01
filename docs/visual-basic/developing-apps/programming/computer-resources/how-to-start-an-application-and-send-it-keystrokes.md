---
title: 'Instrukcje: Uruchamianie aplikacji i wysyłanie do niej uderzeń w klawisze (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: f130429e5b0964dc8680441fb83cb06d45904a69
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966206"
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
