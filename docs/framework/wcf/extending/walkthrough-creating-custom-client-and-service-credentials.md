---
title: 'Wskazówki: tworzenie niestandardowego klienta i poświadczeń usługi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
ms.openlocfilehash: e59d578407ece9f22925abff57737cca8bf78eac
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374462"
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a>Przewodnik: tworzenie niestandardowego klienta i poświadczeń usługi

W tym temacie pokazano, jak zaimplementować niestandardowe poświadczenia klienta i usługi oraz jak używać poświadczeń niestandardowych z kodu aplikacji.

## <a name="credentials-extensibility-classes"></a>Klasy rozszerzalności poświadczeń

Klasy <xref:System.ServiceModel.Description.ClientCredentials> i<xref:System.ServiceModel.Description.ServiceCredentials> są głównym punktem wejścia dla rozszerzalności zabezpieczeń Windows Communication Foundation (WCF). Te klasy poświadczeń zapewniają interfejsy API, które umożliwiają kodowi aplikacji Ustawianie informacji o poświadczeniach i konwertowanie typów poświadczeń na tokeny zabezpieczające. (*Tokeny zabezpieczające* są formularzem używanym do przesyłania informacji o poświadczeniach wewnątrz komunikatów SOAP). Obowiązki tych klas poświadczeń można podzielić na dwa obszary:

- Podaj interfejsy API dla aplikacji, aby ustawić informacje o poświadczeniach.

- Wykonaj jako fabrykę dla <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementacji.

Domyślne implementacje w programie WCF obsługują typy poświadczeń udostępniane przez system i tworzą Menedżera tokenów zabezpieczających, który może obsługiwać te typy poświadczeń.

## <a name="reasons-to-customize"></a>Przyczyny dostosowywania

Istnieje wiele powodów, dla których należy dostosować klienta lub klasy poświadczeń usług. Przede wszystkim jest wymagana zmiana domyślnego zachowania zabezpieczeń WCF w odniesieniu do obsługi typów poświadczeń dostarczonych przez system, szczególnie z następujących powodów:

- Zmiany, które nie są możliwe przy użyciu innych punktów rozszerzalności.

- Dodawanie nowych typów poświadczeń.

- Dodawanie nowych niestandardowych typów tokenów zabezpieczających.

W tym temacie opisano sposób implementowania niestandardowych poświadczeń klienta i usługi oraz sposób ich używania z kodu aplikacji.

## <a name="first-in-a-series"></a>Pierwszy w serii

Tworzenie klasy poświadczeń niestandardowych jest tylko pierwszym krokiem, ponieważ powodem dostosowywania poświadczeń jest zmiana zachowania WCF dotyczącego aprowizacji poświadczeń, serializacji tokenu zabezpieczeń lub uwierzytelniania. W innych tematach w tej sekcji opisano sposób tworzenia niestandardowych serializatorów i wystawców uwierzytelniania. W tym przypadku Tworzenie klasy poświadczeń niestandardowych jest pierwszym tematem w serii. Kolejne akcje (Tworzenie serializatorów niestandardowych i wystawców) można wykonać tylko po utworzeniu poświadczeń niestandardowych. Dodatkowe tematy, które zostały skompilowane w tym temacie, to m.in.:

- [Instrukcje: Tworzenie niestandardowego dostawcy tokenów zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)

- [Instrukcje: Tworzenie niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)

- [Instrukcje: Utwórz token](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)niestandardowy.

## <a name="procedures"></a>Procedury

#### <a name="to-implement-custom-client-credentials"></a>Aby zaimplementować niestandardowe poświadczenia klienta

1. Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Description.ClientCredentials> klasy.

2. Opcjonalny. Dodaj nowe metody lub właściwości dla nowych typów poświadczeń. Jeśli nie dodasz nowych typów poświadczeń, Pomiń ten krok. Poniższy przykład dodaje `CreditCardNumber` właściwość.

3. Zastąp <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> metody. Ta metoda jest automatycznie wywoływana przez infrastrukturę zabezpieczeń WCF, gdy jest używane niestandardowe poświadczenie klienta. Ta metoda jest odpowiedzialna za utworzenie i zwrócenie wystąpienia implementacji <xref:System.IdentityModel.Selectors.SecurityTokenManager> klasy.

    > [!IMPORTANT]
    > Należy pamiętać, że <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> Metoda jest zastępowana, aby utworzyć niestandardowy Menedżer tokenów zabezpieczających. Menedżer tokenów zabezpieczających, pochodzący z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>, musi zwrócić niestandardowego dostawcę tokenów zabezpieczających, który pochodzi od <xref:System.IdentityModel.Selectors.SecurityTokenProvider>, aby utworzyć rzeczywisty token zabezpieczający. Jeśli nie korzystasz z tego wzorca do tworzenia tokenów zabezpieczających, aplikacja może działać nieprawidłowo <xref:System.ServiceModel.ChannelFactory> , gdy obiekty są buforowane (to jest domyślne zachowanie dla serwerów proxy klienta WCF), co może spowodować podniesienie uprawnień. Obiekt poświadczeń niestandardowych jest buforowany w ramach elementu <xref:System.ServiceModel.ChannelFactory>. Jednak niestandardowy <xref:System.IdentityModel.Selectors.SecurityTokenManager> jest tworzony przy każdym wywołaniu, co zmniejsza zagrożenie bezpieczeństwa, o ile logika tworzenia tokenów została umieszczona <xref:System.IdentityModel.Selectors.SecurityTokenManager>w.

