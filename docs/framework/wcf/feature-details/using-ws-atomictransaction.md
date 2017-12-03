---
title: "Używanie elementu WS-AtomicTransaction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 12e6e2be3e01ea920b45cce7a27814dd19c00935
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="using-ws-atomictransaction"></a>Używanie elementu WS-AtomicTransaction
WS-AtomicTransaction (WS-AT) to protokół interoperacyjne transakcji. Umożliwia ona przepływu transakcji rozproszonych za pomocą komunikatów usługi sieci Web oraz koordynować w sposób współpraca między infrastruktury heterogenicznych transakcji. WS-AT Protokół dwufazowego dysków wyników częściowych między aplikacji rozproszonych, menedżerów transakcji i menedżerów zasobów.  
  
 Implementacja protokołu WS-AT [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zapewnia obejmują usługę protokołu wbudowane w Menedżera transakcji koordynatora transakcji rozproszonych (MSDTC). Za pomocą usługi WS-AT [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji przepływ transakcji do innych aplikacji, takich jak współdziałanie usługi sieci Web utworzony za pomocą innych technologii.  
  
 Podczas przepływu transakcji od aplikacji klienckiej i aplikacji serwera, protokół transakcji używany jest określana przez powiązanie, czy serwer udostępnia w punkcie końcowym klienta wybrana. Niektóre [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] domyślne powiązania dostarczane przez system do określania `OleTransactions` protokołu formacie propagacji transakcji, podczas gdy inne domyślne do określania WS-AT. Wybór protokół transakcji wewnątrz podane powiązanie również programowo można modyfikować.  
  
 Wybór protokołu wpływ:  
  
-   Format nagłówki komunikatów używane w celu przekazania transakcji od klienta do serwera.  
  
-   Protokół używany do uruchomienia dwufazowego protokołu wykonania Menedżera transakcji klienta i serwera transakcji, aby rozwiązać wyniku transakcji.  
  
 Jeśli serwera i klienta są napisane przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], nie trzeba używać protokołu WS-AT. Zamiast tego można użyć ustawień domyślnych `NetTcpBinding` z `TransactionFlow` włączone, atrybut, który będzie używany `OleTransactions` zamiast tego protokołu. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md). W przeciwnym razie są przepływy transakcji do usług sieci Web oparty na technologii innych firm, należy użyć protokołu WS-AT.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie obsługi protokołu WS-Atomic Transaction](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
