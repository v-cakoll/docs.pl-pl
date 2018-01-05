---
title: "Migrowanie aplikacji usług zdalnych platformy .NET do programu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7d305adf1810832016cdafbb60fc025f17e0786
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migrowanie aplikacji usług zdalnych platformy .NET do programu WCF
**Ten temat dotyczy starszych technologia, która została zachowana na potrzeby zgodności z poprzednimi wersjami z istniejącymi aplikacjami i nie jest zalecane w przypadku nowych wdrożeń. Teraz należy opracować aplikacji rozproszonych za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**  
  
 Istnieją dwa sposoby, aby móc korzystać z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] z istniejących aplikacji .NET Remoting: integracja i migracji. Integracji pozwala na program .net Remoting 2.0 i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] działa obok siebie, dzięki czemu naraża te same obiekty biznesowych w obu tych technologii jednocześnie bez konieczności modyfikowania Twoje istniejące .net Remoting 2.0 kodu. Integracja wymaga się, że są uruchomione na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 lub nowszej. Jeśli chcesz móc korzystać z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkcje i czy nie wymagają okablować zgodność z systemów zdalnych 2.0, można migrować całą usługa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Migracja z usług zdalnych .NET 2.0 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wymaga wprowadzenia zmian obiektu zdalnego interfejsu i jego ustawień konfiguracji. Oba te tematy zostały omówione w [z Remoting do programu Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie pojęć](../../../../docs/framework/wcf/conceptual-overview.md)
