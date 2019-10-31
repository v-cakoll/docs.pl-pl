---
title: 'Porady: Tworzenie wstępnie obliczonych zadań'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
ms.openlocfilehash: f5d2a70685fe0401d0219b99ada6936ac04691f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123138"
---
# <a name="how-to-create-pre-computed-tasks"></a>Porady: Tworzenie wstępnie obliczonych zadań
W tym dokumencie opisano sposób użycia metody <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> do pobierania wyników asynchronicznych operacji pobierania przechowywanych w pamięci podręcznej. Metoda <xref:System.Threading.Tasks.Task.FromResult%2A> zwraca gotowy obiekt <xref:System.Threading.Tasks.Task%601>, który posiada podaną wartość jako właściwość <xref:System.Threading.Tasks.Task%601.Result%2A>. Ta metoda jest przydatna w przypadku wykonywania operacji asynchronicznej, która zwraca obiekt <xref:System.Threading.Tasks.Task%601>, a wynik tego obiektu <xref:System.Threading.Tasks.Task%601> jest już obliczony.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera ciągi z sieci Web. Definiuje metodę `DownloadStringAsync`. Ta metoda umożliwia pobieranie ciągów z sieci Web asynchronicznie. Ten przykład używa również obiektu <xref:System.Collections.Concurrent.ConcurrentDictionary%602> do buforowania wyników poprzednich operacji. Jeśli adres wejściowy jest przechowywany w tej pamięci podręcznej, `DownloadStringAsync` używa metody <xref:System.Threading.Tasks.Task.FromResult%2A> do tworzenia obiektu <xref:System.Threading.Tasks.Task%601> zawierającego zawartość na tym adresie. W przeciwnym razie `DownloadStringAsync` pobiera plik z sieci Web i dodaje wynik do pamięci podręcznej.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Ten przykład oblicza czas wymagany do pobrania wielu ciągów dwa razy. Drugi zestaw operacji pobierania powinien trwać krócej niż pierwszy zestaw, ponieważ wyniki są przechowywane w pamięci podręcznej. Metoda <xref:System.Threading.Tasks.Task.FromResult%2A> włącza metodę `DownloadStringAsync` do tworzenia obiektów <xref:System.Threading.Tasks.Task%601>, które zawierają te wstępnie obliczone wyniki.  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
