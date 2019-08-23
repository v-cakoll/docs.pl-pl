---
title: Mechanizmy rozpoznawania elementów równorzędnych
ms.date: 03/30/2017
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
ms.openlocfilehash: 0547bb37b03235c61f43cec365551438f7931ad1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909913"
---
# <a name="peer-resolvers"></a>Mechanizmy rozpoznawania elementów równorzędnych
Aby można było połączyć się z siatką, węzeł równorzędny wymaga adresów IP innych węzłów. Adresy IP można uzyskać, kontaktując się z usługą rozpoznawania nazw, która pobiera identyfikator sieci i zwraca listę adresów odpowiadającą węzłom zarejestrowanym w określonym IDENTYFIKATORze sieci. Mechanizm rozwiązywania konfliktów zachowuje listę zarejestrowanych adresów tworzonych przez każdy węzeł sieci w rejestrze w usłudze.  
  
 Możesz określić, która usługa konkretna elementu PeerResolver ma być używana przez `Resolver` właściwość. <xref:System.ServiceModel.NetPeerTcpBinding>  
  
## <a name="supported-peer-resolvers"></a>Obsługiwane rozpoznawania elementów równorzędnych  
 Kanał równorzędny obsługuje dwa typy resolverów: Protokół rozpoznawania nazw równorzędnych (PNRP) i niestandardowe usługi programu rozpoznawania nazw.  
  
 Domyślnie kanał równorzędny używa usługi rozpoznawania równorzędnego PNRP do odnajdywania elementów równorzędnych i sąsiadów w sieci. W przypadku sytuacji/platform, w których usługa PNRP jest niedostępna lub jest nieosiągalna, Windows Communication Foundation (WCF) stanowi alternatywną <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>, opartą na serwerze usługę odnajdywania —. Możesz również jawnie zdefiniować niestandardową usługę programu rozpoznawania nazw, pisząc klasę, <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> która implementuje interfejs.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>Protokół rozpoznawania nazw równorzędnych (PNRP)  
 Protokół PNRP, domyślny program rozpoznawania [!INCLUDE[wv](../../../../includes/wv-md.md)]nazw dla programu, to dystrybuowana, bezserwerowa usługa rozpoznawania nazw. Protokołu PNRP można używać również w [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] przypadku instalowania pakietu zaawansowanej sieci. Każdy klient z uruchomioną tą samą wersją protokołu PNRP może zlokalizować siebie nawzajem, pod warunkiem, że spełniają określone warunki (na przykład brak interwencji firmowej zapory). Należy zauważyć, że wersja protokołu PNRP dostarczana [!INCLUDE[wv](../../../../includes/wv-md.md)] z programem jest nowsza niż wersja zawarta w zaawansowanym pakiecie sieciowym. Zapoznaj się z centrum pobierania Microsoft, aby uzyskać [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]aktualizacje protokołu PNRP dla programu.  
  
### <a name="custom-resolver-services"></a>Niestandardowe usługi rozpoznawania nazw  
 Gdy usługa PNRP jest niedostępna lub chcesz uzyskać pełną kontrolę nad kształtami siatki, możesz użyć niestandardowej, opartej na serwerze usługi rozpoznawania nazw. Tę usługę można jawnie zdefiniować, pisząc klasę resolvera implementującą <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> interfejs lub używając domyślnej <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>implementacji w miejscu.  
  
 W ramach domyślnej implementacji usługi rejestracje klientów wygasają po upływie określonego czasu, jeśli klient nie odświeża jawnie rejestracji. Klienci korzystający z usługi rozpoznawania nazw muszą znać górną granicę opóźnienia na serwerze klienta, aby pomyślnie odświeżać rejestracje w czasie. Obejmuje to wybranie odpowiedniego czasu odświeżania (`RefreshInterval`) w usłudze rozpoznawania nazw. (Aby uzyskać więcej informacji, [Zobacz wewnątrz Szczegóły usługi CustomPeerResolverService: Rejestracje klienta)](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md).  
  
 Moduł zapisujący aplikacji musi również rozważyć zabezpieczenie połączenia między klientami a usługą niestandardowego programu rozpoznawania nazw. Można to zrobić za pomocą ustawień zabezpieczeń na <xref:System.ServiceModel.NetTcpBinding> klientach programu, aby skontaktować się z usługą rozpoznawania nazw. Należy określić poświadczenia (jeśli są używane) na `ChannelFactory` potrzeby tworzenia kanału równorzędnego. Te poświadczenia są przesyłane do `ChannelFactory` użycia w celu utworzenia kanałów dla niestandardowego programu rozpoznawania nazw.  
  
> [!NOTE]
> W przypadku korzystania z lokalnych i nieobsługiwanych sieci z niestandardowym programem rozpoznawania nazw zdecydowanie zaleca się, aby aplikacje używające lub obsłużenia sieci lokalne lub nieplanowane nie obejmowały logiki, która wybiera pojedynczy adres lokalny łącza, który ma być używany podczas nawiązywania połączenia. Zapobiega to ewentualnemu niepomyleniu, który może być spowodowany przez komputery z wieloma adresami lokalnymi linków. W związku z tym kanał równorzędny obsługuje tylko używanie pojedynczego adresu lokalnego łącza w dowolnym momencie. Możesz określić ten adres przy użyciu `ListenIpAddress` właściwości <xref:System.ServiceModel.NetPeerTcpBinding>w.  
  
 Aby zapoznać się z zaimplementowaniem niestandardowego programu rozpoznawania nazw, zobacz temat [niestandardowy element równorzędny peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90)).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wewnątrz Szczegóły usługi CustomPeerResolverService: Rejestracje klientów](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia kanałów równorzędnych](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
- [Zabezpieczenia kanału równorzędnego](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
