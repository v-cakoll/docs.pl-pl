---
title: 'Instrukcje: Tworzenie niestandardowego szablonu działań'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: 4ec84658dbe3039a4d7d714f8da183e6a5eb6ca4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989712"
---
# <a name="how-to-create-a-custom-activity-template"></a>Instrukcje: Tworzenie niestandardowego szablonu działań

Niestandardowe szablony działań służą do dostosowywania konfiguracji działań, w tym niestandardowych działań złożonych, dzięki czemu użytkownicy nie muszą tworzyć poszczególnych działań osobno i konfigurować ich właściwości oraz inne ustawienia ręcznie. Te szablony niestandardowe można udostępnić w **przyborniku** w [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] programie lub z poziomu projektanta, z którego użytkownicy mogą przeciągać je na wstępnie skonfigurowaną powierzchnię projektu. [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]są dostarczane z dobrymi przykładami takich szablonów: [Projektant szablonów SendAndReceiveReply](/visualstudio/workflow-designer/sendandreceivereply-template-designer) oraz [Projektant szablonów ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer) w kategorii [Projektant działań związanych z obsługą wiadomości](/visualstudio/workflow-designer/messaging-activity-designers) .

 W pierwszej procedurze w tym temacie opisano sposób tworzenia niestandardowego szablonu działania dla działania **opóźnienia** i drugiej procedury opisano krótko, jak udostępnić go w programie, [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] aby sprawdzić, czy szablon niestandardowy działa.

 Niestandardowe szablony działań muszą implementować <xref:System.Activities.Presentation.IActivityTemplateFactory>. Interfejs ma pojedynczą <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> metodę, za pomocą której można tworzyć i konfigurować wystąpienia działań używane w szablonie.

## <a name="to-create-a-template-for-the-delay-activity"></a>Aby utworzyć szablon dla działania opóźnionego

1. Uruchom program Visual Studio 2010.

2. W menu **plik** wskaż polecenie **Nowy**, a następnie wybierz pozycję **projekt**.

     **Nowy projekt** zostanie otwarte okno dialogowe.

3. W okienku **typy projektów** wybierz **przepływ pracy** z projektów **wizualnych C#**  lub grup **Visual Basic** w zależności od preferencji językowych.

4. W okienku **Szablony** wybierz pozycję **Biblioteka działań**.

5. W polu **Nazwa** wprowadź `DelayActivityTemplate`wartość.

6. Zaakceptuj wartości domyślne w polach tekstowych **Lokalizacja** i **Nazwa rozwiązania** , a następnie kliknij przycisk **OK**.

7. Kliknij prawym przyciskiem myszy katalog odwołania projektu DelayActivityTemplate w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj odwołanie** , aby otworzyć okno dialogowe **Dodawanie odwołania** .

8. Przejdź do karty **.NET** i wybierz pozycję **platformie docelowej** w kolumnie **Nazwa składnika** po lewej stronie, a następnie kliknij przycisk **OK** , aby dodać odwołanie do pliku platformie docelowej. dll.

9. Powtórz tę procedurę, aby dodać odwołania do plików system. Activities. Presentation. dll i 'Windowsbase. dll.

10. Kliknij prawym przyciskiem myszy projekt DelayActivityTemplate w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj** , a następnie pozycję **nowy element** , aby otworzyć okno dialogowe **Dodaj nowy element** .

11. Wybierz szablon **klasy** , nadaj mu nazwę MyDelayTemplate, a następnie kliknij przycisk **OK**.

12. Otwórz plik MyDelayTemplate.cs i Dodaj następujące instrukcje.

    ```csharp
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. Zaimplementuj <xref:System.Activities.Presentation.IActivityTemplateFactory> `MyDelayActivity` z klasą przy użyciu następującego kodu. Spowoduje to skonfigurowanie opóźnienia o długości 10 sekund.

    ```csharp
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
    ```

14. Wybierz opcję **Kompiluj rozwiązanie** z menu **kompilacja** , aby wygenerować plik DelayActivityTemplate. dll.

### <a name="to-make-the-template-available-in-a-workflow-designer"></a>Aby udostępnić szablon w Projektant przepływu pracy

1. Kliknij prawym przyciskiem myszy rozwiązanie DelayActivityTemplate w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj** , a następnie **Nowy projekt** , aby otworzyć okno dialogowe **Dodawanie nowego projektu** .

2. Wybierz szablon **aplikacja konsoli przepływu pracy** , nadaj mu `CustomActivityTemplateApp`nazwę, a następnie kliknij przycisk **OK**.

3. Kliknij prawym przyciskiem myszy katalog odwołania projektu CustomActivityTemplateApp w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj odwołanie** , aby otworzyć okno dialogowe **Dodawanie odwołania** .

4. Przejdź do karty **projekty** i wybierz pozycję **DelayActivityTemplate** z kolumny **Nazwa projektu** po lewej stronie, a następnie kliknij przycisk **OK** , aby dodać odwołanie do pliku DelayActivityTemplate. dll, który został utworzony w pierwszej procedurze.

5. Kliknij prawym przyciskiem myszy projekt CustomActivityTemplateApp w **Eksplorator rozwiązań** i wybierz polecenie **Kompiluj** , aby skompilować aplikację.

6. Kliknij prawym przyciskiem myszy projekt CustomActivityTemplateApp w **Eksplorator rozwiązań** i wybierz pozycję **Ustaw jako projekt startowy**.

7. Wybierz opcję **Uruchom bez debugowania** z menu **Debuguj** i naciśnij dowolny klawisz, aby kontynuować po wyświetleniu monitu z okna cmd. exe.

8. Otwórz plik Workflow1. XAML i Otwórz **Przybornik**.

9. Znajdź szablon " **Opóźnij** " w kategorii **DelayActivityTemplate** . Przeciągnij go na powierzchnię projektu. Upewnij się, że `Duration` w oknie właściwości ustawiono wartość 10 sekund.

## <a name="example"></a>Przykład
 Plik MyDelayActivity.cs powinien zawierać następujący kod.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

//Namespaces added
using System.Activities;
using System.Activities.Statements;
using System.Activities.Presentation;
using System.Windows;

namespace DelayActivityTemplate
{
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
}
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [Dostosowywanie środowiska projektowania przepływu pracy](customizing-the-workflow-design-experience.md)
