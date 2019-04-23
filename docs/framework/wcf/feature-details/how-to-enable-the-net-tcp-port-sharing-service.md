---
title: 'Instrukcje: włączanie usługi współużytkowania portów Net.TCP'
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 20db0ef427a5e791bd6b8dcef90bf7911ae0d4a9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343483"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>Instrukcje: włączanie usługi współużytkowania portów Net.TCP
Windows Communication Foundation (WCF) używa usługi Windows o nazwie usługi udostępniania portów Net.TCP, ułatwiające Udostępnianie portów TCP wiele procesów. Ta usługa jest instalowana jako część usługi WCF, ale usługa nie jest włączona domyślnie w celu zapewnienia bezpieczeństwa i dlatego musi być włączone ręcznie przed pierwszym użyciu. W tym temacie opisano sposób konfigurowania sieci TCP usługi udostępniania portów za pomocą przystawki programu Microsoft Management Console (MMC).  
  
 Po włączyć usługi udostępniania portów Net.TCP i uruchom ją ręcznie, zobacz [jak: Konfigurowanie usługi WCF na potrzeby współużytkowania portów użyj](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) informacji o sposobie konfigurowania usługi, aby używać tej usługi.  
  
 Dla przykładu korzystającego z usługi współużytkowania portów net.tcp://, zobacz [przykładowe udostępniania portów Net.TCP](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>Aby włączyć usługi udostępniania portów Net.TCP przy użyciu konsoli MMC  
  
1. Z Start menu, otwórz konsolę zarządzania usługami, albo, otwierając okno wiersza polecenia i wpisując `services.msc` lub przez otwarcie wykonywania i wpisując `services.msc` w polu Otwórz.  
  
2. W **nazwa** kolumny na liście usług, kliknij prawym przyciskiem myszy **usługi udostępniania portów Net.Tcp**i wybierz **właściwości** z menu.  
  
3. Do włączenia ręcznym uruchomieniu usługi, w **właściwości** wybierz okno **ogólne** kartę i w **uruchamiana** wybierz ręcznego, a następnie kliknij przycisk **Zastosuj**.  
  
4. Aby uruchomić usługę, w obszarze stanu usługi, kliknij przycisk **Start** przycisku. Stan usługi powinien być teraz ustawiony na "Uruchomiono".  
  
5. Aby powrócić do listy usług, kliknij przycisk **OK**i zamknąć okno konsoli MMC.  
  
## <a name="example"></a>Przykład  
  
## <a name="see-also"></a>Zobacz także

- [Współużytkowanie portów w składniku Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Konfigurowanie usługi współużytkowania portów Net.TCP](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
