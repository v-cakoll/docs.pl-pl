---
title: 'Instrukcje: Uzyskiwanie dostępu do usługi z poziomu aplikacji przepływu pracy'
ms.date: 03/30/2017
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
ms.openlocfilehash: 5bc18b446d4bf818c874839a421793a997ddc543
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43674060"
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a>Instrukcje: Uzyskiwanie dostępu do usługi z poziomu aplikacji przepływu pracy
W tym temacie opisano sposób wywoływania usługi przepływu pracy z aplikacji konsoli przepływu pracy. To zależy od ukończenia [jak: Tworzenie usługi przepływu pracy przy użyciu działań Messaging](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) tematu. Mimo że w tym temacie opisano sposób wywoływania usługi przepływu pracy z poziomu aplikacji przepływu pracy, te same metody można wywołać dowolną usługę Windows Communication Foundation (WCF) z poziomu aplikacji przepływu pracy.

### <a name="create-a-workflow-console-application-project"></a>Utwórz projekt aplikacji konsoli przepływu pracy

1.  Rozpocznij [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].

2.  Załaduj projekt MyWFService został utworzony w [porady: Tworzenie usługi przepływu pracy przy użyciu działań Messaging](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) tematu.

3.  Kliknij prawym przyciskiem myszy **MyWFService** rozwiązania **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy projekt**. Wybierz **przepływu pracy** w **zainstalowane szablony** i **Aplikacja konsoli przepływu pracy** z listy typów projektów. Nazwij projekt MyWFClient i użyj domyślnej lokalizacji, jak pokazano na poniższej ilustracji.

     ![Dodawanie okna dialogowego Nowy projekt](../../../../docs/framework/wcf/feature-details/media/addnewprojectdlg.JPG "AddNewProjectDlg")

     Kliknij przycisk **OK** przycisk, aby odrzucić **okna dialogowego Dodawanie nowego projektu**.

4.  Po utworzeniu projektu plik Workflow1.xaml zostanie otwarty w projektancie. Kliknij przycisk **przybornika** kartę, aby otworzyć przybornik, jeśli nie jest już otworzyć i kliknij przycisk pinezki, aby nie zamykaj okna przybornika.

5.  Naciśnij klawisz **Ctrl**+**F5** Aby skompilować i uruchomić usługę. Tak jak poprzednio jest uruchamiane w ASP.NET Development Server i programu Internet Explorer wyświetla stronę pomocy programu WCF. Należy zauważyć identyfikator URI dla tej strony, ponieważ musisz ją wykorzystać w następnym kroku.

     ![IE wyświetlanie Pomocy programu WCF — strona oraz identyfikatora URI](../../../../docs/framework/wcf/feature-details/media/iewcfhelppagewuri.JPG "IEWCFHelpPageWURI")

6.  Kliknij prawym przyciskiem myszy **MyWFClient** projektu w **Eksploratora rozwiązań** i wybierz **Dodaj** > **odwołanie do usługi**. Kliknij przycisk **odnajdź** przycisk, aby wyszukać bieżące rozwiązanie dla wszystkich usług. Kliknij przycisk trójkąta obok Service1.xamlx na liście usług. Kliknij przycisk trójkąta obok Service1, aby wyświetlić listę zamówień implementowane przez usługę Service1. Rozwiń **Service1** w węźle **usług** listy. Operacja echa są wyświetlane w **operacji** listy, jak pokazano na poniższej ilustracji.

     ![Dodaj odwołanie do usługi w oknie dialogowym](../../../../docs/framework/wcf/feature-details/media/addservicereference.JPG "AddServiceReference")

     Zachowaj domyślny obszar nazw i kliknij przycisk **OK** odrzucać **Dodaj odwołanie do usługi** okna dialogowego. Zostanie wyświetlone następujące okno dialogowe.

     ![Okno dialogowe Dodawanie usługi odwołanie powiadomień](../../../../docs/framework/wcf/feature-details/media/asrdlg.JPG "ASRDlg")

     Kliknij przycisk **OK** aby zamknąć okno dialogowe. Następnie naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie. Powiadomienia w przyborniku dodano nową sekcję o nazwie **MyWFClient.ServiceReference1.Activities**. Rozwiń tę sekcję i zwróć uwagę, działanie Echo, do którego dodano, jak pokazano na poniższej ilustracji.

     ![Echo działania w przyborniku](../../../../docs/framework/wcf/feature-details/media/echoactivity.JPG "EchoActivity")

7.  Przeciąganie i upuszczanie <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` działania na powierzchnię projektanta. Jest on w **przepływ sterowania** sekcji przybornika.

8.  Za pomocą <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` działania w trybie koncentracji uwagi, kliknij przycisk **zmienne** łącze i Dodaj zmienną ciągu o nazwie `inString`. Jej nadać wartość domyślną `"Hello, world"` oraz na zmienną ciągu o nazwie `outString` jak pokazano na poniższym diagramie.

     ![Dodawanie zmiennej](../../../../docs/framework/wcf/feature-details/media/instringvar.JPG "inStringVar")

9. Przeciąganie i upuszczanie **Echo** działanie do <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence`. W oknie dialogowym Właściwości powiązania `inMsg` argument `inString` zmiennej i `outMsg` argument `outString` zmiennej, jak pokazano na poniższej ilustracji. To powoduje przekazanie wartości `inString` zmiennej do operacji i przyjmuje wartość zwracaną i umieszcza je w `outString` zmiennej.

     ![Powiązywanie argumenty zmienne](../../../../docs/framework/wcf/feature-details/media/argumentbind.JPG "ArgumentBind")

10. Przeciąganie i upuszczanie **WriteLine** działania poniżej **Echo** działanie, aby wyświetlić ciąg zwracany przez wywołanie usługi. **WriteLine** działań znajduje się w **podstawowych** węzła w przyborniku. Powiązanie **tekstu** argument **WriteLine** działanie `outString` zmiennej, wpisując `outString` w polu tekstowym na **WriteLine** działania. Przepływ pracy powinien teraz wyglądać podobnie do poniższej ilustracji.

     ![Przepływ pracy klienta pełną](../../../../docs/framework/wcf/feature-details/media/completeclientwf.JPG "CompleteClientWF")

11. Kliknij prawym przyciskiem myszy rozwiązanie MyWFService, a następnie wybierz pozycję **Ustaw projekty startowe...** . Wybierz **wiele projektów startowych** przycisk radiowy, a następnie wybierz pozycję **Start** dla każdego projektu w **akcji** kolumny, jak pokazano na poniższej ilustracji.

     ![Uruchamianie projektów opcje](../../../../docs/framework/wcf/feature-details/media/startupprojects.JPG "projektów startowych")

12. Naciśnij klawisze Ctrl + F5, aby uruchomić usługę i klienta. ASP.NET Development Server hostuje usługę, program Internet Explorer wyświetla programu WCF — strona pomocy, a aplikacja kliencka przepływu pracy jest uruchamiany w oknie konsoli i wyświetla ciąg zwracany przez usługę ("Hello, world").

## <a name="see-also"></a>Zobacz też

- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Instrukcje: tworzenie przepływu pracy usługi przy użyciu działań dotyczących komunikatów](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Korzystanie z usługi WCF z przepływu pracy w projekcie sieci Web](https://go.microsoft.com/fwlink/?LinkId=207725)