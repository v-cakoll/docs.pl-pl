---
title: 'Porada: Tworzenie przepływu pracy usługi przy użyciu działań dotyczących komunikatów'
ms.date: 03/30/2017
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
ms.openlocfilehash: b4991fc9f8a6c45cae3943f1506247c42ed2b30b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597127"
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a>Porada: Tworzenie przepływu pracy usługi przy użyciu działań dotyczących komunikatów
W tym temacie opisano sposób tworzenia prostej usługi przepływu pracy przy użyciu działań związanych z wiadomościami. Ten temat koncentruje się na Mechanics tworzenia usługi przepływu pracy, w której usługa składa się wyłącznie z działań związanych z obsługą komunikatów. W przypadku usługi w świecie przepływ pracy zawiera wiele innych działań. Usługa implementuje jedną operację o nazwie echo, która pobiera ciąg i zwraca ciąg do obiektu wywołującego. Ten temat jest pierwszą częścią serii dwóch tematów. Następny temat [: uzyskiwanie dostępu do usługi z poziomu aplikacji przepływu pracy](how-to-access-a-service-from-a-workflow-application.md) omawia sposób tworzenia aplikacji przepływu pracy, która może wywołać usługę utworzoną w tym temacie.  
  
### <a name="to-create-a-workflow-service-project"></a>Aby utworzyć projekt usługi przepływu pracy  
  
1. Uruchom program Visual Studio 2012.  
  
2. Kliknij menu **plik** , wybierz polecenie **Nowy**, a następnie **projekt** , aby wyświetlić **okno dialogowe Nowy projekt**. Z listy typów projektów wybierz pozycję **przepływ pracy** z listy zainstalowanych szablonów i **aplikacji usługi przepływu pracy WCF** . Nazwij projekt `MyWFService` i Użyj domyślnej lokalizacji, jak pokazano na poniższej ilustracji.  
  
     Kliknij przycisk **OK** , aby zamknąć **okno dialogowe Nowy projekt**.  
  
3. Po utworzeniu projektu plik Service1. xamlx zostanie otwarty w projektancie, jak pokazano na poniższej ilustracji.  
  
     ![Zrzut ekranu pokazuje otwarty plik Service1. xamlx w projektancie.](./media/how-to-create-a-workflow-service-with-messaging-activities/default-workflow-service.jpg)  
  
     Kliknij prawym przyciskiem myszy działanie z etykietą **Usługa sekwencyjna** i wybierz polecenie **Usuń**.  
  
### <a name="to-implement-the-workflow-service"></a>Aby zaimplementować usługę przepływu pracy  
  
1. Wybierz kartę **Przybornik** po lewej stronie ekranu, aby wyświetlić przybornik, a następnie kliknij pinezkę, aby pozostawić otwarte okno. Rozwiń sekcję **wiadomości** w przyborniku, aby wyświetlić działania obsługi komunikatów i szablony aktywności komunikatów, jak pokazano na poniższej ilustracji.  
  
     ![Zrzut ekranu pokazujący Przybornik z rozwiniętą sekcją komunikatów.](./media/how-to-create-a-workflow-service-with-messaging-activities/toolbox-messaging-section.jpg)  
  
2. Przeciągnij i upuść szablon **ReceiveAndSendReply** do projektanta przepływu pracy. Spowoduje to utworzenie <xref:System.Activities.Statements.Sequence> działania z działaniem **Receive** , po którym następuje <xref:System.ServiceModel.Activities.SendReply> działanie, jak pokazano na poniższej ilustracji.  
  
     ![Zrzut ekranu przedstawiający szablon ReceiveAndSendReply.](./media/how-to-create-a-workflow-service-with-messaging-activities/receiveandsendreply-template.jpg)  
  
     Zauważ, że <xref:System.ServiceModel.Activities.SendReply> Właściwość działania <xref:System.ServiceModel.Activities.SendReply.Request%2A> jest ustawiona na wartość `Receive` , nazwa <xref:System.ServiceModel.Activities.Receive> działania, z którym <xref:System.ServiceModel.Activities.SendReply> odpowiada działanie.  
  
3. W <xref:System.ServiceModel.Activities.Receive> typie działania `Echo` do pola tekstowego zatytułowanego nazwa **operacji**. Definiuje nazwę operacji implementującej usługę.  
  
     ![Zrzut ekranu pokazujący, gdzie należy określić nazwę operacji.](./media/how-to-create-a-workflow-service-with-messaging-activities/define-operation-name.jpg)  
  
4. <xref:System.ServiceModel.Activities.Receive>Po wybraniu działania Otwórz okno właściwości, jeśli nie jest jeszcze otwarte, klikając menu **Widok** i wybierając polecenie **okno właściwości**. W **oknie właściwości** przewiń w dół do momentu wyświetlenia **CanCreateInstance** i kliknięcia pola wyboru, jak pokazano na poniższej ilustracji. To ustawienie włącza hosta usługi przepływu pracy w celu utworzenia nowego wystąpienia usługi (jeśli jest to konieczne) w momencie odebrania komunikatu.  
  
     ![Zrzut ekranu przedstawiający Właściwość CanCreateInstance.](./media/how-to-create-a-workflow-service-with-messaging-activities/cancreateinstance-property.jpg)  
  
