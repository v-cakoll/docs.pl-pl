---
ms.openlocfilehash: 2872c5909b382e01fdd231019a12970caa3b77d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "72526766"
---
## <a name="installation-instructions---visual-studio-installer"></a>Instrukcje instalacji — Instalator programu Visual Studio

Istnieją dwa różne sposoby znajdowania **sdk platformy kompilatora .NET** w **Instalatorze programu Visual Studio:**

### <a name="install-using-the-visual-studio-installer---workloads-view"></a>Instalowanie przy użyciu widoku Instalator programu Visual Studio — obciążenia

Zestaw SDK platformy kompilatora .NET nie jest automatycznie wybierany jako część obciążenia programistycznego rozszerzenia programu Visual Studio. Należy wybrać go jako komponent opcjonalny.

1. Uruchamianie **Instalatora programu Visual Studio**
1. Wybierz **pozycję Modyfikuj**
1. Sprawdź obciążenie **programistyczne rozszerzenia programu Visual Studio.**
1. Otwórz węzeł **rozwoju rozszerzenia programu Visual Studio** w drzewie podsumowania.
1. Zaznacz pole wyboru Dla **sdk platformy kompilatora .NET**. Znajdziesz go ostatnio pod opcjonalnymi składnikami.

Opcjonalnie należy również edytor **DGML** wyświetlać wykresy w wizualizatoru:

1. Otwórz węzeł **Poszczególne składniki** w drzewie podsumowania.
1. Zaznacz pole wyboru **edytora DGML**

### <a name="install-using-the-visual-studio-installer---individual-components-tab"></a>Instalowanie przy użyciu karty Instalator programu Visual Studio — poszczególne składniki

1. Uruchamianie **Instalatora programu Visual Studio**
1. Wybierz **pozycję Modyfikuj**
1. Wybieranie karty **Poszczególne komponenty**
1. Zaznacz pole wyboru Dla **sdk platformy kompilatora .NET**. Znajdziesz go u góry w sekcji **Kompilatory, narzędzia kompilacji i czas wykonywania.**

Opcjonalnie należy również edytor **DGML** wyświetlać wykresy w wizualizatoru:

1. Zaznacz pole **wyboru edytora DGML**. Znajdziesz go w sekcji **Narzędzia kodu.**
