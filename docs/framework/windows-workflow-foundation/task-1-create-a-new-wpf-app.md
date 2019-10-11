---
title: Zadanie 1. Tworzenie nowej aplikacji Windows Presentation Foundation
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 3205840da575041b449eb841fc8084e89937fca7
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031897"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>Zadanie 1. Tworzenie nowej aplikacji Windows Presentation Foundation

W tym zadaniu utworzysz pustą aplikację Windows Presentation Foundation (WPF) za pomocą szablonu aplikacji WPF programu Visual Studio i dodasz odwołania do odpowiednich zestawów przepływów pracy [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].  
  
## <a name="to-create-the-wpf-application-project"></a>Aby utworzyć projekt aplikacji WPF

1. Otwórz program Visual Studio i w menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

2. W oknie dialogowym **Nowy projekt** wybierz pozycję **Wizualizacja C#**  lub **Visual Basic** w okienku **zainstalowane szablony** po lewej stronie pola. Jeśli wybrany język nie jest wyświetlany, zapoznaj się z **innymi językami**.

3. W okienku **zainstalowane szablony** wybierz pozycję **Windows** .

4. W górnym okienku upewnij się, że (wartość domyślna) **.NET Framework 4** została wybrana w polu listy rozwijanej, a następnie wybierz pozycję **Aplikacja WPF**.

5. Ustaw nazwę projektu na **HostingApplication** w dolnej części okna.

6. Ustaw nazwę rozwiązania na **RehostingTheDesigner**.

7. Kliknij przycisk **OK** , aby utworzyć projekt aplikacji. Program Visual Studio tworzy podstawowy interfejs użytkownika WPF dla aplikacji i zawiera odpowiednie pliki XAML i powiązane z kodem.

8. Dodaj odwołania do zestawów **WorkflowModel** . W tym celu w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **HostingApplication** i wybierz polecenie **Dodaj odwołanie**.

9. W oknie dialogowym **Dodaj odwołanie** kliknij kartę **.NET** , przytrzymaj wciśnięty klawisz CTRL, wybierz następujące zestawy, a następnie kliknij przycisk **OK**:

    - System. Activities
    - System. Activities. Presentation
    - System. Activities. Core. Presentation

10. Zobacz [zadanie 2: hostowanie Projektant przepływu pracy,](task-2-host-the-workflow-designer.md) aby dowiedzieć się, jak hostować kanwę projektu projektanta przepływu pracy.

## <a name="see-also"></a>Zobacz także

- [Hostowanie Projektant przepływu pracy](rehosting-the-workflow-designer.md)
- [Zadanie 2. hostowanie Projektant przepływu pracy](task-2-host-the-workflow-designer.md)
