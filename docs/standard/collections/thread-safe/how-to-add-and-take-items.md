---
title: "Porady: dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c19e78ca05b339898a27a1e5f98412224586aae9
ms.sourcegitcommit: c3ebb11a66e85a465c9ba2c42592222630b7ff9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a>Porady: dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection
W tym przykładzie pokazano, jak dodawać i usuwać elementy z <xref:System.Collections.Concurrent.BlockingCollection%601> blokujący i sposób bez blokowania. Aby uzyskać więcej informacji na temat <xref:System.Collections.Concurrent.BlockingCollection%601>, zobacz [BlockingCollection — Przegląd](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
 Na przykład jak wyliczyć <xref:System.Collections.Concurrent.BlockingCollection%601> do czasu jest pusty i zostanie dodany ma więcej elementów, zobacz [porady: użycie ForEach do usuwanie elementów blockingcollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).
  
## <a name="example"></a>Przykład  
 Pierwszym przykładzie pokazano sposób, aby dodać, a następnie elementy, aby operacje zablokują kolekcji jest tymczasowo pusta (podejmując) lub w maksymalnej pojemności (podczas dodawania) lub jeśli upłynął określony limit czasu. Należy pamiętać, że blokowania na maksymalną pojemność jest włączona tylko po utworzeniu kolekcji BlockingCollection o pojemności maksymalnej określonym w konstruktorze.  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a>Przykład  
 W tym drugim przykładzie przedstawiono sposób Dodawanie i pobieranie elementów, aby operacje nie powoduje blokowania. Jeśli element nie jest obecny, osiągnięto maksymalną pojemność kolekcji ograniczonego lub upłynął limit czasu, a następnie <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> lub <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operacji zwraca wartość false. Pozwala to na inne przydatne pracy na chwilę i spróbuj ponownie później do pobrania nowego elementu, lub spróbuj dodać ten sam element, którego nie można dodać wcześniej wątku. Program również pokazuje, jak wdrożyć anulowania podczas uzyskiwania dostępu do <xref:System.Collections.Concurrent.BlockingCollection%601>.  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [BlockingCollection — omówienie](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
