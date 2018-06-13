---
title: 'Zadanie 1: Tworzenie nowej aplikacji systemu Windows Presentation Foundation'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 5576d6f893aa405d454758387334b85a473b0c73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517952"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>Zadanie 1: Tworzenie nowej aplikacji systemu Windows Presentation Foundation
W ramach tego zadania utworzysz pustą aplikację systemu Windows Presentation Foundation (WPF) przy użyciu szablonu z programu Visual Studio aplikacji WPF i dodać odwołanie do odpowiedniego [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] zestawy przepływu pracy.  
  
### <a name="to-create-the-wpf-application-project"></a>Aby utworzyć projekt aplikacji WPF  
  
1.  Otwórz program Visual Studio i na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** oknie dialogowym wybierz **Visual C#** lub **Visual Basic** z **zainstalowane szablony** w okienku po lewej stronie pole. Jeśli nie ma preferowanego języka, sprawdź w obszarze **inne języki**.  
  
3.  Wybierz **Windows** w **zainstalowane szablony** okienka.  
  
4.  W górnym okienku, upewnij się, że (wartość domyślna) **.NET Framework 4** zostało wybrane w polu listy rozwijanej, a następnie wybierz **aplikacji WPF**.  
  
5.  Ustaw nazwę projektu, aby **HostingApplication** w dolnej części okna.  
  
6.  Ustaw nazwę rozwiązania **RehostingTheDesigner**.  
  
7.  Kliknij przycisk **OK** do utworzenia projektu aplikacji. Program Visual Studio podstawowy interfejs użytkownika WPF aplikacji i zawiera odpowiednią XAML i plików z kodem.  
  
8.  Dodaj odwołania do **WorkflowModel** zestawów. Aby to zrobić, w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **HostingApplication** projekt i wybierz **Dodaj odwołanie**.  
  
9. W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET** , naciśnij i przytrzymaj klawisz CTRL, wybierz następujące zestawy, a następnie kliknij **OK**:  
  
    -   System.Activities  
  
    -   System.Activities.Presentation  
  
    -   System.Activities.Core.Presentation  
  
10. Kliknij przycisk **OK**.  
  
11. Zobacz [zadanie 2: Host projektanta przepływów pracy](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) informacje na temat hosta kanwy projektanta projektu przepływu pracy.  
  
## <a name="see-also"></a>Zobacz też  
 [Rehostowanie projektanta przepływu pracy](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Zadanie 2: Hostowanie projektanta przepływu pracy](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
