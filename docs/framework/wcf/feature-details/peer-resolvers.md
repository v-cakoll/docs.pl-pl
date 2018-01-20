---
title: "Mechanizmy rozpoznawania elementów równorzędnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d86d12a1-7358-450f-9727-b6afb95adb9c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79c26ca9e167455dfbd664ea96e574c130cdc3d2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="peer-resolvers"></a>Mechanizmy rozpoznawania elementów równorzędnych
Aby można było nawiązać siatkę, węzła równorzędnego wymaga adresów IP innych węzłów. Adresy IP są uzyskiwane poprzez bezpośredni kontakt z usługi rozpoznawania nazw, która przyjmuje identyfikator sieci i zwraca listę adresów odpowiadającego do węzłów w zarejestrowany ten identyfikator określonego siatki. Mechanizm rozpoznawania przechowuje listę zarejestrowanych adresów, które tworzy się przez każdy węzeł w siatce przeprowadzić rejestrację w usłudze.  
  
 Można określić do użycia przez usługę PeerResolver `Resolver` właściwość <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
## <a name="supported-peer-resolvers"></a>Mechanizmy rozpoznawania elementów równorzędnych obsługiwane  
 Kanał elementu równorzędnego obsługuje dwa rodzaje rozwiązujący: rozpoznawania protokołu PNRP (Peer Name) i usługi niestandardowego programu rozpoznawania nazw.  
  
 Domyślnie kanału równorzędnego korzysta z usługi rozpoznawania nazw równorzędnych PNRP odnajdywania elementów równorzędnych i sąsiadów w siatce. Dla sytuacji/platform, których usługa PNRP nie jest dostępne lub możliwe [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] udostępnia usługę alternatywną, na serwerze odnajdywania - <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>. Można również jawnie zdefiniować usługi niestandardowego programu rozpoznawania nazw, pisząc klasy, która implementuje <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> interfejsu.  
  
### <a name="peer-name-resolution-protocol-pnrp"></a>Protokołu rozpoznawania nazw równorzędnych (PNRP)  
 Usługa PNRP, domyślny program rozpoznawania nazw dla [!INCLUDE[wv](../../../../includes/wv-md.md)], jest rozproszonych, niekorzystającą usługi rozpoznawania nazw. Usługa PNRP może być również używany na [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] instalując pakiet zaawansowane sieci. Wszyscy klienci dwóch uruchomiona ta sama wersja PNRP można znaleźć wzajemny dostęp przy użyciu tego protokołu, pod warunkiem spełniają pewne warunki (np. Brak pośrednicząca Zapora firmowej). Należy pamiętać, że wersja usługi PNRP, który dostarczany z [!INCLUDE[wv](../../../../includes/wv-md.md)] jest nowsza niż wersja zawarte w pakiecie zaawansowane sieci. Sprawdź Microsoft Download Center aktualizacje PNRP dla [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)].  
  
### <a name="custom-resolver-services"></a>Niestandardowego programu rozpoznawania nazw usługi  
 Gdy usługa PNRP jest niedostępna lub mają pełną kontrolę nad kształtowania siatki, można użyć usługi rozpoznawania niestandardowych, na serwerze. Ta usługa może jawnie definiować pisząc klasy programu rozpoznawania nazw implementacja <xref:System.ServiceModel.PeerResolvers.IPeerResolverContract> interfejsu lub przy użyciu implementacji domyślnej w polu <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>.  
  
 W obszarze Domyślna implementacja usługi rejestracji klienta wygaśnie po określonym czasie, jeśli klient nie powoduje odświeżenia jawnie rejestracji. Aby można było pomyślnie odświeżyć w czasie rejestracji musi należy pamiętać o górna granica opóźnienia klient serwer klientów korzystających z usługi rozpoznawania nazw. Obejmuje to wybranie odpowiednich odświeżania limitu czasu (`RefreshInterval`) w usłudze rozpoznawania nazw. (Aby uzyskać więcej informacji, zobacz [wewnątrz CustomPeerResolverService: rejestracje klienta](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md).)  
  
 Moduł zapisujący aplikacji należy również wziąć pod uwagę Zabezpieczanie połączeń między klientami a service niestandardowego programu rozpoznawania nazw. Może to zrobić przy użyciu ustawień zabezpieczeń na <xref:System.ServiceModel.NetTcpBinding> że klienci używają do kontaktowania się z usługi rozpoznawania nazw. Należy określić poświadczenia (jeśli jest używany) na `ChannelFactory` pozwala utworzyć kanał elementu równorzędnego. Te poświadczenia są przekazywane do `ChannelFactory` używany do tworzenia kanałów niestandardowego programu rozpoznawania nazw.  
  
> [!NOTE]
>  Podczas korzystania z sieci lokalnej i natychmiast z niestandardowego programu rozpoznawania nazw, zdecydowanie zaleca się czy aplikacji przy użyciu lub podtrzymywania połączenia lokalnego lub nieplanowane sieci obejmują logikę, która wybiera jeden adres połączenia lokalnego do użycia podczas połączenia. Zapobiega to niezgodności potencjalnie spowodowane przez komputery z wielu adresów połączenia lokalnego. Zgodnie z tym kanału równorzędnego obsługuje tylko, używając pojedynczy adres połączenia lokalnego w dowolnym momencie. Można określić tego adresu z `ListenIpAddress` właściwość <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
 Aby demonstracyjne sposób implementowania niestandardowego programu rozpoznawania nazw, zobacz [program rozpoznawania elementów równorzędnych niestandardowego elementu równorzędnego kanału](http://msdn.microsoft.com/library/5b75a2bb-7ff1-4a14-abe7-3debf0537d23).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Szczegóły usługi CustomPeerResolverService: rejestracje klienta](../../../../docs/framework/wcf/feature-details/inside-the-custompeerresolverservice-client-registrations.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia kanałów równorzędnych](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)  
 [Zabezpieczenia kanału równorzędnego](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
