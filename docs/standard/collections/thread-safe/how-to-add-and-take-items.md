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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711301"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a>Porady: dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection
W tym przykładzie pokazano, jak <xref:System.Collections.Concurrent.BlockingCollection%601> dodawać i usuwać elementy z pliku w sposób blokujący i nieblokujący. Aby uzyskać <xref:System.Collections.Concurrent.BlockingCollection%601>więcej informacji na temat , zobacz [BlockingCollection Omówienie](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
 Na przykład jak wyliczyć a <xref:System.Collections.Concurrent.BlockingCollection%601> dopóki nie jest pusty i nie więcej elementów zostaną dodane, zobacz [Jak: Użyj ForEach usunąć elementy w BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).
  
## <a name="example"></a>Przykład  
 W tym pierwszym przykładzie pokazano, jak dodawać i przyjmować elementy, tak aby operacje blokowały, jeśli kolekcja jest tymczasowo pusta (podczas przyjmowania) lub przy maksymalnej pojemności (podczas dodawania) lub jeśli upłynął określony okres czasu. Należy zauważyć, że blokowanie maksymalnej pojemności jest włączona tylko wtedy, gdy BlockingCollection został utworzony z maksymalną pojemnością określoną w konstruktorze.  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a>Przykład  
 W tym drugim przykładzie pokazano, jak dodawać i przyjmować elementy, aby operacje nie blokowały. Jeśli żaden element nie jest obecny, osiągnięto maksymalną pojemność ograniczonej kolekcji lub upłynął <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> okres czasu, a następnie lub operacja zwraca false. Dzięki temu wątek do wykonywania innych przydatnych prac na chwilę, a następnie spróbuj ponownie później, aby pobrać nowy element lub spróbuj dodać ten sam element, który nie może być dodany wcześniej. Program pokazuje również, jak zaimplementować <xref:System.Collections.Concurrent.BlockingCollection%601>anulowanie podczas uzyskiwania dostępu do pliku .  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [BlockingCollection — Przegląd](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
