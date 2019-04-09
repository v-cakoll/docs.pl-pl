---
title: 'Instrukcje: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: 70b8e2f28559d5fc54736db1319d2309aa5b86a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111335"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a>Instrukcje: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows
W tym temacie przedstawiono sposób włączania zabezpieczenia transportu usługi Windows Communication Foundation (WCF), który znajduje się w domenie, Windows i jest wywoływana przez klientów w tej samej domenie. Aby uzyskać więcej informacji na temat tego scenariusza, zobacz [zabezpieczenia transportu z uwierzytelnianiem Windows](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md). Dla przykładowej aplikacji, zobacz [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) próbki.  
  
 W tym temacie przyjęto założenie, masz istniejący interfejs kontrakt i implementacja już zdefiniowane i dodaje się, że. Można także modyfikować istniejące usługi i klienta.  
  
 Aby zabezpieczyć usługi przy użyciu poświadczeń Windows całkowicie w kodzie. Alternatywnie możesz pominąć część kodu przy użyciu pliku konfiguracji. W tym temacie pokazano w obu kierunkach. Upewnij się, że używasz tylko jednej z metod, nie obydwa.  
  
 Pierwsze trzy procedury pokazują, jak zabezpieczyć usługę za pomocą kodu. Czwarty i piąty procedura pokazuje, jak to zrobić za pomocą pliku konfiguracji.  
  
## <a name="using-code"></a>Przy użyciu kodu  
 Kompletny kod dla usługi i klienta znajduje się w sekcji przykład, na końcu tego tematu.  
  
 Pierwsza procedura przeprowadzi tworzenia i konfigurowania <xref:System.ServiceModel.WSHttpBinding> klasy w kodzie. Powiązanie korzysta z protokołu HTTP. Tego samego powiązania jest używany na komputerze klienckim.  
  
#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a>Aby utworzyć WSHttpBinding, który używa poświadczeń Windows i zabezpieczeń komunikatów  
  
1.  Ta procedura kod dodaje się na początku `Run` metody `Test` klasy w kodzie usługi, w sekcji przykład.  
  
2.  Utworzenie wystąpienia <xref:System.ServiceModel.WSHttpBinding> klasy.  
  
3.  Ustaw <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> właściwość <xref:System.ServiceModel.WSHttpSecurity> klasy <xref:System.ServiceModel.SecurityMode.Message>.  
  
4.  Ustaw <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> właściwość <xref:System.ServiceModel.MessageSecurityOverHttp> klasy <xref:System.ServiceModel.MessageCredentialType.Windows>.  
  
