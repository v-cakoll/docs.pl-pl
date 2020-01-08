---
title: Dostawca Entity Framework (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: b6d49f20f72282ac2ce51c26fc4eb941b7ef6734
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346094"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Dostawca Entity Framework (Usługi danych programu WCF)
Podobnie jak Usługi danych programu WCF, Entity Framework ADO.NET jest oparty na Entity Data Model, który jest typem modelu relacji jednostki. Entity Framework tłumaczy operacje na implementację Entity Data Model, która jest nazywana *modelem koncepcyjnym*w równoważne operacje względem źródła danych. Dzięki temu Entity Framework idealnym dostawcą usług danych opartych na danych relacyjnych, a każda baza danych, która ma dostawca danych, który obsługuje Entity Framework, może być używana z Usługi danych programu WCFem. Aby zapoznać się z listą źródeł danych, które obecnie obsługują Entity Framework, zobacz [Entity Framework dostawcy](/ef/ef6/fundamentals/providers/).
  
 W modelu koncepcyjnym kontener jednostki jest katalogiem głównym usługi. Model koncepcyjny należy zdefiniować w Entity Framework zanim dane będą mogły być udostępniane przez usługę danych. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi danych przy użyciu źródła danych ADO.NET Entity Framework](create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
 Usługi danych programu WCF obsługuje optymistyczny model współbieżności, umożliwiając zdefiniowanie tokenu współbieżności dla jednostki. Ten token współbieżności, który zawiera co najmniej jedną właściwość jednostki, jest używany przez usługę danych w celu ustalenia, czy wprowadzono zmianę w danych, które są żądane, aktualizowane lub usuwane. Gdy wartości tokenu uzyskane z elementu eTag w żądaniu różnią się od bieżących wartości jednostki, wyjątek jest wywoływany przez usługę danych. Aby wskazać, że właściwość jest częścią tokenu współbieżności, należy zastosować atrybut `ConcurrencyMode="Fixed"` w modelu danych zdefiniowanym przez dostawcę Entity Framework. Token współbieżności nie może zawierać właściwości Key ani właściwości nawigacji. Aby uzyskać więcej informacji, zobacz [Aktualizowanie usługi danych](updating-the-data-service-wcf-data-services.md).  
  
 Aby dowiedzieć się więcej na temat Entity Framework, zobacz [Omówienie usługi Entity Framework](../adonet/ef/overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Dostawcy usług danych](data-services-providers-wcf-data-services.md)
- [Dostawca odbicia](reflection-provider-wcf-data-services.md)
- [Model danych jednostki](../adonet/entity-data-model.md)
