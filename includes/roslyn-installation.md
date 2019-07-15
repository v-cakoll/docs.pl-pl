---
ms.openlocfilehash: dab6b435a885d862d08f94dd31de79625f19bcc0
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2019
ms.locfileid: "67870509"
---
## <a name="installation-instructions---visual-studio-installer"></a>Instrukcje dotyczące instalacji — Instalatora programu Visual Studio

Istnieją dwa różne sposoby, aby znaleźć **zestawu SDK platformy kompilatora .NET** w **Instalatora programu Visual Studio**:

### <a name="install-using-the-visual-studio-installer---workloads-view"></a>Instalowanie przy użyciu Instalatora programu Visual Studio — Wyświetlanie obciążeń

Zestaw SDK platformy kompilatora .NET nie jest automatycznie wybierany jako część obciążenia projektowania rozszerzenia programu Visual Studio. Musisz wybrać go jako składnik opcjonalny.

1. Uruchom **Instalatora programu Visual Studio** 
1. Wybierz **zmodyfikować** 
1. Sprawdź **programowanie rozszerzeń programu Visual Studio** obciążenia.
1. Otwórz **programowanie rozszerzeń programu Visual Studio** węzeł w drzewie podsumowania.
1. Pole wyboru dla **zestawu SDK platformy kompilatora .NET**. Znajdziesz go ostatnio w ramach opcjonalnych składników.

Opcjonalnie można też **Edytor DGML** do wyświetlania wykresów w wizualizatorze:

1. Otwórz **poszczególne składniki** węzeł w drzewie podsumowania.
1. Pole wyboru dla **Edytor DGML**

### <a name="install-using-the-visual-studio-installer---individual-components-tab"></a>Instalowanie przy użyciu Instalatora programu Visual Studio — karcie poszczególne składniki

1. Uruchom **Instalatora programu Visual Studio** 
1. Wybierz **zmodyfikować** 
1. Wybierz **poszczególne składniki** kartę 
1. Pole wyboru dla **zestawu SDK platformy kompilatora .NET**. Znajdziesz ją u góry strony, w obszarze **kompilatory, narzędzia do kompilacji i środowiska uruchomieniowe** sekcji.

Opcjonalnie można też **Edytor DGML** do wyświetlania wykresów w wizualizatorze:

1. Pole wyboru dla **Edytor DGML**. Znajdziesz go w folderze **kodu narzędzia** sekcji.
