---
title: 'Instrukcje: Dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e24c6b5aa02e8bc7ca4bcbf2c69bffd06216962
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535449"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a>Instrukcje: Dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection
W tym przykładzie przedstawiono sposób dodawania i usuwania elementów z <xref:System.Collections.Concurrent.BlockingCollection%601> blokowania i sposób bez blokowania. Aby uzyskać więcej informacji na temat <xref:System.Collections.Concurrent.BlockingCollection%601>, zobacz [BlockingCollection — Przegląd](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
 Na przykład jak wyliczyć <xref:System.Collections.Concurrent.BlockingCollection%601> dopóki nie jest pusta i nie więcej elementy zostaną dodane, zobacz [jak: Używanie metody ForEach do usuwanie elementów blockingcollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).
  
## <a name="example"></a>Przykład  
 W pierwszym przykładzie pokazano, jak dodawanie i elementy tak, aby operacje spowoduje zablokowanie, jeśli kolekcja jest albo tymczasowo puste (robiąc) lub na maksymalną pojemność (podczas dodawania) lub jeśli upłynął określony limit czasu. Należy pamiętać, że blokowania na maksymalną pojemność jest włączony tylko BlockingCollection zostało utworzone z maksymalną pojemność określony w konstruktorze.  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a>Przykład  
 Ten drugi przykład pokazuje, jak dodawanie i pobieranie elementów tak, aby operacje nie będzie blokować. Jeśli element nie jest obecny, osiągnął maksymalną pojemność w kolekcji ograniczonego lub upłynął limit czasu, a następnie <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> lub <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operacji zwraca wartość false. Dzięki temu wątek wykonywania niektórych użytecznej pracy przez jakiś czas i spróbuj ponownie później do pobrania nowego elementu lub próba dodania tego samego elementu, którego nie można dodać wcześniej. Program ilustruje też sposób implementacji anulowania podczas uzyskiwania dostępu do <xref:System.Collections.Concurrent.BlockingCollection%601>.  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [BlockingCollection — omówienie](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
