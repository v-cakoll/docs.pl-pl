---
title: "Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6491faa6134c1e80e07294d8f888200c04fa8704
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-a-wcf-service-in-a-managed-application"></a>Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji
Aby obsługiwać usługę w aplikacji zarządzanej, osadzanie kodu dla usługi w kodzie aplikacji zarządzanych, albo imperatively w kodzie, deklaratywnego za pomocą konfiguracji lub użyciu domyślne punkty końcowe, określić punkt końcowy usługi, a następnie utwórz wystąpienie klasy <xref:System.ServiceModel.ServiceHost>.  
  
 Aby rozpocząć odbieranie komunikatów, należy wywołać <xref:System.ServiceModel.ICommunicationObject.Open%2A> na <xref:System.ServiceModel.ServiceHost>. Tworzy i otwiera odbiornika dla usługi. Hosting usług w ten sposób jest często określany jako "hostingu samodzielnego" ponieważ wykonuje hostingu pracy samego zarządzanej aplikacji. Aby zamknąć tę usługę, należy wywołać <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.ServiceHost>.  
  
 Usługi mogą być również obsługiwane w usłudze zarządzanej systemu Windows, w konsoli Internet Information Services (IIS) lub w usługi aktywacji procesów systemu Windows (WAS). [!INCLUDE[crabout](../../../includes/crabout-md.md)]hosting opcje dla usługi, zobacz [Hosting usług](../../../docs/framework/wcf/hosting-services.md).  
  
 Usługi w zarządzanej aplikacji hosta jest najbardziej elastycznym opcja, ponieważ wymaga co najmniej infrastruktury do wdrożenia. [!INCLUDE[crabout](../../../includes/crabout-md.md)]hosting usług aplikacji zarządzanych, zobacz [Hosting w zarządzanej aplikacji](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).  
  
 W poniższej procedurze przedstawiono implementowania samodzielnie hostowana usługa w aplikacji konsoli.  
  
### <a name="to-create-a-self-hosted-service"></a>Aby utworzyć usługę hostowanie Samoobsługowe  
  
1.  Otwórz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] i wybierz **nowy**, **projektu...**  z **pliku** menu.  
  
2.  W **zainstalowane szablony** listy, wybierz **Visual C#**, **Windows** lub **Visual Basic**, **Windows**. W zależności od Twojego [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ustawienia, jeden lub oba te mogą być w obszarze **inne języki** w węźle **zainstalowane szablony** listy.  
  
3.  Wybierz **aplikacji konsoli** z **Windows** listy. Typ `SelfHost` w **nazwa** polu i kliknij przycisk **OK**.  
  
4.  Kliknij prawym przyciskiem myszy **SelfHost** w **Eksploratora rozwiązań** i wybierz **Dodawanie odwołania...** . Wybierz **System.ServiceModel** z **.NET** i kliknij polecenie **OK**.  
  
    > [!TIP]
    >  Jeśli **Eksploratora rozwiązań** okno nie jest widoczny, wybierz pozycję **Eksploratora rozwiązań** z **widoku** menu.  
  
5.  Kliknij dwukrotnie **Program.cs** lub **Module1.vb** w **Eksploratora rozwiązań** aby otworzyć go w oknie kodu, jeśli nie jest już otwarty. Dodaj następujące instrukcje w górnej części pliku.  
  
     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]  
  
6.  Definiowanie i implementowanie kontraktu usługi. W tym przykładzie definiuje `HelloWorldService` zwracającą wiadomości na podstawie danych wprowadzonych z usługą.  
  
     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]  
  
    > [!NOTE]
    >  [!INCLUDE[crabout](../../../includes/crabout-md.md)]Zdefiniuj i zaimplementuj interfejs usługi, zobacz [porady: definiowanie kontraktu usługi](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) i [porady: Implementowanie kontraktu usługi](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).  
  
7.  W górnej części `Main` metody, Utwórz wystąpienie <xref:System.Uri> klasy adres podstawowy usługi.  
  
     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]  
  
8.  Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy, przekazując <xref:System.Type> reprezentująca typu usługi i podstawowym adresów identyfikator URI (Uniform Resource) do <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>. Włącz publikowanie metadanych, a następnie wywołać <xref:System.ServiceModel.ICommunicationObject.Open%2A> metoda <xref:System.ServiceModel.ServiceHost> zainicjować usługi i przygotowywania ich do odbierania wiadomości.  
  
     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]       
  
    > [!NOTE]
    >  W tym przykładzie używane domyślne punkty końcowe, a nie plik konfiguracji jest wymagany dla tej usługi. Jeśli nie skonfigurowano żadnych punktów końcowych, środowisko uruchomieniowe tworzy jeden punkt końcowy dla każdego adresu podstawowego dla każdej umowy serwisowej zaimplementowanych przez usługę. [!INCLUDE[crabout](../../../includes/crabout-md.md)]domyślne punkty końcowe, zobacz [uproszczony konfiguracji](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
9. Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
### <a name="to-test-the-service"></a>Aby przetestować usługę  
  
1.  Naciśnij klawisze Ctrl + F5, aby uruchomić usługę.  
  
2.  Otwórz **klienta testowego WCF**.  
  
    > [!TIP]
    >  Aby otworzyć **klienta testowego WCF**, otwórz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] wiersz polecenia i wykonywanie **WcfTestClient.exe**.  
  
3.  Wybierz **dodawania usługi...**  z **pliku** menu.  
  
4.  Typ `http://localhost:8080/hello` w polu adres i kliknij przycisk **OK**.  
  
    > [!TIP]
    >  Upewnij się, że usługa jest uruchomiona. w przeciwnym razie ten krok nie powiedzie się. Jeśli zmieniono adres podstawowy w kodzie, użyj zmodyfikowanego adres podstawowy w tym kroku.  
  
5.  Kliknij dwukrotnie **SayHello** w obszarze **Moje projekty usług** węzła. Wpisz nazwę w **wartość** kolumny w **żądania** listy, a następnie kliknij przycisk **Invoke**. Zostanie wyświetlony komunikat odpowiedzi w **odpowiedzi** listy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.ServiceModel.ServiceHost> obiektu do obsługi usługi typu `HelloWorldService`, a następnie wywołuje <xref:System.ServiceModel.ICommunicationObject.Open%2A> metody na <xref:System.ServiceModel.ServiceHost>. Adres podstawowy jest zawarte w kodzie, publikowanie metadanych jest włączona i domyślne punkty końcowe są używane.  
  
 [!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
 [!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Uri>  
 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>  
 <xref:System.Configuration.ConfigurationManager>  
 [Instrukcje: hostowanie usługi WCF w programie IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [Host samodzielny](../../../docs/framework/wcf/samples/self-host.md)  
 [Usługi hostingowe](../../../docs/framework/wcf/hosting-services.md)  
 [Instrukcje: definiowanie kontraktu usługi](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [Instrukcje: implementowanie kontraktu usługi](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Powiązania dostarczane przez system](../../../docs/framework/wcf/system-provided-bindings.md)
