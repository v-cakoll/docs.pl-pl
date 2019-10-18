---
ms.openlocfilehash: 2872c5909b382e01fdd231019a12970caa3b77d2
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72526766"
---
## <a name="installation-instructions---visual-studio-installer"></a>Instrukcje dotyczące instalacji — Instalator programu Visual Studio

Istnieją dwa różne sposoby znajdowania **zestawu SDK .NET compiler platform** w **Instalator programu Visual Studio**:

### <a name="install-using-the-visual-studio-installer---workloads-view"></a>Instalowanie przy użyciu widoku Instalator programu Visual Studio — obciążenia

Zestaw .NET Compiler Platform SDK nie jest automatycznie wybierany jako część obciążenia programowania rozszerzeń programu Visual Studio. Należy zaznaczyć go jako składnik opcjonalny.

1. Uruchom **Instalator programu Visual Studio**
1. Wybieranie opcji **Modyfikuj**
1. Sprawdź obciążenie **programowanie rozszerzenia programu Visual Studio** .
1. Otwórz węzeł **programowanie rozszerzeń programu Visual Studio** w drzewie podsumowującym.
1. Zaznacz pole wyboru **.NET COMPILER Platform SDK**. Znajdziesz go jako ostatni w obszarze opcjonalnych składników.

Opcjonalnie, aby **Edytor DGML** wyświetlał wykresy w wizualizatorze:

1. Otwórz węzeł **poszczególne składniki** w drzewie podsumowania.
1. Zaznacz pole wyboru dla **edytora DGML**

### <a name="install-using-the-visual-studio-installer---individual-components-tab"></a>Instalowanie przy użyciu karty Instalator programu Visual Studio poszczególnych składników

1. Uruchom **Instalator programu Visual Studio**
1. Wybieranie opcji **Modyfikuj**
1. Wybierz kartę **poszczególne składniki**
1. Zaznacz pole wyboru **.NET COMPILER Platform SDK**. Znajdziesz go u góry w sekcji **kompilatory, narzędzia kompilacji i środowiska uruchomieniowe** .

Opcjonalnie, aby **Edytor DGML** wyświetlał wykresy w wizualizatorze:

1. Zaznacz pole wyboru **Edytor DGML**. Znajdziesz go w sekcji **Narzędzia kodu** .
