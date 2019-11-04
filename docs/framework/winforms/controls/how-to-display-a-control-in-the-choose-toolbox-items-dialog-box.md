---
title: 'Porady: wyświetlanie kontroli w oknie dialogowym Wybierz elementy przybornika'
ms.date: 08/23/2019
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db4b3ac020e967a6a0c291103d825ac71cebda23
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458281"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Porady: wyświetlanie kontroli w oknie dialogowym Wybierz elementy przybornika

Podczas opracowywania i rozpowszechniania formantów można chcieć, aby te kontrolki były wyświetlane w oknie dialogowym **Wybierz elementy przybornika** programu Visual Studio, który jest wyświetlany po kliknięciu prawym przyciskiem myszy **przybornika** i wybraniu **pozycji Wybierz elementy**. Aby formant był widoczny w tym oknie dialogowym, można użyć procedury rejestracji AssemblyFoldersEx.

Aby wyświetlić swój formant w oknie dialogowym Wybierz elementy przybornika:

- Zainstaluj zestaw kontrolny w globalnej pamięci podręcznej zestawów. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../app-domains/install-assembly-into-gac.md).

  —lub—

- Zarejestruj swój formant i powiązane z nim zestawy czasu projektowania przy użyciu procedury rejestracji AssemblyFoldersEx. AssemblyFoldersEx to lokalizacja w rejestrze, w której dostawcy innych firm przechowują ścieżki dla każdej wersji obsługiwanej platformy. Rozwiązanie czasu projektowania może wyszukać w tej lokalizacji rejestru, aby znaleźć zestawy referencyjne. Skrypt rejestru może określać kontrolki, które mają być wyświetlane w przyborniku.

## <a name="see-also"></a>Zobacz także

- [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](developing-windows-forms-controls-at-design-time.md)
- [Instrukcje: instalowanie zestawu w pamięci Global Assembly Cache](../../app-domains/install-assembly-into-gac.md)
- [Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
