---
title: 'Wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
ms.openlocfilehash: ddd9f03e26f7a8345f1070715e4877c533c361fb
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345267"
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a>Wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi

W tym temacie pokazano, jak zaimplementować niestandardowe poświadczenia klienta i usługi oraz jak używać niestandardowych poświadczeń z kodu aplikacji.

## <a name="credentials-extensibility-classes"></a>Klasy rozszerzalności poświadczeń

I <xref:System.ServiceModel.Description.ClientCredentials> <xref:System.ServiceModel.Description.ServiceCredentials> klasy są głównymi punktami wejścia do rozszerzalności zabezpieczeń Programu Windows Communication Foundation (WCF). Te klasy poświadczeń zapewniają interfejsy API, które umożliwiają kod aplikacji, aby ustawić informacje o poświadczeniach i przekonwertować typy poświadczeń na tokeny zabezpieczające. *(Tokeny zabezpieczające* są formularzem używanym do przesyłania informacji o poświadczeniach w komunikatach PROTOKOŁU SOAP). Obowiązki tych klas poświadczeń można podzielić na dwa obszary:

- Podaj interfejsy API dla aplikacji, aby ustawić informacje o poświadczeniach.

- Wykonaj jako fabryka dla <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementacji.

Domyślne implementacje podane w WCF obsługują typy poświadczeń dostarczonych przez system i tworzą menedżera tokenu zabezpieczającego, który jest w stanie obsługiwać te typy poświadczeń.

## <a name="reasons-to-customize"></a>Powody, dla których warto dostosować

Istnieje wiele powodów, dla dostosowywania klas poświadczeń klienta lub usługi. Przede wszystkim jest wymaganie, aby zmienić domyślne zachowanie zabezpieczeń WCF w odniesieniu do obsługi typów poświadczeń dostarczonych przez system, szczególnie z następujących powodów:

- Zmiany, które nie są możliwe przy użyciu innych punktów rozszerzalności.

- Dodawanie nowych typów poświadczeń.

- Dodawanie nowych niestandardowych typów tokenów zabezpieczających.

W tym temacie opisano sposób implementowania niestandardowych poświadczeń klienta i usługi oraz sposobu ich używania z kodu aplikacji.

## <a name="first-in-a-series"></a>Pierwszy w serii

Tworzenie klasy poświadczeń niestandardowych jest tylko pierwszym krokiem, ponieważ powodem dostosowywania poświadczeń jest zmiana zachowania WCF dotyczące inicjowania obsługi administracyjnej poświadczeń, serializacji tokenu zabezpieczającego lub uwierzytelniania. Inne tematy w tej sekcji opisano sposób tworzenia niestandardowych serializatorów i wystaw uwierzytelnienia. W związku z tym tworzenie klasy niestandardowych poświadczeń jest pierwszym tematem w serii. Kolejne akcje (tworzenie niestandardowych serializatorów i wystawców uwierzytelniających) można wykonać tylko po utworzeniu niestandardowych poświadczeń. Dodatkowe tematy, które opierają się na tym temacie obejmują:

- [Instrukcje: tworzenie niestandardowego dostawcy tokenów zabezpieczeń](how-to-create-a-custom-security-token-provider.md)

- [Instrukcje: Tworzenie niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń](how-to-create-a-custom-security-token-authenticator.md)

- [Jak: Tworzenie tokenu niestandardowego](how-to-create-a-custom-token.md).

## <a name="procedures"></a>Procedury

#### <a name="to-implement-custom-client-credentials"></a>Aby zaimplementować niestandardowe poświadczenia klienta

1. Zdefiniuj nową <xref:System.ServiceModel.Description.ClientCredentials> klasę pochodną klasy.

2. Element opcjonalny. Dodaj nowe metody lub właściwości dla nowych typów poświadczeń. Jeśli nie dodasz nowych typów poświadczeń, pomiń ten krok. Poniższy przykład `CreditCardNumber` dodaje właściwość.

