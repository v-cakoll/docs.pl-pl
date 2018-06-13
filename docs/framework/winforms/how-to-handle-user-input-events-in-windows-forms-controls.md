---
title: 'Porady: obsługa zdarzeń związanych z danymi użytkownika w kontrolkach formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
ms.openlocfilehash: 1faff6112f7857c2b1d6e4ac70c87f1a2adb62a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538773"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a>Porady: obsługa zdarzeń związanych z danymi użytkownika w kontrolkach formularzy systemu Windows
W tym przykładzie pokazano, jak obsługiwać większość klawiatura, mysz, fokus i zdarzenia walidacji, które mogą wystąpić w formancie formularzy systemu Windows. Pole tekstowe o nazwie `TextBoxInput` odbiera zdarzenia, gdy fokus, a informacje o każdym zdarzeniu są zapisywane w polu tekstowym o nazwie `TextBoxOutput` w kolejności, w której zostaną podniesione zdarzenia. Aplikacja zawiera także zestaw pól wyboru, które mogą służyć do filtrowania zdarzeń do raportu.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 [Dane użytkownika w formularzach Windows Forms](../../../docs/framework/winforms/user-input-in-windows-forms.md)
