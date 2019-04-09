---
title: Używanie elementu WS-AtomicTransaction
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
ms.openlocfilehash: 8a8265873e4287e1455659aa4d9fae7e1d570a00
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165499"
---
# <a name="using-ws-atomictransaction"></a>Używanie elementu WS-AtomicTransaction
WS-AtomicTransaction (WS-AT) jest protokołem interoperacyjne transakcji. Umożliwia ona przepływu transakcji rozproszonych za pomocą wiadomości usługi sieci Web i koordynacji w sposób interoperacyjny między infrastruktury heterogenicznych transakcji. WS-AT korzysta z protokołu dwufazowego, można dostarczać atomic wyniku między aplikacji rozproszonych, menedżerowie transakcji i menedżerów zasobów.  
  
 Implementacja WS-AT przez Windows Communication Foundation (WCF) obejmuje protokół oferująca do transakcji Menedżera transakcji Koordynator MSDTC (Microsoft Distributed). Za pomocą WS-AT, aplikacji WCF może przepływać transakcji do innych aplikacji, w tym usług międzyoperacyjnych w sieci Web utworzone przy użyciu technologii innych firm.  
  
 Podczas przepływu transakcji od aplikacji klienckiej i aplikacji serwera, protokół transakcji jest określana przez powiązanie, czy serwer udostępnia w punkcie końcowym klienta wybrana. Niektórych powiązań dostarczanych przez system WCF wartość domyślna to określanie `OleTransactions` protokołu jako format propagacji transakcji, podczas gdy inne domyślne do określania WS-AT. Można także programowo zmodyfikować wybór protokół transakcji wewnątrz podane powiązanie.  
  
 Wybór protokołu czynników:  
  
-   Format nagłówków wiadomości, używany do przepływu transakcji od klienta do serwera.  
  
-   Protokół sieciowy używany do uruchomienia Protokół dwufazowego Menedżera transakcji klienta i serwera transakcji, aby rozpoznać wyniku transakcji.  
  
 Jeśli serwera i klienta są zapisywane przy użyciu usługi WCF, nie musisz używać WS-AT. Zamiast tego można użyć ustawień domyślnych `NetTcpBinding` z `TransactionFlow` włączony atrybut, który będzie używany `OleTransactions` zamiast tego protokołu. Aby uzyskać więcej informacji, zobacz [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md). W przeciwnym razie przepływają transakcji usługi sieci Web oparta na technologii innych firm, należy użyć WS-AT.  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie obsługi protokołu WS-Atomic Transaction](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
