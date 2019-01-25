---
title: Wywoływania metody lokalnej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: 249ed8425f175b80cb55289c2a7fe68742d8389c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655728"
---
# <a name="local-method-calls"></a>Wywoływania metody lokalnej
Wywołanie metody lokalnej jest taki, który jest wykonywany w ramach modelu obiektu. Wywołanie metody zdalnej jest jeden, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przekłada się na SQL i przesyła je do aparatu bazy danych w celu wykonania. Wywoływania metody lokalnej są wymagane podczas [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie może tłumaczyć wywołań do SQL. W przeciwnym razie <xref:System.InvalidOperationException> zgłaszany.  
  
## <a name="example-1"></a>Przykład 1  
 W poniższym przykładzie `Order` klasy jest mapowany do tabeli zamówienia w bazie danych Northwind. Metoda wystąpienia lokalnego, dodano do klasy.  
  
 Zapytanie 1, Konstruktor `Order` klasy jest wykonywana lokalnie. W zapytania 2, jeśli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] próbował tłumaczenie `LocalInstanceMethod()`w bazie SQL, próba zakończy się niepowodzeniem i <xref:System.InvalidOperationException> będzie zgłaszany wyjątek. Ale ponieważ [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia obsługę wywoływania metody lokalnej kwerenda2 nie spowoduje zgłoszenie wyjątku.  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a>Zobacz także
- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
