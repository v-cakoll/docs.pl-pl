---
title: 'Wskazówki: tworzenie niestandardowego klienta i poświadczeń usługi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
ms.openlocfilehash: db137eb84108c6adbbf04a380934bb6da6936d61
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343054"
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a>Przewodnik: tworzenie niestandardowego klienta i poświadczeń usługi
W tym temacie pokazano, jak zaimplementować niestandardowego klienta i poświadczeń usługi i sposobu użycia niestandardowych poświadczeń w kodzie aplikacji.  
  
## <a name="credentials-extensibility-classes"></a>Poświadczenia rozszerzania klasy  
 <xref:System.ServiceModel.Description.ClientCredentials> i <xref:System.ServiceModel.Description.ServiceCredentials> klasy są głównym punktami wejściowymi umożliwiającymi rozszerzalność zabezpieczeń Windows Communication Foundation (WCF). W ramach tych zajęć poświadczenia zapewniają interfejsy API, pozwalających na korzystanie z kodu aplikacji, aby ustawić informacje o poświadczeniach i przekonwertować typy poświadczeń na tokeny zabezpieczające. (*Tokenów zabezpieczających* są formą używany do przesyłania informacji o poświadczeniach wewnątrz komunikaty protokołu SOAP.) Obowiązki klasy te poświadczenia można podzielić na dwóch obszarach:  
  
-   Podaj interfejsów API dla aplikacji ustawić informacje o poświadczeniach.  
  
-   Wykonaj jako fabryki dla <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementacji.  
  
 Zarówno <xref:System.ServiceModel.Description.ClientCredentials> i <xref:System.ServiceModel.Description.ServiceCredentials> klasy dziedziczą abstrakcyjnej <xref:System.ServiceModel.Security.SecurityCredentialsManager> klasę, która definiuje kontrakt dla zwracania <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
 Domyślnej implementacji dostarczane w programie WCF obsługują typy poświadczeń dostarczanych przez system i utworzyć Menedżer tokenów, który może obsługiwać te typy poświadczeń zabezpieczeń.  
  
## <a name="reasons-to-customize"></a>Powody do dostosowywania  
 Istnieje wiele przyczyn dostosowywania klas poświadczeń klienta lub usługę. Spełniono jest wymaganie, aby zmienić domyślne zachowanie zabezpieczeń usługi WCF w odniesieniu do obsługi poświadczeń dostarczanych przez system typów, szczególnie w przypadku następujących przyczyn:  
  
-   Zmiany, które nie są możliwe, korzystając z innych punktów rozszerzeń.  
  
-   Dodawanie nowych typów poświadczeń.  
  
-   Dodawanie nowych typów tokenu zabezpieczeń niestandardowych.  
  
 W tym temacie opisano sposób implementacji niestandardowego klienta i poświadczeń usługi i sposobu ich używania w kodzie aplikacji.  
  
## <a name="first-in-a-series"></a>Pierwszy z serii  
 Tworzenie klasy niestandardowych poświadczeń jest tylko pierwszym krokiem, ponieważ Przyczyna Dostosowywanie poświadczeń jest, aby zmienić zachowanie WCF dotyczące inicjowania obsługi poświadczeń, serializacji tokenu zabezpieczeń lub uwierzytelnianie. Inne tematy w tej sekcji opisano, jak utworzyć serializatorów niestandardowych obiektów i wystawców uwierzytelnienia. W tym zakresie tworzenie niestandardowe poświadczenia klasy jest pierwszym temacie w tej serii. Kolejne czynności (Tworzenie serializatorów niestandardowych obiektów i wystawców uwierzytelnienia) jest możliwe tylko po tworzenie niestandardowych poświadczeń. Dodatkowe tematy, które bazują na w tym temacie obejmują:  
  
