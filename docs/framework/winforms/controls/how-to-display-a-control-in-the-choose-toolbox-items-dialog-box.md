---
title: "Porady: wyświetlanie kontroli w oknie dialogowym Wybierz elementy przybornika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3964551ba2eec0980541e95a7db20ef057a1dd61
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Porady: wyświetlanie kontroli w oknie dialogowym Wybierz elementy przybornika
Jak należy opracować i rozpowszechnić formantów, może być tych kontrolek w wynikach **wybierz elementy przybornika** okno dialogowe, w którym jest wyświetlany po kliknięciu prawym przyciskiem myszy **przybornika** i wybierz  **Wybierz elementy**. Można włączyć formantu pojawią się w tym oknie dialogowym przy użyciu procedury rejestracji AssemblyFoldersEx.  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a>Aby wyświetlić formantu w oknie dialogowym Wybierz elementy przybornika  
  
-   Zainstaluj z zestawu formantu do globalnej pamięci podręcznej zestawów. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
  
     —lub—  
  
-   Zarejestruj formantu i jego skojarzone zestawy czasu projektowania przy użyciu procedury rejestracji AssemblyFoldersEx. AssemblyFoldersEx jest lokalizacji rejestru, w którym dostawców innych firm przechowywać ścieżki dla każdej wersji platformy, które obsługują. Podczas projektowania rozwiązania mogą zobaczyć w tej lokalizacji rejestru, aby znaleźć zestawów odwołań. Skrypt rejestru można określić formanty, które mają być wyświetlane w przyborniku. Aby uzyskać więcej informacji, zobacz [wdrażanie formant niestandardowy i czasu projektowania zestawy (Visual Studio 2013)](http://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).  
  
## <a name="see-also"></a>Zobacz też  
 [Wybierz elementy przybornika, okno dialogowe (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [Wdrażanie kontrolkę niestandardową oraz czasu projektowania zestawy (Visual Studio 2013)](http://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Instrukcje: instalowanie zestawu w pamięci Global Assembly Cache](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
