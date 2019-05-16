---
title: 'Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji'
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: b6d1c9c38e2cc5f1b1b7b5538af0339987563de6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637580"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a>Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji

Aby hostować usługi w ramach zarządzaną aplikację, Osadź kod dla usługi w kodzie aplikacji zarządzanej, albo obowiązkowo w kodzie, w sposób deklaratywny za pośrednictwem konfiguracji lub przy użyciu domyślnych punktów końcowych, definiowanie punktu końcowego usługi, a następnie utwórz wystąpienie <xref:System.ServiceModel.ServiceHost>.

Aby rozpocząć odbieranie komunikatów, należy wywołać <xref:System.ServiceModel.ICommunicationObject.Open%2A> na <xref:System.ServiceModel.ServiceHost>. Umożliwia utworzenie i otwiera odbiornika dla usługi. Usługi w ten sposób hostingu często nazywa się "hostingu samodzielnego", ponieważ aplikacja zarządzana wykonuje utwór hostingu. Aby zamknąć tę usługę, należy wywołać <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.ServiceHost>.

Usługa może też być hostowana w zarządzanych usług Windows, w Internet Information Services (IIS) lub w Windows Process Activation Service (WAS). Aby uzyskać więcej informacji na temat opcji usługi hostingu, zobacz [usług obsługującego](../../../docs/framework/wcf/hosting-services.md).

Usługi w zarządzanej aplikacji hosta jest najbardziej elastyczna opcja, ponieważ wymaga co najmniej infrastruktury do wdrożenia. Aby uzyskać więcej informacji o hostingu usług w zarządzanych aplikacjach, zobacz [hostowanie w aplikacji Managed](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).

Poniższa procedura demonstruje sposób implementacji usługi samodzielnie hostowanej w aplikacji konsoli.

## <a name="create-a-self-hosted-service"></a>Tworzenie własnego usługi

1. Utwórz nową aplikację konsoli:

   1. Otwórz program Visual Studio i wybierz **New** > **projektu** z **pliku** menu.

   2. W **zainstalowane szablony** listy wybierz **Visual C#** lub **języka Visual Basic**, a następnie wybierz pozycję **pulpitu Windows**.

   3. Wybierz **aplikacja Konsolowa** szablonu. Typ `SelfHost` w **nazwa** pole, a następnie wybierz **OK**.

2. Kliknij prawym przyciskiem myszy **host własny** w **Eksploratora rozwiązań** i wybierz **Dodaj odwołanie**. Wybierz **System.ServiceModel** z **.NET** kartę, a następnie wybierz **OK**.

    > [!TIP]
    > Jeśli **Eksploratora rozwiązań** okno nie jest widoczny, wybierz opcję **Eksploratora rozwiązań** z **widoku** menu.

3. Kliknij dwukrotnie **Program.cs** lub **Module1.vb** w **Eksploratora rozwiązań** aby otworzyć go w oknie kodu, jeśli nie jest jeszcze otwarty. Dodaj następujące instrukcje w górnej części pliku:

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. Definiowanie i implementowanie kontraktu usługi. Ten przykład definiuje `HelloWorldService` , zwraca komunikat na podstawie danych wejściowych do usługi.

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > Aby uzyskać więcej informacji o tym, jak definiować ani implementować interfejsu usługi, zobacz [jak: Definiowanie kontraktu usługi](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) i [jak: Implementowanie kontraktu usługi](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).

5. W górnej części `Main` metody, Utwórz wystąpienie obiektu <xref:System.Uri> klasy przy użyciu podstawowego adresu usługi.

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. Utwórz wystąpienie obiektu <xref:System.ServiceModel.ServiceHost> klasy, przekazując <xref:System.Type> który reprezentuje typ usługi, a podstawą adresu identyfikator (URI) do <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>. Włączanie publikowania metadanych, a następnie wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A> metody <xref:System.ServiceModel.ServiceHost> do inicjowania usługi i przygotować je do odbierania komunikatów.

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > W tym przykładzie użyto domyślnych punktów końcowych, a plik konfiguracji nie jest wymagana dla tej usługi. Jeśli punkty końcowe nie są skonfigurowane, środowisko uruchomieniowe tworzy jeden punkt końcowy dla każdego adresu podstawowego dla każdej umowy serwisowej implementowane przez usługę. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).

7. Naciśnij klawisz **Ctrl**+**Shift**+**B** do skompilowania rozwiązania.

## <a name="test-the-service"></a>Testowanie usługi

1. Naciśnij klawisz **Ctrl**+**F5** do uruchamiania usługi.

2. Otwórz **klienta testowego WCF**.

    > [!TIP]
    > Aby otworzyć **klienta testowego WCF**, otwórz wiersz polecenia dla deweloperów programu Visual Studio i wykonywanie **WcfTestClient.exe**.

3. Wybierz **Dodaj usługę** z **pliku** menu.

4. Typ `http://localhost:8080/hello` w polu adresu i kliknij przycisk **OK**.

    > [!TIP]
    > Upewnij się, że usługa jest uruchomiona. w przeciwnym razie ten krok zakończy się niepowodzeniem. Jeśli zmienisz adres podstawowy w kodzie, użyj zmodyfikowany adres podstawowy, w tym kroku.

5. Kliknij dwukrotnie **SayHello** w obszarze **Moje projekty usług** węzła. Wpisz nazwę w **wartość** kolumny w **żądania** listy, a następnie kliknij przycisk **Invoke**.

   W odpowiedzi zostanie wyświetlony komunikat **odpowiedzi** listy.

## <a name="example"></a>Przykład

Poniższy przykład tworzy <xref:System.ServiceModel.ServiceHost> obiektu do hostowania usługi typu `HelloWorldService`, a następnie wywołuje <xref:System.ServiceModel.ICommunicationObject.Open%2A> metody w <xref:System.ServiceModel.ServiceHost>. Adres podstawowy jest zawarte w kodzie, włączono publikowanie metadanych i domyślne punkty końcowe są używane.

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [Instrukcje: Hostowanie usługi WCF w programie IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [Host samodzielny](../../../docs/framework/wcf/samples/self-host.md)
- [Usługi hostingowe](../../../docs/framework/wcf/hosting-services.md)
- [Instrukcje: Definiowanie kontraktu usługi](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [Instrukcje: Implementowanie kontraktu usługi](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Powiązania dostarczane przez system](../../../docs/framework/wcf/system-provided-bindings.md)
