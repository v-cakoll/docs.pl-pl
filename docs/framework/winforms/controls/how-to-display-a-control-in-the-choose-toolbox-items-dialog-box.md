---
title: 'Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika'
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
ms.openlocfilehash: 86ec8f9ae76f010ebbc3be393d8d257ba5cfc6b6
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834613"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika

Podczas opracowywania i rozpowszechniania formantów można chcieć, aby te kontrolki były wyświetlane w oknie dialogowym **Wybierz elementy przybornika** programu Visual Studio, który jest wyświetlany po kliknięciu prawym przyciskiem myszy **przybornika** i wybraniu **pozycji Wybierz elementy**. Aby formant był widoczny w tym oknie dialogowym, można użyć procedury rejestracji AssemblyFoldersEx.

Aby wyświetlić swój formant w oknie dialogowym Wybierz elementy przybornika:

- Zainstaluj zestaw kontrolny w globalnej pamięci podręcznej zestawów. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../app-domains/install-assembly-into-gac.md).

  — lub —

- Zarejestruj swój formant i powiązane z nim zestawy czasu projektowania przy użyciu procedury rejestracji AssemblyFoldersEx. AssemblyFoldersEx to lokalizacja w rejestrze, w której dostawcy innych firm przechowują ścieżki dla każdej wersji obsługiwanej platformy. Rozwiązanie czasu projektowania może wyszukać w tej lokalizacji rejestru, aby znaleźć zestawy referencyjne. Skrypt rejestru może określać kontrolki, które mają być wyświetlane w przyborniku.

## <a name="see-also"></a>Zobacz także

- [Opracowywanie formantów Windows Forms w czasie projektowania](developing-windows-forms-controls-at-design-time.md)
- [Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../app-domains/install-assembly-into-gac.md)
- [Przewodnik: automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
