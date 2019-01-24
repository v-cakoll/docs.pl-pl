---
title: 'Zadanie 1: Tworzenie nowej aplikacji Windows Presentation Foundation'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 39cd901c0129124bece8e8d3a573fd45209cfb00
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679412"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>Zadanie 1: Tworzenie nowej aplikacji Windows Presentation Foundation
W tym zadaniu utworzysz pustą aplikację Windows Presentation Foundation (WPF) za pomocą szablonu programu Visual Studio w aplikacji WPF i dodać odwołania do odpowiednich [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] zestawy przepływu pracy.  
  
### <a name="to-create-the-wpf-application-project"></a>Aby utworzyć projekt aplikacji WPF  
  
1.  Otwórz program Visual Studio i **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** okna dialogowego wybierz opcję **Visual C#**  lub **języka Visual Basic** z **zainstalowane szablony** w okienku po lewej stronie strony pola. Jeśli nie ma preferowanego języka, sprawdź w obszarze **inne języki**.  
  
3.  Wybierz **Windows** w **zainstalowane szablony** okienka.  
  
4.  W górnym okienku upewnij się, że (wartość domyślna) **.NET Framework 4** zostało wybrane w polu listy rozwijanej, a następnie wybierz **aplikacji WPF**.  
  
5.  Ustaw nazwę projektu, aby **HostingApplication** w dolnej części okna.  
  
6.  Ustaw nazwę rozwiązania na **RehostingTheDesigner**.  
  
7.  Kliknij przycisk **OK** utworzenie projektu aplikacji. Visual Studio tworzy podstawowe WPF UI dla aplikacji i obejmuje odpowiednie XAML i plikami CodeBehind.  
  
8.  Dodaj odwołania do **WorkflowModel** zestawów. Aby to zrobić, w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **HostingApplication** projektu, a następnie wybierz **Dodaj odwołanie**.  
  
9. W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET** kartę, naciśnij i przytrzymaj klawisz CTRL, wybierz następujące zestawy, a następnie kliknij **OK**:  
  
    -   System.Activities  
  
    -   System.Activities.Presentation  
  
    -   System.Activities.Core.Presentation  
  
10. Kliknij przycisk **OK**.  
  
11. Zobacz [zadanie 2: Hostowanie projektanta przepływu pracy](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) Aby dowiedzieć się, jak hostować na kanwie projektanta projektu przepływu pracy.  
  
## <a name="see-also"></a>Zobacz także
- [Rehostowanie projektanta przepływu pracy](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)
- [Zadanie 2. Hostowanie projektanta przepływu pracy](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
