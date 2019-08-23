---
title: 'Instrukcje: Włącz dostęp do usługi danych (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 82b2ec9313c6e0d4b9fa05862209a3ea838f31fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918622"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Instrukcje: Włącz dostęp do usługi danych (Usługi danych programu WCF)
W [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]programie należy jawnie udzielić dostępu do zasobów, które są udostępniane przez usługę danych. Oznacza to, że po utworzeniu nowej usługi danych nadal trzeba jawnie zapewnić dostęp do poszczególnych zasobów jako zestawy jednostek. W tym temacie pokazano, jak włączyć dostęp do odczytu i zapisu do pięciu zestawów jednostek w usłudze danych Northwind, która została utworzona po zakończeniu przewodnika [Szybki Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Ponieważ Wyliczenie jest zdefiniowane przy <xref:System.FlagsAttribute>użyciu, można użyć operatora logicznego OR do określenia wielu uprawnień dla pojedynczego zestawu jednostek. <xref:System.Data.Services.EntitySetRights>  
  
> [!NOTE]
> Każdy klient, który może uzyskać dostęp do aplikacji ASP.NET, może również uzyskać dostęp do zasobów udostępnianych przez usługę danych. W przypadku usługi danych produkcyjnych aby zapobiec nieautoryzowanemu dostępowi do zasobów, należy również zabezpieczyć samą aplikację. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie witryn sieci Web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
### <a name="to-enable-access-to-the-data-service"></a>Aby włączyć dostęp do usługi danych  
  
- W kodzie usługi danych Zastąp symbol zastępczy w `InitializeService` funkcji następującymi elementami:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     Dzięki temu klienci mają dostęp do odczytu i zapisu do `Orders` zestawów jednostek oraz `Order_Details` dostęp tylko do odczytu do `Customers` zestawów jednostek.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie usługi danych programu WCF uruchomionej w usługach IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)
- [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
