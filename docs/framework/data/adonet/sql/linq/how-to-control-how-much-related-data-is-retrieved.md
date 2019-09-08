---
title: 'Instrukcje: Kontrolowanie, ile jest pobieranych powiązanych danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: 2112600dfcef65b1c85445b03806ce8e9cab6a27
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782055"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a>Instrukcje: Kontrolowanie, ile jest pobieranych powiązanych danych
<xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> Użyj metody, aby określić, które dane związane z głównym miejscem docelowym powinny być pobierane w tym samym czasie. Jeśli na przykład wiesz, że potrzebujesz informacji o zamówieniach klientów, możesz użyć <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> programu, aby upewnić się, że informacje o zamówieniach są pobierane w tym samym czasie co informacje o kliencie. To podejście powoduje tylko jedną podróż do bazy danych dla obu zestawów informacji.  
  
> [!NOTE]
> Dane związane z głównym celem zapytania można pobrać, pobierając jeden z wielu produktów, takich jak pobieranie zamówień w przypadku docelowych klientów. Ale takie podejście często ma wady. Na przykład wyniki są tylko projekcjami, a nie jednostkami, które mogą być zmieniane i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]utrwalane przez program. Możesz też pobrać wiele niepotrzebnych danych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie wszystkie `Orders` dla `Customers` wszystkich osób, które znajdują się w Londynie, są pobierane po wykonaniu zapytania. W efekcie dostęp do `Orders` właściwości `Customer` na obiekcie nie wyzwala nowej kwerendy bazy danych.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie zapytania w bazie danych](querying-the-database.md)
