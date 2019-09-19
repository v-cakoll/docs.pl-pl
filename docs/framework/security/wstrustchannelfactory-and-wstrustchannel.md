---
title: WSTrustChannelFactory i WSTrustChannel
ms.date: 03/30/2017
ms.assetid: 96cec467-e963-4132-b18b-7d0b3a2e979f
author: BrucePerlerMS
ms.openlocfilehash: e00f3ae25a50c2fb3f34f4c04d02cde574b3da17
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044915"
---
# <a name="wstrustchannelfactory-and-wstrustchannel"></a>WSTrustChannelFactory i WSTrustChannel
Jeśli znasz już program Windows Communication Foundation (WCF), wiesz, że klient WCF jest już świadomy. Konfigurując klienta WCF przy użyciu <xref:System.ServiceModel.WSFederationHttpBinding> lub podobnego niestandardowego powiązania, można włączyć uwierzytelnianie federacyjne w usłudze.

 Usługa WCF uzyskuje token wystawiony przez usługę tokenu zabezpieczającego (STS) w tle i używa tego tokenu do uwierzytelniania w usłudze. Głównym ograniczeniem tego podejścia jest to, że nie ma wglądu w komunikację klienta z serwerem. Usługa WCF automatycznie generuje token zabezpieczeń żądania (RST) do usługi STS na podstawie parametrów wystawionego tokenu dla powiązania. Oznacza to, że klient nie może różnić się do RST parametrów na żądanie, sprawdzać odpowiedź tokenu zabezpieczeń żądania (RSTR) w celu uzyskania informacji, takich jak wyświetlanie oświadczeń lub buforowanie tokenu do użytku w przyszłości.

 Obecnie klient WCF jest odpowiedni dla podstawowych scenariuszy federacyjnych. Jednak jednym z głównych scenariuszy, które obsługuje usługa Windows Identity Foundation (WIF), wymaga kontroli nad RST na poziomie, który nie jest łatwo dozwolony przez WCF. W związku z tym WIF dodaje funkcje, które zapewniają większą kontrolę komunikacji z usługą STS.

 WIF obsługuje następujące scenariusze federacyjne:

- Używanie klienta WCF bez żadnych zależności WIF do uwierzytelniania w usłudze federacyjnej

- Włączanie WIF na kliencie WCF, aby wstawić element ActAs lub OnBehalfOf do RST do usługi STS

