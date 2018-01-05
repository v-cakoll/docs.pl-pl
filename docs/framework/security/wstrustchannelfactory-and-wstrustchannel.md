---
title: Obiekt WSTrustChannelFactory i WSTrustChannel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96cec467-e963-4132-b18b-7d0b3a2e979f
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 35f4449f7a826ea49be750cd750cb989c8c455fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wstrustchannelfactory-and-wstrustchannel"></a>Obiekt WSTrustChannelFactory i WSTrustChannel
Jeśli znasz już z programu Windows Communication Foundation (WCF), wiesz klienta WCF jest już pamiętać federacyjnego. Konfigurując klienta WCF z <xref:System.ServiceModel.WSFederationHttpBinding> lub podobne niestandardowe powiązanie, można włączyć uwierzytelnianie Sfederowane z usługą.  
  
 Usługi WCF uzyskuje token wystawiony przez usługę tokenu zabezpieczającego (STS) w tle, który używa tego tokenu do uwierzytelnienia w usłudze. Główne ograniczenia tego podejścia jest nie wgląd w komunikacji klienta z serwerem. Usługi WCF automatycznie generuje żądanie tokenu zabezpieczającego (RST) do usługi STS na podstawie parametrów wystawionego tokenu w powiązaniu. To oznacza, że klient nie różnią się parametrami RST na żądanie, sprawdzić odpowiedzi tokenu zabezpieczeń (RSTR), aby uzyskać informacje, takie jak wyświetlanie oświadczeń żądania lub pamięci podręcznej tokenu do użytku w przyszłości.  
  
 Obecnie klienta WCF jest odpowiednia dla Federacji podstawowe scenariusze. Jednak jeden z głównych scenariuszy obsługiwanych przez usługę Windows Identity Foundation (WIF) wymaga kontrolę nad RST na poziomie, który WCF nie pozwolą. W związku z tym WIF dodatkowe funkcje, które zapewniają większą kontrolę nad komunikacji z STS.  
  
 WIF obsługuje następujące scenariusze federacyjnej:  
  
-   Za pomocą klienta WCF bez zależności WIF do uwierzytelniania usługi federacyjnej  
  
-   Włączanie programu WIF na klienta WCF można wstawić elementu ActAs lub OnBehalfOf do RST do usługi STS  
  
