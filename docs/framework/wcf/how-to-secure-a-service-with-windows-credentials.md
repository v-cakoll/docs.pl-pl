---
title: 'Instrukcje: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows'
description: Dowiedz się, jak włączyć zabezpieczenia transportu w usłudze WCF, która znajduje się w domenie systemu Windows i jest wywoływana przez klientów w tej samej domenie.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: 8ef164e1475bfd5f047a99426a2bed43a7aa7353
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244636"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a>Instrukcje: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows

W tym temacie pokazano, jak włączyć zabezpieczenia transportu w usłudze Windows Communication Foundation (WCF), która znajduje się w domenie systemu Windows i jest wywoływana przez klientów w tej samej domenie. Aby uzyskać więcej informacji na temat tego scenariusza, zobacz [zabezpieczenia transportu z uwierzytelnianiem systemu Windows](./feature-details/transport-security-with-windows-authentication.md). Aby uzyskać przykładową aplikację, zobacz przykład [WSHttpBinding](./samples/wshttpbinding.md) .

W tym temacie przyjęto założenie, że masz już zdefiniowany interfejs kontraktu i implementację, i dodaje do niego. Możesz również zmodyfikować istniejącą usługę i klienta.

Usługę można zabezpieczyć za pomocą poświadczeń systemu Windows w kodzie. Alternatywnie można pominąć część kodu przy użyciu pliku konfiguracji. W tym temacie przedstawiono obie metody. Upewnij się, że używasz tylko jednej z tych metod, a nie obu.

Pierwsze trzy procedury pokazują, jak zabezpieczyć usługę przy użyciu kodu. Czwarta i piąta procedura pokazuje, jak to zrobić za pomocą pliku konfiguracji.

## <a name="using-code"></a>Korzystanie z kodu

Kompletny kod dla usługi i klienta znajduje się w sekcji przykład na końcu tego tematu.

Pierwsza procedura zawiera instrukcje tworzenia i konfigurowania <xref:System.ServiceModel.WSHttpBinding> klasy w kodzie. Powiązanie używa transportu HTTP. To samo powiązanie jest używane na kliencie.

#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a>Aby utworzyć element WSHttpBinding, który używa poświadczeń systemu Windows i zabezpieczeń komunikatów

1. Kod tej procedury jest wstawiany na początku `Run` metody `Test` klasy w kodzie usługi w sekcji przykład.

2. Utworzenie wystąpienia <xref:System.ServiceModel.WSHttpBinding> klasy.

3. Ustaw <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> Właściwość <xref:System.ServiceModel.WSHttpSecurity> klasy na <xref:System.ServiceModel.SecurityMode.Message> .

4. Ustaw <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> Właściwość <xref:System.ServiceModel.MessageSecurityOverHttp> klasy na <xref:System.ServiceModel.MessageCredentialType.Windows> .

