---
title: 'Instrukcje: Filtrowanie powiązanych danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: 3dbedfb7065ac4b1a570a3f6cdbcdcc2177f20cf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218228"
---
# <a name="how-to-filter-related-data"></a>Instrukcje: Filtrowanie powiązanych danych
Użyj <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> metodę, aby określić podzapytaniach, aby ograniczyć ilość pobierane są dane.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> limity metoda `Orders` pobierane do tych, które nie zostały wysłane już dziś. Bez tego podejścia wszystkich `Orders` będzie pobierana, nawet jeśli wymagane jest tylko ich podzestaw.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [wykonywanie zapytania w bazie danych](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
