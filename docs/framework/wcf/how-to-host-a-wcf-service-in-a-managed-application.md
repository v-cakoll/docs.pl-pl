---
title: 'Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji'
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: e3adcad6ba70aa64b797325cd45a043301d7e680
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320977"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a>Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji

Aby hostować usługę wewnątrz zarządzanej aplikacji, należy osadzić kod usługi w kodzie zarządzanej aplikacji, zdefiniować punkt końcowy usługi w sposób bezwzględny w kodzie, deklaratywnie za pośrednictwem konfiguracji lub użyć domyślnych punktów końcowych, a następnie utworzyć wystąpienie <xref:System.ServiceModel.ServiceHost>.

Aby rozpocząć otrzymywanie komunikatów, wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A> w <xref:System.ServiceModel.ServiceHost>. Spowoduje to utworzenie i otwarcie odbiornika dla usługi. Hosting usługi w ten sposób jest często określany jako "hosting samodzielny", ponieważ zarządzana aplikacja wykonuje działania hostingowe. Aby zamknąć usługę, wywołaj <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> w <xref:System.ServiceModel.ServiceHost>.

Usługa może być również hostowana w usłudze zarządzanej systemu Windows, w Internet Information Services (IIS) lub w usłudze aktywacji procesów systemu Windows (WAS). Aby uzyskać więcej informacji na temat opcji hostingu dla usługi, zobacz [usługi hostingu](hosting-services.md).

Hostowanie usługi w aplikacji zarządzanej jest najbardziej elastyczną opcją, ponieważ wymaga ona najmniejszej infrastruktury do wdrożenia. Aby uzyskać więcej informacji na temat usług hostingu w zarządzanych aplikacjach, zobacz [hosting w aplikacji zarządzanej](./feature-details/hosting-in-a-managed-application.md).

Poniższa procedura przedstawia sposób implementacji usługi samodzielnej w aplikacji konsolowej.

## <a name="create-a-self-hosted-service"></a>Tworzenie usługi samodzielnej

1. Utwórz nową aplikację konsolową:

   1. Otwórz program Visual Studio i wybierz pozycję **Nowy** **projekt**  >  z menu **plik** .

   2. Na liście **zainstalowane szablony** wybierz pozycję **Visual C#**  lub **Visual Basic**, a następnie wybierz pozycję **Windows Desktop**.

   3. Wybierz szablon **aplikacja konsoli** . Wpisz `SelfHost` w polu **Nazwa** , a następnie wybierz przycisk **OK**.

2. Kliknij prawym przyciskiem myszy pozycję **SelfHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj odwołanie**. Wybierz **System. ServiceModel** z karty **.NET** , a następnie wybierz przycisk **OK**.

    > [!TIP]
    > Jeśli okno **Eksplorator rozwiązań** nie jest widoczne, wybierz pozycję **Eksplorator rozwiązań** z menu **Widok** .

3. Kliknij dwukrotnie pozycję **program.cs** lub **Module1. vb** w **Eksplorator rozwiązań** , aby otworzyć ją w oknie kodu, jeśli nie jest jeszcze otwarta. Dodaj następujące instrukcje w górnej części pliku:

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. Zdefiniuj i zaimplementuj kontrakt usługi. W tym przykładzie zdefiniowano `HelloWorldService`, która zwraca komunikat na podstawie danych wejściowych usługi.

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > Aby uzyskać więcej informacji na temat sposobu definiowania i implementowania interfejsu usługi, zobacz [How to: define a Service Contract](how-to-define-a-wcf-service-contract.md) and [How to: Implementuj kontrakt usługi](how-to-implement-a-wcf-contract.md).

5. W górnej części metody `Main` Utwórz wystąpienie klasy <xref:System.Uri> z adresem podstawowym usługi.

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. Utwórz wystąpienie klasy <xref:System.ServiceModel.ServiceHost>, przekazując <xref:System.Type> reprezentujące typ usługi i adres podstawowy Uniform Resource Identifier (URI) do <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>. Włącz Publikowanie metadanych, a następnie Wywołaj metodę <xref:System.ServiceModel.ICommunicationObject.Open%2A> na <xref:System.ServiceModel.ServiceHost> w celu zainicjowania usługi i przygotowania jej do odbierania komunikatów.

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > W tym przykładzie są stosowane domyślne punkty końcowe i plik konfiguracji nie jest wymagany dla tej usługi. Jeśli nie skonfigurowano żadnych punktów końcowych, środowisko uruchomieniowe tworzy jeden punkt końcowy dla każdego adresu podstawowego dla każdego kontraktu usługi zaimplementowanego przez usługę. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](./samples/simplified-configuration-for-wcf-services.md).

7. Naciśnij **klawisze Ctrl**+**SHIFT**+**B** , aby skompilować rozwiązanie.

## <a name="test-the-service"></a>Testowanie usługi

1. Naciśnij **klawisze Ctrl**+**F5** , aby uruchomić usługę.

2. Otwórz **klienta testowego WCF**.

    > [!TIP]
    > Aby otworzyć **klienta testowego WCF**, Otwórz wiersz polecenia dla deweloperów dla programu Visual Studio i wykonaj **WcfTestClient. exe**.

3. Wybierz pozycję **Dodaj usługę** z menu **plik** .

4. Wpisz `http://localhost:8080/hello` w polu adres i kliknij przycisk **OK**.

    > [!TIP]
    > Upewnij się, że usługa jest uruchomiona, lub w przeciwnym razie ten krok nie powiedzie się. Jeśli zmieniono adres podstawowy w kodzie, należy użyć zmodyfikowanego adresu podstawowego w tym kroku.

5. Kliknij dwukrotnie pozycję **sayHello** w węźle **Moje projekty usług** . Wpisz swoją nazwę w kolumnie **wartość** na liście **żądanie** , a następnie kliknij pozycję **Wywołaj**.

   Na liście **odpowiedzi** zostanie wyświetlony komunikat odpowiedzi.

## <a name="example"></a>Przykład

Poniższy przykład tworzy obiekt <xref:System.ServiceModel.ServiceHost> w celu hostowania usługi typu `HelloWorldService`, a następnie wywołuje metodę <xref:System.ServiceModel.ICommunicationObject.Open%2A> w <xref:System.ServiceModel.ServiceHost>. Adres podstawowy jest podany w kodzie, funkcja publikowania metadanych jest włączona, a domyślne punkty końcowe są używane.

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [Instrukcje: hostowanie usługi WCF w programie IIS](./feature-details/how-to-host-a-wcf-service-in-iis.md)
- [Host samodzielny](./samples/self-host.md)
- [Usługi hostingowe](hosting-services.md)
- [Instrukcje: definiowanie kontraktu usługi](how-to-define-a-wcf-service-contract.md)
- [Instrukcje: implementowanie kontraktu usługi](how-to-implement-a-wcf-contract.md)
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](using-bindings-to-configure-services-and-clients.md)
- [Powiązania dostarczane przez system](system-provided-bindings.md)
