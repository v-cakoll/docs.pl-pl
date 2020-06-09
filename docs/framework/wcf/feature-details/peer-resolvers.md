---
title: Mechanizmy rozpoznawania elementów równorzędnych
ms.date: 03/30/2017
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
ms.openlocfilehash: a1f5bcfb721ccbc98856e81198a3f7e0b45abe93
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600779"
---
# <a name="peer-resolvers"></a>Mechanizmy rozpoznawania elementów równorzędnych
Aby można było połączyć się z siatką, węzeł równorzędny wymaga adresów IP innych węzłów. Adresy IP można uzyskać, kontaktując się z usługą rozpoznawania nazw, która pobiera identyfikator sieci i zwraca listę adresów odpowiadającą węzłom zarejestrowanym w określonym IDENTYFIKATORze sieci. Mechanizm rozwiązywania konfliktów zachowuje listę zarejestrowanych adresów tworzonych przez każdy węzeł sieci w rejestrze w usłudze.  
  
 Możesz określić, która usługa konkretna elementu PeerResolver ma być używana przez `Resolver` Właściwość <xref:System.ServiceModel.NetPeerTcpBinding> .  
  
## <a name="supported-peer-resolvers"></a>Obsługiwane rozpoznawania elementów równorzędnych  
 Kanały równorzędne obsługują dwa typy resolverów: Protokół PNRP (Peer Name Resolution Protocol) i niestandardowe usługi rozpoznawania nazw.  
  
 Domyślnie kanał równorzędny używa usługi rozpoznawania równorzędnego PNRP do odnajdywania elementów równorzędnych i sąsiadów w sieci. W przypadku sytuacji/platform, w których usługa PNRP jest niedostępna lub jest nieosiągalna, Windows Communication Foundation (WCF) stanowi alternatywną, opartą na serwerze usługę odnajdywania — <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> . Możesz również jawnie zdefiniować niestandardową usługę programu rozpoznawania nazw, pisząc klasę, która implementuje <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> interfejs.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>Protokół rozpoznawania nazw równorzędnych (PNRP)  
 Protokół PNRP, domyślny program rozpoznawania nazw dla systemu Windows Vista, to dystrybuowana, bezserwerowa usługa resolvera. Protokołu PNRP można także używać w systemie Windows XP z dodatkiem SP2 przez zainstalowanie zaawansowanego pakietu sieciowego. Każdy klient z uruchomioną tą samą wersją protokołu PNRP może zlokalizować siebie nawzajem, pod warunkiem, że spełniają określone warunki (na przykład brak interwencji firmowej zapory). Należy zauważyć, że wersja protokołu PNRP dostarczana z systemem Windows Vista jest nowsza niż wersja zawarta w zaawansowanym pakiecie sieciowym. Zapoznaj się z centrum pobierania Microsoft, aby uzyskać aktualizacje protokołu PNRP dla systemu Windows XP z dodatkiem SP2.  
  
### <a name="custom-resolver-services"></a>Niestandardowe usługi rozpoznawania nazw  
 Gdy usługa PNRP jest niedostępna lub chcesz uzyskać pełną kontrolę nad kształtami siatki, możesz użyć niestandardowej, opartej na serwerze usługi rozpoznawania nazw. Tę usługę można jawnie zdefiniować, pisząc klasę resolvera implementującą <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> interfejs lub używając domyślnej implementacji w miejscu <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> .  
  
 W ramach domyślnej implementacji usługi rejestracje klientów wygasają po upływie określonego czasu, jeśli klient nie odświeża jawnie rejestracji. Klienci korzystający z usługi rozpoznawania nazw muszą znać górną granicę opóźnienia na serwerze klienta, aby pomyślnie odświeżać rejestracje w czasie. Obejmuje to wybranie odpowiedniego czasu odświeżania ( `RefreshInterval` ) w usłudze rozpoznawania nazw. (Aby uzyskać więcej informacji, zobacz [wewnątrz Szczegóły usługi CustomPeerResolverService: rejestracje klienta](inside-the-custompeerresolverservice-client-registrations.md)).  
  
 Moduł zapisujący aplikacji musi również rozważyć zabezpieczenie połączenia między klientami a usługą niestandardowego programu rozpoznawania nazw. Można to zrobić za pomocą ustawień zabezpieczeń na <xref:System.ServiceModel.NetTcpBinding> klientach programu, aby skontaktować się z usługą rozpoznawania nazw. Należy określić poświadczenia (jeśli są używane) na potrzeby `ChannelFactory` tworzenia kanału równorzędnego. Te poświadczenia są przesyłane do `ChannelFactory` użycia w celu utworzenia kanałów dla niestandardowego programu rozpoznawania nazw.  
  
> [!NOTE]
> W przypadku korzystania z lokalnych i nieobsługiwanych sieci z niestandardowym programem rozpoznawania nazw zdecydowanie zaleca się, aby aplikacje używające lub obsłużenia sieci lokalne lub nieplanowane nie obejmowały logiki, która wybiera pojedynczy adres lokalny łącza, który ma być używany podczas nawiązywania połączenia. Zapobiega to ewentualnemu niepomyleniu, który może być spowodowany przez komputery z wieloma adresami lokalnymi linków. W związku z tym kanał równorzędny obsługuje tylko używanie pojedynczego adresu lokalnego łącza w dowolnym momencie. Możesz określić ten adres przy użyciu `ListenIpAddress` właściwości w <xref:System.ServiceModel.NetPeerTcpBinding> .  
  
 Aby zapoznać się z zaimplementowaniem niestandardowego programu rozpoznawania nazw, zobacz temat [niestandardowy element równorzędny peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90)).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Szczegóły usługi CustomPeerResolverService: rejestracje klienta](inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Zobacz też

- [Pojęcia kanałów równorzędnych](peer-channel-concepts.md)
- [Zabezpieczenia kanału równorzędnego](peer-channel-security.md)
- [Tworzenie aplikacji kanału równorzędnego](building-a-peer-channel-application.md)
