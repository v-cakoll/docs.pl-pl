---
title: 'Instrukcje: wykonywanie zapytań asynchronicznych usługi danych (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
ms.openlocfilehash: 68e2035315780b7c6dd60e93ae6eb10d252aabb3
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569067"
---
# <a name="how-to-execute-asynchronous-data-service-queries-wcf-data-services"></a>Instrukcje: wykonywanie zapytań asynchronicznych usługi danych (Usługi danych programu WCF)
Za pomocą biblioteki klienta Usługi danych programu WCF można asynchronicznie wykonywać operacje na serwerze klienta, takie jak wykonywanie zapytań i zapisywanie zmian. Aby uzyskać więcej informacji, zobacz [operacje asynchroniczne](asynchronous-operations-wcf-data-services.md).  
  
> [!NOTE]
> W aplikacji, w której wywołanie zwrotne musi być wywoływane w określonym wątku, należy jawnie zorganizować wykonywanie metody <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>. Aby uzyskać więcej informacji, zobacz [operacje asynchroniczne](asynchronous-operations-wcf-data-services.md).  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wykonać zapytanie asynchroniczne przez wywołanie metody <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A>, aby uruchomić zapytanie. Obiekt delegowany w tekście wywołuje metodę <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>, aby wyświetlić wyniki zapytania.  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#executequeryasync)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
