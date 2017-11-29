---
title: "Wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi"
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
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6eae3a91856feff83e8e199cf552a987d99d5ba2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a>Wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi
W tym temacie pokazano sposób użycia niestandardowych poświadczeń z kodu aplikacji oraz sposobu wdrażania niestandardowego klienta i poświadczeń usługi.  
  
## <a name="credentials-extensibility-classes"></a>Klasy rozszerzalności poświadczeń  
 <xref:System.ServiceModel.Description.ClientCredentials> i <xref:System.ServiceModel.Description.ServiceCredentials> występują następujące klasy głównym dojścia do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] rozszerzalność zabezpieczeń. Te klasy poświadczenia zapewniają interfejsów API, które umożliwiają kodu aplikacji, aby ustawić informacje o poświadczeniach i konwertowania poświadczeń w tokenach zabezpieczających. (*Tokeny zabezpieczające* są formularz używany do przesyłania informacji o poświadczeniach wewnątrz wiadomości SOAP.) Obowiązki klasy te poświadczenia można podzielić na dwa obszary:  
  
-   Podaj interfejsów API dla aplikacji, aby określić informacje o poświadczenia.  
  
-   Przeprowadź fabryki dla <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementacji.  
  
 Zarówno <xref:System.ServiceModel.Description.ClientCredentials> i <xref:System.ServiceModel.Description.ServiceCredentials> klasy dziedziczą z klasy abstrakcyjnej <xref:System.ServiceModel.Security.SecurityCredentialsManager> klasa, która definiuje kontrakt dla zwracania <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]klasy poświadczeń i sposobie ich użycia w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Architektura zabezpieczeń, zobacz [Architektura zabezpieczeń](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f).  
  
 W domyślnej implementacji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługi typów poświadczenia dostarczane przez system i utworzyć Menedżer tokenów, który może obsługiwać te typy poświadczeń zabezpieczeń.  
  