5. Kod tej procedury jest następujący:

    [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
    [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]

### <a name="using-the-binding-in-a-service"></a>Korzystanie z powiązania w usłudze

Jest to druga procedura, która pokazuje, jak używać powiązania w usłudze samodzielnej. Aby uzyskać więcej informacji na temat usług hostingu, zobacz [usługi hostingu](hosting-services.md).

##### <a name="to-use-a-binding-in-a-service"></a>Aby użyć powiązania w usłudze

1. Wstaw kod tej procedury po kodzie z poprzedniej procedury.

2. Utwórz <xref:System.Type> zmienną o nazwie `contractType` i przypisz ją do typu interfejsu ( `ICalculator` ). Korzystając z Visual Basic, użyj `GetType` operatora; w przypadku używania języka C#, użyj `typeof` słowa kluczowego.

3. Utwórz drugą <xref:System.Type> zmienną o nazwie `serviceType` i przypisz ją do typu zaimplementowanego kontraktu ( `Calculator` ).

4. Utwórz wystąpienie <xref:System.Uri> klasy o nazwie `baseAddress` z adresem podstawowym usługi. Adres podstawowy musi mieć schemat zgodny z transportem. W tym przypadku schemat transportu to HTTP, a adres zawiera specjalny Uniform Resource Identifier (URI) "localhost" i numer portu (8036), a także podstawowy adres punktu końcowego ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/` .

5. Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy za pomocą `serviceType` `baseAddress` zmiennych i.

6. Dodaj punkt końcowy do usługi przy użyciu elementu `contractType` , powiązania i nazwy punktu końcowego (secureCalculator). Po zainicjowaniu wywołania usługi Klient musi połączyć adres podstawowy i nazwę punktu końcowego.

7. Wywołaj <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metodę, aby uruchomić usługę. Kod tej procedury jest przedstawiony tutaj:

    [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
    [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]

### <a name="using-the-binding-in-a-client"></a>Korzystanie z powiązania w kliencie

Ta procedura pokazuje, jak wygenerować serwer proxy, który komunikuje się z usługą. Serwer proxy jest generowany przy użyciu [Narzędzia do obsługi metadanych ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , które używa metadanych usługi do utworzenia serwera proxy.

Ta procedura powoduje także utworzenie wystąpienia <xref:System.ServiceModel.WSHttpBinding> klasy w celu komunikacji z usługą, a następnie wywołanie usługi.

Ten przykład używa tylko kodu do utworzenia klienta. Alternatywnie można użyć pliku konfiguracji, który jest przedstawiony w sekcji opisanej w poniższej procedurze.

#### <a name="to-use-a-binding-in-a-client-with-code"></a>Aby użyć powiązania w kliencie z kodem

1. Użyj narzędzia SvcUtil.exe do wygenerowania kodu serwera proxy z metadanych usługi. Aby uzyskać więcej informacji, zobacz [How to: Create a Client](how-to-create-a-wcf-client.md). Wygenerowany kod serwera proxy dziedziczy z <xref:System.ServiceModel.ClientBase%601> klasy, co zapewnia, że każdy klient ma wymagane konstruktory, metody i właściwości do komunikowania się z usługą WCF. W tym przykładzie wygenerowany kod zawiera `CalculatorClient` klasę, która implementuje `ICalculator` interfejs, umożliwiając zgodność z kodem usługi.

2. Kod tej procedury jest wstawiany na początku `Main` metody programu klienckiego.

3. Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw jego tryb zabezpieczeń na `Message` i jego typ poświadczeń klienta na `Windows` . Przykład nazwy zmiennej `clientBinding` .

4. Utwórz wystąpienie <xref:System.ServiceModel.EndpointAddress> klasy o nazwie `serviceAddress` . Zainicjuj wystąpienie z adresem podstawowym połączonym z nazwą punktu końcowego.

5. Utwórz wystąpienie wygenerowanej klasy klienta przy użyciu `serviceAddress` i `clientBinding` zmiennych.

6. Wywołaj <xref:System.ServiceModel.ClientBase%601.Open%2A> metodę, jak pokazano w poniższym kodzie.

7. Wywołaj usługę i Wyświetl wyniki.

    [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
    [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]

## <a name="using-the-configuration-file"></a>Korzystanie z pliku konfiguracji

Zamiast tworzyć powiązania z kodem proceduralnym, można użyć poniższego kodu dla sekcji powiązania w pliku konfiguracji.

Jeśli nie masz jeszcze zdefiniowanej usługi, zobacz [projektowanie i implementowanie usług](designing-and-implementing-services.md)oraz [Konfigurowanie usług](configuring-services.md).

> [!NOTE]
> Ten kod konfiguracji jest używany zarówno w plikach konfiguracji usługi, jak i klienta.

#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a>Aby włączyć zabezpieczenia transferu dla usługi w domenie systemu Windows przy użyciu konfiguracji

1. Dodaj [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element do [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) sekcji elementu w pliku konfiguracji.

2. Dodaj `binding` element> <do `WSHttpBinding` elementu <> i ustaw dla `configurationName` atrybutu wartość odpowiednią dla Twojej aplikacji.

3. Dodaj `security` element> <i ustaw dla niego `mode` atrybut Message.

4. Dodaj `message` element> <i ustaw `clientCredentialType` atrybut na Windows.

5. W pliku konfiguracji usługi Zastąp `<bindings>` sekcję poniższym kodem. Jeśli nie masz jeszcze pliku konfiguracji usługi, zobacz temat [Używanie powiązań do konfigurowania usług i klientów](using-bindings-to-configure-services-and-clients.md).

    ```xml
    <bindings>
      <wsHttpBinding>
       <binding name = "wsHttpBinding_Calculator">
         <security mode="Message">
           <message clientCredentialType="Windows"/>
         </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    ```

### <a name="using-the-binding-in-a-client"></a>Korzystanie z powiązania w kliencie

Ta procedura pokazuje, jak generować dwa pliki: serwer proxy, który komunikuje się z usługą i plikiem konfiguracji. Opisano w nim również zmiany programu klienckiego, czyli trzeci plik używany na komputerze klienckim.

#### <a name="to-use-a-binding-in-a-client-with-configuration"></a>Aby użyć powiązania w kliencie z konfiguracją

1. Użyj narzędzia SvcUtil.exe, aby wygenerować kod i plik konfiguracji serwera proxy z metadanych usługi. Aby uzyskać więcej informacji, zobacz [How to: Create a Client](how-to-create-a-wcf-client.md).

2. Zamień [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) sekcję wygenerowanego pliku konfiguracji na kod konfiguracji z poprzedniej sekcji.

3. Kod proceduralny jest wstawiany na początku `Main` metody programu klienckiego.

4. Utwórz wystąpienie wygenerowanej klasy klienta przekazujące nazwę powiązania w pliku konfiguracji jako parametr wejściowy.

5. Wywołaj <xref:System.ServiceModel.ClientBase%601.Open%2A> metodę, jak pokazano w poniższym kodzie.

6. Wywołaj usługę i Wyświetl wyniki.

    [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]

## <a name="example"></a>Przykład

[!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]

[!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)]
[!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]

## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.WSHttpBinding>
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Instrukcje: tworzenie klienta](how-to-create-a-wcf-client.md)
- [Zabezpieczanie usług](securing-services.md)
- [Przegląd zabezpieczeń](./feature-details/security-overview.md)
