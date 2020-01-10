---
title: 'Porady: dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
ms.openlocfilehash: 3f4270d2ec71421bad8974a3e5cd8f1d65db3b74
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711301"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a>Porady: dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection
Ten przykład pokazuje, jak dodawać i usuwać elementy z <xref:System.Collections.Concurrent.BlockingCollection%601> zarówno w bloku blokowania, jak i bez blokowania. Aby uzyskać więcej informacji na temat <xref:System.Collections.Concurrent.BlockingCollection%601>, zobacz [Omówienie BlockingCollection](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
 Aby zapoznać się z przykładem, jak wyliczyć <xref:System.Collections.Concurrent.BlockingCollection%601>, dopóki nie zostanie on pusty i nie zostaną dodane żadne dodatkowe elementy, zobacz [How to: use foreach by Remove Items in BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).
  
## <a name="example"></a>Przykład  
 Ten pierwszy przykład pokazuje, jak dodawać i podejmować elementy, aby operacje były blokowane, jeśli kolekcja jest tymczasowo pusta (podczas wykonywania) lub przy maksymalnej pojemności (podczas dodawania) lub w przypadku, gdy upłynął określony limit czasu. Należy zauważyć, że blokowanie dla maksymalnej pojemności jest włączone tylko wtedy, gdy BlockingCollection został utworzony z maksymalną pojemnością określoną w konstruktorze.  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a>Przykład  
 Ten drugi przykład pokazuje, jak dodawać i podejmować elementy, aby nie blokowały operacji. Jeśli żaden element nie jest obecny, osiągnięto maksymalną pojemność w powiązanej kolekcji lub upłynął limit czasu, a następnie operacja <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> lub <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> zwraca wartość false. Dzięki temu wątek może wykonać inne przydatne działania przez pewien czas, a następnie spróbować ponownie później, aby pobrać nowy element, lub spróbować dodać ten sam element, którego nie można dodać wcześniej. Program demonstruje również sposób implementacji anulowania podczas uzyskiwania dostępu do <xref:System.Collections.Concurrent.BlockingCollection%601>.  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [BlockingCollection — omówienie](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
