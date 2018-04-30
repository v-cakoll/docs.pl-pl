---
title: 'Instrukcje: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
caps.latest.revision: 26
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 2828b6b9df313bab5a904712ad4e97cc7062f387
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a>Instrukcje: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows
W tym temacie przedstawiono sposób włączania zabezpieczeń transportu na [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usługi znajduje się w domenie systemu Windows, który jest wywoływany przez klientów w tej samej domenie. Aby uzyskać więcej informacji na temat tego scenariusza, zobacz [zabezpieczenia transportu z uwierzytelnianiem systemu Windows](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md). Przykładową aplikację, zobacz [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) próbki.  
  
 W tym temacie założono masz istniejący interfejs kontrakt i implementacja już zdefiniowany i dodaje się, że. Można również zmodyfikować istniejącą usługę i klienta.  
  
 Możesz zabezpieczyć usługi za pomocą poświadczeń systemu Windows całkowicie w kodzie. Alternatywnie, można pominąć części kodu przy użyciu pliku konfiguracji. W tym temacie przedstawiono w obu kierunkach. Upewnij się, że można używać tylko sposoby, nie oba.  
  
 Pierwsze trzy procedury pokazują, jak zabezpieczyć usługi przy użyciu kodu. W czwartym i piątym procedurze wyjaśniono, jak to zrobić przy użyciu pliku konfiguracji.  
  
## <a name="using-code"></a>Przy użyciu kodu  
 Kompletny kod dla usługi i klienta znajduje się w sekcji przykład na końcu tego tematu.  
  
 Pierwsza procedura przeprowadzi Cię przez tworzenie i konfigurowanie <xref:System.ServiceModel.WSHttpBinding> klasy w kodzie. Powiązanie używa transportu HTTP. To samo powiązanie jest używany przez klienta.  
  
#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a>Aby utworzyć WSHttpBinding, który używa poświadczeń systemu Windows i zabezpieczeń komunikatów  
  
1.  Kod tej procedury jest wstawiany na początku `Run` metody `Test` klasy w kodzie usługi, w sekcji przykładu.  
  
2.  Utworzenie wystąpienia <xref:System.ServiceModel.WSHttpBinding> klasy.  
  
3.  Ustaw <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> właściwość <xref:System.ServiceModel.WSHttpSecurity> klasy do <xref:System.ServiceModel.SecurityMode.Message>.  
  
4.  Ustaw <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> właściwość <xref:System.ServiceModel.MessageSecurityOverHttp> klasy do <xref:System.ServiceModel.MessageCredentialType.Windows>.  
  
5.  Kod do wykonania tej procedury jest następujący:  
  
     [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
     [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]  
  
### <a name="using-the-binding-in-a-service"></a>Za pomocą tego powiązania w usłudze  
 Jest to druga procedura przedstawia sposób użycia powiązania w samodzielnie hostowana usługa. Aby uzyskać więcej informacji na temat usług hostingu zobacz [Hosting usług](../../../docs/framework/wcf/hosting-services.md).  
  
##### <a name="to-use-a-binding-in-a-service"></a>Aby użyć powiązania w usłudze  
  
1.  Wstawianie kodu tej procedury po kodzie z poprzedniej procedury.  
  
2.  Utwórz <xref:System.Type> zmiennej o nazwie `contractType` i przypisz mu typ interfejsu (`ICalculator`). Korzystając z języka Visual Basic, użyj `GetType` operatora; przy użyciu języka C#, użyj `typeof` — słowo kluczowe.  
  
3.  Tworzenie drugiej `Type` zmiennej o nazwie `serviceType` i przypisz mu typ zaimplementowanego kontraktu (`Calculator`).  
  
4.  Utwórz wystąpienie <xref:System.Uri> klasy o nazwie `baseAddress` z adres podstawowy usługi. Adres podstawowy musi mieć schemat, który odpowiada transportu. W takim przypadku schemat transportu jest protokół HTTP i specjalną obejmuje adres "Localhost" identyfikator URI (Uniform Resource) i portu numer (8036) oraz adres podstawowy punkt końcowy ("serviceModelSamples /): http://localhost:8036/serviceModelSamples/.  
  
5.  Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy z `serviceType` i `baseAddress` zmiennych.  
  
6.  Dodaj punkt końcowy do usługi przy użyciu `contractType`, powiązanie i nazwę punktu końcowego (secureCalculator). Klient musi połączyć adres podstawowy, a nazwa punktu końcowego podczas inicjowania połączenia z usługą.  
  
7.  Wywołanie <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metodę, aby uruchomić usługę. Kod do wykonania tej procedury jest następujący:  
  
     [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
     [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]  
  
### <a name="using-the-binding-in-a-client"></a>Za pomocą tego powiązania na kliencie  
 W tej procedurze pokazano, jak Generowanie serwera proxy, który komunikuje się z usługą. Serwer proxy jest generowana za pomocą [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) metadanych usługi którego używa do utworzenia serwera proxy.  
  
 Ta procedura powoduje utworzenie wystąpienia <xref:System.ServiceModel.WSHttpBinding> klasy do komunikowania się z usługą, a następnie wywołuje usługę.  
  
 W tym przykładzie używane tylko kod, aby utworzyć klienta. Alternatywnie można użyć pliku konfiguracji, który jest wyświetlany w sekcji następującej procedury.  
  
##### <a name="to-use-a-binding-in-a-client-with-code"></a>Aby użyć powiązania w kliencie z kodem  
  
1.  Użyj narzędzia SvcUtil.exe do generowania kodu serwera proxy z metadanych usługi. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Kod wygenerowany serwer proxy dziedziczy <xref:System.ServiceModel.ClientBase%601> klasy, która zapewnia, że każdy klient ma niezbędne konstruktorów, metod i właściwości, aby komunikować się z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi. W tym przykładzie wygenerowany kod obejmuje `CalculatorClient` klasy, która implementuje `ICalculator` interfejsu włączenie zgodności z kodem usługi.  
  
2.  Kod tej procedury jest wstawiany na początku `Main` metody programu klienta.  
  
3.  Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw jego tryb zabezpieczeń `Message` i typu poświadczeń klienta `Windows`. Przykład nazwy zmiennej `clientBinding`.  
  
4.  Utwórz wystąpienie <xref:System.ServiceModel.EndpointAddress> klasy o nazwie `serviceAddress`. Inicjowanie wystąpienia przy użyciu podstawowego adresu połączona z nazwą punktu końcowego.  
  
5.  Utwórz wystąpienie wygenerowanej klasy klienta z `serviceAddress` i `clientBinding` zmiennych.  
  
6.  Wywołanie <xref:System.ServiceModel.ClientBase%601.Open%2A> metody, jak pokazano w poniższym kodzie.  
  
7.  Wywołania tej usługi i wyświetlić wyniki.  
  
     [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
     [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]  
  
## <a name="using-the-configuration-file"></a>Używanie pliku konfiguracji  
 Zamiast tworzenia powiązania z kodem procedur, można użyć poniższego kodu pokazano w sekcji powiązania w pliku konfiguracji.  
  
 Jeśli nie masz już zdefiniowane usługi, zobacz [projektowanie i Implementowanie usług](../../../docs/framework/wcf/designing-and-implementing-services.md), i [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md).  
  
 **Uwaga** kod tej konfiguracji jest używany w plikach konfiguracji usługi i klienta.  
  
#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a>Aby włączyć transfer zabezpieczeń w usłudze przy użyciu konfiguracji domeny systemu Windows  
  
1.  Dodaj [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu [ \<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) sekcji pliku konfiguracji.  
  
2.  Dodaj <`binding`> elementu <`WSHttpBinding`> element i ustaw `configurationName` atrybut na wartość odpowiednią do aplikacji.  
  
3.  Dodaj <`security`> element i ustaw `mode` atrybutu komunikatu.  
  
4.  Dodaj <`message`> element i ustaw `clientCredentialType` atrybutu do systemu Windows.  
  
5.  W pliku konfiguracji usługi, należy zastąpić `<bindings>` sekcję poniższym kodem. Jeśli nie masz już plik konfiguracji usługi, zobacz [za pomocą powiązania do konfigurowania usług i klientów](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
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
  
### <a name="using-the-binding-in-a-client"></a>Za pomocą tego powiązania na kliencie  
 W tej procedurze pokazano, jak wygenerować dwa pliki: serwer proxy, który komunikuje się z usługi i pliku konfiguracji. Zawiera również opis zmian program klienta, który jest trzeci plik używany przez klienta.  
  
##### <a name="to-use-a-binding-in-a-client-with-configuration"></a>Aby użyć powiązania w kliencie z konfiguracją  
  
1.  Użyj narzędzia SvcUtil.exe, aby wygenerować plik kodu i konfiguracji serwera proxy na podstawie metadanych usługi. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Zastąp [ \<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) sekcji pliku konfiguracji wygenerowany kod konfiguracji z poprzedniej sekcji.  
  
3.  Kod procedury dodaje się na początku `Main` metody programu klienta.  
  
4.  Utwórz wystąpienie wygenerowanej klasy klienta przekazywanie nazwę powiązania w pliku konfiguracyjnym jako parametr wejściowy.  
  
5.  Wywołanie <xref:System.ServiceModel.ClientBase%601.Open%2A> metody, jak pokazano w poniższym kodzie.  
  
6.  Wywołania tej usługi i wyświetlić wyniki.  
  
     [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]  
  
 [!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)] 
 [!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]      
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.WSHttpBinding>  
 [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Instrukcje: tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Zabezpieczanie usług](../../../docs/framework/wcf/securing-services.md)  
 [Przegląd zabezpieczeń](../../../docs/framework/wcf/feature-details/security-overview.md)
