---
title: WSTrustChannelFactory i WSTrustChannel
ms.date: 03/30/2017
ms.assetid: 96cec467-e963-4132-b18b-7d0b3a2e979f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 78bf58b6d1b9059d2513b9f81eb382487bb4004b
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2018
ms.locfileid: "42998469"
---
# <a name="wstrustchannelfactory-and-wstrustchannel"></a>WSTrustChannelFactory i WSTrustChannel
Jeśli znasz już za pomocą programu Windows Communication Foundation (WCF), wiesz, klienta programu WCF jest już pamiętać federacji. Konfigurując klienta programu WCF za pomocą <xref:System.ServiceModel.WSFederationHttpBinding> lub podobne niestandardowe powiązanie, aby umożliwić uwierzytelnianie Sfederowane z usługą.  
  
 Usługi WCF uzyskuje token wystawiony przez usługę tokenu zabezpieczającego (STS) w tle, która używa tego tokenu do uwierzytelnienia w usłudze. Głównym ograniczeniem związanym tego podejścia jest nie widoczność komunikacji klienta z serwerem. Usługi WCF automatycznie generuje żądanie tokenu zabezpieczającego (RST) do usługi STS, na podstawie parametrów tokenu wystawionego w powiązaniu. Oznacza to, czy klient nie różnią się parametrami RST na żądanie, sprawdzanie zabezpieczeń tokenu odpowiedzi na żądanie (RSTR), aby uzyskać informacje, takie jak wyświetlanie oświadczeń lub token do użytku w przyszłości w pamięci podręcznej.  
  
 Obecnie klienta WCF jest odpowiednie w scenariuszach Federacji podstawowe. Jednak jedną z głównych scenariuszy, które obsługuje Windows Identity Foundation (WIF) wymaga kontrolę nad RST na poziomie, który nie zapewnia prosty sposób WCF. W związku z tym program WIF dodaje funkcje, które zapewniają większą kontrolę nad komunikacji z usługą STS.  
  
 Program WIF obsługuje następujące scenariusze federacyjnej:  
  
-   Za pomocą klienta WCF, bez żadnych zależności programu WIF do uwierzytelniania usługi federacyjnej  
  
-   Włączania środowiska WIF na klienta programu WCF do Wstawianie elementu ActAs lub OnBehalfOf RST do usługi STS  
  
