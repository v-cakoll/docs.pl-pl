---
title: 'Instrukcje: Uzyskiwanie dostępu do usługi z poziomu aplikacji przepływu pracy'
ms.date: 03/30/2017
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
ms.openlocfilehash: c524dc07106f039d9dc6c17ee6fb966321b6da24
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964528"
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a>Instrukcje: Uzyskiwanie dostępu do usługi z poziomu aplikacji przepływu pracy
W tym temacie opisano sposób wywoływania usługi przepływu pracy z poziomu aplikacji konsolowej przepływu pracy. Jest to zależne od ukończenia procedury [: Tworzenie usługi przepływu pracy z działaniami obsługi komunikatów](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) . Chociaż w tym temacie opisano sposób wywoływania usługi przepływu pracy z poziomu aplikacji przepływu pracy, można używać tych samych metod do wywoływania dowolnej usługi Windows Communication Foundation (WCF) z poziomu aplikacji przepływu pracy.

### <a name="create-a-workflow-console-application-project"></a>Tworzenie projektu aplikacji konsolowej przepływu pracy

1. Start Visual Studio 2012.

2. Załaduj projekt MyWFService utworzony w temacie [instrukcje: Tworzenie usługi przepływu pracy z działaniami obsługi komunikatów](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) .

3. Kliknij prawym przyciskiem myszy rozwiązanie **MyWFService** w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj**, **Nowy projekt**. Wybierz pozycję **przepływ pracy** w **zainstalowanych szablonach** i **aplikacji konsoli przepływu pracy** z listy typów projektów. Nazwij projekt MyWFClient i Użyj domyślnej lokalizacji, jak pokazano na poniższej ilustracji.

     ![Okno dialogowe Dodawanie nowego projektu](./media/how-to-access-a-service-from-a-workflow-application/add-new-project-dialog.jpg)

     Kliknij przycisk **OK** , aby odrzucić **okno dialogowe Dodawanie nowego projektu**.

4. Po utworzeniu projektu plik Workflow1. XAML zostanie otwarty w projektancie. Kliknij kartę **Przybornik** , aby otworzyć przybornik, jeśli nie jest jeszcze otwarty i kliknij pinezkę, aby pozostawić otwarte okno przybornika.

5. Naciśnij klawisz **Ctrl**+**F5** , aby skompilować i uruchomić usługę. Tak jak wcześniej jest uruchamiany serwer ASP.NET Development, a program Internet Explorer wyświetla stronę pomocy programu WCF. Zwróć uwagę na identyfikator URI tej strony, ponieważ musisz użyć jej w następnym kroku.

     ![Przeglądarka IE wyświetlająca stronę pomocy i identyfikator URI programu WCF](./media/how-to-access-a-service-from-a-workflow-application/ie-wcf-help-page-uri.jpg)

6. Kliknij prawym przyciskiem myszy projekt **MyWFClient** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj** > **odwołanie do usługi**. Kliknij przycisk **Odnajdź** , aby wyszukać bieżące rozwiązanie dla dowolnych usług. Kliknij trójkąt obok pozycji Service1. xamlx na liście usługi. Kliknij trójkąt obok pozycji Service1, aby wyświetlić listę kontraktów wdrożonych przez usługę Service1. Rozwiń węzeł **Service1** na liście **usługi** . Operacja echo zostanie wyświetlona na liście **operacje** , jak pokazano na poniższej ilustracji.

     ![Okno dialogowe Dodaj odwołanie do usługi](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference.jpg)

     Zachowaj domyślną przestrzeń nazw i kliknij przycisk **OK** , aby zamknąć okno dialogowe **Dodaj odwołanie do usługi** . Zostanie wyświetlone następujące okno dialogowe.

     ![Okno dialogowe powiadomienia Dodaj odwołanie do usługi](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference-dialog.jpg)

     Kliknij przycisk **OK** , aby zamknąć okno dialogowe. Następnie naciśnij kombinację klawiszy CTRL + SHIFT + B, aby skompilować rozwiązanie. Uwaga w przyborniku dodano nową sekcję o nazwie **MyWFClient. ServiceReference1. Activities**. Rozwiń tę sekcję i zwróć uwagę na działanie ECHA, które zostało dodane, jak pokazano na poniższej ilustracji.

     ![Aktywność Echo w przyborniku](./media/how-to-access-a-service-from-a-workflow-application/echo-activity-toolbox.jpg)

7. Przeciągnij i upuść działanie <xref:System.Activities.Statements.Sequence> na powierzchnię projektanta. Znajduje się w sekcji **przepływ sterowania** w przyborniku.

8. Po zaznaczeniu działania <xref:System.Activities.Statements.Sequence> kliknij łącze **zmienne** i Dodaj zmienną ciągu o nazwie `inString`. Nadaj zmiennej wartość domyślną `"Hello, world"` jak również zmienną ciągu o nazwie `outString`, jak pokazano na poniższym diagramie.

     ![Dodawanie zmiennej niebędącej ciągiem](./media/how-to-access-a-service-from-a-workflow-application/add-instring-variable.jpg)

9. Przeciągnij i upuść działanie **echo** do <xref:System.Activities.Statements.Sequence>. W oknie właściwości Powiąż argument `inMsg` do zmiennej `inString` i argumentu `outMsg` z zmienną `outString`, jak pokazano na poniższej ilustracji. Powoduje to przekazanie wartości zmiennej `inString` do operacji, a następnie wartości zwracanej i umieszczenie jej w zmiennej `outString`.

     ![Powiązywanie argumentów ze zmiennymi](./media/how-to-access-a-service-from-a-workflow-application/bind-arguments-variables.jpg)

10. Przeciągnij i upuść działanie **WriteLine** poniżej działania **echo** , aby wyświetlić ciąg zwracany przez wywołanie usługi. Działanie **WriteLine** znajduje się w węźle elementy **pierwotne** w przyborniku. Powiąż argument **Text** działania **WriteLine** z zmienną `outString`, wpisując `outString` w polu tekstowym działania **WriteLine** . Przepływ pracy powinien teraz wyglądać tak, jak na poniższej ilustracji.

     ![Pełny przepływ pracy klienta](./media/how-to-access-a-service-from-a-workflow-application/complete-client-workflow.jpg)

11. Kliknij prawym przyciskiem myszy rozwiązanie MyWFService i wybierz pozycję **Ustaw projekty startowe..** .. Wybierz przycisk radiowy **wiele projektów startowych** , a następnie wybierz pozycję **Uruchom** dla każdego projektu w kolumnie **Akcja** , jak pokazano na poniższej ilustracji.

     ![Opcje projektów startowych](./media/how-to-access-a-service-from-a-workflow-application/startup-project-options.jpg)

12. Naciśnij kombinację klawiszy CTRL + F5, aby uruchomić usługę i klienta. Serwer programistyczny ASP.NET obsługuje usługę, program Internet Explorer wyświetla stronę pomocy programu WCF, a aplikacja przepływu pracy klienta jest uruchamiana w oknie konsoli i wyświetla ciąg zwracany przez usługę ("Hello, World").

## <a name="see-also"></a>Zobacz także

- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Instrukcje: tworzenie przepływu pracy usługi przy użyciu działań dotyczących komunikatów](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Zużywanie usługi WCF z przepływu pracy w projekcie sieci Web](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