- Korzystanie z programu WIF wyłącznie w celu uzyskania tokenu z usługi STS, a następnie włączenie uwierzytelniania przy użyciu tego tokenu przez klienta programu WCF. Aby uzyskać więcej informacji, zobacz przykład [ClaimsAwareWebService](https://go.microsoft.com/fwlink/?LinkID=248406) .

 Pierwszy scenariusz nie wymaga wyjaśnień: Istniejący klienci WCF będą nadal współdziałać z WIF jednostki uzależnione i usług STS. W tym temacie omówiono pozostałe dwa scenariusze.

## <a name="enhancing-an-existing-wcf-client-with-actas--onbehalfof"></a>Ulepszanie istniejącego klienta WCF przy użyciu usługi ActAs/OnBehalfOf
W typowym scenariuszu delegowania tożsamości klient wywołuje usługę warstwy środkowej, która następnie wywołuje usługę zaplecza. Usługa warstwy środkowej działa jako lub działa w imieniu klienta.

> [!TIP]
> Jaka jest różnica między ActAs i OnBehalfOf?
>
> Z poziomu punktu widzenia protokołu WS-Trust:
>
> 1. ActAs RST wskazuje, że obiekt żądający chce uzyskać token, który zawiera oświadczenia dotyczące dwóch odrębnych jednostek: obiektu żądającego i zewnętrznej jednostki reprezentowanej przez token w elemencie ActAs.
> 2. OnBehalfOf RST wskazuje, że obiekt żądający chce token, który zawiera tylko oświadczenia o jednej jednostce: jednostka zewnętrzna reprezentowana przez token w elemencie OnBehalfOf.
>
> Funkcja ActAs jest zwykle używana w scenariuszach, które wymagają delegowania złożonego, gdzie końcowy odbiorca wystawionego tokenu może sprawdzić cały łańcuch delegowania i zobaczyć nie tylko klienta, ale wszystkich pośredników. Dzięki temu można przeprowadzić kontrolę dostępu, inspekcję i inne powiązane działania w oparciu o cały łańcuch delegowania tożsamości. Funkcja ActAs jest często używana w systemach wielowarstwowych do uwierzytelniania i przekazywania informacji o tożsamościach między warstwami bez konieczności przekazywania tych informacji w warstwie logiki aplikacji/firmy.
>
> Funkcja OnBehalfOf jest używana w scenariuszach, w których ważna jest tylko tożsamość oryginalnego klienta i jest ona efektywnie taka sama jak funkcja personifikacji tożsamości dostępna w systemie Windows. Gdy OnBehalfOf jest używany, końcowy odbiorca wystawionego tokenu może zobaczyć tylko oświadczenia dotyczące oryginalnego klienta, a informacje o pośrednikach nie są zachowywane. Typowym wzorcem, w którym jest używana funkcja OnBehalfOf, jest wzorzec serwera proxy, w którym klient nie może uzyskać dostępu bezpośrednio do usługi STS, ale zamiast tego komunikuje się za pomocą bramy serwera proxy. Brama serwera proxy uwierzytelnia obiekt wywołujący i umieszcza informacje o wywołującym w elemencie OnBehalfOf w komunikacie RST, który następnie wysyła do prawdziwej usługi STS do przetworzenia. Wygenerowany token zawiera tylko oświadczenia powiązane z klientem serwera proxy, co sprawia, że serwer proxy całkowicie niewidoczny dla odbiorcy wystawionego tokenu. Należy zauważyć, że WIF nie \<obsługuje wsse: element SecurityTokenReference > \<ani wsa: EndpointReferences \<> jako element podrzędny wst: OnBehalfOf >. Specyfikacja WS-Trust umożliwia trzy sposoby zidentyfikowania oryginalnego obiektu żądającego (w imieniu kogo działa serwer proxy). Są to:
>
> - Odwołanie do tokenu zabezpieczającego. Odwołanie do tokenu, w wiadomości lub prawdopodobnie pobrane poza pasmem.
> - Odwołanie do punktu końcowego. Służy jako klucz do wyszukiwania danych, ponownie poza pasmem.
> - Token zabezpieczający. Identyfikuje oryginalny obiekt żądający bezpośrednio.
>
> WIF obsługuje tylko tokeny zabezpieczające, zaszyfrowane lub niezaszyfrowane, jako bezpośredni element \<podrzędny wst: OnBehalfOf >.

 Te informacje są przekazywane do wystawcy protokołu WS-Trust przy użyciu elementów tokenów ActAs i OnBehalfOf w RST.

 Środowisko WCF uwidacznia punkt rozszerzalności powiązania, które umożliwia dodawanie dowolnych elementów XML do RST. Jednak ze względu na to, że punkt rozszerzalności jest powiązany z powiązaniem, scenariusze wymagające najwyższego poziomu zawartości dla każdego wywołania muszą ponownie utworzyć klienta dla każdego wywołania, co zmniejsza wydajność. WIF używa metod rozszerzających klasy `ChannelFactory` , aby umożliwić deweloperom dołączenie dowolnego tokenu, który jest uzyskiwany z pasma do RST. Poniższy przykład kodu pokazuje, jak zastosować token reprezentujący klienta (na przykład token X. 509, username lub SAML (SAML)) i dołączyć go do parametru RST, który jest wysyłany do wystawcy.

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelActingAs<IHelloService>(clientSamlToken);
serviceChannel.Hello("Hi!");
```

 WIF zapewnia następujące korzyści:

- Parametr RST można zmodyfikować na kanał; w związku z tym usługi warstwy środkowej nie muszą ponownie tworzyć fabryki kanałów dla każdego klienta, co zwiększa wydajność.

- Jest to możliwe w przypadku istniejących klientów programu WCF, co umożliwia łatwą ścieżkę uaktualnienia dla istniejących usług warstwy środkowej WCF, które chcą włączyć semantykę delegowania tożsamości.

 Jednak nadal nie ma wglądu w komunikację klienta z usługą STS. Sprawdzimy to w trzecim scenariuszu.

## <a name="communicating-directly-with-an-issuer-and-using-the-issued-token-to-authenticate"></a>Bezpośrednie komunikowanie się z wystawcą i użycie wystawionego tokenu do uwierzytelniania
W przypadku niektórych zaawansowanych scenariuszy zwiększenie klienta WCF jest niewystarczające. Deweloperzy korzystający tylko z usług WCF zazwyczaj używają kontraktów komunikatów w wiadomościach i komunikatów i obsługują analizę po stronie klienta ręcznie.

WIF wprowadza <xref:System.ServiceModel.Security.WSTrustChannelFactory> klasy i <xref:System.ServiceModel.Security.WSTrustChannel> , aby umożliwić klientowi komunikowanie się bezpośrednio z wystawcą WS-Trust. Klasy <xref:System.ServiceModel.Security.WSTrustChannelFactory> i<xref:System.ServiceModel.Security.WSTrustChannel> umożliwiają silnie wpisane obiekty RST i RSTR do przepływu między klientem i wystawcą, jak pokazano w poniższym przykładzie kodu.

```csharp
WSTrustChannelFactory trustChannelFactory = new WSTrustChannelFactory(stsBinding, stsAddress);
WSTrustChannel channel = (WSTrustChannel) trustChannelFactory.CreateChannel();
RequestSecurityToken rst = new RequestSecurityToken(RequestTypes.Issue);
rst.AppliesTo = new EndpointAddress(serviceAddress);
RequestSecurityTokenResponse rstr = null;
SecurityToken token = channel.Issue(rst, out rstr);
```

Należy zauważyć, `out` że parametr <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> metody umożliwia dostęp do RSTR na potrzeby inspekcji po stronie klienta.

Do tej pory pokazano, jak uzyskać token. Token, który jest zwracany z <xref:System.ServiceModel.Security.WSTrustChannel> obiektu `GenericXmlSecurityToken` , zawiera wszystkie informacje niezbędne do uwierzytelnienia dla jednostki uzależnionej. Poniższy przykład kodu pokazuje, jak używać tego tokenu.

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelWithIssuedToken<IHelloService>( token );
serviceChannel.Hello("Hi!");
```

<xref:System.ServiceModel.ChannelFactory%601.CreateChannelWithIssuedToken%2A> Metoda`ChannelFactory` rozszerzająca obiektu wskazuje na WIF, że uzyskano token poza pasmem i że powinien zatrzymać normalne wywołanie WCF do wystawcy, a zamiast tego użyć tokenu uzyskanego do uwierzytelnienia dla jednostki uzależnionej. Ma to następujące zalety:

- Zapewnia pełną kontrolę nad procesem wystawiania tokenów.

- Obsługuje scenariusze ActAs/OnBehalfOf przez bezpośrednie ustawianie tych właściwości na wychodzącym RST.

- Umożliwia dynamiczne podejmowanie decyzji dotyczących zaufania po stronie klienta na podstawie zawartości RSTR.

- Umożliwia ona buforowanie i ponowne użycie tokenu zwracanego z <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> metody.

- <xref:System.ServiceModel.Security.WSTrustChannelFactory>i <xref:System.ServiceModel.Security.WSTrustChannel> umożliwiają kontrolę semantyki buforowania, błędów i odporności kanału zgodnie z najlepszymi rozwiązaniami WCF.

## <a name="see-also"></a>Zobacz także

- [Funkcje programu WIF](wif-features.md)