5.  Kod do wykonania tej procedury jest następująca:  
  
     [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
     [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]  
  
### <a name="using-the-binding-in-a-service"></a>Za pomocą tego powiązania w ramach usługi  
 Jest to druga procedura pokazuje, jak stosować powiązanie samodzielnie hostowanej usługi. Aby uzyskać więcej informacji na temat usługi hostingowe zobacz [usług obsługującego](../../../docs/framework/wcf/hosting-services.md).  
  
##### <a name="to-use-a-binding-in-a-service"></a>Aby użyć powiązania w ramach usługi  
  
1.  Wstaw kod tej procedury po kodu z poprzedniej procedury.  
  
2.  Tworzenie <xref:System.Type> zmiennej o nazwie `contractType` i przypisać jej typ interfejsu (`ICalculator`). Podczas korzystania z języka Visual Basic należy używać `GetType` operatora; przy użyciu języka C#, użyj `typeof` — słowo kluczowe.  
  
3.  Utwórz drugi <xref:System.Type> zmiennej o nazwie `serviceType` i przypisać jej typ kontraktu zaimplementowano (`Calculator`).  
  
4.  Utwórz wystąpienie obiektu <xref:System.Uri> klasę o nazwie `baseAddress` przy użyciu podstawowego adresu usługi. Adres podstawowy musi mieć schemat, który odpowiada transportu. W takim przypadku schemat transportu jest protokół HTTP, a adres zawiera specjalne identyfikator (URI) "localhost" i numer portu (8036) oraz adres podstawowego punktu końcowego ("serviceModelSamples /): `http://localhost:8036/serviceModelSamples/`.  
  
5.  Utwórz wystąpienie obiektu <xref:System.ServiceModel.ServiceHost> klasy `serviceType` i `baseAddress` zmiennych.  
  
6.  Dodawanie punktu końcowego do usługi za pomocą `contractType`, powiązanie i nazwę punktu końcowego (secureCalculator). Klienta należy złączyć adres podstawowy, a nazwa punktu końcowego za zaufany podczas inicjowania połączenia z usługą.  
  
7.  Wywołaj <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metodę, aby uruchomić usługę. Kod do wykonania tej procedury jest następujący:  
  
     [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
     [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]  
  
### <a name="using-the-binding-in-a-client"></a>Za pomocą tego powiązania w kliencie WPF  
 Ta procedura pokazuje sposób generowania serwera proxy, który komunikuje się z usługą. Serwer proxy jest generowany przy użyciu [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) który używa metadanych usługi w celu utworzenia serwera proxy.  
  
 Ta procedura powoduje utworzenie wystąpienia <xref:System.ServiceModel.WSHttpBinding> klasy do komunikowania się z usługą, a następnie wywołuje usługę.  
  
 W tym przykładzie używa tylko kod tworzenia klienta. Alternatywnie można użyć pliku konfiguracji, który jest pokazany w sekcji następującej procedury.  
  
##### <a name="to-use-a-binding-in-a-client-with-code"></a>Aby użyć powiązania w kliencie przy użyciu kodu  
  
1.  Użyj narzędzia SvcUtil.exe do generowania kodu serwera proxy z metadanych usługi. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Kod wygenerowany serwer proxy dziedziczy <xref:System.ServiceModel.ClientBase%601> klasy, która gwarantuje, że każdy klient ma niezbędne konstruktorów, metod i właściwości w celu komunikowania się z usługą WCF. W tym przykładzie zawiera wygenerowanego kodu `CalculatorClient` klasy, która implementuje `ICalculator` interfejsu, włączanie zgodności z kodem usługi.  
  
2.  Ta procedura kod dodaje się na początku `Main` metoda program kliencki.  
  
3.  Utwórz wystąpienie obiektu <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw jego tryb zabezpieczeń `Message` i typ do poświadczeń klienta `Windows`. Przykład nazwy zmiennej `clientBinding`.  
  
4.  Utwórz wystąpienie obiektu <xref:System.ServiceModel.EndpointAddress> klasę o nazwie `serviceAddress`. Inicjuje wystąpienie przy użyciu podstawowego adresu połączona z wybranej nazwy punktu końcowego.  
  
5.  Utwórz wystąpienie wygenerowanej klasy klienta za pomocą `serviceAddress` i `clientBinding` zmiennych.  
  
6.  Wywołaj <xref:System.ServiceModel.ClientBase%601.Open%2A> metodzie, jak pokazano w poniższym kodzie.  
  
7.  Wywoła usługę i wyświetlić wyniki.  
  
     [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
     [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]  
  
## <a name="using-the-configuration-file"></a>Przy użyciu pliku konfiguracji  
 Zamiast tworzenia powiązania z kodem proceduralnym, można użyć następującego kodu pokazano sekcję powiązania w pliku konfiguracji.  
  
 Jeśli nie masz już usługę zdefiniowane, zobacz [projektowanie i Implementowanie usług](../../../docs/framework/wcf/designing-and-implementing-services.md), i [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md).  
  
 **Uwaga** kod tej konfiguracji jest używany w plikach konfiguracji usługi i klienta.  
  
#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a>Aby włączyć zabezpieczenia transferu na usługi w domenie Windows przy użyciu konfiguracji  
  
1.  Dodaj [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu [ \<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) sekcji pliku konfiguracji.  
  
2.  Dodaj <`binding`> elementu <`WSHttpBinding`> element i ustaw `configurationName` atrybut na wartość, które są odpowiednie dla aplikacji.  
  
3.  Dodaj <`security`> element i ustaw `mode` atrybutu do wiadomości.  
  
4.  Dodaj <`message`> element i ustaw `clientCredentialType` atrybutu Windows.  
  
5.  W pliku konfiguracji usługi, należy zastąpić `<bindings>` sekcję poniższym kodem. Jeśli nie masz jeszcze pliku konfiguracji usługi, zobacz [przy użyciu powiązania do konfigurowania usług i klientów](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
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
  
### <a name="using-the-binding-in-a-client"></a>Za pomocą tego powiązania w kliencie WPF  
 Ta procedura pokazuje, jak można wygenerować dwa pliki: serwer proxy, który komunikuje się z usługą i pliku konfiguracji. Omówiono także zmiany w programie klienckim jest trzeci plik używany przez klienta.  
  
##### <a name="to-use-a-binding-in-a-client-with-configuration"></a>Aby użyć powiązania w kliencie za pomocą konfiguracji  
  
1.  Użyj narzędzia SvcUtil.exe do generowania pliku kodu i konfiguracji serwera proxy z metadanych usługi. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Zastąp [ \<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) części pliku konfiguracyjnego wygenerowane z kodu konfiguracji z poprzedniej sekcji.  
  
3.  Kod proceduralny zostanie wstawiony na początku `Main` metoda program kliencki.  
  
4.  Utwórz wystąpienie wygenerowanej klasy klienta przekazując nazwę powiązania w pliku konfiguracyjnym jako parametr wejściowy.  
  
5.  Wywołaj <xref:System.ServiceModel.ClientBase%601.Open%2A> metodzie, jak pokazano w poniższym kodzie.  
  
6.  Wywoła usługę i wyświetlić wyniki.  
  
     [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]  
  
 [!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)] 
 [!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]      
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.WSHttpBinding>
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Instrukcje: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [Zabezpieczanie usług](../../../docs/framework/wcf/securing-services.md)
- [Przegląd zabezpieczeń](../../../docs/framework/wcf/feature-details/security-overview.md)
