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
ms.openlocfilehash: 6f829fc0b399f5cfd10d98f6b7439de757674f11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586376"
---
# <a name="reader-writer-locks"></a>Klasa reader_writer_lock
<xref:System.Threading.ReaderWriterLockSlim> Klasa umożliwia wiele wątków jednocześnie odczytać zasobu, ale wymaga wątku oczekiwania na wyłączność w celu zapisu do tego zasobu.  
  
 Można na przykład <xref:System.Threading.ReaderWriterLockSlim> w Twojej aplikacji w celu umożliwienia współpracy synchronizacji między wątków, które uzyskują dostęp do zasobu udostępnionego. Blokady są pobierane <xref:System.Threading.ReaderWriterLockSlim> samej siebie.  
  
 Zgodnie z wątku mechanizm synchronizacji, należy się upewnić, że nie ma wątków obejścia blokowania zapewnianej przez <xref:System.Threading.ReaderWriterLockSlim>. Jest jednym ze sposobów zapewnienia zaprojektować klasy, która hermetyzuje zasób udostępniony. Ta klasa zapewni elementów członkowskich, który dostępu prywatnego udostępnionych zasobów, które korzystają z prywatnej <xref:System.Threading.ReaderWriterLockSlim> do synchronizacji. Na przykład, zobacz przykład kodu <xref:System.Threading.ReaderWriterLockSlim> klasy. <xref:System.Threading.ReaderWriterLockSlim> jest za mało wydajne, ma być używany do synchronizowania poszczególnych obiektów.  
  
 Struktury aplikacji w taki sposób, aby zminimalizować czas trwania odczytu i zapisu. Operacje zapisu długi wpływa na przepływność bezpośrednio ponieważ blokady zapisu jest na wyłączność. Czas odczytu autorów oczekiwania bloku operacji, i jeśli co najmniej jeden wątek oczekuje na dostęp do zapisu, wątków, które żądają dostępu do odczytu będzie również zablokowany.  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Ma dwa reader_writer_lock, <xref:System.Threading.ReaderWriterLockSlim> i <xref:System.Threading.ReaderWriterLock>. <xref:System.Threading.ReaderWriterLockSlim> jest zalecana dla wszystkich nowych wdrożeń. <xref:System.Threading.ReaderWriterLockSlim> przypomina <xref:System.Threading.ReaderWriterLock>, ale jest prostszy zasady rekursji oraz uaktualniania i zmiany na starszą wersję stan blokady. <xref:System.Threading.ReaderWriterLockSlim> pozwala uniknąć wielu przypadkach potencjalnych zakleszczenia. Ponadto wydajność <xref:System.Threading.ReaderWriterLockSlim> jest znacznie lepszą niż <xref:System.Threading.ReaderWriterLock>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.ReaderWriterLockSlim>  
 <xref:System.Threading.ReaderWriterLock>  
 [Wątkowość](../../../docs/standard/threading/index.md)  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)
