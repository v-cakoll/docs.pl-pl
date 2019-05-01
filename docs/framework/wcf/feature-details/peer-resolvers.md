---
title: Mechanizmy rozpoznawania elementów równorzędnych
ms.date: 03/30/2017
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
ms.openlocfilehash: de19e08c1c001076c56e26020584d17079f1a45f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038704"
---
# <a name="peer-resolvers"></a>Mechanizmy rozpoznawania elementów równorzędnych
Aby można było nawiązać siatki, węzeł równorzędny wymaga adresów IP innych węzłów. Adresy IP są pobierane, kontaktując się z usługi rozpoznawania nazw, która przyjmuje identyfikator siatki i zwraca listę adresów odpowiadającego do węzłów zarejestrowanych za pomocą tego identyfikatora określonej siatki. Mechanizm rozpoznawania przechowuje listę zarejestrowanych adresów, które tworzy się przez każdy węzeł w siatce, rejestracji w usłudze.  
  
 Można określić za pośrednictwem której usługi PeerResolver `Resolver` właściwość <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
## <a name="supported-peer-resolvers"></a>Mechanizmy rozpoznawania elementów równorzędnych obsługiwane  
 Kanał elementu równorzędnego obsługuje dwa rodzaje mechanizmów rozpoznawania: Protokół Instrumentacji zarządzania Windows (PNRP, Peer Name Resolution Protocol), niestandardowym programem rozpoznawania nazw usługi i.  
  
 Domyślnie kanał elementu równorzędnego korzysta z usługi rozpoznawania nazw równorzędnych PNRP odnajdywania elementów równorzędnych i sąsiadów w siatce. W przypadku sytuacji/platform gdzie PNRP jest niedostępna lub jest to możliwe Windows Communication Foundation (WCF) udostępnia usługę odnajdywania alternatywne, oparte na serwerze - <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>. Można także jawnie w celu zdefiniowania niestandardowego mechanizmu usługi przez napisanie klasę, która implementuje <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> interfejsu.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>Protokołu rozpoznawania nazw równorzędnych (PNRP)  
 Protokół PNRP, domyślny mechanizm dla [!INCLUDE[wv](../../../../includes/wv-md.md)], to rozproszona, bez użycia serwera usługi rozpoznawania nazw. Protokół PNRP pozwala także na [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] , instalując pakiet zaawansowane sieci. Wszyscy klienci dwóch uruchomiona ta sama wersja PNRP można zlokalizować sobie nawzajem przy użyciu tego protokołu, pod warunkiem spełniają określone warunki (takie jak brak pośrednicząca zapora firmy). Należy pamiętać, że wersja PNRP współpracującym z [!INCLUDE[wv](../../../../includes/wv-md.md)] jest nowsza niż wersja zawarte w pakiecie zaawansowane sieci. Sprawdź Microsoft Download Center dla aktualizacji PNRP dla [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)].  
  
### <a name="custom-resolver-services"></a>Custom Resolver Services  
 Gdy usługa PNRP jest niedostępna lub mają pełną kontrolę nad kształtowaniem siatki, można użyć usługa niestandardowych, na serwerze programu rozpoznawania nazw. Można jawnie zdefiniować tę usługę, pisząc klasy programu rozpoznawania nazw Implementowanie <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> interfejs lub przy użyciu implementacji domyślnej skrzynkach odbiorczych, <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>.  
  
 W obszarze Domyślna implementacja usługi rejestracje klienta tracą ważność po upływie określonego czasu, jeśli klient nie powoduje odświeżenia jawnie rejestracji. Klienci korzystający z usługi rozpoznawania nazw muszą znać górną granicę opóźnieniem klient serwer w celu pomyślnie Odśwież rejestracje w czasie. Obejmuje to, wybierając odpowiednie odświeżania limitu czasu (`RefreshInterval`) na usługi rozpoznawania nazw. (Aby uzyskać więcej informacji, zobacz [wewnątrz CustomPeerResolverService: Rejestracje klienta](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md).)  
  
 Moduł zapisujący aplikacji należy również skonfigurować zabezpieczenia połączeń między klientami a usługą niestandardowym programem rozpoznawania nazw. Może to zrobić przy użyciu ustawień zabezpieczeń na <xref:System.ServiceModel.NetTcpBinding> , aby klienci korzystali do kontaktowania się z usługi rozpoznawania nazw. Należy określić poświadczenia (jeśli jest używany) na `ChannelFactory` użyty do utworzenia kanału równorzędnego. Te poświadczenia są przekazywane do `ChannelFactory` używany do tworzenia kanałów na niestandardowym programem rozpoznawania nazw.  
  
> [!NOTE]
>  Korzystając z sieci lokalnej i natychmiast z niestandardowym programem rozpoznawania nazw, zdecydowanie zalecane jest, za pomocą lub obsługa sieci połączenia lokalnego lub nieplanowane zastosowań logikę, która wybiera pojedynczy adres połączenia lokalnego do użycia podczas łączenia. Zapobiega to niezgodności potencjalnie spowodowane przez komputery z wieloma adresami połączenia lokalnego. Zgodnie z tym kanał elementu równorzędnego obsługuje tylko, używając pojedynczy adres połączenia lokalnego w dowolnym momencie. Użytkownik może określić tego adresu za pomocą `ListenIpAddress` właściwość <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
 Implementacji niestandardowego mechanizmu demonstracyjne, zobacz [elementu równorzędnego kanału niestandardowego elementu równorzędnego programu rozpoznawania nazw](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90)).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Usługi custompeerresolverservice: Rejestracje klienta](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia kanałów równorzędnych](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
- [Zabezpieczenia kanału równorzędnego](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
