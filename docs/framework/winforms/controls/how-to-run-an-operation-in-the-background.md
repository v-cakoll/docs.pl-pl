---
title: 'Porady: uruchamianie operacji w tle'
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
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 5b56e2aa-dc05-444f-930c-2d7b23f9ad5b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9a92427310dc36392b35f22e39c1d4ae101db74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-run-an-operation-in-the-background"></a>Porady: uruchamianie operacji w tle
Jeśli masz operacji potrwa długo, i nie chcesz powodować opóźnienia w interfejsie użytkownika, można użyć <xref:System.ComponentModel.BackgroundWorker> klasę, aby uruchomić operację w innym wątku.  
  
 Poniższy przykład kodu pokazuje sposób uruchamiania czasochłonna operacja w tle. Formularz zawiera **Start** i **anulować** przycisków. Kliknij przycisk **Start** przycisk, aby uruchomić operację asynchroniczną. Kliknij przycisk **anulować** przycisk, aby zatrzymać operację uruchomiona asynchroniczną. Wynik każdej operacji jest wyświetlany w <xref:System.Windows.Forms.MessageBox>.  
  
 Brak kompleksową obsługę tego zadania w [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].  
  
 Zobacz też [wskazówki: przeprowadzanie operacji w tle](http://msdn.microsoft.com/library/ms233672\(v=vs.110\)).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.  
  
 Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [Instrukcje: implementowanie formularza korzystającego z operacji w tle](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [BackgroundWorker, składnik](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
