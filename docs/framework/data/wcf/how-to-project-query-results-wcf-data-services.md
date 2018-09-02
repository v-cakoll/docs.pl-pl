---
title: 'Porady: projekt wyników zapytania (WCF Data Services)'
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
ms.openlocfilehash: c1eb2618e14f0e02aa5e1a2e91aa93fe0831c7c7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418489"
---
# <a name="how-to-project-query-results-wcf-data-services"></a>Porady: projekt wyników zapytania (WCF Data Services)
Projekcja zapewnia mechanizm, aby zmniejszyć ilość danych zwracanych przez zapytanie, określając, że zwracane są tylko niektóre właściwości jednostki w odpowiedzi. Można przeprowadzić projekcji na wynikach [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zapytania przy użyciu `$select` opcji zapytania lub za pomocą [wybierz](~/docs/csharp/language-reference/keywords/select-clause.md) klauzuli ([wybierz](~/docs/visual-basic/language-reference/queries/select-clause.md) w języku Visual Basic) w zapytaniu programu LINQ. Aby uzyskać więcej informacji, zobacz [zapytań usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 W przykładzie w tym temacie użyto Northwind przykładowe dane usługi i automatycznie wygenerowany klas usługi danych klienta. Ta usługa i klas danych klienta, są tworzone po ukończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje zapytanie LINQ tego projektów jednostek klientów do nowego typu adresem klienta, który zawiera tylko właściwości specyficzne dla adresu, a także właściwości tożsamości. To `CustomerAddress` klasa jest zdefiniowana na komputerze klienckim i została przypisana, tak aby biblioteki klienckiej je rozpoznać jako typ jednostki.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono LINQ zapytania tego projektów zwrócone jednostki klientów do nowego typu CustomerAddressNonEntity, zawierającą tylko adres określonych właściwości i nie właściwości tożsamości. To `CustomerAddressNonEntity` klasa jest zdefiniowana na komputerze klienckim i nie jest określane jako typ jednostki.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano definicje `CustomerAddress` i `CustomerAddressNonEntity` typy, które są używane w poprzednich przykładach.  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customeraddress.vb#customeraddressdefinition)]