-   Przy użyciu programu WIF samodzielnie uzyskać token z usługi STS, a następnie Włącz klienta programu WCF do uwierzytelniania za pomocą tego tokenu. Aby uzyskać więcej informacji, zobacz [ClaimsAwareWebService](http://go.microsoft.com/fwlink/?LinkID=248406) próbki.  
  
 Pierwszy scenariusz jest oczywista: WCF istniejący klienci będą nadal działać z jednostki uzależnionej stron programu WIF i usługi STS. W tym temacie omówiono dwa pozostałe scenariusze.  
  
## <a name="enhancing-an-existing-wcf-client-with-actas--onbehalfof"></a>Udoskonalanie istniejącego klienta programu WCF za pomocą ActAs / OnBehalfOf  
 W typowy scenariusz delegowania tożsamości klient wywołuje usługi warstwy środkowej, która następnie wywołuje usługi zaplecza. Usługi warstwy środkowej działa jako lub działa w imieniu klienta.  
  
> [!TIP]
>  Jaka jest różnica między ActAs i OnBehalfOf?  
>   
>  Z punktu widzenia protokołu WS-Trust:  
>   
> 1. Element ActAs RST wskazuje, że obiekt żądający chce, token, który zawiera oświadczeń o dwóch odrębnych jednostek: obiekt żądający i obiekt zewnętrzny, reprezentowane przez token w elemencie ActAs.  
> 2. Element OnBehalfOf RST wskazuje, że obiekt żądający chce tokenu, który zawiera oświadczenia tylko o jedną jednostkę: zewnętrznej jednostki reprezentowanej przez token w elemencie OnBehalfOf.  
>   
>  W scenariuszach, które wymagają złożonej delegowania, gdzie końcowym odbiorcą wystawiony token sprawdzić delegowania całego łańcucha zobaczyć i nie tylko klient, ale wszystkie pośredników zwykle jest używana funkcja ActAs. Dzięki temu wykonanie kontroli dostępu, inspekcji i inne powiązane działania oparte na tożsamości całego łańcucha delegowania. Funkcja ActAs jest często używane w systemach wielopoziomowe do uwierzytelniania i przekazywania informacji o tożsamościach między warstwami, bez konieczności przekazać te informacje na poziomie warstwy logiki biznesowej/aplikacji.  
>   
>  Funkcja OnBehalfOf jest używana w scenariuszach, gdzie tożsamość tylko oryginalny klient jest ważne i skutecznie jest taka sama jak tożsamość personifikacji funkcji dostępnych w programie Windows. Stosowania OnBehalfOf końcowym odbiorcą wystawiony token może zobaczyć tylko oświadczenia dotyczące oryginalnego klienta i informacje o pośredników nie są zachowywane. Jedna jest typowy wzorzec, w którym jest używana funkcja OnBehalfOf wzorzec serwera proxy, gdy klient nie może uzyskać dostępu usługi STS bezpośrednio, ale zamiast tego komunikuje się za pośrednictwem bramy serwera proxy. Brama proxy uwierzytelnia wywołującego i umieszcza informacje o obiekcie wywołującym z elementu OnBehalfOf ERWSZY komunikat, następnie wysyła go do rzeczywistego usługi STS do przetworzenia. Wynikowy token zawiera tylko oświadczenia dotyczące klienta serwera proxy, dzięki czemu serwer proxy całkowicie przezroczysty do odbiorcy wystawiony token. Należy zauważyć, że nie obsługuje programu WIF \<wsse:SecurityTokenReference > lub \<wsa:EndpointReferences > jako element podrzędny elementu \<wst:OnBehalfOf >. Trzy sposoby zidentyfikować oryginalnego obiektu żądającego (w imieniu którego jest działający serwer proxy) umożliwia specyfikację protokołu WS-Trust. Są to:  
>   
>  -   Odwołania do tokenu zabezpieczającego. Odwołanie do tokenu w wiadomości lub prawdopodobnie pobrane poza pasmem).  
> -   Odwołania do punktu końcowego. Używane jako klucz wyszukiwać dane, ponownie poza pasmem.  
> -   Token zabezpieczający. Identyfikuje bezpośrednio oryginalnego obiektu żądającego.  
>   
>  Program WIF obsługuje tylko tokeny zabezpieczające, szyfrowane lub niezaszyfrowanego jako element podrzędny \<wst:OnBehalfOf >.  
  
 Te informacje jest przekazywany do wystawcy WS-Trust, przy użyciu elementów tokenu ActAs i OnBehalfOf w RST.  
  
 Usługa WCF umożliwia rozszerzalność punkcie powiązania, które umożliwia dowolne elementy XML, które mają zostać dodane do RST. Jednakże ponieważ punkt rozszerzeń jest powiązane powiązanie, scenariusze, które wymagają zawartość RST, aby być różne dla każdego wywołania należy ponownie utworzyć klienta dla każdego wywołania, co obniża wydajność. Program WIF wykorzystuje metody rozszerzeń na `ChannelFactory` klasy, aby umożliwić deweloperom Dołącz dowolny token uzyskany poza pasmem do RST. W poniższym przykładzie kodu pokazano, jak można zająć tokenu, który reprezentuje klienta (na przykład X.509, nazwa użytkownika lub token zabezpieczeń Assertion Markup Language (SAML)) i dołączyć je do RST, wysyłany z wystawcą.  
  
```  
IHelloService serviceChannel = channelFactory.CreateChannelActingAs<IHelloService>( clientSamlToken );  
serviceChannel.Hello("Hi!");  
```  
  
 Program WIF oferuje następujące korzyści:  
  
-   RST mogą być modyfikowane na kanał; usługi warstwy środkowej nie więc ponownie utworzyć fabryki kanałów dla każdego klienta, co zwiększa wydajność.  
  
