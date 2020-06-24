---
title: 'Instrukcje: Włączanie usługi współużytkowania portów Net.TCP'
description: Dowiedz się, jak skonfigurować usługę net. TCP do udostępniania portów TCP, która jest domyślnie wyłączona.
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 0292559e3befde7f0b00b36aa10a2d9615daf049
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247003"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>Instrukcje: Włączanie usługi współużytkowania portów Net.TCP
Windows Communication Foundation (WCF) używa usługi systemu Windows o nazwie Usługa udostępniania portów Net. TCP w celu ułatwienia udostępniania portów TCP w wielu procesach. Ta usługa jest instalowana w ramach programu WCF, ale usługa nie jest domyślnie włączona z zabezpieczeniami i dlatego musi być włączona ręcznie przed pierwszym użyciem. W tym temacie opisano sposób konfigurowania usługi udostępniania portów TCP sieci przy użyciu przystawki programu Microsoft Management Console (MMC).  
  
 Po włączeniu usługi udostępniania portów Net. TCP i uruchomieniu jej ręcznie zapoznaj się z tematem [jak: Konfigurowanie usługi WCF do używania udostępniania portów](how-to-configure-a-wcf-service-to-use-port-sharing.md) , aby uzyskać informacje o sposobie konfigurowania usługi do korzystania z tej usługi.  
  
 Aby uzyskać przykład, który używa net. TCP://udostępniania portów, zobacz [przykład udostępniania portów Net. TCP](../samples/net-tcp-port-sharing-sample.md).  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>Aby włączyć usługę udostępniania portów Net. TCP przy użyciu programu MMC  
  
1. Z menu Start Otwórz konsolę zarządzania usługami, otwierając okno wiersza polecenia i wpisując `services.msc` lub otwierając polecenie Uruchom i wpisując `services.msc` w polu Otwórz.  
  
2. W kolumnie **Nazwa** listy usług kliknij prawym przyciskiem myszy **usługę udostępniania portów Net. TCP**, a następnie wybierz polecenie **Właściwości** z menu.  
  
3. Aby włączyć ręczne uruchamianie usługi, w oknie **Właściwości** wybierz kartę **Ogólne** , a następnie w polu **Typ uruchomienia** wybierz pozycję ręcznie, a następnie kliknij pozycję **Zastosuj**.  
  
4. Aby uruchomić usługę, w obszarze Stan usługi kliknij przycisk **Uruchom** . Stan usługi powinien teraz zawierać wartość "uruchomiona".  
  
5. Aby powrócić do listy usług, kliknij przycisk **OK**i zamknij konsolę MMC.  
  
## <a name="example"></a>Przykład  
  
## <a name="see-also"></a>Zobacz też

- [Współużytkowanie portów w składniku Net.TCP](net-tcp-port-sharing.md)
- [Konfigurowanie usługi współużytkowania portów Net.TCP](configuring-the-net-tcp-port-sharing-service.md)
