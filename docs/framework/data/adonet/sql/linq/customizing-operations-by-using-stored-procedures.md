---
title: Dostosowywanie operacji przy użyciu procedur składowanych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a
ms.openlocfilehash: 08cc8aedac545ffa5648034119fc2267c860d499
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963292"
---
# <a name="customizing-operations-by-using-stored-procedures"></a>Dostosowywanie operacji przy użyciu procedur składowanych
Procedury składowane reprezentują typowe podejście do zastępowania zachowania domyślnego. W przykładach w tym temacie pokazano, jak można użyć wygenerowanych otok metod dla procedur składowanych oraz jak można wywołać procedury składowane bezpośrednio.  
  
 Jeśli używasz programu Visual Studio, możesz użyć Object Relational Designer, aby przypisać procedury składowane do wykonywania operacji wstawiania, aktualizacji i usuwania.  
  
> [!NOTE]
> Aby odczytać wartości z wygenerowanej bazy danych, użyj parametrów wyjściowych w procedurach składowanych. Jeśli nie możesz użyć parametrów wyjściowych, Zapisz implementację metody częściowej zamiast zastępowania zastąpień generowanych przez Object Relational Designer. Elementy członkowskie zamapowane do wartości generowanych przez bazę danych muszą być ustawione `INSERT` na `UPDATE` odpowiednie wartości po pomyślnym zakończeniu operacji lub. Aby uzyskać więcej informacji, zobacz [obowiązki dewelopera w celu przesłania domyślnego zachowania](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie Załóżmy, że `Northwind` Klasa zawiera dwie metody wywołania procedur składowanych, które są używane dla zastąpień w klasie pochodnej.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#1)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższej klasie są wykorzystywane te metody przesłonięcia.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#2)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Możesz użyć `NorthwindThroughSprocs` dokładnie tak, jak `Northwnd`chcesz.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Obowiązki dewelopera podczas zastępowania domyślnego zachowania](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
