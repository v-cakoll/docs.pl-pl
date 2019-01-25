---
title: 'Instrukcje: Kontrolowanie, ile powiązane dane są pobierane.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: 3b52e2cdefefce011be7d729569b76f919f9bb33
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715611"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a>Instrukcje: Kontrolowanie, ile powiązane dane są pobierane.
Użyj <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> metodę, aby określić, które dane powiązane z głównym docelowej mają zostać pobrane w tym samym czasie. Na przykład, jeśli wiesz, konieczne będą informacje dotyczące zamówień klientów, można użyć <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> aby upewnić się, że informacje o kolejności są pobierane w tym samym czasie jako informacje o kliencie. To podejście powoduje tylko jeden podróży do bazy danych dla obu zestawów informacji.  
  
> [!NOTE]
>  Możesz pobrać dane związane z głównym celem zapytania, pobierając obejmujących wiele produktów jako jeden duży projekcji, takie jak pobieranie zamówień, gdy skierowane do klientów. Jednak to podejście ma często wady. Na przykład, wyniki są po prostu projekcje i nie jednostki, które można zmienić i utrwalone przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. A może pobieranie dużej ilości danych, która nie ma potrzeby.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie wszystkie `Orders` dla wszystkich `Customers` kto znajdują się w Londynie są pobierane, gdy zapytanie jest wykonywane. Dzięki temu usługa następujących po sobie dostęp do `Orders` właściwość `Customer` obiektu nie wyzwalają nowej kwerendy bazy danych.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także
- [Wykonywanie zapytania w bazie danych](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
