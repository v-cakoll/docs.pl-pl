---
title: Dostawca Entity Framework (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: 612888aaa11c606112527f01864897560061845f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790852"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Dostawca Entity Framework (Usługi danych programu WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Na przykład ADO.NET Entity Framework jest oparty na Entity Data Model, który jest typem modelu relacji jednostek. Entity Framework tłumaczy operacje na implementację Entity Data Model, która jest nazywana *modelem koncepcyjnym*w równoważne operacje względem źródła danych. Dzięki temu Entity Framework idealnym dostawcą usług danych opartych na danych relacyjnych, a każda baza danych, która ma dostawcę danych obsługującą Entity Framework, może być używana z programem [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Aby zapoznać się z listą źródeł danych, które obecnie obsługują Entity Framework, zobacz [dostawców innych firm dla Entity Framework](https://go.microsoft.com/fwlink/?LinkId=143699).  
  
 W modelu koncepcyjnym kontener jednostki jest katalogiem głównym usługi. Model koncepcyjny należy zdefiniować w Entity Framework zanim dane będą mogły być udostępniane przez usługę danych. Aby uzyskać więcej informacji, zobacz [jak: Utwórz usługę danych przy użyciu źródła](create-a-data-service-using-an-adonet-ef-data-wcf.md)danych ADO.NET Entity Framework.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]obsługuje optymistyczny model współbieżności, umożliwiając zdefiniowanie tokenu współbieżności dla jednostki. Ten token współbieżności, który zawiera co najmniej jedną właściwość jednostki, jest używany przez usługę danych w celu ustalenia, czy wprowadzono zmianę w danych, które są żądane, aktualizowane lub usuwane. Gdy wartości tokenu uzyskane z elementu eTag w żądaniu różnią się od bieżących wartości jednostki, wyjątek jest wywoływany przez usługę danych. Aby wskazać, że właściwość jest częścią tokenu współbieżności, należy zastosować atrybut `ConcurrencyMode="Fixed"` w modelu danych zdefiniowanym [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] przez dostawcę. Token współbieżności nie może zawierać właściwości Key ani właściwości nawigacji. Aby uzyskać więcej informacji, zobacz [Aktualizowanie usługi danych](updating-the-data-service-wcf-data-services.md).  
  
 Aby dowiedzieć się więcej na temat Entity Framework, zobacz [Omówienie usługi Entity Framework](../adonet/ef/overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Dostawcy usług danych](data-services-providers-wcf-data-services.md)
- [Dostawca odbicia](reflection-provider-wcf-data-services.md)
- [Model danych jednostki](../adonet/entity-data-model.md)
