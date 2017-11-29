---
title: Federacja
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
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 71b685b372edc99ffa8ea00180cdf622c5e48632
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="federation"></a>Federacja
Ten temat zawiera krótki przegląd koncepcji zabezpieczeń. Opisano również [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] obsługę wdrażania architektury zabezpieczeń. Przykładową aplikację prezentującą federacyjnego, zobacz [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="definition-of-federated-security"></a>Definicja zabezpieczeń  
 Zabezpieczeń umożliwia czyste rozdzielenie klient uzyskuje dostęp do usługi i skojarzone procedury uwierzytelniania i autoryzacji. Zabezpieczeń umożliwia także współpracy w wielu systemów, sieci i organizacji w obszarach różnych zaufania.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Umożliwia tworzenie i wdrażanie systemów rozproszonych, korzystających z federacyjnego zabezpieczenia.  
  
### <a name="elements-of-a-federated-security-architecture"></a>Elementy architektury zabezpieczeń  
 Architektura zabezpieczeń ma trzy kluczowe elementy, zgodnie z opisem w poniższej tabeli.  
  
|Element|Opis|  
|-------------|-----------------|  
|Domena/obszaru|Pojedynczą jednostkę administrowania zabezpieczeniami lub relacji zaufania. Typowe domeny mogą obejmować pojedynczej organizacji.|  
|Federacja|Kolekcja domen, które zostało ustanowione zaufania. Poziom zaufania może się różnić, ale zwykle obejmuje uwierzytelniania i prawie zawsze zawiera autoryzacji. Typowy Federacji może obejmować wiele organizacji, które zostało ustanowione zaufania, aby uzyskać dostęp do zestawu zasobów.|  
|Usługa tokenu zabezpieczającego (STS)|Usługi sieci Web, która wystawia tokeny zabezpieczające; oznacza to ułatwia potwierdzenia oparte na dowód, któremu ufa do każdego, kto w relacji zaufania. Ten proces jest podstawą przekazywania zaufania między domenami.|  
  
### <a name="example-scenario"></a>Przykładowy scenariusz  
 Na poniższej ilustracji przedstawiono przykład zabezpieczeń.  
  
 ![Federacyjna](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")  
  
 Taki scenariusz obejmuje dwie organizacje: A i B organizacji B. zawiera zasobu sieci Web (usługa sieci Web) niektórzy użytkownicy w organizacji A znaleźć cenne.  
  
> [!NOTE]
>  Ta sekcja używa warunki *zasobów*, *usługi*, i *usługi sieci Web* zamiennie.  
  
 Zazwyczaj organizacji B wymaga użytkownik z organizacji A podania niektórych prawidłowy formy uwierzytelniania przed uzyskaniem dostępu do usługi. Ponadto organizacja może również wymagać, użytkownik mieć możliwość dostępu do określonego zasobu w. Jednym ze sposobów rozwiązania tego problemu i umożliwienie użytkownikom w organizacji, A dostęp do zasobu w organizacji B wygląda następująco:  
  
-   Użytkownicy z organizacji, A zarejestrować poświadczeń (nazwy użytkownika i hasło) z organizacją B.  
  
-   Podczas dostępu do zasobów użytkownicy z organizacji A prezentować swoje poświadczenia dla organizacji B oraz uwierzytelniania przed uzyskaniem dostępu do zasobu.  
  
 Takie podejście ma trzy znaczących wady:  
  
-   Organizacja B ma zarządzać poświadczenia dla użytkowników z organizacji, A oprócz zarządzania poświadczeń użytkowników lokalnych.  
  
-   Użytkownicy w organizacji A należy obsługiwać dodatkowy zestaw poświadczeń (oznacza to, należy pamiętać o nazwę dodatkowe użytkownika i hasło) oprócz poświadczenia używają zwykle uzyskują dostęp do zasobów w organizacji A. To zwykle zachęca do rozwiązania przy użyciu tej samej nazwy użytkownika i hasła w wielu lokacjach usługi, która jest słaby zabezpieczenie.  
  
-   Architektura nie działa zgodnie z organizacji więcej postrzegać zasobów w organizacji B jako pewnej wartości.  
  
 Alternatywne podejście, które dotyczy wady opisane powyżej, jest fragmentów zabezpieczeń. W takie podejście organizacji, A i B ustanawiania relacji zaufania i stosować zabezpieczeń tokenu usługi (STS) umożliwia utrzymywanie właściwych ustanowić relacji zaufania.  
  
 W architekturze zabezpieczeń użytkownicy z organizacji A pamiętać, że jeśli chcą, aby uzyskać dostęp do usługi sieci Web w organizacji B, który muszą prezentować tokenu zabezpieczającego prawidłowe z STS w organizacji B, który uwierzytelnia i autoryzuje dostępu do określonej usługi.  
  
 Na skontaktowanie się z STS B, użytkownicy otrzymują inny poziom pośredników od zasady skojarzone z usługi STS. Podmioty zabezpieczeń muszą prezentować tokenu z STS A (to znaczy obszar zaufania klienta), przed STS B mogą wystawiać ich tokenu zabezpieczającego. To jest następstwem relacji zaufania między dwiema organizacjami i oznacza organizacji B nie musi zarządzać tożsamościami użytkowników z organizacji A. W praktyce STS B zazwyczaj ma wartość null `issuerAddress` i `issuerMetadataAddress`. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Porady: Konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md). W takim przypadku klient sprawdza zasad lokalnych można znaleźć usługi STS A. Ta konfiguracja jest nazywana *home federacyjnego obszaru* i lepiej skaluje ponieważ STS B nie ma do przechowywania informacji o STS A.  
  
 Następnie skontaktuj się z STS w organizacji, A użytkownicy i uzyskania tokenu zabezpieczającego z uwzględnieniem poświadczenia uwierzytelniania, które zazwyczaj używają do uzyskiwania dostępu do innych zasobów organizacji A. Eliminuje to również problem użytkownicy muszą obsługiwać wiele zestawów poświadczeń lub w wielu lokacjach usługi przy użyciu tego samego zestawu poświadczeń.  
  
 Gdy użytkownicy uzyskują tokenu zabezpieczającego z STS A, ich obecny token do usługi STS B. organizacji B będzie kontynuowane do wykonania autoryzację żądań użytkowników i wystawia token zabezpieczający dla użytkowników z własny zestaw tokenów zabezpieczających. Użytkownicy można prezentować swoje token do zasobu w organizacji B i uzyskania dostępu do usługi.  
  
## <a name="support-for-federated-security-in-wcf"></a>Obsługa zabezpieczeń w programie WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zapewnia obsługę gotowe do wdrożenia architektury zabezpieczeń za pomocą [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 [ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element zapewnia bezpieczne, niezawodne i interoperacyjne powiązanie, które powoduje użycie protokołu HTTP jako podstawowy mechanizm transportu dla stylu komunikacji "żądanie-odpowiedź" wykorzystujące tekst i kodu XML, ponieważ format kodowania danych przesyłanych w sieci.  
  
 Korzystanie z [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) w federacyjnego zabezpieczenia scenariusz może być odłączona na dwa etapy logicznie niezależny, zgodnie z opisem w poniższych sekcjach.  
  
### <a name="phase-1-design-phase"></a>Faza 1: Faza projektowania  
 W fazie projektowania, klient używa [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) odczytać zasad udostępnia punkt końcowy usługi i gromadzić wymagania usługi uwierzytelniania i autoryzacji. Odpowiednie serwery proxy, tak aby utworzyć następującego wzorca komunikacji zabezpieczeń po stronie klienta:  
  
-   Uzyskania tokenu zabezpieczającego z STS w obszarze zaufania klienta.  
  
-   Przedstawia tokenu Zabezpieczającego w obszarze zaufania usługi.  
  
-   Uzyskania tokenu zabezpieczającego z STS w obszarze zaufania usługi.  
  
-   Przedstawia token do usługi, aby uzyskać dostęp do usługi.  
  
### <a name="phase-2-run-time-phase"></a>Faza 2: Faza środowiska wykonawczego  
 Podczas fazy środowiska wykonawczego klient tworzy wystąpienie obiektu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klasy klienta i sprawia, że wywołanie za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta. Struktura podstawowej [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje opisane powyżej kroki we wzorcu federacyjnego zabezpieczenia komunikacji i umożliwia klientowi bezproblemowo korzystanie z usługi.  
  
## <a name="sample-implementation-using-wcf"></a>Przykładowe zastosowanie przy użyciu programu WCF  
 Na poniższej ilustracji przedstawiono przykładowe zastosowanie dla architektury zabezpieczeń przy użyciu natywnej obsługi z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 ![Federacyjna zabezpieczeń w programie WCF](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")  
  
### <a name="example-myservice"></a>Przykład Moja_usługa  
 Usługa `MyService` udostępnia jeden punkt końcowy za pośrednictwem `MyServiceEndpoint`. Na poniższej ilustracji przedstawiono address, binding i kontrakt skojarzony z punktem końcowym.  
  
 ![Federacyjna](../../../../docs/framework/wcf/feature-details/media/myservice.gif "Moja_usługa")  
  
 Punkt końcowy usługi `MyServiceEndpoint` używa [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i wymaga prawidłowego tokenu zabezpieczeń potwierdzenia Markup Language (SAML) z `accessAuthorized` oświadczenia wydane przez usługę STS B. Jest to deklaratywnie określone w konfiguracji usługi.  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.MyService"      
        behaviorConfiguration='MyServiceBehavior'>  
        <endpoint address=""  
            binding=" wsFederationHttpBinding"  
            bindingConfiguration='MyServiceBinding'  
            contract="Federation.IMyService" />  
   </service>  
  </services>  
  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by MyService. It redirects   
    clients to STS-B. -->  
      <binding name='MyServiceBinding'>  
        <security mode="Message">  
           <message issuedTokenType=  
"http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
           <issuer address="http://localhost/FederationSample/STS-B/STS.svc" />  
            <issuerMetadata   
           address=  
"http://localhost/FederationSample/STS-B/STS.svc/mex" />  
         <requiredClaimTypes>  
            <add claimType="http://tempuri.org:accessAuthorized" />  
         </requiredClaimTypes>  
        </message>  
      </security>  
      </binding>  
    </wsFederationHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <behavior name='MyServiceBehavior'>  
      <serviceAuthorization   
operationRequirementType="FederationSample.MyServiceOperationRequirement, MyService" />  
       <serviceCredentials>  
         <serviceCertificate findValue="CN=FederationSample.com"  
         x509FindType="FindBySubjectDistinguishedName"  
         storeLocation='LocalMachine'  
         storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
>  Niewielkie punktu należy zauważyć, dotyczących oświadczeń wymagane przez `MyService`. Druga liczba wskazuje, że `MyService` wymaga tokenu SAML z `accessAuthorized` oświadczeń. Mówiąc ściślej, określa typ oświadczenia, które `MyService` wymaga. Pełna nazwa tego typu oświadczenia jest http://tempuri.org:accessAuthorized (wraz z skojarzona przestrzeń nazw), który jest używany w pliku konfiguracji usługi. Wartość tego oświadczenia wskazuje na obecność tego oświadczenia i przyjęto, że można ustawić `true` przez usługę STS B.  
  
 W czasie wykonywania, te zasady są wymuszane przez `MyServiceOperationRequirement` klasy, która jest zaimplementowany jako część `MyService`.  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>STS B  
 Na poniższej ilustracji przedstawiono STS B. Jak wspomniano wcześniej, Usługa tokenu zabezpieczającego (STS) jest również usługi sieci Web i może mieć jego skojarzone punkty końcowe, zasad i tak dalej.  
  
 ![Federacyjna](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")  
  
 STS B udostępnia jeden punkt końcowy o nazwie `STSEndpoint` które może być używany do żądania tokenów zabezpieczających. W szczególności STS B wystawia tokeny SAML z `accessAuthorized` oświadczenia, które mogą być przedstawiane w `MyService` lokacji usługi do uzyskiwania dostępu do usługi. Jednak STS B wymaga od użytkowników istnieje prawidłowy token SAML wystawione przez usługi STS A, który zawiera `userAuthenticated` oświadczeń. Jest to deklaratywnie określony w konfiguracji usługi STS.  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_B" behaviorConfiguration=  
     "STS-B_Behavior">  
    <endpoint address=""  
              binding="wsFederationHttpBinding"  
              bindingConfiguration='STS-B_Binding'  
      contract="FederationSample.ISts" />  
    </service>  
  </services>  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by STS-B. It redirects clients to   
         STS-A. -->  
      <binding name='STS-B_Binding'>  
        <security mode='Message'>  
          <message issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
          <issuer address='http://localhost/FederationSample/STS-A/STS.svc' />  
          <issuerMetadata address='http://localhost/FederationSample/STS-A/STS.svc/mex'/>  
          <requiredClaimTypes>  
            <add claimType='http://tempuri.org:userAuthenticated'/>  
          </requiredClaimTypes>  
          </message>  
        </security>  
    </binding>  
   </wsFederationHttpBinding>  
  </bindings>  
  <behaviors>  
  <behavior name='STS-B_Behavior'>  
    <serviceAuthorization   operationRequirementType='FederationSample.STS_B_OperationRequirement, STS_B' />  
    <serviceCredentials>  
      <serviceCertificate findValue='CN=FederationSample.com'  
      x509FindType='FindBySubjectDistinguishedName'  
       storeLocation='LocalMachine'  
       storeName='My' />  
     </serviceCredentials>  
   </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
>  Ponownie `userAuthenticated` oświadczenia jest typ oświadczenia, który jest wymagany przez usługę STS B. Pełna nazwa tego typu oświadczenia jest http://tempuri.org:userAuthenticated (wraz z skojarzona przestrzeń nazw), który jest używany w pliku konfiguracji usługi STS. Wartość tego oświadczenia wskazuje na obecność tego oświadczenia i przyjęto, że można ustawić `true` przez usługę STS A.  
  
 W czasie wykonywania `STS_B_OperationRequirement` klasy wymusza tych zasad, które zostało zaimplementowane jako część usługi STS B.  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 Jeśli dostęp do wyboru jest wyczyszczone, STS B wystawia token SAML z `accessAuthorized` oświadczeń.  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>STS A  
 Na poniższej ilustracji przedstawiono STS A.  
  
 ![Federacyjna](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")  
  
 Podobnie STS B, A usługi STS jest również usługa sieci Web, która wystawia tokeny zabezpieczające i udostępnia jeden punkt końcowy do tego celu. Jednak używa inne powiązanie (`wsHttpBinding`) i wymaga od użytkowników istnieje prawidłowy [!INCLUDE[infocard](../../../../includes/infocard-md.md)] z `emailAddress` oświadczeń. W odpowiedzi, wystawia tokeny SAML z `userAuthenticated` oświadczeń. Jest to deklaratywnie określone w konfiguracji usługi.  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_A" behaviorConfiguration="STS-A_Behavior">  
      <endpoint address=""  
                binding="wsHttpBinding"  
                bindingConfiguration="STS-A_Binding"  
                contract="FederationSample.ISts">  
       <identity>  
       <certificateReference findValue="CN=FederationSample.com"    
                       x509FindType="FindBySubjectDistinguishedName"  
                       storeLocation="LocalMachine"   
                       storeName="My" />  
       </identity>  
    <endpoint>  
  </service>  
</services>  
  
<bindings>  
  <wsHttpBinding>  
  <!-- This is the binding used by STS-A. It requires users to present  
   a CardSpace. -->  
    <binding name='STS-A_Binding'>  
      <security mode='Message'>  
        <message clientCredentialType="CardSpace" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
  
<behaviors>  
  <behavior name='STS-A_Behavior'>  
    <serviceAuthorization operationRequirementType=  
     "FederationSample.STS_A_OperationRequirement, STS_A" />  
      <serviceCredentials>  
  <serviceCertificate findValue="CN=FederationSample.com"  
                     x509FindType='FindBySubjectDistinguishedName'  
                     storeLocation='LocalMachine'  
                     storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
 W czasie wykonywania `STS_A_OperationRequirement` klasy wymusza tych zasad, które zostało zaimplementowane jako część usługi STS A.  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 Jeśli dostęp jest `true`, A usługi STS wystawia token SAML z `userAuthenticated` oświadczeń.  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>Klient w organizacji A  
 Na poniższej ilustracji przedstawiono klienta w organizacji A, wraz z kroki do wykonania w tworzeniu `MyService` do działu obsługi. Inne składniki funkcjonalności uwzględniono również informacje były kompletne.  
  
 ![Federacyjna](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")  
  
## <a name="summary"></a>Podsumowanie  
 Zabezpieczeń zawiera jasny podział odpowiedzialności i ułatwia tworzenie architektur bezpiecznego, skalowalnego usługi. Jako platformę umożliwiającą tworzenie i wdrażanie aplikacji rozproszonych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia macierzystą obsługę wdrażania zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczeń](../../../../docs/framework/wcf/feature-details/security.md)
