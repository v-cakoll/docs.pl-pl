---
title: "Instrukcje: Uzyskiwanie dostępu do usługi z poziomu aplikacji przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d2d87c045fe81e3f5bf2cb490e47fb5fbd6bc7a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a>Instrukcje: Uzyskiwanie dostępu do usługi z poziomu aplikacji przepływu pracy
W tym temacie opisano sposób wywoływania usługi przepływu pracy z aplikacji konsoli przepływu pracy. Zależy on od zakończenia [porady: Tworzenie usługi przepływu pracy z działaniami wiadomości](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) tematu. Mimo że w tym temacie opisano sposób wywoływania usługi przepływu pracy z poziomu aplikacji przepływu pracy, te same metody można wywołać żadnego [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi z poziomu aplikacji przepływu pracy.  
  
### <a name="create-a-workflow-console-application-project"></a>Utwórz projekt aplikacji konsoli przepływu pracy  
  
1.  Uruchom [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Załadować projekt MyWFService utworzony w [porady: Tworzenie usługi przepływu pracy z działaniami wiadomości](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) tematu.  
  
3.  Kliknij prawym przyciskiem myszy **MyWFService** rozwiązania **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy projekt**. Wybierz **przepływu pracy** w **zainstalowane szablony** i **Aplikacja konsoli przepływu pracy** z listy typów projektów. Nazwij projekt MyWFClient i użyj domyślnej lokalizacji, jak pokazano na poniższej ilustracji.  
  
     ![Okno dialogowe nowego projektu dodać](../../../../docs/framework/wcf/feature-details/media/addnewprojectdlg.JPG "AddNewProjectDlg")  
  
     Kliknij przycisk **OK** przycisk, aby odrzucić **okno dialogowe Dodawanie nowego projektu**.  
  
4.  Po utworzeniu projektu Workflow1.xaml plik jest otwarty w projektancie. Kliknij przycisk **przybornika** kartę, aby otworzyć przybornika, jeśli nie jest już otworzyć i kliknij przycisk pinezki, aby utrzymać otwarte okno przybornika.  
  
5.  Naciśnij klawisze Ctrl + F5, aby skompilować i uruchomić usługę. Jak wcześniej jest uruchamiane w ASP.NET Development Server i programu Internet Explorer zostanie wyświetlona strona pomocy usługi WCF. Identyfikator URI dla tej strony można zauważyć, jak korzystać w następnym kroku.  
  
     ![IE wyświetlania programu WCF — strona pomocy oraz identyfikatora URI](../../../../docs/framework/wcf/feature-details/media/iewcfhelppagewuri.JPG "IEWCFHelpPageWURI")  
  
6.  Kliknij prawym przyciskiem myszy **MyWFClient** projektu w **Eksploratora rozwiązań** i wybierz **Dodaj odwołanie do usługi**. Kliknij przycisk **odnajdowania** przycisk, aby wyszukać bieżącego rozwiązania dla wszystkich usług. Kliknij trójkąt obok Service1.xamlx na liście usług. Kliknij trójkąt obok Service1 na liście kontraktów zaimplementowanych przez usługę Service1. Rozwiń węzeł **Service1** w węźle **usług** listy. Operacja Echo jest wyświetlany w **operacji** listy, jak pokazano na poniższej ilustracji.  
  
     ![Dodaj odwołanie do usługi w oknie dialogowym](../../../../docs/framework/wcf/feature-details/media/addservicereference.JPG "AddServiceReference")  
  
     Zachowaj domyślną przestrzeń nazw i kliknij przycisk **OK** aby odrzucić **Dodaj odwołanie do usługi** okna dialogowego. Zostanie wyświetlone następujące okno dialogowe.  
  
     ![Dodaj usługi powiadomień okna dialogowego odwołania do](../../../../docs/framework/wcf/feature-details/media/asrdlg.JPG "ASRDlg")  
  
     Kliknij przycisk **OK** aby zamknąć okno dialogowe. Następnie naciśnij kombinację klawiszy CTRL + SHIFT + B w celu skompilowania rozwiązania. Powiadomienie w przyborniku dodano nową sekcję o nazwie **MyWFClient.ServiceReference1.Activities**. Rozwiń tę sekcję i zwróć uwagę, działanie Echo dodano, jak pokazano na poniższej ilustracji.  
  
     ![Echo działania w przyborniku](../../../../docs/framework/wcf/feature-details/media/echoactivity.JPG "EchoActivity")  
  
7.  Przeciągnij i upuść <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` działania na powierzchnię projektanta. Znajduje się w **przepływ sterowania** sekcji przybornika.  
  
8.  Z <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` działania w fokus, kliknij przycisk **zmienne** link i dodaj ciąg zmiennej o nazwie `inString`. Nadaj wartość domyślną zmiennej `"Hello, world"` oraz zmienna typu ciąg o nazwie `outString` jak pokazano na poniższym diagramie.  
  
     ![Dodawanie zmiennej](../../../../docs/framework/wcf/feature-details/media/instringvar.JPG "inStringVar")  
  
9. Przeciągnij i upuść **Echo** działania do <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence`. W oknie Właściwości powiązania `inMsg` argument `inString` zmiennej i `outMsg` argument `outString` zmiennej, jak pokazano na poniższej ilustracji. To przekazuje wartości `inString` zmiennej dla działania i przyjmuje wartość zwracaną i umieszcza je w `outString` zmiennej.  
  
     ![Powiązanie argumenty zmienne](../../../../docs/framework/wcf/feature-details/media/argumentbind.JPG "ArgumentBind")  
  
10. Przeciągnij i upuść **WriteLine** działania poniżej **Echo** działanie, aby wyświetlić ciąg zwrócony przez wywołanie usługi. **WriteLine** działanie znajduje się w **podstawowych** węzła w przyborniku. Powiąż **tekst** argument **WriteLine** do działania `outString` zmiennej, wpisując `outString` w polu tekstowym na **WriteLine** działania. Przepływ pracy powinna wyglądać podobnie do poniższej ilustracji.  
  
     ![Przepływ pracy klienta pełną](../../../../docs/framework/wcf/feature-details/media/completeclientwf.JPG "CompleteClientWF")  
  
11. Kliknij prawym przyciskiem myszy rozwiązanie MyWFService i wybierz **Ustaw projekty startowe...** . Wybierz **wiele projektów startowych** przycisku radiowego i wybierz **Start** dla każdego projektu w **akcji** kolumny, jak pokazano na poniższej ilustracji.  
  
     ![Opcje projektów uruchamiania](../../../../docs/framework/wcf/feature-details/media/startupprojects.JPG "projektów startowych")  
  
12. Naciśnij klawisze Ctrl + F5, aby uruchomić zarówno usługę i klienta. ASP.NET Development Server hostuje usługę, program Internet Explorer zostanie wyświetlona strona pomocy WCF i aplikacji klienckiej przepływu pracy jest uruchamiane w oknie konsoli i wyświetla ciąg zwrócony przez usługę ("Hello, world").  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Porady: Tworzenie usługi przepływu pracy za pomocą działań dotyczących komunikatów](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [Korzystanie z usługi WCF z przepływu pracy w projekcie sieci Web](http://go.microsoft.com/fwlink/?LinkId=207725)