3. Zastąd <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> w tej metodzie. Ta metoda jest automatycznie wywoływana przez infrastrukturę zabezpieczeń WCF, gdy używane jest niestandardowe poświadczenia klienta. Ta metoda jest odpowiedzialny za tworzenie i zwracanie <xref:System.IdentityModel.Selectors.SecurityTokenManager> wystąpienia implementacji klasy.

    > [!IMPORTANT]
    > Należy pamiętać, że <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> metoda jest zastępowana w celu utworzenia niestandardowego menedżera tokenów zabezpieczających. Menedżer tokenów zabezpieczających, <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>pochodzący z , musi zwrócić niestandardowego dostawcy tokenu zabezpieczającego, pochodzi od <xref:System.IdentityModel.Selectors.SecurityTokenProvider>, aby utworzyć rzeczywisty token zabezpieczający. Jeśli nie zastosujesz się do tego wzorca do tworzenia <xref:System.ServiceModel.ChannelFactory> tokenów zabezpieczających, aplikacja może działać niepoprawnie, gdy obiekty są buforowane (co jest domyślnym zachowaniem dla serwerów proxy klienta WCF), co może spowodować podniesienie uprawnień ataku. Obiekt poświadczeń niestandardowych <xref:System.ServiceModel.ChannelFactory>jest buforowany jako część pliku . Jednak niestandardowe <xref:System.IdentityModel.Selectors.SecurityTokenManager> jest tworzony przy każdym wywołaniu, co zmniejsza zagrożenie bezpieczeństwa, tak <xref:System.IdentityModel.Selectors.SecurityTokenManager>długo, jak logika tworzenia tokenu jest umieszczana w .

