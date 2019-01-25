---
title: Dostawcy programu Entity Framework (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: 94a708ca33aa94c7a0143d195803d17d49be4bdb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569118"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Dostawcy programu Entity Framework (WCF Data Services)
Podobnie jak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], ADO.NET Entity Framework jest oparta na modelu danych jednostki, który jest typem jednostki relacji modelu. Entity Framework tłumaczy operacji wykonywanych względem jego implementacja obiektu modelu danych jednostki, która jest wywoływana *modelu koncepcyjnego*, na równoważne operacje w odniesieniu do źródła danych. To sprawia, że platforma Entity Framework dostawcę idealne rozwiązanie dla usług danych, które są oparte na danych relacyjnych i wszelkie bazy danych, w której dostawcy danych, który obsługuje platformy Entity Framework może być używany z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Aby uzyskać listę źródeł danych, które obecnie obsługuje platformy Entity Framework, zobacz [dostawców innych firm dla programu Entity Framework](https://go.microsoft.com/fwlink/?LinkId=143699).  
  
 W model koncepcyjny kontener jednostek jest głównym usługi. Należy zdefiniować model koncepcyjny platformy Entity Framework, zanim dane mogą być udostępniane przez usługę danych. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsługuje model optymistycznej współbieżności, umożliwiając Definiowanie tokenem współbieżności dla jednostki. Ten token współbieżności, który zawiera jedną lub więcej właściwości jednostki, jest używany przez usługę danych do określenia, czy nastąpiła zmiana w danych, która jest wymagana, zaktualizowanych lub usuniętych. Gdy token wartości z elementu eTag w żądaniu różnią się od wartości bieżącej jednostki, wyjątek jest zgłaszany przez usługę danych. Aby wskazać, że właściwość jest częścią tokenu współbieżności, należy zastosować atrybut `ConcurrencyMode="Fixed"` w modelu danych zdefiniowane przez [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] dostawcy. Token współbieżności nie może zawierać właściwości klucza lub właściwości nawigacji. Aby uzyskać więcej informacji, zobacz [aktualizacja usługi danych](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 Aby dowiedzieć się więcej na temat programu Entity Framework, zobacz [Omówienie programu Entity Framework](../../../../docs/framework/data/adonet/ef/overview.md).  
  
## <a name="see-also"></a>Zobacz także
- [Dostawcy usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Dostawca odbicia](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
- [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
