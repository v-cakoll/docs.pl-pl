---
title: Klasa reader_writer_lock
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ReaderWriterLock class, about ReaderWriterLock class
- threading [.NET Framework], ReaderWriterLock class
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8be9b4eef30333fbbdc26915635d17157176d6fc
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45513504"
---
# <a name="reader-writer-locks"></a>Klasa reader_writer_lock
<xref:System.Threading.ReaderWriterLockSlim> Klasy umożliwia wielu wątków, które można jednocześnie odczytać zasobu, ale wymaga wątku oczekiwania blokady na wyłączność w celu pisania do zasobu.  
  
 Można na przykład <xref:System.Threading.ReaderWriterLockSlim> w aplikacji, aby zapewnić kooperatywnej synchronizacji między wątków, uzyskujących dostęp do zasobu udostępnionego. Blokady są wykonywane <xref:System.Threading.ReaderWriterLockSlim> sam.  
  
 Jak za pomocą dowolnego mechanizmu synchronizacji wątku, należy upewnić się, że żadne wątki obejścia, blokowanie, które są dostarczane przez <xref:System.Threading.ReaderWriterLockSlim>. Jednym ze sposobów, aby upewnić się, to jest projektowanie klasę, która hermetyzuje zasobu udostępnionego. Ta klasa zapewni elementów członkowskich, które mają dostęp do prywatnego zasobu udostępnionego, które używają prywatnego <xref:System.Threading.ReaderWriterLockSlim> synchronizacji. Aby uzyskać przykład, zobacz przykład kodu dla <xref:System.Threading.ReaderWriterLockSlim> klasy. <xref:System.Threading.ReaderWriterLockSlim> jest dostatecznie efektywne, aby używane do synchronizowania poszczególnych obiektów.  
  
 Struktury aplikacji w taki sposób, aby zminimalizować czas trwania odczytu i zapisu. Operacje zapisu długie wpływa na przepływność bezpośrednio ponieważ blokada zapisywania jest na wyłączność. Długi przeczytaj autorzy oczekiwania bloku operacji, a jeśli co najmniej jeden wątek czeka na dostęp do zapisu, wątki, które żądają dostępu do odczytu będą mieć również.  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Ma dwa reader_writer_lock, <xref:System.Threading.ReaderWriterLockSlim> i <xref:System.Threading.ReaderWriterLock>. <xref:System.Threading.ReaderWriterLockSlim> jest zalecana dla wszystkich nowych wdrożeń. <xref:System.Threading.ReaderWriterLockSlim> jest podobny do <xref:System.Threading.ReaderWriterLock>, ale oferuje uproszczone, zasady rekursji oraz uaktualnianie i zmiany na starszą wersję stan blokady. <xref:System.Threading.ReaderWriterLockSlim> pozwala uniknąć wielu przypadkach potencjalnych zakleszczenia. Ponadto wydajność <xref:System.Threading.ReaderWriterLockSlim> jest znacznie lepsze niż <xref:System.Threading.ReaderWriterLock>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.ReaderWriterLockSlim>  
- <xref:System.Threading.ReaderWriterLock>  
- [Wątkowość](../../../docs/standard/threading/index.md)  
- [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)
