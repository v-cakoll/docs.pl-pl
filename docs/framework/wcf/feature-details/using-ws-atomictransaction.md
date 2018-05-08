---
title: Używanie elementu WS-AtomicTransaction
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
ms.openlocfilehash: 7880d46d4827b36c7806c61877edf79faa766371
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-ws-atomictransaction"></a>Używanie elementu WS-AtomicTransaction
WS-AtomicTransaction (WS-AT) to protokół interoperacyjne transakcji. Umożliwia ona przepływu transakcji rozproszonych za pomocą komunikatów usługi sieci Web oraz koordynować w sposób współpraca między infrastruktury heterogenicznych transakcji. WS-AT Protokół dwufazowego dysków wyników częściowych między aplikacji rozproszonych, menedżerów transakcji i menedżerów zasobów.  
  
 Implementacja protokołu WS-AT przez Windows Communication Foundation (WCF) obejmują usługę protokołu wbudowane w Menedżera transakcji koordynatora transakcji rozproszonych (MSDTC). Za pomocą usługi WS-AT, aplikacje WCF przepływ transakcji do innych aplikacji, takich jak współdziałanie usługi sieci Web utworzony za pomocą innych technologii.  
  
 Podczas przepływu transakcji od aplikacji klienckiej i aplikacji serwera, protokół transakcji używany jest określana przez powiązanie, czy serwer udostępnia w punkcie końcowym klienta wybrana. Niektóre domyślne powiązania dostarczane przez system WCF do określania `OleTransactions` protokołu formacie propagacji transakcji, podczas gdy inne domyślne do określania WS-AT. Wybór protokół transakcji wewnątrz podane powiązanie również programowo można modyfikować.  
  
 Wybór protokołu wpływ:  
  
-   Format nagłówki komunikatów używane w celu przekazania transakcji od klienta do serwera.  
  
-   Protokół używany do uruchomienia dwufazowego protokołu wykonania Menedżera transakcji klienta i serwera transakcji, aby rozwiązać wyniku transakcji.  
  
 Przy użyciu programu WCF są zapisywane serwera i klienta, nie trzeba używać protokołu WS-AT. Zamiast tego można użyć ustawień domyślnych `NetTcpBinding` z `TransactionFlow` włączone, atrybut, który będzie używany `OleTransactions` zamiast tego protokołu. Aby uzyskać więcej informacji, zobacz [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md). W przeciwnym razie są przepływy transakcji do usług sieci Web oparty na technologii innych firm, należy użyć protokołu WS-AT.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie obsługi protokołu WS-Atomic Transaction](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