-   To współpracuje z istniejącymi klientami programu WCF, co sprawia, że łatwo ścieżki uaktualniania możliwe dla istniejących usług warstwy środkowej WCF, które chcesz włączyć semantyki delegowania tożsamości.  
  
 Istnieje jednak nadal nie widoczność komunikacji klienta z usługi STS. Zajmiemy się to w trzeci scenariusz.  
  
## <a name="communicating-directly-with-an-issuer-and-using-the-issued-token-to-authenticate"></a>Komunikują się bezpośrednio z wystawcę i uwierzytelniania z użyciem wystawiony Token  
 Dla niektórych zaawansowanych scenariuszach udoskonalanie klienta WCF jest niewystarczająca. Deweloperzy, którzy używają tylko WCF zwykle używać wiadomości w / komunikat o poziomie umów oraz obsługę po stronie klienta podczas analizowania odpowiedzi wystawcy ręcznie.  
  
 Program WIF przedstawia <xref:System.ServiceModel.Security.WSTrustChannelFactory> i <xref:System.ServiceModel.Security.WSTrustChannel> klasy, aby umożliwić klientowi komunikowanie się bezpośrednio z wystawcą WS-Trust. <xref:System.ServiceModel.Security.WSTrustChannelFactory> i <xref:System.ServiceModel.Security.WSTrustChannel> klasy Włącz Silnie typizowanych obiektów RST i RSTR przepływ między klientem a wystawcy, jak pokazano w poniższym przykładzie kodu.  
  
```  
WSTrustChannelFactory trustChannelFactory = new WSTrustChannelFactory( stsBinding, stsAddress );  
WSTrustChannel channel = (WSTrustChannel) trustChannelFactory.CreateChannel();  
RequestSecurityToken rst = new RequestSecurityToken(RequestTypes.Issue);  
rst.AppliesTo = new EndpointAddress(serviceAddress);  
RequestSecurityTokenResponse rstr = null;  
SecurityToken token = channel.Issue(rst, out rstr);  
```  
  
 Należy pamiętać, że `out` parametru <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> metoda umożliwia dostęp do RSTR inspekcji po stronie klienta.  
  
 Jak dotąd przedstawiono tylko sposób uzyskiwania tokenu. Token, który jest zwracany z <xref:System.ServiceModel.Security.WSTrustChannel> obiekt jest `GenericXmlSecurityToken` zawierający wszystkie informacje, które są niezbędne do uwierzytelniania do jednostki uzależnionej. W poniższym przykładzie kodu pokazano, jak na używanie tego tokenu.  
  
```  
IHelloService serviceChannel = channelFactory.CreateChannelWithIssuedToken<IHelloService>( token ); serviceChannel.Hello("Hi!");  
```  
  
 <xref:System.ServiceModel.ChannelFactory%601.CreateChannelWithIssuedToken%2A> Metody rozszerzenia `ChannelFactory` obiektu wskazuje do wersji WIF uzyskał token poza pasmem i należy ją zatrzymać normalne wywołanie WCF wystawcy i zamiast tego użyć tokenu, który został pobrany do uwierzytelniania do jednostki uzależnionej. Ma to następujące korzyści:  
  
-   Daje pełną kontrolę nad procesem wystawiania tokenu.  
  
-   Obsługuje ona ActAs / scenariusze OnBehalfOf przez bezpośrednie ustawienie tych właściwości na RST wychodzących.  
  
-   Umożliwia podjęcie decyzji na podstawie zawartości RSTR dynamiczne zaufania po stronie klienta.  
  
-   Dzięki temu można w pamięci podręcznej i ponowne użycie tokenu, który jest zwracany z <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> metody.  
  
-   <xref:System.ServiceModel.Security.WSTrustChannelFactory> i <xref:System.ServiceModel.Security.WSTrustChannel> umożliwiają kontrolę nad kanału pamięci podręcznej, odporności i odzyskiwania semantyki zgodnie z najlepszymi rozwiązaniami WCF.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje programu WIF](../../../docs/framework/security/wif-features.md)
