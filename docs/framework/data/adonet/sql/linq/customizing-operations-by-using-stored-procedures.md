---
title: Dostosowywanie operacji przy użyciu procedur składowanych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a
ms.openlocfilehash: d9f8d15b46f6e5575bd206bf572ffda0365e58f6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743553"
---
# <a name="customizing-operations-by-using-stored-procedures"></a>Dostosowywanie operacji przy użyciu procedur składowanych
Procedury składowane reprezentują Typowym rozwiązaniem w przypadku zastępowania domyślnego zachowania. W przykładach w tym temacie przedstawiono sposób korzystania generowane metody otoki dla procedur przechowywanych i jak można wywoływać procedury składowane bezpośrednio.  
  
 Jeśli używasz programu Visual Studio umożliwia Object Relational Designer przypisywanie procedur składowanych do wykonywania operacji wstawienia, aktualizacje i usunięcia.  
  
> [!NOTE]
>  Aby odczytać wartości z powrotem wygenerowanych w bazie danych, należy użyć parametrów wyjściowych w przechowywanych procedur. Jeśli nie możesz użyć parametrów wyjściowych, zapisu przesłonięcia implementację metody częściowej, zamiast polegania na generowane przez Object Relational Designer. Elementy członkowskie wygenerowanych w bazie danych wartości musi być ustawione na odpowiednie wartości po `INSERT` lub `UPDATE` operacje zostały pomyślnie ukończone. Aby uzyskać więcej informacji, zobacz [obowiązki dewelopera w zastępowanie domyślne zachowanie](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przyjęto założenie, że `Northwind` klasy zawiera dwie metody do wywołania procedur składowanych, które są używane do zastąpienia w klasie pochodnej.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#1)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Następujące klasy są używane do przesłonięcia.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#2)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Możesz użyć `NorthwindThroughSprocs` dokładnie tak jak w przypadku `Northwnd`.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Obowiązki dewelopera podczas zastępowania domyślnego zachowania](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
