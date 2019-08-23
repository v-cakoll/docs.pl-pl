---
title: 'Instrukcje: Wyniki zapytania projektu (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: 474ac625-8770-43ba-8320-d3315ea9530f
ms.openlocfilehash: b53da9c1ecfcc5061fe551c4e180774319beaf5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952224"
---
# <a name="how-to-project-query-results-wcf-data-services"></a>Instrukcje: Wyniki zapytania projektu (Usługi danych programu WCF)
Projekcja zapewnia mechanizm zmniejszania ilości danych zwracanych przez zapytanie przez określenie, że tylko niektóre właściwości jednostki są zwracane w odpowiedzi. Można wykonywać projekcje [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] na wynikach zapytania przy `$select` użyciu opcji zapytania lub klauzuli [SELECT](../../../csharp/language-reference/keywords/select-clause.md) ([SELECT](../../../visual-basic/language-reference/queries/select-clause.md) in Visual Basic) w zapytaniu LINQ. Aby uzyskać więcej informacji, zobacz [wykonywanie zapytań dotyczących usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje zapytanie LINQ, które projektuje jednostki klientów do nowego typu CustomerAddress, który zawiera tylko właściwości specyficzne dla adresu i właściwość Identity. Ta `CustomerAddress` Klasa jest zdefiniowana na kliencie i jest przypisywana, tak aby Biblioteka klienta mogła rozpoznać ją jako typ jednostki.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje zapytanie LINQ, że projekty zwracają jednostki klientów do nowego typu CustomerAddressNonEntity, który zawiera tylko właściwości specyficzne dla adresu i bez właściwości tożsamości. Ta `CustomerAddressNonEntity` Klasa jest zdefiniowana na kliencie i nie jest przypisana do typu jednostki.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono definicje `CustomerAddress` typów i `CustomerAddressNonEntity` , które są używane w poprzednich przykładach.  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customeraddress.vb#customeraddressdefinition)]
