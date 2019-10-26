---
title: 'Instrukcje: uruchamianie aplikacji i wysyłanie naciśnięć klawiszy IT — Visual Basic'
ms.date: 10/23/2019
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 033999c07bb5839a264122b2ca330916bdf844b8
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919388"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>Instrukcje: uruchamianie aplikacji i wysyłanie naciśnięć klawiszy (Visual Basic)

W tym przykładzie użyto metody <xref:Microsoft.VisualBasic.Interaction.Shell%2A>, aby uruchomić aplikację Notatnik, a następnie drukuje zdanie przez wysłanie naciśnięć klawiszy przy użyciu metody [My. Computer. Keyboard. WyślijKlawisze](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) .

## <a name="example"></a>Przykład

[!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]

## <a name="robust-programming"></a>Niezawodne programowanie

Wyjątek <xref:System.ArgumentException> jest zgłaszany, jeśli nie można odnaleźć aplikacji z żądanym identyfikatorem procesu.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework

Wywołanie funkcji `Shell` wymaga pełnego zaufania (<xref:System.Security.SecurityException> Class).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
