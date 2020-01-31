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
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a>Porady: obsługa zdarzeń związanych z danymi użytkownika w kontrolkach formularzy systemu Windows
W tym przykładzie pokazano, jak obsłużyć większość zdarzeń klawiatury, myszy, fokusu i walidacji, które mogą wystąpić w kontrolce Windows Forms. Pole tekstowe o nazwie `TextBoxInput` otrzymuje zdarzenia, gdy ma fokus, a informacje o każdym zdarzeniu są zapisywane w polu tekstowym o nazwie `TextBoxOutput` w kolejności, w jakiej zdarzenia zostały zgłoszone. Aplikacja zawiera również zestaw pól wyboru, których można użyć do filtrowania zdarzeń do raportowania.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- [Dane użytkownika w formularzach Windows Forms](user-input-in-windows-forms.md)
