---
title: Mechanizmy rozpoznawania elementów równorzędnych
ms.date: 03/30/2017
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
ms.openlocfilehash: 33afffcbf11d757dfd003d1fd2bc9a17a3047a69
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837379"
---
# <a name="peer-resolvers"></a>Mechanizmy rozpoznawania elementów równorzędnych
Aby można było połączyć się z siatką, węzeł równorzędny wymaga adresów IP innych węzłów. Adresy IP można uzyskać, kontaktując się z usługą rozpoznawania nazw, która pobiera identyfikator sieci i zwraca listę adresów odpowiadającą węzłom zarejestrowanym w określonym IDENTYFIKATORze sieci. Mechanizm rozwiązywania konfliktów zachowuje listę zarejestrowanych adresów tworzonych przez każdy węzeł sieci w rejestrze w usłudze.  
  
 Możesz określić, która usługa konkretna elementu PeerResolver ma być używana przez właściwość `Resolver` <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
## <a name="supported-peer-resolvers"></a>Obsługiwane rozpoznawania elementów równorzędnych  
 Kanały równorzędne obsługują dwa typy resolverów: Protokół PNRP (Peer Name Resolution Protocol) i niestandardowe usługi rozpoznawania nazw.  
  
 Domyślnie kanał równorzędny używa usługi rozpoznawania równorzędnego PNRP do odnajdywania elementów równorzędnych i sąsiadów w sieci. W przypadku sytuacji/platform, w których usługa PNRP jest niedostępna lub możliwe, Windows Communication Foundation (WCF) stanowi alternatywną, opartą na serwerze usługę odnajdywania — <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>. Możesz również jawnie zdefiniować niestandardową usługę programu rozpoznawania nazw, pisząc klasę implementującą interfejs <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract>.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>Protokół rozpoznawania nazw równorzędnych (PNRP)  
 Protokół PNRP, domyślny program rozpoznawania nazw dla systemu Windows Vista, to dystrybuowana, bezserwerowa usługa resolvera. Protokołu PNRP można także używać na [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] przez zainstalowanie zaawansowanego pakietu sieciowego. Każdy klient z uruchomioną tą samą wersją protokołu PNRP może zlokalizować siebie nawzajem, pod warunkiem, że spełniają określone warunki (na przykład brak interwencji firmowej zapory). Należy zauważyć, że wersja protokołu PNRP dostarczana z systemem Windows Vista jest nowsza niż wersja zawarta w zaawansowanym pakiecie sieciowym. Zapoznaj się z centrum pobierania Microsoft, aby uzyskać aktualizacje protokołu PNRP dla [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)].  
  
### <a name="custom-resolver-services"></a>Niestandardowe usługi rozpoznawania nazw  
 Gdy usługa PNRP jest niedostępna lub chcesz uzyskać pełną kontrolę nad kształtami siatki, możesz użyć niestandardowej, opartej na serwerze usługi rozpoznawania nazw. Tę usługę można jawnie zdefiniować, pisząc klasę resolvera implementującą interfejs <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> lub używając domyślnej implementacji wbudowanej <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>.  
  
 W ramach domyślnej implementacji usługi rejestracje klientów wygasają po upływie określonego czasu, jeśli klient nie odświeża jawnie rejestracji. Klienci korzystający z usługi rozpoznawania nazw muszą znać górną granicę opóźnienia na serwerze klienta, aby pomyślnie odświeżać rejestracje w czasie. Obejmuje to wybranie czasu odpowiedniej operacji odświeżania (`RefreshInterval`) w usłudze rozpoznawania nazw. (Aby uzyskać więcej informacji, zobacz [wewnątrz Szczegóły usługi CustomPeerResolverService: rejestracje klienta](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)).  
  
 Moduł zapisujący aplikacji musi również rozważyć zabezpieczenie połączenia między klientami a usługą niestandardowego programu rozpoznawania nazw. Można to zrobić za pomocą ustawień zabezpieczeń na <xref:System.ServiceModel.NetTcpBinding> używany przez klientów do kontaktowania się z usługą rozpoznawania nazw. Należy określić poświadczenia (jeśli są używane) na `ChannelFactory` używanym do tworzenia kanału równorzędnego. Te poświadczenia są przesyłane do `ChannelFactory` używany do tworzenia kanałów dla niestandardowego programu rozpoznawania nazw.  
  
> [!NOTE]
> W przypadku korzystania z lokalnych i nieobsługiwanych sieci z niestandardowym programem rozpoznawania nazw zdecydowanie zaleca się, aby aplikacje używające lub obsłużenia sieci lokalne lub nieplanowane nie obejmowały logiki, która wybiera pojedynczy adres lokalny łącza, który ma być używany podczas nawiązywania połączenia. Zapobiega to ewentualnemu niepomyleniu, który może być spowodowany przez komputery z wieloma adresami lokalnymi linków. W związku z tym kanał równorzędny obsługuje tylko używanie pojedynczego adresu lokalnego łącza w dowolnym momencie. Możesz określić ten adres przy użyciu właściwości `ListenIpAddress` w <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
 Aby zapoznać się z zaimplementowaniem niestandardowego programu rozpoznawania nazw, zobacz temat [niestandardowy element równorzędny peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90)).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Szczegóły usługi CustomPeerResolverService: rejestracje klienta](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia kanałów równorzędnych](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
- [Zabezpieczenia kanału równorzędnego](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
