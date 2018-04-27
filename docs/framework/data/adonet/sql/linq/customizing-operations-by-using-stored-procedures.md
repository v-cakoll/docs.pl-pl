---
title: Dostosowywanie operacje przy użyciu procedur składowanych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 5d47089092de80488fbae107da630352cb38c1d9
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="customizing-operations-by-using-stored-procedures"></a>Dostosowywanie operacje przy użyciu procedur składowanych
Procedury składowane reprezentują wspólnego podejścia do Zastępowanie domyślnego zachowania. Przykłady w tym temacie przedstawiono sposób korzystania wygenerować otoki metody dla procedury składowane i jak można wywoływać procedur składowanych bezpośrednio.  
  
 Jeśli używasz programu Visual Studio, możesz użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] można przypisać procedur składowanych do wykonywania operacji wstawiania, aktualizacji i usunięć.  
  
> [!NOTE]
>  Można odczytać wartości powrotem generowanych przez bazę danych, należy użyć parametrów wyjściowych w Twojej procedur składowanych. Jeśli nie możesz użyć parametrów wyjściowych, zapisać implementacji metody częściowej zamiast polegania na zastąpienia generowane przez [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Elementy członkowskie mapowane na wartości generowanych przez bazy danych musi być ustawiona na odpowiednie wartości po `INSERT` lub `UPDATE` operacje zostały pomyślnie ukończone. Aby uzyskać więcej informacji, zobacz [obowiązki deweloperów w zastępowanie domyślne zachowanie](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przyjęto założenie, że `Northwind` klasa zawiera dwie metody do wywołania procedur składowanych, które są używane dla zastąpienia w klasie pochodnej.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#1)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Następujące klasy są używane do zastąpienia.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#2)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Można użyć `NorthwindThroughSprocs` dokładnie tak jak w przypadku `Northwnd`.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Obowiązki dewelopera podczas zastępowania domyślnego zachowania](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
