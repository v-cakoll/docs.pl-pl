---
title: 'Instrukcje: wyniki zapytania projektu (Usługi danych programu WCF)'
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
ms.openlocfilehash: 1e94b5f65229887b2d310f15499a2b14ef7c0536
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569007"
---
# <a name="how-to-project-query-results-wcf-data-services"></a>Instrukcje: wyniki zapytania projektu (Usługi danych programu WCF)
Projekcja zapewnia mechanizm zmniejszania ilości danych zwracanych przez zapytanie przez określenie, że tylko niektóre właściwości jednostki są zwracane w odpowiedzi. Można wykonywać projekcje na wynikach zapytania Usługi danych programu WCF albo przy użyciu opcji zapytania `$select` lub przy użyciu klauzuli [SELECT](../../../csharp/language-reference/keywords/select-clause.md) ([SELECT](../../../visual-basic/language-reference/queries/select-clause.md) in Visual Basic) w zapytaniu LINQ. Aby uzyskać więcej informacji, zobacz [wykonywanie zapytań dotyczących usługi danych](querying-the-data-service-wcf-data-services.md).  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje zapytanie LINQ, które projektuje jednostki klientów do nowego typu CustomerAddress, który zawiera tylko właściwości specyficzne dla adresu i właściwość Identity. Ta klasa `CustomerAddress` jest zdefiniowana na kliencie i jest przypisywana, tak aby Biblioteka klienta mogła rozpoznać ją jako typ jednostki.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje zapytanie LINQ, że projekty zwracają jednostki klientów do nowego typu CustomerAddressNonEntity, który zawiera tylko właściwości specyficzne dla adresu i bez właściwości tożsamości. Ta klasa `CustomerAddressNonEntity` jest zdefiniowana na kliencie i nie jest przypisana do typu jednostki.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono definicje typów `CustomerAddress` i `CustomerAddressNonEntity`, które są używane w poprzednich przykładach.  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customeraddress.vb#customeraddressdefinition)]
