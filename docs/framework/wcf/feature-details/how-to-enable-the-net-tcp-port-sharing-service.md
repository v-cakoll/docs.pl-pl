---
title: 'Instrukcje: Włączanie usługi współużytkowania portów Net.TCP'
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 490c0d8c4c95eeb2b1cd9b43134720c9e44467ac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619600"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>Instrukcje: Włączanie usługi współużytkowania portów Net.TCP
Windows Communication Foundation (WCF) używa usługi Windows o nazwie usługi udostępniania portów Net.TCP, ułatwiające Udostępnianie portów TCP wiele procesów. Ta usługa jest instalowana jako część usługi WCF, ale usługa nie jest włączona domyślnie w celu zapewnienia bezpieczeństwa i dlatego musi być włączone ręcznie przed pierwszym użyciu. W tym temacie opisano sposób konfigurowania sieci TCP usługi udostępniania portów za pomocą przystawki programu Microsoft Management Console (MMC).  
  
 Po włączyć usługi udostępniania portów Net.TCP i uruchom ją ręcznie, zobacz [jak: Konfigurowanie usługi WCF na potrzeby współużytkowania portów użyj](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) informacji o sposobie konfigurowania usługi, aby używać tej usługi.  
  
 Dla przykładu korzystającego z usługi współużytkowania portów net.tcp://, zobacz [przykładowe udostępniania portów Net.TCP](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>Aby włączyć usługi udostępniania portów Net.TCP przy użyciu konsoli MMC  
  
1.  Z Start menu, otwórz konsolę zarządzania usługami, albo, otwierając okno wiersza polecenia i wpisując `services.msc` lub przez otwarcie wykonywania i wpisując `services.msc` w polu Otwórz.  
  
2.  W **nazwa** kolumny na liście usług, kliknij prawym przyciskiem myszy **usługi udostępniania portów Net.Tcp**i wybierz **właściwości** z menu.  
  
3.  Do włączenia ręcznym uruchomieniu usługi, w **właściwości** wybierz okno **ogólne** kartę i w **uruchamiana** wybierz ręcznego, a następnie kliknij przycisk **Zastosuj**.  
  
4.  Aby uruchomić usługę, w obszarze stanu usługi, kliknij przycisk **Start** przycisku. Stan usługi powinien być teraz ustawiony na "Uruchomiono".  
  
5.  Aby powrócić do listy usług, kliknij przycisk **OK**i zamknąć okno konsoli MMC.  
  
## <a name="example"></a>Przykład  
  
## <a name="see-also"></a>Zobacz także
- [Współużytkowanie portów w składniku Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Konfigurowanie usługi współużytkowania portów Net.TCP](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