4. Zastąd <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A> w tej metodzie.

    [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
    [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]

#### <a name="to-implement-a-custom-client-security-token-manager"></a>Aby zaimplementować niestandardowy menedżer tokenów zabezpieczeń klienta

1. Zdefiniuj nową <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>klasę pochodną .

2. Element opcjonalny. Zastąd <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> w przypadku <xref:System.IdentityModel.Selectors.SecurityTokenProvider> utworzenia implementacji niestandardowej należy zastąpić metodę. Aby uzyskać więcej informacji na temat niestandardowych dostawców tokenów zabezpieczających, zobacz [Jak: Tworzenie niestandardowego dostawcy tokenów zabezpieczających](how-to-create-a-custom-security-token-provider.md).

3. Element opcjonalny. Zastąd <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> w przypadku <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> utworzenia implementacji niestandardowej należy zastąpić metodę. Aby uzyskać więcej informacji na temat niestandardowych tokenów zabezpieczających, zobacz [Jak: Tworzenie niestandardowego tokenu zabezpieczającego.](how-to-create-a-custom-security-token-authenticator.md)

4. Element opcjonalny. Zastąd <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> w przypadku <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> konieczności utworzenia metody niestandardowej należy zastąpić metodę niestandardową. Aby uzyskać więcej informacji na temat niestandardowych tokenów zabezpieczających i niestandardowych serializatorów tokenów zabezpieczających, zobacz [Jak: Tworzenie tokenu niestandardowego](how-to-create-a-custom-token.md).

    [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
    [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]

#### <a name="to-use-a-custom-client-credentials-from-application-code"></a>Aby użyć niestandardowych poświadczeń klienta z kodu aplikacji

1. Utwórz wystąpienie wygenerowanego klienta, który reprezentuje interfejs usługi, <xref:System.ServiceModel.ChannelFactory> lub utworzyć wystąpienie wskazujące na usługę, z którą chcesz się komunikować.

2. Usuń zachowanie poświadczeń klienta <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> dostarczonych przez system z <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> kolekcji, które są dostępne za pośrednictwem właściwości.

3. Utwórz nowe wystąpienie klasy poświadczeń <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> klienta niestandardowego i dodaj <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> ją do kolekcji, do której można uzyskać dostęp za pośrednictwem właściwości.

    [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
    [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]

Poprzednia procedura pokazuje, jak używać poświadczeń klienta z kodu aplikacji. Poświadczenia WCF można również skonfigurować przy użyciu pliku konfiguracji aplikacji. Korzystanie z konfiguracji aplikacji jest często lepsze niż kodowanie na twardo, ponieważ umożliwia modyfikację parametrów aplikacji bez konieczności modyfikowania źródła, ponownego komppilowania i ponownego rozmieszczania.

W następnej procedurze opisano sposób zapewnienia obsługi konfiguracji poświadczeń niestandardowych.

#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a>Tworzenie programu obsługi konfiguracji dla niestandardowych poświadczeń klienta

1. Zdefiniuj nową <xref:System.ServiceModel.Configuration.ClientCredentialsElement>klasę pochodną .

2. Element opcjonalny. Dodaj właściwości dla wszystkich dodatkowych parametrów konfiguracji, które chcesz udostępnić za pośrednictwem konfiguracji aplikacji. W poniższym przykładzie `CreditCardNumber`dodano jedną właściwość o nazwie .

3. Zastąpuj właściwość, <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> aby zwrócić typ niestandardowej klasy poświadczeń klienta utworzonej za pomocą elementu konfiguracji.

4. Zastąd <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A> w tej metodzie. Metoda jest odpowiedzialna za tworzenie i zwracanie wystąpienia niestandardowej klasy poświadczeń na podstawie ustawień załadowanych z pliku konfiguracji. Wywołanie <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> metody podstawowej z tej metody, aby pobrać ustawienia poświadczeń dostarczonych przez system załadowany do wystąpienia poświadczeń klienta niestandardowego.

5. Element opcjonalny. Jeśli dodano dodatkowe właściwości w kroku 2, należy <xref:System.Configuration.ConfigurationElement.Properties%2A> zastąpić właściwość w celu zarejestrowania dodatkowych ustawień konfiguracji dla struktury konfiguracji, aby je rozpoznać. Połącz swoje właściwości z właściwości klasy podstawowej, aby umożliwić ustawienia dostarczone przez system, które mają być skonfigurowane za pośrednictwem tego elementu konfiguracji poświadczeń klienta niestandardowego.

    [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
    [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]

Po uzyskaniu klasy obsługi konfiguracji można zintegrować z platformą konfiguracji WCF. Dzięki temu niestandardowe poświadczenia klienta mają być używane w elementach zachowania punktu końcowego klienta, jak pokazano w następnej procedurze.

#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a>Aby zarejestrować i używać niestandardowego programu obsługi konfiguracji poświadczeń klienta w konfiguracji aplikacji

1. Dodaj element `extensions`> <i <`behaviorExtensions`> element do pliku konfiguracyjnego.

2. Dodaj element `add`> <do <`behaviorExtensions`> element i ustaw atrybut na `name` odpowiednią wartość.

3. Ustaw `type` atrybut na w pełni kwalifikowaną nazwę typu. Należy również uwzględnić nazwę zestawu i inne atrybuty zestawu.

    ```xml
    <system.serviceModel>
      <extensions>
        <behaviorExtensions>
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
        </behaviorExtensions>
      </extensions>
    </system.serviceModel>
    ```

4. Po zarejestrowaniu programu obsługi konfiguracji, niestandardowy element poświadczeń może być używany wewnątrz `clientCredentials` tego samego pliku konfiguracji zamiast <> elementu dostarczonego przez system. Można użyć zarówno właściwości dostarczonych przez system, jak i wszystkie nowe właściwości dodane do implementacji programu obsługi konfiguracji. W poniższym przykładzie ustawia wartość `creditCardNumber` właściwości niestandardowej przy użyciu atrybutu.

    ```xml
    <behaviors>
      <endpointBehaviors>
        <behavior name="myClientCredentialsBehavior">
          <myClientCredentials creditCardNumber="123-123-123"/>
        </behavior>
      </endpointBehaviors>
    </behaviors>
    ```

#### <a name="to-implement-custom-service-credentials"></a>Aby zaimplementować poświadczenia usługi niestandardowej

1. Zdefiniuj nową <xref:System.ServiceModel.Description.ServiceCredentials>klasę pochodną .

2. Element opcjonalny. Dodaj nowe właściwości, aby zapewnić interfejsy API dla nowych wartości poświadczeń, które są dodawane. Jeśli nie dodasz nowych wartości poświadczeń, pomiń ten krok. Poniższy przykład `AdditionalCertificate` dodaje właściwość.

3. Zastąd <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> w tej metodzie. Ta metoda jest automatycznie wywoływana przez infrastrukturę WCF, gdy używane jest niestandardowe poświadczenia klienta. Metoda jest odpowiedzialna za tworzenie i zwracanie wystąpienia <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementacji klasy (opisane w następnej procedurze).

4. Element opcjonalny. Zastąd <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A> w tej metodzie. Jest to wymagane tylko wtedy, gdy dodawanie nowych właściwości lub pól wewnętrznych do implementacji poświadczeń klienta niestandardowego.

    [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
    [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]

#### <a name="to-implement-a-custom-service-security-token-manager"></a>Aby zaimplementować menedżera tokenów zabezpieczeń usługi niestandardowej

1. Zdefiniuj nową <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> klasę pochodną klasy.

2. Element opcjonalny. Zastąd <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> w przypadku <xref:System.IdentityModel.Selectors.SecurityTokenProvider> utworzenia implementacji niestandardowej należy zastąpić metodę. Aby uzyskać więcej informacji na temat niestandardowych dostawców tokenów zabezpieczających, zobacz [Jak: Tworzenie niestandardowego dostawcy tokenów zabezpieczających](how-to-create-a-custom-security-token-provider.md).

3. Element opcjonalny. Zastąd <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> w przypadku <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> utworzenia implementacji niestandardowej należy zastąpić metodę. Aby uzyskać więcej informacji na temat niestandardowych tokenów zabezpieczających, zobacz [Jak: Tworzenie tematu Uwierzytelniającego niestandardowego tokenu zabezpieczającego.](how-to-create-a-custom-security-token-authenticator.md)

4. Element opcjonalny. Zastąd <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> w przypadku <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> konieczności utworzenia metody niestandardowej należy zastąpić metodę niestandardową. Aby uzyskać więcej informacji na temat niestandardowych tokenów zabezpieczających i niestandardowych serializatorów tokenów zabezpieczających, zobacz [Jak: Tworzenie tokenu niestandardowego](how-to-create-a-custom-token.md).

    [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
    [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]

#### <a name="to-use-custom-service-credentials-from-application-code"></a>Aby użyć niestandardowych poświadczeń usługi z kodu aplikacji

1. Utwórz wystąpienie elementu <xref:System.ServiceModel.ServiceHost>.

2. Usuń zachowanie poświadczeń usługi <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> dostarczone przez system z kolekcji.

3. Utwórz nowe wystąpienie klasy poświadczeń <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> usługi niestandardowej i dodaj ją do kolekcji.

    [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
    [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]

Dodaj obsługę konfiguracji, wykonując kroki opisane wcześniej`To create a configuration handler for custom client credentials`w procedurach " " i "."`To register and use a custom client credentials configuration handler in the application configuration` Jedyną różnicą jest <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> użycie klasy <xref:System.ServiceModel.Configuration.ClientCredentialsElement> zamiast klasy jako klasy podstawowej dla programu obsługi konfiguracji. Element poświadczeń usługi niestandardowej może `<serviceCredentials>` być następnie używany wszędzie tam, gdzie używany jest element dostarczony przez system.

## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Security.SecurityCredentialsManager>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- [Instrukcje: tworzenie niestandardowego dostawcy tokenów zabezpieczeń](how-to-create-a-custom-security-token-provider.md)
- [Instrukcje: Tworzenie niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń](how-to-create-a-custom-security-token-authenticator.md)
- [Instrukcje: tworzenie tokenu niestandardowego](how-to-create-a-custom-token.md)