4. Zastąp <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A> metody.

    [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
    [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]

#### <a name="to-implement-a-custom-client-security-token-manager"></a>Aby zaimplementować niestandardowego menedżera tokenów zabezpieczeń klienta

1. Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.

2. Opcjonalny. Zastąp <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metodę, jeśli należy <xref:System.IdentityModel.Selectors.SecurityTokenProvider> utworzyć implementację niestandardową. Aby uzyskać więcej informacji o dostawcach niestandardowych tokenów [zabezpieczających, zobacz How to: Utwórz niestandardowego dostawcę](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)tokenów zabezpieczających.

3. Opcjonalny. Zastąp <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> metodę, jeśli należy <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> utworzyć implementację niestandardową. Aby uzyskać więcej informacji na temat wystawców niestandardowych tokenów [zabezpieczających, zobacz How to: Tworzenie niestandardowego wystawcy uwierzytelnienia](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)tokenu zabezpieczeń.

4. Opcjonalna. Zastąp <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> metodę, jeśli należy <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> utworzyć niestandardowy. Aby uzyskać więcej informacji na temat niestandardowych tokenów zabezpieczających i serializatorów niestandardowych [tokenów zabezpieczających, zobacz How to: Utwórz token](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)niestandardowy.

    [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
    [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]

#### <a name="to-use-a-custom-client-credentials-from-application-code"></a>Aby użyć niestandardowych poświadczeń klienta z kodu aplikacji

1. Utwórz wystąpienie wygenerowanego klienta, które reprezentuje interfejs usługi, lub Utwórz wystąpienie <xref:System.ServiceModel.ChannelFactory> wskazujące usługę, z którą chcesz się komunikować.

2. Usuń zachowanie poświadczeń klienta dostarczone przez system z <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> kolekcji, do której można uzyskać dostęp <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> za pośrednictwem właściwości.

3. Utwórz nowe wystąpienie niestandardowej klasy poświadczeń klienta i Dodaj je do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> kolekcji, do której można uzyskać dostęp <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> za pomocą właściwości.

    [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
    [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]

Poprzednia procedura pokazuje, jak używać poświadczeń klienta z kodu aplikacji. Poświadczenia usługi WCF można także skonfigurować przy użyciu pliku konfiguracji aplikacji. Korzystanie z konfiguracji aplikacji jest często lepszym kodowaniem, ponieważ umożliwia modyfikowanie parametrów aplikacji bez konieczności modyfikowania źródła, ponownej kompilacji i ponownego wdrożenia.

W następnej procedurze opisano, jak zapewnić obsługę konfiguracji poświadczeń niestandardowych.

#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a>Tworzenie programu obsługi konfiguracji dla niestandardowych poświadczeń klienta

1. Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Configuration.ClientCredentialsElement>.

2. Opcjonalny. Dodaj właściwości dla wszystkich dodatkowych parametrów konfiguracji, które chcesz uwidocznić za poorednictwem konfiguracji aplikacji. W poniższym przykładzie dodano jedną właściwość o `CreditCardNumber`nazwie.

3. Zastąp <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> właściwość w celu zwrócenia typu niestandardowej klasy poświadczeń klienta utworzonej za pomocą elementu konfiguracji.

4. Zastąp <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A> metody. Metoda jest odpowiedzialna za utworzenie i zwrócenie wystąpienia niestandardowej klasy poświadczeń na podstawie ustawień załadowanych z pliku konfiguracji. Wywołaj metodę <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> podstawową z tej metody, aby pobrać ustawienia poświadczeń dostarczonych przez system do niestandardowego wystąpienia poświadczeń klienta.

5. Opcjonalny. Jeśli dodano dodatkowe właściwości w kroku 2, należy zastąpić <xref:System.Configuration.ConfigurationElement.Properties%2A> właściwość w celu zarejestrowania dodatkowych ustawień konfiguracji dla platformy konfiguracji w celu ich rozpoznania. Połącz właściwości z właściwościami klasy bazowej, aby zezwolić na skonfigurowanie ustawień dostarczonych przez system za pomocą tego niestandardowego elementu konfiguracji poświadczeń klienta.

    [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
    [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]

Po utworzeniu klasy programu obsługi konfiguracji można ją zintegrować z platformą konfiguracji WCF. Pozwala to na użycie niestandardowych poświadczeń klienta w elementach zachowania punktu końcowego klienta, jak pokazano w następnej procedurze.

#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a>Rejestrowanie i używanie niestandardowej procedury obsługi konfiguracji poświadczeń klienta w konfiguracji aplikacji

1. Dodaj element >`extensions`< i <`behaviorExtensions`elementu > do pliku konfiguracji.

2. Dodaj element >`add`< do elementu <`behaviorExtensions` `name` > i ustaw odpowiednią wartość atrybutu.

3. `type` Ustaw atrybut na w pełni kwalifikowaną nazwę typu. Należy również uwzględnić nazwę zestawu i inne atrybuty zestawu.

    ```xml
    <system.serviceModel>
      <extensions>
        <behaviorExtensions>
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
        </behaviorExtensions>
      </extensions>
    <system.serviceModel>
    ```

4. Po zarejestrowaniu programu obsługi konfiguracji element poświadczeń niestandardowych może być używany w tym samym pliku konfiguracji, a nie w > <ego`clientCredentials`elementu. Można użyć zarówno właściwości dostarczonych przez system, jak i nowych właściwości, które zostały dodane do implementacji programu obsługi konfiguracji. Poniższy przykład ustawia wartość właściwości niestandardowej przy użyciu `creditCardNumber` atrybutu.

    ```xml
    <behaviors>
      <endpointBehaviors>
        <behavior name="myClientCredentialsBehavior">
          <myClientCredentials creditCardNumber="123-123-123"/>
        </behavior>
      </endpointBehaviors>
    </behaviors>
    ```

#### <a name="to-implement-custom-service-credentials"></a>Aby zaimplementować niestandardowe poświadczenia usługi

1. Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Description.ServiceCredentials>.

2. Opcjonalny. Dodaj nowe właściwości, aby udostępnić interfejsy API dla nowych wartości poświadczeń, które są dodawane. Jeśli nie dodasz nowych wartości poświadczeń, Pomiń ten krok. Poniższy przykład dodaje `AdditionalCertificate` właściwość.

3. Zastąp <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> metody. Ta metoda jest automatycznie wywoływana przez infrastrukturę WCF, gdy jest używane niestandardowe poświadczenie klienta. Metoda jest odpowiedzialna za utworzenie i zwrócenie wystąpienia implementacji <xref:System.IdentityModel.Selectors.SecurityTokenManager> klasy (opisany w następnej procedurze).

4. Opcjonalny. Zastąp <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A> metody. Jest to wymagane tylko wtedy, gdy dodajesz nowe właściwości lub pola wewnętrzne do niestandardowej implementacji poświadczeń klienta.

    [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
    [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]

#### <a name="to-implement-a-custom-service-security-token-manager"></a>Aby zaimplementować niestandardowego menedżera tokenów zabezpieczeń usługi

1. Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> klasy.

2. Opcjonalny. Zastąp <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> metodę, jeśli należy <xref:System.IdentityModel.Selectors.SecurityTokenProvider> utworzyć implementację niestandardową. Aby uzyskać więcej informacji o dostawcach niestandardowych tokenów [zabezpieczających, zobacz How to: Utwórz niestandardowego dostawcę](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)tokenów zabezpieczających.

3. Opcjonalny. Zastąp <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> metodę, jeśli należy <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> utworzyć implementację niestandardową. Aby uzyskać więcej informacji na temat wystawców niestandardowych tokenów [zabezpieczających, zobacz How to: Tworzenie niestandardowego tematu wystawcy](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md) uwierzytelnienia tokenu zabezpieczeń.

4. Opcjonalna. Zastąp <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> metodę, jeśli należy <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> utworzyć niestandardowy. Aby uzyskać więcej informacji na temat niestandardowych tokenów zabezpieczających i serializatorów niestandardowych [tokenów zabezpieczających, zobacz How to: Utwórz token](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)niestandardowy.

    [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
    [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]

#### <a name="to-use-custom-service-credentials-from-application-code"></a>Aby użyć niestandardowych poświadczeń usługi z kodu aplikacji

1. Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost>obiektu.

2. Usuń zachowanie poświadczeń usługi dostarczone przez system z <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekcji.

3. Utwórz nowe wystąpienie klasy poświadczeń usługi niestandardowej i Dodaj je do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekcji.

    [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
    [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]

Dodaj obsługę konfiguracji, wykonując czynności opisane wcześniej w procedurach "`To create a configuration handler for custom client credentials`" i "`To register and use a custom client credentials configuration handler in the application configuration`." Jedyną różnicą jest użycie <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> klasy zamiast <xref:System.ServiceModel.Configuration.ClientCredentialsElement> klasy jako klasy bazowej dla programu obsługi konfiguracji. Elementu niestandardowego poświadczenia usługi można użyć wszędzie tam, gdzie jest używany element udostępniony `<serviceCredentials>` przez system.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Security.SecurityCredentialsManager>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- [Instrukcje: Tworzenie niestandardowego dostawcy tokenów zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)
- [Instrukcje: Tworzenie niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)
- [Instrukcje: Tworzenie niestandardowego tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)
