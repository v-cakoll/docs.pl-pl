---
title: 'Porady: projekt wyników kwerendy (usługi danych WCF)'
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
ms.openlocfilehash: 4b75eb21cab7cd3acf25f7bcb9a3f009e8d5748b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353895"
---
# <a name="how-to-project-query-results-wcf-data-services"></a>Porady: projekt wyników kwerendy (usługi danych WCF)
Projekcja udostępnia mechanizm zmniejszyć ilość danych zwróconych przez zapytanie, określając, że niektóre właściwości jednostki są zwracane w odpowiedzi. Można wykonać rzutowania z wyników [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zapytania przy użyciu `$select` opcji zapytania lub za pomocą [wybierz](~/docs/csharp/language-reference/keywords/select-clause.md) klauzuli ([wybierz](~/docs/visual-basic/language-reference/queries/select-clause.md) w języku Visual Basic) w zapytaniu składnika LINQ. Aby uzyskać więcej informacji, zobacz [zapytanie usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Przykład, w tym temacie korzysta z Northwind przykładowych danych wygenerowany automatycznie i usługi klienta danych usługi klas. Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia zapytania LINQ tego projektów jednostek klientów na nowy typ adresem klienta, zawierający tylko właściwości specyficzne dla adres oraz właściwości tożsamości. To `CustomerAddress` klasa jest zdefiniowana na kliencie i jest przypisane, aby biblioteka klienta może rozpoznać go jako typu jednostki.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono LINQ zapytania tego projektów zwrócone jednostki klientów na nowy typ CustomerAddressNonEntity, zawierającą tylko określonych adresów właściwości i ma właściwości tożsamości. To `CustomerAddressNonEntity` klasa jest zdefiniowana na komputerze klienckim i nie jest przypisana jako typu jednostki.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono definicje `CustomerAddress``CustomerAddressNonEntity` typy, które są używane w poprzednich przykładach.  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customeraddress.vb#customeraddressdefinition)]
