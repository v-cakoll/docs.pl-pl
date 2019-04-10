---
title: 'Instrukcje: Dodawanie opcji zapytania do zapytania usługi danych (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: e4258526-557e-4e96-91e1-2175400c7c8f
ms.openlocfilehash: 07e327846e2fdda279e38b4f05ca0a2b3bbacb61
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211078"
---
# <a name="how-to-add-query-options-to-a-data-service-query-wcf-data-services"></a>Instrukcje: Dodawanie opcji zapytania do zapytania usługi danych (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umożliwia wykonywanie zapytań usługi danych z aplikacji klienta opartego na programie .NET Framework przy użyciu klas usługi danych wygenerowanego klienta. Najłatwiejszy w tym celu jest do redagowania wyrażenie zapytania Language Integrated Query (LINQ), która obejmuje opcje żądanego zapytania. Można również wywołać szereg metod zapytań LINQ do redagowania równoważne zapytania. Na koniec można użyć <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metodę, aby dodać opcje zapytania do zapytania. W każdym z tych przypadków identyfikator URI, który jest generowany przez klienta zawiera zestaw żądanej jednostki przy użyciu opcji wybrane zapytanie stosowane. Aby uzyskać więcej informacji, zobacz [zapytań usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 W przykładzie w tym temacie użyto Northwind przykładowe dane usługi i automatycznie wygenerowany klas usługi danych klienta. Ta usługa i klas danych klienta, są tworzone po ukończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć wyrażenie zapytania LINQ, które zwraca tylko zamówień za pomocą transportu koszt ponad 30 USD i że zamówienia wyniki według daty dostawy w kolejności malejącej.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinq)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinq)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak do redagowania zapytania LINQ za pomocą metody zapytań LINQ, który jest odpowiednikiem poprzednie zapytanie.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqexpression)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqexpression)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak za pomocą <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metodę w celu utworzenia <xref:System.Data.Services.Client.DataServiceQuery%601> oznacza to równoważne do poprzednich przykładów.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptions)]
 [!code-vb[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptions)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `$orderby` opcji zapytania do filtrowania i kolejność zwracane obiekty zamówienia przez właściwość transportu.  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#orderwithfilter)]  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie zapytań do usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
- [Instrukcje: Projekt wyników zapytania](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)