5. Wybierz <xref:System.Activities.Statements.Sequence> działanie, a następnie kliknij przycisk **zmienne** w lewym dolnym rogu projektanta. Spowoduje to wyświetlenie edytora zmiennych. Kliknij link **Utwórz zmienną** , aby dodać zmienną do przechowywania ciągu wysyłanego do operacji. Nazwij zmienną `msg` i ustaw jej typ **zmiennej** na ciąg, jak pokazano na poniższej ilustracji.  
  
     ![Zrzut ekranu, który pokazuje, jak dodać zmienną.](./media/how-to-create-a-workflow-service-with-messaging-activities/add-variable-msg-string.jpg)  
  
     Kliknij ponownie przycisk **zmienne** , aby zamknąć Edytor zmiennych.  
  
6. Kliknij przycisk **Definiuj..** link w polu tekstowym **zawartość** <xref:System.ServiceModel.Activities.Receive> działania, aby wyświetlić okno dialogowe **definicji zawartości** . Wybierz przycisk radiowy **Parametry** , kliknij link **Dodaj nowy parametr** , wpisz `inMsg` w polu tekstowym **Nazwa** , wybierz **ciąg** w polu listy rozwijanej **Typ** , a następnie wpisz `msg` w polu tekstowym **Przypisz do** , jak pokazano na poniższej ilustracji.  
  
     ![Zrzut ekranu pokazujący Dodawanie zawartości parametrów.](./media/how-to-create-a-workflow-service-with-messaging-activities/adding-parameters-content.jpg)  
  
     Oznacza to, że działanie Receive odbiera parametr ciągu, a dane są powiązane ze `msg` zmienną. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **definicji zawartości** .  
  
7. Kliknij link **Definiuj...** w polu **zawartość** w <xref:System.ServiceModel.Activities.SendReply> działaniu, aby wyświetlić okno dialogowe **definicji zawartości** . Wybierz przycisk radiowy **Parametry** , kliknij link **Dodaj nowy parametr** , wpisz w polu tekstowym `outMsg` **Nazwa** , a następnie wybierz **ciąg** na liście rozwijanej **Typ** , a następnie `msg` w polu tekstowym **wartość** , jak pokazano na poniższej ilustracji.  
  
     ![Zrzut ekranu, który pokazuje, jak dodać parametr outMsg.](./media/how-to-create-a-workflow-service-with-messaging-activities/outmsg-parameters-content.jpg)  
  
     Oznacza to, że <xref:System.ServiceModel.Activities.SendReply> działanie wysyła komunikat lub typ kontraktu komunikatu, a dane są powiązane ze `msg` zmienną. Ponieważ jest to <xref:System.ServiceModel.Activities.SendReply> działanie, oznacza to, że dane w programie `msg` służą do wypełniania komunikatu wysyłanego z powrotem do klienta. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **definicji zawartości** .  
  
8. Zapisz i skompiluj rozwiązanie, klikając menu **kompilacja** i wybierając polecenie **Kompiluj rozwiązanie**.  
  
## <a name="configure-the-workflow-service-project"></a>Konfigurowanie projektu usługi przepływu pracy  
 Usługa przepływu pracy została ukończona. W tej sekcji opisano sposób konfigurowania rozwiązania usługi przepływu pracy w celu ułatwienia hostowania i uruchamiania programu. To rozwiązanie używa serwera deweloperskiego ASP.NET do hostowania usługi.  
  
#### <a name="to-set-project-start-up-options"></a>Aby ustawić opcje uruchamiania projektu  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **MyWFService** i wybierz pozycję **Właściwości** , aby wyświetlić okno dialogowe **właściwości projektu** .  
  
2. Wybierz kartę **Sieć Web** i wybierz opcję **określona Strona** w obszarze **Rozpocznij akcję** , a następnie wpisz `Service1.xamlx` w polu tekstowym, jak pokazano na poniższej ilustracji.  
  
     ![Zrzut ekranu przedstawiający okno dialogowe właściwości projektu.](./media/how-to-create-a-workflow-service-with-messaging-activities/project-properties-dialog.jpg)  
  
     To hostuje usługę zdefiniowaną w Service1. xamlx na serwerze deweloperskim ASP.NET.  
  
3. Naciśnij klawisze CTRL + F5, aby uruchomić usługę. Ikona serwera deweloperskiego ASP.NET jest wyświetlana w prawym dolnym rogu pulpitu, jak pokazano na poniższej ilustracji.  
  
     ![Zrzut ekranu pokazujący ikonę serwera dewelopera ASP.NET.](./media/how-to-create-a-workflow-service-with-messaging-activities/asp-net-dev-server-icon.jpg)  
  
     Ponadto program Internet Explorer wyświetla stronę pomocy usługi WCF dla usługi.  
  
     ![Zrzut ekranu przedstawiający stronę pomocy usługi WCF.](./media/how-to-create-a-workflow-service-with-messaging-activities/wcf-service-help-page.jpg)  
  
4. Przejdź do tematu [: uzyskiwanie dostępu do usługi z poziomu aplikacji przepływu pracy](how-to-access-a-service-from-a-workflow-application.md) w celu utworzenia klienta przepływu pracy wywołującego tę usługę.  
  
## <a name="see-also"></a>Zobacz też

- [Usługi przepływu pracy](workflow-services.md)
- [Przegląd hostowania usług przepływu pracy](hosting-workflow-services-overview.md)
- [Działania dotyczące komunikatów](messaging-activities.md)