-   Przy użyciu programu WIF wyłącznie do uzyskania tokenu z STS, a następnie włączyć klienta programu WCF do uwierzytelniania za pomocą tego tokenu. Aby uzyskać więcej informacji, zobacz [ClaimsAwareWebService](http://go.microsoft.com/fwlink/?LinkID=248406) próbki.  
  
 Pierwszy scenariusz jest oczywiste: WCF istniejący klienci będą nadal działać z WIF jednostek uzależnionych i STSs. W tym temacie omówiono dwa scenariusze pozostałych.  
  
## <a name="enhancing-an-existing-wcf-client-with-actas--onbehalfof"></a>Udoskonalanie istniejącego klienta WCF z ActAs / OnBehalfOf  
 W typowy scenariusz delegowania tożsamości klient wywołuje usługi warstwy środkowej, który wywołuje usługi zaplecza. Usługa warstwy środkowej zachowuje się jak lub działa w imieniu klienta.  
  
> [!TIP]
>  Jaka jest różnica między ActAs i OnBehalfOf?  
>   
>  Z punktu widzenia protokołu WS-Trust:  
>   
>  1.  Element ActAs RST wskazuje, czy obiekt żądający oczekuje, że token zawiera oświadczenia około dwie różne jednostki: obiekt żądający i reprezentowany przez tokenu w elemencie ActAs jednostki zewnętrznej.  
> 2.  Element OnBehalfOf RST wskazuje, czy obiekt żądający oczekuje, że token zawiera oświadczenia dotyczące tylko jednego jednostkę: zewnętrznej jednostki reprezentowanej przez tokenu w elemencie OnBehalfOf.  
>   
>  Funkcja ActAs jest zwykle używanych w scenariuszach wymagających złożonego delegowania, gdzie końcowym odbiorcą wystawionego tokenu sprawdzić delegowania całego łańcucha zobaczyć, a nie tylko klienta, ale wszystkie pośredników. W ten sposób wykonywania kontroli dostępu, inspekcji i inne powiązane działania oparte na tożsamości całego łańcucha delegowania. Funkcja ActAs jest najczęściej używany w systemach wielowarstwowych do uwierzytelniania i przekazywania informacji o tożsamości między warstwami bez konieczności przekazać te informacje w warstwie logiki aplikacji/biznesowej.  
>   
>  Funkcja OnBehalfOf jest używana w scenariuszach, w którym tożsamości klienta oryginalnym jest ważne i efektywnie jest taka sama jak tożsamość personifikacji funkcji dostępnych w systemie Windows. Użycie OnBehalfOf końcowym odbiorcą wystawiony token może zobaczyć tylko oświadczenia dotyczące klienta oryginalnym i informacji o pośredników nie są zachowywane. Jednego z typowych wzorzec, gdy jest używana funkcja OnBehalfOf wzorzec serwera proxy, gdy klient nie może uzyskać dostępu usługi STS bezpośrednio, ale zamiast tego komunikuje się za pośrednictwem bramy serwera proxy. Brama proxy uwierzytelnia wywołującego i umieszcza informacje o elemencie wywołującym element OnBehalfOf wiadomości RST następnie wysyła go do rzeczywistego STS do przetwarzania. Wynikowy token zawiera tylko oświadczenia dotyczące klienta serwera proxy, co serwer proxy całkowicie niewidoczne odbiorcy wystawionego tokenu. Należy pamiętać, że WIF nie obsługuje \<wsse:SecurityTokenReference > lub \<wsa:EndpointReferences > jako element podrzędny \<wst:OnBehalfOf >. Specyfikacja WS-Trust zezwala na trzy sposoby można określić oryginalnego obiektu żądającego (imieniu którego serwer proxy działa). Są to:  
>   
>  -   Odwołania do tokenu zabezpieczeń. Odwołanie do tokenu w wiadomości lub prawdopodobnie pobrane poza pasmem).  
> -   Odwołanie do punktu końcowego. Używany jako klucz, aby wyszukiwać dane ponownie poza pasmem.  
> -   Token zabezpieczający. Identyfikuje bezpośrednio oryginalnego obiektu żądającego.  
>   
>  WIF obsługuje tylko tokenów, szyfrowane albo niezaszyfrowanej jako elementu podrzędnego bezpośredniego \<wst:OnBehalfOf >.  
  
 Ta informacja jest przekazywana do przy użyciu elementów tokenów ActAs i OnBehalfOf w RST wystawcy WS-Trust.  
  
 Usługa WCF umożliwia rozszerzalności punkcie powiązania, które umożliwia dowolnego elementów XML w celu dodania do RST. Jednak ponieważ punkcie rozszerzenia jest związany z powiązania, scenariusze, które wymagają zawartość RST różnicującej na wywołanie musi odtworzyć klienta dla każdego wywołania, co obniża wydajność. WIF używa metody rozszerzenia na `ChannelFactory` klasa umożliwia deweloperom dołączyć dowolny uzyskany poza pasmem do RST token. Poniższy przykład kodu pokazuje, jak można zająć tokenu, który reprezentuje klienta (na przykład X.509, nazwa użytkownika lub token potwierdzenia języka SAML (Security Markup)) i dołączenie go do RST, wysyłany do wystawcy.  
  
```  
IHelloService serviceChannel = channelFactory.CreateChannelActingAs<IHelloService>( clientSamlToken );  
serviceChannel.Hello("Hi!");  
```  
  
 WIF zapewnia następujące korzyści:  
  
-   RST można zmodyfikować na kanał; w związku z tym warstwy środkowej usług ma ponownie utworzyć fabryki kanałów dla każdego klienta, co zwiększa wydajność.  
  