## <a name="reasons-to-customize"></a>Powodów do dostosowania  
 Istnieje wiele przyczyn dostosowywania klas poświadczeń klienta lub usługi. Przedniej jest wymaganie, aby zmienić domyślny [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zachowania zabezpieczeń w zakresie obsługi poświadczenia dostarczane przez system typów, szczególnie z następujących powodów:  
  
-   Zmiany, które nie są możliwe przy użyciu innych punktów rozszerzania.  
  
-   Dodawanie nowych typów poświadczeń.  
  
-   Dodawanie nowych typów tokenu zabezpieczeń niestandardowych.  
  
 W tym temacie opisano sposób wdrażania niestandardowego klienta i poświadczeń usługi i z nich korzystać z kodu aplikacji.  
  
## <a name="first-in-a-series"></a>Pierwszy z serii  
 Tworzenie klasy niestandardowych poświadczeń jest tylko pierwszym krokiem, ponieważ jest przyczyna Dostosowywanie poświadczenia, aby zmienić [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zachowanie dotyczące poświadczeń inicjowania obsługi administracyjnej serializacji tokenu zabezpieczeń i uwierzytelniania. Innych tematach w tej sekcji opisano sposób tworzenia niestandardowych serializatorów i wystawcy uwierzytelnienia. W tym zakresie Tworzenie niestandardowego poświadczenia klasy jest pierwszym temacie w serii. Kolejne czynności (Tworzenie niestandardowych serializatorów i wystawcy uwierzytelnienia) jest możliwe tylko po tworzenia niestandardowych poświadczeń. Dodatkowe tematy, które na ten temat zawiera:  
  
-   [Jak: utworzyć dostawcę tokenu zabezpieczającego niestandardowych](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
  
-   [Porady: tworzenie wystawcy uwierzytelnienia tokenu zabezpieczeń niestandardowych](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
  
-   [Porady: Tworzenie tokenu niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-implement-custom-client-credentials"></a>Aby zaimplementować poświadczeń klienta  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Description.ClientCredentials> klasy.  
  
2.  Opcjonalny. Dodaj nowe metody lub właściwości dla nowych typów poświadczeń. Jeśli nie zostaną dodane nowe typy poświadczeń, Pomiń ten krok. W poniższym przykładzie dodano `CreditCardNumber` właściwości.  
  
3.  Zastąpienie <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> metody. Ta metoda jest automatycznie wywoływana przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury zabezpieczeń stosowania poświadczeń klienta. Ta metoda jest odpowiedzialny za tworzenie i zwracanie wystąpienia implementacja <xref:System.IdentityModel.Selectors.SecurityTokenManager> klasy.  
  
    > [!IMPORTANT]
    >  Należy zauważyć, że <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> metoda zostanie przesłonięta do tworzenia niestandardowych zabezpieczeń Menedżer tokenów. Menedżer tokenów zabezpieczających pochodną <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>, musi zwracać niestandardowego dostawcy tokenów zabezpieczających, pochodzących z <xref:System.IdentityModel.Selectors.SecurityTokenProvider>, aby utworzyć token zabezpieczający rzeczywistego. Jeśli ten wzorzec służący do tworzenia tokenów zabezpieczających nie są zgodne, aplikacja może działać niepoprawnie podczas <xref:System.ServiceModel.ChannelFactory> buforowania obiektów (to jest domyślne zachowanie dla serwerów proxy klienta WCF) skutkująca potencjalnie atakom podniesienie uprawnień. Niestandardowe poświadczenia obiektu w pamięci podręcznej jako część <xref:System.ServiceModel.ChannelFactory>. Jednak niestandardowego <xref:System.IdentityModel.Selectors.SecurityTokenManager> jest tworzona na każdego wywołania, co zmniejsza zagrożenie bezpieczeństwa, tak długo, jak logika tworzenia tokenu jest umieszczany w <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
4.  Zastąpienie <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A> metody.  
  
     [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
     [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]  
  
#### <a name="to-implement-a-custom-client-security-token-manager"></a>Aby zaimplementować Menedżer tokenów zabezpieczających klienta  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.  
  
2.  Opcjonalny. Zastąpienie <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metodę, jeśli niestandardowego <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementacji musi zostać utworzony. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]dostawcy tokenów zabezpieczeń niestandardowych, zobacz [porady: Tworzenie niestandardowego dostawcy tokenów zabezpieczających](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3.  Opcjonalny. Zastąpienie <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> metodę, jeśli niestandardowego <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> implementacji musi zostać utworzony. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]wystawcy uwierzytelnienia tokenu zabezpieczeń niestandardowych, zobacz [porady: Tworzenie niestandardowego wystawcę uwierzytelnienia tokenów zabezpieczających](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).  
  
4.  Opcjonalny. Zastąpienie <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> metodę, jeśli niestandardowego <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> musi zostać utworzony. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]tokeny zabezpieczające niestandardowych i serializatorów tokenu zabezpieczeń niestandardowych, zobacz [porady: Tworzenie niestandardowego tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
     [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]  
  
#### <a name="to-use-a-custom-client-credentials-from-application-code"></a>Aby użyć niestandardowego klienta poświadczenia z kodu aplikacji  
  
1.  Utwórz wystąpienie wygenerowanego klienta, który reprezentuje interfejs usługi lub utworzenia wystąpienia <xref:System.ServiceModel.ChannelFactory> wskazuje usługi, aby komunikować się z.  
  
2.  Usuń zachowanie poświadczeń klienta dostarczane przez system z <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> kolekcji, które mogą być udostępniane za pośrednictwem <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> właściwości.  
  
3.  Utwórz nowe wystąpienie klasy poświadczenia niestandardowego klienta i dodaj go do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> kolekcji, które mogą być udostępniane za pośrednictwem <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> właściwości.  
  
     [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
     [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]  
  
 Opisane w poprzedniej procedurze pokazano, jak użyć poświadczeń klienta z kodu aplikacji. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]poświadczenia można również skonfigurować przy użyciu pliku konfiguracji aplikacji. Za pomocą konfiguracji aplikacji jest często kodować, ponieważ umożliwia modyfikowanie parametrów aplikacji bez konieczności modyfikowania źródła, ponowną kompilację i ponownego wdrażania.  
  
 Następna procedura opisuje sposób zapewnienia obsługi konfiguracji niestandardowych poświadczeń.  
  
#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a>Tworzenie konfiguracji obsługę klientów niestandardowych poświadczeń  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Configuration.ClientCredentialsElement>.  
  
2.  Opcjonalny. Dodaj właściwości dla wszystkich parametrów dodatkowe czynności konfiguracyjne, które chcesz udostępnić za pośrednictwem konfiguracji aplikacji. W poniższym przykładzie dodaje jedną właściwość o nazwie `CreditCardNumber`.  
  
3.  Zastąpienie <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> klasy utworzone za pomocą elementu konfiguracji poświadczenia właściwość, aby zwracany typ niestandardowego klienta.  
  
4.  Zastąpienie <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A> metody. Metoda jest odpowiedzialna za tworzenie i zwraca wystąpienie klasy niestandardowego poświadczenia zgodnie z ustawieniami załadowanego z pliku konfiguracji. Wywołaj podstawowym <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> metody z tej metody można pobrać ustawień poświadczenia dostarczane przez system ładowane do wystąpienia poświadczeń klienta.  
  
5.  Opcjonalny. Jeśli dodano dodatkowe właściwości w kroku 2, należy zastąpić <xref:System.Configuration.ConfigurationElement.Properties%2A> właściwości do zarejestrowania ustawień dodatkowych konfiguracji dla konfiguracji struktury rozpoznać ich. Łączenie właściwości z właściwościami klasy podstawowej umożliwia dostarczane przez system ustawienia, które mają zostać skonfigurowane przy użyciu tego elementu konfiguracji poświadczenia niestandardowego klienta.  
  
     [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
     [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]  
  
 Po utworzeniu klasy obsługi konfiguracji, mogą zostać włączone do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration framework. Poświadczenia niestandardowego klienta do użycia w elementach zachowania punktu końcowego klienta, który umożliwia opisane w następnej procedurze.  
  
#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a>Aby zarejestrować i użyć niestandardowego klienta poświadczenia obsługi konfiguracji w konfiguracji aplikacji  
  
1.  Dodaj <`extensions`> element i <`behaviorExtensions`> elementu do pliku konfiguracji.  
  
2.  Dodaj <`add`> elementu <`behaviorExtensions`> element i ustaw `name` atrybutu odpowiednią wartość.  
  
3.  Ustaw `type` atrybutu do w pełni kwalifikowaną nazwę typu. Obejmuje to też nazwa zestawu i inne atrybuty zestawu.  
  
    ```xml  
    <system.serviceModel>  
      <extensions>  
        <behaviorExtensions>  
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
      </extensions>  
    <system.serviceModel>  
    ```  
  
4.  Po zarejestrowaniu programu obsługi konfiguracji elementu niestandardowych poświadczeń można używać wewnątrz tego samego pliku konfiguracji, a nie dostarczane przez system <`clientCredentials`> elementu. Można użyć zarówno właściwości dostarczane przez system i wszystkie nowe właściwości, które zostały dodane do implementację programu obsługi konfiguracji. W poniższym przykładzie ustawiono wartość właściwości niestandardowej, używając `creditCardNumber` atrybutu.  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myClientCredentialsBehavior">  
          <myClientCredentials creditCardNumber="123-123-123"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
#### <a name="to-implement-custom-service-credentials"></a>Aby zaimplementować poświadczenia usługi niestandardowe  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Description.ServiceCredentials>.  
  
2.  Opcjonalny. Dodaj nowe właściwości do zapewnienia interfejsów API nowej wartości poświadczeń, które są dodawane. Jeśli nie zostaną dodane nowe wartości poświadczeń, Pomiń ten krok. W poniższym przykładzie dodano `AdditionalCertificate` właściwości.  
  
3.  Zastąpienie <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> metody. Ta metoda jest automatycznie wywoływana przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury stosowania poświadczeń klienta. Metoda jest odpowiedzialna za tworzenie i zwracanie wystąpienia implementacja <xref:System.IdentityModel.Selectors.SecurityTokenManager> klasy (opisany w następnej procedurze).  
  
4.  Opcjonalny. Zastąpienie <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A> metody. Jest to wymagane tylko w przypadku dodawania nowych właściwości lub pól wewnętrznej implementacji poświadczeń klienta.  
  
     [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
     [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]  
  
#### <a name="to-implement-a-custom-service-security-token-manager"></a>Aby zaimplementować niestandardowe usługi Menedżer tokenów zabezpieczających  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> klasy.  
  
2.  Opcjonalny. Zastąpienie <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> metodę, jeśli niestandardowego <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementacji musi zostać utworzony. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]dostawcy tokenów zabezpieczeń niestandardowych, zobacz [porady: Tworzenie niestandardowego dostawcy tokenów zabezpieczających](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3.  Opcjonalny. Zastąpienie <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> metodę, jeśli niestandardowego <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> implementacji musi zostać utworzony. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]wystawcy uwierzytelnienia tokenu zabezpieczeń niestandardowych, zobacz [porady: Tworzenie niestandardowego wystawcę uwierzytelnienia tokenów zabezpieczających](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md) tematu.  
  
4.  Opcjonalny. Zastąpienie <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> metodę, jeśli niestandardowego <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> musi zostać utworzony. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]tokeny zabezpieczające niestandardowych i serializatorów tokenu zabezpieczeń niestandardowych, zobacz [porady: Tworzenie niestandardowego tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
     [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]  
  
#### <a name="to-use-custom-service-credentials-from-application-code"></a>Korzystanie z usług niestandardowych poświadczeń z kodu aplikacji  
  
1.  Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost>.  
  
2.  Usuń zachowanie poświadczenia usługi dostarczane przez system z <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekcji.  
  
3.  Utwórz nowe wystąpienie klasy poświadczenia usługi niestandardowe i dodaj go do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekcji.  
  
     [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
     [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]  
  
 Dodaj obsługę konfiguracji, korzystając z procedury opisanej wcześniej w procedurze "`To create a configuration handler for custom client credentials`"i"`To register and use a custom client credentials configuration handler in the application configuration`." Jedyną różnicą jest użycie <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> klasy zamiast <xref:System.ServiceModel.Configuration.ClientCredentialsElement> klasy jako klasę podstawową dla konfiguracji programu obsługi. Element poświadczeń usługi niestandardowej następnie mogą być używane wszędzie tam, gdzie dostarczane przez system `<serviceCredentials>` element jest używany.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.Security.SecurityCredentialsManager>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 [Jak: utworzyć dostawcę tokenu zabezpieczającego niestandardowych](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Porady: tworzenie wystawcy uwierzytelnienia tokenu zabezpieczeń niestandardowych](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Porady: Tworzenie tokenu niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)
