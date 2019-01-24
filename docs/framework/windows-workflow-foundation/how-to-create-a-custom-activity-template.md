---
title: 'Instrukcje: Tworzenie niestandardowego szablonu działań'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: c90721676fc5b77704ee86bcd5e98c99e3af6683
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512714"
---
# <a name="how-to-create-a-custom-activity-template"></a>Instrukcje: Tworzenie niestandardowego szablonu działań

Szablony niestandardowe działania są używane do dostosowywania konfiguracji działań, w tym złożone działania niestandardowe, aby użytkownicy muszą utworzyć każde działanie indywidualnie i skonfigurować ich właściwości i inne ustawienia ręcznie. Te szablony niestandardowe mogą być udostępniane w **przybornika** na [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] lub rehostowanym projektancie, z którego użytkowników można przeciągnąć je na powierzchni projektowej wstępnie skonfigurowane. [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] jest dostarczany z dobrym przykładem takich szablonów: [SendAndReceiveReply, Projektant szablonów](/visualstudio/workflow-designer/sendandreceivereply-template-designer) i [ReceiveAndSendReply, Projektant szablonów](/visualstudio/workflow-designer/receiveandsendreply-template-designer) w [Projektanci działań Messaging](/visualstudio/workflow-designer/messaging-activity-designers) kategorii.

 Pierwsza procedura w tym temacie opisano sposób tworzenia niestandardowego szablonu działań dla **opóźnienie** działanie i druga procedura krótko opisano sposób udostępnić go w [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] można sprawdzić, czy działa szablonu niestandardowego.

 Szablony niestandardowe działanie musi implementować <xref:System.Activities.Presentation.IActivityTemplateFactory>. Interfejs ma jeden <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> metoda, za pomocą którego można tworzyć i konfigurować wystąpienia działania używany w szablonie.

## <a name="to-create-a-template-for-the-delay-activity"></a>Aby utworzyć szablon działania opóźnienia

1.  Start Visual Studio 2010.

2.  Na **pliku** menu wskaż **New**, a następnie wybierz pozycję **projektu**.

     **Nowy projekt** zostanie otwarte okno dialogowe.

3.  W **typów projektów** okienku wybierz **przepływu pracy** albo **Visual C#** projektów lub **języka Visual Basic** grupowania w zależności od usługi Preferencje językowe.

4.  W **szablony** okienku wybierz **Biblioteka działań**.

5.  W **nazwa** wprowadź `DelayActivityTemplate`.

6.  Zaakceptuj ustawienia domyślne w **lokalizacji** i **Nazwa rozwiązania** pól tekstowych, a następnie kliknij **OK**.

7.  Kliknij prawym przyciskiem myszy katalog odwołania do projektu DelayActivityTemplate w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj odwołanie** otworzyć **Dodaj odwołanie** okno dialogowe.

8.  Przejdź do **.NET** kartę, a następnie wybierz pozycję **PresentationFramework** z **nazwa składnika** kolumnę po lewej stronie i kliknij przycisk **OK** można dodać odwołania w pliku PresentationFramework.dll.

9. Powtórz tę procedurę, aby dodać odwołania do plików WindowsBase.dll i System.Activities.Presentation.dll.

10. Kliknij prawym przyciskiem myszy projekt DelayActivityTemplate w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** i następnie **nowy element** otworzyć **Dodaj nowy element**okno dialogowe.

11. Wybierz **klasy** szablonu, nadaj jej nazwę MyDelayTemplate, a następnie kliknij przycisk **OK**.

12. Otwórz plik MyDelayTemplate.cs i dodaj następujące instrukcje.

    ```
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. Implementowanie <xref:System.Activities.Presentation.IActivityTemplateFactory> z `MyDelayActivity` klasy z następującym kodem. Umożliwia skonfigurowanie opóźnienie na czas trwania jest równy 10 sekund.

    ```
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

14. Wybierz **Kompiluj rozwiązanie** z **kompilacji** menu, aby wygenerować plik DelayActivityTemplate.dll.

### <a name="to-make-the-template-available-in-a-workflow-designer"></a>Aby szablon był dostępny w Projektancie przepływu pracy

1.  Kliknij prawym przyciskiem myszy rozwiązanie DelayActivityTemplate w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** i następnie **nowy projekt** otworzyć **Dodaj nowy projekt** okno dialogowe.

2.  Wybierz **Aplikacja konsoli przepływu pracy** szablonu, nadaj jej nazwę `CustomActivityTemplateApp`, a następnie kliknij przycisk **OK**.

3.  Kliknij prawym przyciskiem myszy katalog odwołania do projektu CustomActivityTemplateApp w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj odwołanie** otworzyć **Dodaj odwołanie** okna dialogowego pole.

4.  Przejdź do **projektów** kartę, a następnie wybierz pozycję **DelayActivityTemplate** z **Nazwa projektu** kolumnę po lewej stronie i kliknij przycisk **OK** do dodania Odwołanie do pliku DelayActivityTemplate.dll, który został utworzony w pierwszej procedurze.

5.  Kliknij prawym przyciskiem myszy projekt CustomActivityTemplateApp w **Eksploratora rozwiązań** i wybierz polecenie **kompilacji** do kompilowania aplikacji.

6.  Kliknij prawym przyciskiem myszy projekt CustomActivityTemplateApp w **Eksploratora rozwiązań** i wybierz polecenie **Ustaw jako projekt startowy**.

7.  Wybierz **Rozpocznij bez debugowania** z **debugowania** menu i naciśnij dowolny klawisz, aby kontynuować po wyświetleniu monitu z okna cmd.exe.

8.  Otwórz plik Workflow1.xaml a **przybornika**.

9. Znajdź **MyDelayActivity** szablonu w **DelayActivityTemplate** kategorii. Przeciągnij go na powierzchni projektowej. Upewnij się, w **właściwości** okna, `Duration` właściwość została ustawiona na 10 sekund.

## <a name="example"></a>Przykład
 Plik MyDelayActivity.cs powinien zawierać następujący kod.

```
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
- [Dostosowywanie środowiska projektowania przepływu pracy](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)