-   To działanie z istniejących klientów usługi WCF, która umożliwia łatwe ścieżki uaktualniania istniejącej usługi WCF warstwy środkowej, które chcesz włączyć semantyki delegowania tożsamości.  
  
 Ponieważ nie ma jeszcze nie wgląd w komunikacji klienta z usługi STS. Zajmiemy się to w trzeci scenariusz.  
  
## <a name="communicating-directly-with-an-issuer-and-using-the-issued-token-to-authenticate"></a>Komunikują się bezpośrednio z wystawcę i przy użyciu wystawionego tokenu uwierzytelniania  
 Dla niektórych zaawansowanych scenariuszy udoskonalanie klienta WCF jest niewystarczająca. Deweloperzy, którzy używają tylko WCF zwykle użyć wiadomości w / komunikatów wychodzących umów oraz obsługę po stronie klienta podczas analizowania odpowiedzi wystawcy ręcznie.  
  
 Wprowadza WIF <xref:System.ServiceModel.Security.WSTrustChannelFactory> i <xref:System.ServiceModel.Security.WSTrustChannel> klasy, aby umożliwić klientowi bezpośredniego komunikowania się z wystawców WS-Trust. <xref:System.ServiceModel.Security.WSTrustChannelFactory> i <xref:System.ServiceModel.Security.WSTrustChannel> klasy włączyć silnie typizowanych obiektów RST i odpowiedź RSTR przepływ między klientem a wystawcy, jak pokazano w poniższym przykładzie kodu.  
  
```  
WSTrustChannelFactory trustChannelFactory = new WSTrustChannelFactory( stsBinding, stsAddress );  
WSTrustChannel channel = (WSTrustChannel) trustChannelFactory.CreateChannel();  
RequestSecurityToken rst = new RequestSecurityToken(RequestTypes.Issue);  
rst.AppliesTo = new EndpointAddress(serviceAddress);  
RequestSecurityTokenResponse rstr = null;  
SecurityToken token = channel.Issue(rst, out rstr);  
```  
  
 Należy pamiętać, że `out` parametru <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> metoda zapewnia dostęp do komunikacie RSTR inspekcji po stronie klienta.  
  
 Firma Microsoft do tej pory tylko przedstawiono sposób uzyskiwania tokenu. Token, który jest zwracany z <xref:System.ServiceModel.Security.WSTrustChannel> obiekt jest `GenericXmlSecurityToken` zawiera wszystkie informacje, które są niezbędne do uwierzytelniania do jednostki uzależnionej. Poniższy przykładowy kod przedstawia sposób użycia tego tokenu.  
  
```  
IHelloService serviceChannel = channelFactory.CreateChannelWithIssuedToken<IHelloService>( token ); serviceChannel.Hello("Hi!");  
```  
  
 <xref:System.ServiceModel.ChannelFactory%601.CreateChannelWithIssuedToken%2A> — Metoda rozszerzenia na `ChannelFactory` obiektu wskazuje WIF uzyskaniu tokenu poza pasmem i należy ją zatrzymać normalne wywołanie WCF wystawca i zamiast tego użyć tokenu, który został pobrany do uwierzytelniania do jednostki uzależnionej. Ma to następujące korzyści:  
  
-   Udostępnia pełną kontrolę nad procesem wydawania tokenów.  
  
-   Obsługuje ona ActAs / scenariusze OnBehalfOf bezpośrednio ustawienie tych właściwości na RST wychodzących.  
  
-   Umożliwia podjęcie decyzji na podstawie zawartości o komunikacie RSTR dynamiczne zaufania po stronie klienta.  
  
-   Dzięki temu można buforować i ponowne użycie token, który jest zwracany z <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> metody.  
  
-   <xref:System.ServiceModel.Security.WSTrustChannelFactory>i <xref:System.ServiceModel.Security.WSTrustChannel> umożliwiają kontrolę nad kanału semantyki pamięci podręcznej, odporności i odzyskiwania zgodnie z najlepszymi rozwiązaniami WCF.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje programu WIF](../../../docs/framework/security/wif-features.md)
