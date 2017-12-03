---
title: "Porady: Tworzenie szablonu niestandardowego działania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ae81b96a348712af58c5e8527f0f04a59689368
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-activity-template"></a>Porady: Tworzenie szablonu niestandardowego działania
Szablony niestandardowe działania są używane do dostosowywania konfiguracji działania, w tym niestandardowych działań złożonych, dzięki czemu użytkownicy nie mają utworzyć każde działanie oddzielnie i skonfigurować ich właściwości i inne ustawienia ręcznie. Te szablony niestandardowe mogą być udostępniane w **przybornika** na [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] lub przy użyciu projektanta rehosted, z którego użytkownicy mogą przeciągnij je na powierzchnię projektu wstępnie skonfigurowane. [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]jest dostarczany z dobrym przykładem takich szablonów: [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) i [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) w [wiadomości projektantów działań](/visualstudio/workflow-designer/messaging-activity-designers) kategorii.  
  
 Pierwsza procedura w tym temacie opisano sposób tworzenia szablonu działań niestandardowych do **opóźnienie** działania, a druga procedura krótko opisano sposób udostępnić go w [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] Aby sprawdzić, czy działa szablonu niestandardowego.  
  
 Szablony niestandardowe działania musi implementować <xref:System.Activities.Presentation.IActivityTemplateFactory>. Interfejs ma jeden <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> metody tworzenia i konfigurowania wystąpienia działania używane w szablonie.  
  
### <a name="to-create-a-template-for-the-delay-activity"></a>Aby utworzyć szablon działania opóźnienia  
  
1.  Uruchom [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3.  W **typów projektów** okienku wybierz **przepływu pracy** z jednej **Visual C#** projektów lub **Visual Basic** grupowania w zależności od sieci Preferencje językowe.  
  
4.  W **szablony** okienku wybierz **Biblioteka działań**.  
  
5.  W **nazwa** wprowadź `DelayActivityTemplate`.  
  
6.  Zaakceptuj ustawienia domyślne w **lokalizacji** i **Nazwa rozwiązania** pola tekstowe, a następnie kliknij przycisk **OK**.  
  
7.  Kliknij prawym przyciskiem myszy katalogu odwołania projektu DelayActivityTemplate w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj odwołanie** otworzyć **Dodaj odwołanie** okno dialogowe.  
  
8.  Przejdź do **.NET** i wybierz **PresentationFramework** z **nazwa składnika** kolumnę po lewej i kliknij przycisk **OK** można dodać odwołania w pliku PresentationFramework.dll.  
  
9. Powtórz tę procedurę, aby dodać odwołania do plików WindowsBase.dll i System.Activities.Presentation.dll.  
  
10. Kliknij prawym przyciskiem myszy projekt DelayActivityTemplate w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** , a następnie **nowy element** otworzyć **Dodaj nowy element**okno dialogowe.  
  
11. Wybierz **klasy** szablonu, nadaj jej nazwę MyDelayTemplate, a następnie kliknij przycisk **OK**.  
  
12. Otwórz plik MyDelayTemplate.cs i dodaj następujące instrukcje.  
  
    ```  
    //Namespaces added  
    using System.Activities;  
    using System.Activities.Statements;  
    using System.Activities.Presentation;  
    using System.Windows;  
    ```  
  
13. Implementowanie <xref:System.Activities.Presentation.IActivityTemplateFactory> z `MyDelayActivity` klasy następującym kodem. Spowoduje to skonfigurowanie opóźnienia na czas trwania 10 sekund.  
  
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
  
### <a name="to-make-the-template-available-in-a-workflow-designer"></a>Aby udostępnić szablon w Projektancie przepływów pracy  
  
1.  Kliknij prawym przyciskiem myszy rozwiązanie DelayActivityTemplate w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** , a następnie **nowy projekt** otworzyć **Dodawanie nowego projektu** okno dialogowe.  
  
2.  Wybierz **Aplikacja konsoli przepływu pracy** szablonu, nadaj jej nazwę `CustomActivityTemplateApp`, a następnie kliknij przycisk **OK**.  
  
3.  Kliknij prawym przyciskiem myszy katalogu odwołania projektu CustomActivityTemplateApp w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj odwołanie** otworzyć **Dodaj odwołanie** okna dialogowego pole.  
  
4.  Przejdź do **projekty** i wybierz **DelayActivityTemplate** z **Nazwa projektu** kolumnę po lewej i kliknij przycisk **OK** do dodania Odwołanie do pliku DelayActivityTemplate.dll utworzonego w ramach pierwszej procedury.  
  
5.  Kliknij prawym przyciskiem myszy projekt CustomActivityTemplateApp w **Eksploratora rozwiązań** i wybierz polecenie **kompilacji** do kompilowania aplikacji.  
  
6.  Kliknij prawym przyciskiem myszy projekt CustomActivityTemplateApp w **Eksploratora rozwiązań** i wybierz polecenie **Ustaw jako projekt startowy**.  
  
7.  Wybierz **uruchomić bez debugowania** z **debugowania** menu i naciśnij dowolny klawisz, aby kontynuować po wyświetleniu monitu z okna cmd.exe.  
  
8.  Otwórz plik Workflow1.xaml a **przybornika**.  
  
9. Zlokalizuj **MyDelayActivity** szablonu w **DelayActivityTemplate** kategorii. Przeciągnij go na powierzchnię projektu. Upewnij się, w **właściwości** okna który `Duration` właściwość została ustawiona na 10 sekund.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.Presentation.IActivityTemplateFactory>  
 [Dostosowywanie projektu przepływu pracy](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)