-   [Instrukcje: Tworzenie niestandardowego dostawcy tokenów zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
  
-   [Instrukcje: Tworzenie wystawcy uwierzytelniania tokenu zabezpieczeń niestandardowych](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
  
-   [Instrukcje: Tworzenie tokenu niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-implement-custom-client-credentials"></a>Aby zaimplementować poświadczeń klienta  
  
1. Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Description.ClientCredentials> klasy.  
  
2. Opcjonalna. Dodaj nowe metody lub właściwości dla nowych typów poświadczeń. Jeśli nie zostaną dodane nowe typy poświadczeń, Pomiń ten krok. W poniższym przykładzie dodano `CreditCardNumber` właściwości.  
  
3. Zastąp <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> metody. Ta metoda jest wywoływana automatycznie przez infrastrukturę zabezpieczeń WCF, stosowania poświadczenia niestandardowego klienta. Ta metoda jest odpowiedzialny za tworzenie i zwrócenia wystąpienia implementację <xref:System.IdentityModel.Selectors.SecurityTokenManager> klasy.  
  
    > [!IMPORTANT]
    >  Ważne jest, aby pamiętać, że <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> metoda zostanie przesłonięta do tworzenia niestandardowych zabezpieczeń Menedżer tokenów. Menedżer tokenów zabezpieczeń pochodzące z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>, musi zwracać niestandardowego dostawcy tokenów zabezpieczeń, pochodzące z <xref:System.IdentityModel.Selectors.SecurityTokenProvider>, aby utworzyć token zabezpieczający rzeczywistych. Jeśli nie wykonuj tego wzorca do tworzenia tokenów zabezpieczających, aplikacja może działać niepoprawnie podczas <xref:System.ServiceModel.ChannelFactory> (co to jest domyślne zachowanie dla serwerów proxy klienta WCF), buforowania obiektów potencjalnie wynikowy do podniesienia poziomu uprawnień. Obiektu niestandardowego poświadczenia w pamięci podręcznej jako część <xref:System.ServiceModel.ChannelFactory>. Jednak niestandardowej <xref:System.IdentityModel.Selectors.SecurityTokenManager> jest tworzony na każdego wywołania, co zmniejsza zagrożenie bezpieczeństwa, tak długo, jak logiki tworzenia tokenu jest umieszczany w <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
4. Zastąp <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A> metody.  
  
     [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
     [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]  
  
#### <a name="to-implement-a-custom-client-security-token-manager"></a>Aby zaimplementować niestandardowego klienta Menedżer tokenów zabezpieczeń  
  
1. Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.  
  
2. Opcjonalna. Zastąp <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metodę, jeśli niestandardowy <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementacja musi zostać utworzona. Aby uzyskać więcej informacji na temat dostawcy tokenów zabezpieczeń niestandardowe zobacz [jak: Tworzenie niestandardowego dostawcy tokenów zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3. Opcjonalna. Zastąp <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> metodę, jeśli niestandardowy <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> implementacja musi zostać utworzona. Aby uzyskać więcej informacji na temat wystawcy uwierzytelniania tokenu zabezpieczeń niestandardowych zobacz [jak: Tworzenie wystawcy uwierzytelniania tokenu zabezpieczeń niestandardowych](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).  
  
4. Opcjonalna. Zastąp <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> metodę, jeśli niestandardowy <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> musi zostać utworzona. Aby uzyskać więcej informacji na temat tokenów zabezpieczających niestandardowych i serializatorów tokenu zabezpieczeń niestandardowych, zobacz [jak: Tworzenie tokenu niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
     [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]  
  
#### <a name="to-use-a-custom-client-credentials-from-application-code"></a>Aby użyć niestandardowego klienta poświadczeń w kodzie aplikacji  
  
1. Utwórz wystąpienie obiektu wygenerowanego klienta, który reprezentuje interfejs usługi lub Utwórz wystąpienie obiektu <xref:System.ServiceModel.ChannelFactory> wskazujący chcesz komunikować się za pomocą usługi.  
  
2. Usuń zachowanie poświadczeń klienta dostarczane przez system z <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> kolekcji, która jest możliwy za pośrednictwem <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> właściwości.  
  
3. Utwórz nowe wystąpienie klasy poświadczenia niestandardowego klienta i dodać go do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> kolekcji, która jest możliwy za pośrednictwem <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> właściwości.  
  
     [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
     [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]  
  
 Poprzedniej procedurze pokazano, jak przy użyciu poświadczeń klienta w kodzie aplikacji. Poświadczenia usługi WCF można również skonfigurować przy użyciu pliku konfiguracji aplikacji. Za pomocą konfiguracji aplikacji jest często kodować ponieważ umożliwia modyfikowanie parametry aplikacji bez konieczności modyfikowania źródła, ponownego kompilowania i ponownego wdrażania.  
  
 Następna procedura opisuje sposób zapewnienia obsługi konfiguracji niestandardowych poświadczeń.  
  
#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a>Tworzenie modułu obsługi konfiguracji poświadczeń klienta  
  
1. Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Configuration.ClientCredentialsElement>.  
  
2. Opcjonalna. Dodaj właściwości dla wszystkich parametrów dodatkowe czynności konfiguracyjne, które chcesz udostępnić za pośrednictwem konfiguracji aplikacji. Poniższy przykład dodaje jedną właściwość o nazwie `CreditCardNumber`.  
  
3. Zastąp <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> właściwość, aby zwracany typ klientów niestandardowych poświadczeń klasy utworzone za pomocą elementu konfiguracji.  
  
4. Zastąp <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A> metody. Metoda jest odpowiedzialna za tworzenie i zwrócenia wystąpienia klasy niestandardowe poświadczenia zgodnie z ustawieniami załadowanego z pliku konfiguracji. Wywołanie bazy <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> metody z tej metody można pobrać ustawień poświadczeń dostarczanych przez system załadowane do swojego wystąpienia poświadczenia niestandardowego klienta.  
  
5. Opcjonalna. Jeśli dodano dodatkowe właściwości w kroku 2, należy zastąpić <xref:System.Configuration.ConfigurationElement.Properties%2A> właściwości, aby zarejestrować swoje dodatkowe ustawienia konfiguracji dla konfiguracji struktury je rozpoznać. Połącz swoje właściwości, za pomocą właściwości klasy bazowej, aby zezwolić dostarczane przez system ustawienia można skonfigurować za pomocą tego elementu konfiguracji poświadczeń klienta.  
  
     [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
     [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]  
  
 Po utworzeniu klasy obsługi konfiguracji, może zostać zintegrowany w ramach konfiguracji usługi WCF. Poświadczenia niestandardowego klienta do użycia w elementach zachowanie punktu końcowego klienta, który umożliwia jak pokazano w następnej procedurze.  
  
#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a>Do zarejestrowania i używania programu obsługi konfiguracji poświadczeń klienta w konfiguracji aplikacji  
  
1. Dodaj <`extensions`> element i <`behaviorExtensions`> element pliku konfiguracji.  
  
2. Dodaj <`add`> elementu <`behaviorExtensions`> element i ustaw `name` atrybutu do odpowiedniej wartości.  
  
3. Ustaw `type` atrybutu do w pełni kwalifikowaną nazwę typu. Również obejmować nazwę zestawu i innych atrybutów zestawu.  
  
    ```xml  
    <system.serviceModel>  
      <extensions>  
        <behaviorExtensions>  
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
      </extensions>  
    <system.serviceModel>  
    ```  
  
4. Po zarejestrowaniu programu obsługi konfiguracji elementu niestandardowych poświadczeń można użyć wewnątrz tego samego pliku konfiguracji, a nie dostarczane przez system <`clientCredentials`> element. Można użyć właściwości dostarczanych przez system i nowe właściwości, które zostały dodane do implementację programu obsługi konfiguracji. W poniższym przykładzie ustawiono wartość właściwości niestandardowej, w którym używana jest `creditCardNumber` atrybutu.  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myClientCredentialsBehavior">  
          <myClientCredentials creditCardNumber="123-123-123"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
#### <a name="to-implement-custom-service-credentials"></a>Aby zaimplementować niestandardowy poświadczenia  
  
1. Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Description.ServiceCredentials>.  
  
2. Opcjonalna. Dodaj nowe właściwości, aby zapewnić interfejsów API dla nowych wartości poświadczenia, które są dodawane. Jeśli nie zostaną dodane nowe wartości poświadczeń, Pomiń ten krok. W poniższym przykładzie dodano `AdditionalCertificate` właściwości.  
  
3. Zastąp <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> metody. Ta metoda jest wywoływana automatycznie przez infrastrukturę usługi WCF, gdy poświadczenia niestandardowe klienta są używane. Metoda jest odpowiedzialny za tworzenie i zwrócenia wystąpienia implementację <xref:System.IdentityModel.Selectors.SecurityTokenManager> klasy (opisany w następnej procedurze).  
  
4. Opcjonalna. Zastąp <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A> metody. Jest to wymagane, tylko wtedy, gdy dodawania nowych właściwości lub pól wewnętrznej implementacji poświadczenia niestandardowego klienta.  
  
     [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
     [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]  
  
#### <a name="to-implement-a-custom-service-security-token-manager"></a>Aby zaimplementować niestandardowy usługi Menedżer tokenów zabezpieczeń  
  
1. Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> klasy.  
  
2. Opcjonalna. Zastąp <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> metodę, jeśli niestandardowy <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementacja musi zostać utworzona. Aby uzyskać więcej informacji na temat dostawcy tokenów zabezpieczeń niestandardowe zobacz [jak: Tworzenie niestandardowego dostawcy tokenów zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3. Opcjonalna. Zastąp <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> metodę, jeśli niestandardowy <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> implementacja musi zostać utworzona. Aby uzyskać więcej informacji na temat wystawcy uwierzytelniania tokenu zabezpieczeń niestandardowych zobacz [jak: Tworzenie niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md) tematu.  
  
4. Opcjonalna. Zastąp <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> metodę, jeśli niestandardowy <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> musi zostać utworzona. Aby uzyskać więcej informacji na temat tokenów zabezpieczających niestandardowych i serializatorów tokenu zabezpieczeń niestandardowych, zobacz [jak: Tworzenie tokenu niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
     [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]  
  
#### <a name="to-use-custom-service-credentials-from-application-code"></a>Przy użyciu poświadczeń usługi niestandardowe w kodzie aplikacji  
  
1. Utwórz wystąpienie obiektu <xref:System.ServiceModel.ServiceHost>.  
  
2. Usuń zachowanie poświadczenia usługi dostarczane przez system z <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekcji.  
  
3. Utwórz nowe wystąpienie klasy poświadczenia usługi niestandardowe i dodać go do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekcji.  
  
     [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
     [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]  
  
 Dodanie obsługi konfiguracji, korzystając z procedury opisanej wcześniej w procedurze "`To create a configuration handler for custom client credentials`"i"`To register and use a custom client credentials configuration handler in the application configuration`." Jedyną różnicą jest użycie <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> klasy zamiast <xref:System.ServiceModel.Configuration.ClientCredentialsElement> klasy jako klasę bazową dla programu obsługi konfiguracji. Element poświadczeń usługa niestandardowa następnie może być używane wszędzie tam, gdzie dostarczane przez system `<serviceCredentials>` element jest używany.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Security.SecurityCredentialsManager>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- [Instrukcje: Tworzenie niestandardowego dostawcy tokenów zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)
- [Instrukcje: Tworzenie wystawcy uwierzytelniania tokenu zabezpieczeń niestandardowych](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)
- [Instrukcje: Tworzenie tokenu niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)
