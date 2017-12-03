---
title: "Dostawcy programu Entity Framework (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 26c054e3cc9dbf920ab280df43d97acdb90ca055
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="entity-framework-provider-wcf-data-services"></a>Dostawcy programu Entity Framework (usługi danych WCF)
Podobnie jak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], ADO.NET Entity Framework jest oparta na modelu danych jednostki, który jest typem modelu Relacja jednostki. Entity Framework tłumaczy operacji przed jej implementacja modelu danych jednostki, która jest wywoływana *modelu koncepcyjnego*, na równoważne operacje względem źródła danych. Dzięki temu programu Entity Framework idealne dostawcy usług danych, które są oparte na danych relacyjnych i wszystkie bazy danych, w której dostawcy danych, który obsługuje programu Entity Framework może być używany z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Aby uzyskać listę źródeł danych, które obecnie obsługuje programu Entity Framework, zobacz [dostawców dla programu Entity Framework](http://go.microsoft.com/fwlink/?LinkId=143699).  
  
 W modelu koncepcyjnym kontenera jednostek jest katalogiem głównym usługi. Należy zdefiniować model koncepcyjny w programu Entity Framework, zanim dane mogą być udostępniane przez usługę danych. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]obsługuje model optymistycznej współbieżności, umożliwiając zdefiniowanie tokenem współbieżności dla jednostki. Ten token współbieżności, który zawiera co najmniej jednej właściwości jednostki, jest używany przez usługę danych do określenia, czy w danych, który jest wymagany, zaktualizowanych lub usuniętych nastąpiła zmiana. Gdy wartości tokenu z elementem eTag w żądaniu różnią się od bieżących wartości podmiotu, wyjątek zgłoszony przez usługę danych. Aby wskazać, że właściwość jest częścią tokenu współbieżności, należy zastosować atrybut `ConcurrencyMode="Fixed"` w modelu danych, wynika z [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] dostawcy. Token współbieżności nie może zawierać właściwości klucza lub właściwości nawigacji. Aby uzyskać więcej informacji, zobacz [aktualizacji usługi danych](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 Aby dowiedzieć się więcej na temat programu Entity Framework, zobacz [Omówienie struktury jednostek](../../../../docs/framework/data/adonet/ef/overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostawców usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Dostawca odbicia](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)  
 [Modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
