---
title: 'Instrukcje: Wyświetlanie kontroli w wybierz elementy przybornika — okno dialogowe'
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
ms.openlocfilehash: 191a0848d01eb043420866052b64e2284eb92b49
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720137"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Instrukcje: Wyświetlanie kontroli w wybierz elementy przybornika — okno dialogowe
Podczas tworzenia i Rozłóż kontrolki, może okazać się te kontrolki, które będą wyświetlane na **wybierz elementy przybornika** okno dialogowe, które jest wyświetlany po kliknięciu prawym przyciskiem myszy **przybornika** i wybierz  **Wybierz elementy**. Można włączyć kontroli nad pojawią się w tym oknie dialogowym za pomocą procedury rejestracji AssemblyFoldersEx.  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a>Aby wyświetlić formant w oknie dialogowym Wybierz elementy przybornika  
  
-   Zainstaluj zestaw formantu do globalnej pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie zestawu w globalnej pamięci podręcznej](../../app-domains/how-to-install-an-assembly-into-the-gac.md)  
  
     —lub—  
  
-   Zarejestruj kontrolki i jego skojarzone zestawy czasu projektowania przy użyciu procedury rejestracji AssemblyFoldersEx. AssemblyFoldersEx prowadzi do lokalizacji rejestru, w której inni dostawcy przechowywać ścieżki dla każdej wersji framework, które obsługują. Podczas projektowania rozwiązania można sprawdzić w tej lokalizacji rejestru można znaleźć zestawów odwołań. Skrypt rejestru można określić formanty, które mają być wyświetlane w przyborniku. Aby uzyskać więcej informacji, zobacz [wdrażania kontrolkę niestandardową i zestawy czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz także
- [Wybierz elementy przybornika, okno dialogowe (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))
- [Wdrażanie niestandardowego formantu i zestawy czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100))
- [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](developing-windows-forms-controls-at-design-time.md)
- [Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej](../../app-domains/how-to-install-an-assembly-into-the-gac.md)
- [Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
