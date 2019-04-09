---
title: 'Instrukcje: Zapewnianie dostępu do usługi danych (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 44f3709cf0a1485c772940e7460d3436a52aa3eb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163660"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Instrukcje: Zapewnianie dostępu do usługi danych (WCF Data Services)
W [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], należy jawnie zezwolić na dostęp do zasobów, które są udostępniane przez usługę danych. Oznacza to, że po utworzeniu nowej usługi danych, należy nadal jawnie określić, dostęp do poszczególnych zasobów jako zestawy jednostek. W tym temacie przedstawiono sposób włączania odczytu i zapisu do pięciu jednostki zestawy w usługi danych Northwind, który jest tworzony po ukończeniu [Szybki Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Ponieważ <xref:System.Data.Services.EntitySetRights> wyliczenia jest definiowana za pomocą <xref:System.FlagsAttribute>, można użyć logicznych lub operatora, aby określić wiele uprawnień dla pojedynczej jednostki.  
  
> [!NOTE]
>  Każdy klient, który może uzyskiwać dostęp do aplikacji ASP.NET również dostęp do zasobów udostępnianych przez usługę danych. W środowisku produkcyjnym usługi danych Aby uniemożliwić nieautoryzowany dostęp do zasobów, należy także zabezpieczyć samej aplikacji. Aby uzyskać więcej informacji, zobacz [zabezpieczania witryn sieci Web platformy ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
### <a name="to-enable-access-to-the-data-service"></a>Aby umożliwić dostęp do usługi danych  
  
-   W kodzie dla usługi danych, Zastąp kod symbolu zastępczego `InitializeService` funkcji następującym kodem:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     Dzięki temu klienci do odczytu i zapisu do `Orders` i `Order_Details` zestawów jednostek i dostęp tylko do odczytu do `Customers` zestawy jednostek.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie usługi danych WCF działającej na serwerze IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)
- [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
