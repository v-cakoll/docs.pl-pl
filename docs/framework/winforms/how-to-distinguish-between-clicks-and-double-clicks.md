---
title: "Porady: rozróżnianie między kliknięciami a dwukrotnymi kliknięciami"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- mouse [Windows Forms], click
- mouse [Windows Forms], double-click
- mouse clicks [Windows Forms], single versus double
ms.assetid: d836ac8c-85bc-4f3a-a761-8aee03dc682c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9b407f7c00454b0a14b4c90694d015b38ffd72ef
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-distinguish-between-clicks-and-double-clicks"></a>Porady: rozróżnianie między kliknięciami a dwukrotnymi kliknięciami
Zazwyczaj pojedynczy *kliknij* inicjuje akcji interfejsu użytkownika a *kliknij dwukrotnie* rozszerza akcji. Na przykład jednego kliknięcia zazwyczaj wybiera element, a następnie dwukrotne Edytuje wybrany element. Jednak zdarzenia kliknięcia formularze systemu Windows nie łatwo zmiany scenariusz, w którym przez kliknięcie i dwukrotne akcje niezgodne, ponieważ powiązane akcji <xref:System.Windows.Forms.Control.Click> lub <xref:System.Windows.Forms.Control.MouseClick> zdarzeń jest wykonywane przed akcją powiązane <xref:System.Windows.Forms.Control.DoubleClick>lub <xref:System.Windows.Forms.Control.MouseDoubleClick> zdarzeń. W tym temacie przedstawiono dwa rozwiązania tego problemu. Rozwiązanie polega na kliknij dwukrotnie zdarzenie i wycofać akcje obsługi zdarzenia kliknięcia. W rzadkich przypadkach może być konieczne symulować kliknij i dwukrotnie kliknij zachowanie obsługa <xref:System.Windows.Forms.Control.MouseDown> zdarzeń i za pomocą <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> i <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> właściwości <xref:System.Windows.Forms.SystemInformation> klasy. Pomiar czasu między kliknięciami a jeśli drugie kliknięcie występuje przed wartością <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> osiągnięciu i kliknięcie mieści się w prostokącie zdefiniowane przez <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>, wykonania akcji kliknij dwukrotnie; w przeciwnym razie wykonaj akcję kliknij.  
  
### <a name="to-roll-back-a-click-action"></a>Aby wycofać akcji kliknij pozycję  
  
-   Sprawdź, czy użytkownik pracuje z formantu ma standard kliknij dwukrotnie zachowanie. Jeśli nie, Włącz kontrolki z <xref:System.Windows.Forms.Control.SetStyle%2A> metody. Kliknij dwukrotnie zdarzenie i wycofać kliknij akcję, a także akcji kliknij dwukrotnie. Poniższy przykład kodu pokazuje, jak utworzyć niestandardowe przycisk z włączone, a także wycofywaniu akcji kliknij kod obsługi zdarzenia kliknij dwukrotnie kliknij dwukrotnie.  
  
     [!code-csharp[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/VB/Form1.vb#1)]  
  
### <a name="to-distinguish-between-clicks-in-the-mousedown-event"></a>Aby odróżnić kliknięć w MouseDown — zdarzenie  
  
-   Obsługa <xref:System.Windows.Forms.Control.MouseDown> zdarzeń i określenie miejsca i czasu span między kliknięciami za pomocą odpowiedniej <xref:System.Windows.Forms.SystemInformation> właściwości i <xref:System.Windows.Forms.Timer> składnika. Wykonaj odpowiednią akcję w zależności od tego, czy odbywa się kliknij lub kliknij dwukrotnie. W poniższym przykładzie kodu pokazano, jak to zrobić.  
  
     [!code-cpp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/cpp/form1.cpp#0)]
     [!code-csharp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/CS/form1.cs#0)]
     [!code-vb[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Wymagaj te przykłady:  
  
-   Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.  
  
 Informacji dotyczących tworzenia tych przykładów z wiersza polecenia dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tych przykładach [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] wklejając kod w nowych projektach.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 [Wejście myszy w systemie Windows formularzy aplikacji](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
