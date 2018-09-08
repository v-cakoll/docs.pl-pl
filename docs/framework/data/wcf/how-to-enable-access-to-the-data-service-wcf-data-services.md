---
title: 'Instrukcje: Zapewnianie dostępu do usługi danych (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: eb9d7cd8e62a73f49fd2b0f2fc2572b01109553b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44214839"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Instrukcje: Zapewnianie dostępu do usługi danych (WCF Data Services)
W [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], należy jawnie zezwolić na dostęp do zasobów, które są udostępniane przez usługę danych. Oznacza to, że po utworzeniu nowej usługi danych, należy nadal jawnie określić, dostęp do poszczególnych zasobów jako zestawy jednostek. W tym temacie przedstawiono sposób włączania odczytu i zapisu do pięciu jednostki zestawy w usługi danych Northwind, który jest tworzony po ukończeniu [Szybki Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Ponieważ <xref:System.Data.Services.EntitySetRights> wyliczenia jest definiowana za pomocą <xref:System.FlagsAttribute>, można użyć logicznych lub operatora, aby określić wiele uprawnień dla pojedynczej jednostki.  
  
> [!NOTE]
>  Każdy klient, który może uzyskiwać dostęp do aplikacji ASP.NET również dostęp do zasobów udostępnianych przez usługę danych. W środowisku produkcyjnym usługi danych Aby uniemożliwić nieautoryzowany dostęp do zasobów, należy także zabezpieczyć samej aplikacji. Aby uzyskać więcej informacji, zobacz [NIB: zabezpieczenia programu ASP.NET](https://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d).  
  
### <a name="to-enable-access-to-the-data-service"></a>Aby umożliwić dostęp do usługi danych  
  
-   W kodzie dla usługi danych, Zastąp kod symbolu zastępczego `InitializeService` funkcji następującym kodem:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     Dzięki temu klienci do odczytu i zapisu do `Orders` i `Order_Details` zestawów jednostek i dostęp tylko do odczytu do `Customers` zestawy jednostek.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Tworzenie usługi danych WCF działającej na serwerze IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)  
 [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
