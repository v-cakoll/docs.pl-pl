---
title: 'Instrukcje: Filtrowanie powiązanych danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: e8e63c139f38d6de46390925428e18682a65818d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793603"
---
# <a name="how-to-filter-related-data"></a>Instrukcje: Filtrowanie powiązanych danych
Użyj metody <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> , aby określić podzapytania, aby ograniczyć ilość pobranych danych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> Metoda `Orders` ogranicza pobrane elementy do tych, które nie zostały wysłane dzisiaj. Bez tego podejścia wszystkie `Orders` zostałyby pobrane, nawet jeśli pożądane jest tylko podzbiór.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie zapytania w bazie danych](querying-the-database.md)
