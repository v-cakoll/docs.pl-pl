---
title: 'Instrukcje: wyświetlanie kontroli w oknie dialogowym Wybierz elementy przybornika'
ms.date: 08/23/2019
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f52c1d127df8f0e831db0749e3453bb1c54d5886
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972068"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Instrukcje: wyświetlanie kontroli w oknie dialogowym Wybierz elementy przybornika

Podczas opracowywania i rozpowszechniania formantów można chcieć, aby te kontrolki były wyświetlane w oknie dialogowym **Wybierz elementy przybornika** programu Visual Studio, który jest wyświetlany po kliknięciu prawym przyciskiem myszy **przybornika** i wybraniu **pozycji Wybierz elementy**. Aby formant był widoczny w tym oknie dialogowym, można użyć procedury rejestracji AssemblyFoldersEx.

Aby wyświetlić swój formant w oknie dialogowym Wybierz elementy przybornika:

- Zainstaluj zestaw kontrolny w globalnej pamięci podręcznej zestawów. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../app-domains/install-assembly-into-gac.md)

  —lub—

- Zarejestruj swój formant i powiązane z nim zestawy czasu projektowania przy użyciu procedury rejestracji AssemblyFoldersEx. AssemblyFoldersEx to lokalizacja w rejestrze, w której dostawcy innych firm przechowują ścieżki dla każdej wersji obsługiwanej platformy. Rozwiązanie czasu projektowania może wyszukać w tej lokalizacji rejestru, aby znaleźć zestawy referencyjne. Skrypt rejestru może określać kontrolki, które mają być wyświetlane w przyborniku.

## <a name="see-also"></a>Zobacz także

- [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](developing-windows-forms-controls-at-design-time.md)
- [Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../app-domains/install-assembly-into-gac.md)
- [Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
