---
title: "Porada: Tworzenie przepływu pracy usługi przy użyciu działań dotyczących komunikatów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 24456bbbefe305a3e9620e5396c8d300163e00d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a>Porada: Tworzenie przepływu pracy usługi przy użyciu działań dotyczących komunikatów
W tym temacie opisano sposób tworzenia usługi simple przepływu pracy przy użyciu działań komunikacji. Ten temat koncentruje się na weryfikowaniu Tworzenie usługi przepływu pracy, gdy usługa składa się wyłącznie z działań dotyczących komunikatów. W usłudze rzeczywistych przepływ pracy zawiera wiele innych działań. Usługa implementuje jednej operacji o nazwie Echo, która przyjmuje ciągiem i zwraca ciąg do obiektu wywołującego. Ten temat jest pierwszy z serii dwa tematy. Następnego tematu [jak: dostęp do usługi z przepływu pracy aplikacji](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md) omówiono sposób tworzenia aplikacji przepływu pracy, który można wywołać usługi utworzone w tym temacie.  
  
### <a name="to-create-a-workflow-service-project"></a>Aby utworzyć projekt usługi przepływu pracy  
  
1.  Uruchom [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Kliknij przycisk **pliku** menu, wybierz opcję **nowy**, a następnie **projektu** do wyświetlenia **okno dialogowe nowego projektu**. Wybierz **przepływu pracy** z listy zainstalowanych szablonów i **aplikacji usługi przepływu pracy WCF** z listy typów projektów. Nazwij projekt `MyWFService` i użyj domyślnej lokalizacji, jak pokazano na poniższej ilustracji.  
  
     Kliknij przycisk **OK** przycisk, aby odrzucić **okno dialogowe nowego projektu**.  
  
3.  Po utworzeniu projektu plik Service1.xamlx jest otwarty w projektancie, jak pokazano na poniższej ilustracji.  
  
     ![Domyślny przepływ pracy wyświetlone w Projektancie](../../../../docs/framework/wcf/feature-details/media/defaultworkflowservice.JPG "DefaultWorkflowService")  
  
     Kliknij prawym przyciskiem myszy działanie etykietą **usługa Sekwencyjna** i wybierz **usunąć**.  
  
### <a name="to-implement-the-workflow-service"></a>Aby zaimplementować usługi przepływu pracy  
  
1.  Wybierz **przybornika** karcie po lewej stronie ekranu, aby wyświetlić przybornik, a następnie kliknij przycisk pinezki, aby pozostawić okna otwarte. Rozwiń węzeł **wiadomości** sekcji przybornika do wyświetlenia wiadomości działania i obsługi komunikatów szablony działania, jak pokazano na poniższej ilustracji.  
  
     ![Rozszerzona przybornika z kartą komunikatów](../../../../docs/framework/wcf/feature-details/media/wfdesignertoolbox.JPG "WFDesignerToolbox")  
  
2.  Przeciągnij i upuść **ReceiveAndSendReply** szablon do projektanta przepływów pracy. Spowoduje to utworzenie <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` działania o **Receive** następuje działanie <xref:System.ServiceModel.Activities.SendReply> działania, jak pokazano na poniższej ilustracji.  
  
     ![ReceiveAndSendReply szablon w Projektancie](../../../../docs/framework/wcf/feature-details/media/receiveandsendreply.JPG "ReceiveAndSendReply")  
  
     Zwróć uwagę, że <xref:System.ServiceModel.Activities.SendReply> działania <xref:System.ServiceModel.Activities.SendReply.Request%2A> właściwość jest ustawiona na `Receive`, nazwa <xref:System.ServiceModel.Activities.Receive> działania, do którego <xref:System.ServiceModel.Activities.SendReply> działania jest odpowiedź.  
  
3.  W <xref:System.ServiceModel.Activities.Receive> typ działania `Echo` w pole tekstowe z etykietą **OperationName**. Definiuje nazwy operacji usługa implementuje.  
  
     ![Określ nazwę operacji](../../../../docs/framework/wcf/feature-details/media/defineoperation.JPG "DefineOperation")  
  
4.  Z <xref:System.ServiceModel.Activities.Receive> działania zaznaczone, Otwórz okno właściwości, jeśli nie już otworzyć, klikając **widoku** menu i wybierając **okna właściwości**. W **okna właściwości** przewiń w dół do momentu wyświetlenia **CanCreateInstance** i zaznacz pole wyboru, jak pokazano na poniższej ilustracji. To ustawienie włącza hosta usługi przepływu pracy do utworzenia nowego wystąpienia usługi (w razie potrzeby), gdy wiadomość zostanie odebrana.  
  
     ![Właściwości CanCreateInstance](../../../../docs/framework/wcf/feature-details/media/cancreateinstance.JPG "CanCreateInstance")  
  
5.  Wybierz <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` działania i kliknij przycisk **zmienne** przycisk w lewym dolnym rogu projektanta. Spowoduje to wyświetlenie Edytor zmiennych. Kliknij przycisk **utworzyć zmienną** łącze, aby dodać zmienną do przechowywania ciągów wysłana do tej operacji. Nazwa zmiennej `msg` i ustawić jej **zmiennej** typu ciąg, jak pokazano na poniższej ilustracji.  
  
     ![Dodawanie zmiennej](../../../../docs/framework/wcf/feature-details/media/addvariable.JPG "AddVariable")  
  
     Kliknij przycisk **zmienne** przycisk ponownie, aby zamknąć Edytor zmiennych.  
  
6.  Kliknij przycisk **zdefiniuj...** łącze w **zawartości** polu tekstowym <xref:System.ServiceModel.Activities.Receive> działanie, aby wyświetlić **definicję zawartości** okna dialogowego. Wybierz **parametry** przycisk radiowy, kliknij przycisk **dodać nowego parametru** połączyć, wpisz `inMsg` w **nazwa** pole tekstowe, wybierz opcję **ciąg**w **typu** listy rozwijanej pola listy, a typ `msg` w **przypisać do** pola tekstowego, jak pokazano na poniższej ilustracji.  
  
     ![Dodawanie zawartości parametrów](../../../../docs/framework/wcf/feature-details/media/parameterscontent.jpg "ParametersContent")  
  
     To oznacza, że działanie Receive odbiera parametr ciągu i powiązania danych z `msg` zmiennej. Kliknij przycisk **OK** zamknąć **definicję zawartości** okna dialogowego.  
  
7.  Kliknij przycisk **zdefiniuj...**  łącze w **zawartości** polu <xref:System.ServiceModel.Activities.SendReply> działanie, aby wyświetlić **definicję zawartości** okna dialogowego. Wybierz **parametry** przycisk radiowy, kliknij przycisk **dodać nowego parametru** połączyć, wpisz `outMsg` w **nazwa** pole tekstowe, wybierz opcję **ciąg**w **typu** lista rozwijana i `msg` w **wartość** pola tekstowego, jak pokazano na poniższej ilustracji.  
  
     ![Dodawanie zawartości parametrów](../../../../docs/framework/wcf/feature-details/media/parameterscontent2.jpg "ParametersContent2")  
  
     Oznacza to, że <xref:System.ServiceModel.Activities.SendReply> działanie wysyła wiadomości lub typ kontraktu komunikatu i danych jest powiązany z `msg` zmiennej. Ponieważ jest to <xref:System.ServiceModel.Activities.SendReply> działania, oznacza to dane w `msg` używany do wypełnienia komunikat działanie wysyła do klienta. Kliknij przycisk **OK** zamknąć **definicję zawartości** okna dialogowego.  
  
8.  Zapisz i Skompiluj rozwiązanie, klikając **kompilacji** menu i wybierając **Kompiluj rozwiązanie**.  
  
## <a name="configure-the-workflow-service-project"></a>Konfigurowanie projektu usługi przepływu pracy  
 Usługi przepływu pracy zostało ukończone. W tej sekcji opisano sposób konfigurowania rozwiązania usługi przepływu pracy, aby ułatwić hostowanie i uruchamianie. To rozwiązanie wymaga ASP.NET Development Server do obsługi usługi.  
  
#### <a name="to-set-project-start-up-options"></a>Aby ustawić opcje uruchamiania projektu  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyWFService** i wybierz **właściwości** do wyświetlenia **właściwości projektu** okna dialogowego.  
  
2.  Wybierz **Web** i wybierz **określonej strony** w obszarze **Akcja uruchamiania** i typu `Service1.xamlx` w polu tekstowym, jak pokazano na poniższej ilustracji.  
  
     ![Okno dialogowe właściwości projektu](../../../../docs/framework/wcf/feature-details/media/projectpropertiesdlg.JPG "ProjectPropertiesDlg")  
  
     To jest hostowana usługa, zdefiniowane w Service1.xamlx w ASP.NET Development Server.  
  
3.  Naciśnij klawisze Ctrl + F5, aby uruchomić usługę. W prawym dolnym pulpitu jest wyświetlana ikona ASP.NET Development Server, jak pokazano na poniższej ilustracji.  
  
     ![Ikona serwera ASP.NET Developer](../../../../docs/framework/wcf/feature-details/media/aspnetdevservericon.JPG "ASPNETDEVServerIcon")  
  
     Ponadto program Internet Explorer wyświetla stronę pomocy usługi WCF dla usługi.  
  
     ![Strona pomocy WCF](../../../../docs/framework/wcf/feature-details/media/wcfhelppate.JPG "WCFHelpPate")  
  
4.  W dalszym ciągu na [jak: dostęp do usługi z przepływu pracy aplikacji](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md) tematu, aby utworzyć klienta przepływu pracy, który wywołuje tej usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Przegląd hostowania usług przepływu pracy](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [Działania dotyczące komunikatów](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
