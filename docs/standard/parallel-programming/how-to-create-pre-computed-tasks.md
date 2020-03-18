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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123138"
---
# <a name="how-to-create-pre-computed-tasks"></a>Porady: Tworzenie wstępnie obliczonych zadań
W tym dokumencie opisano sposób używania <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody do pobierania wyników operacji pobierania asynchronicznego, które są przechowywane w pamięci podręcznej. Metoda <xref:System.Threading.Tasks.Task.FromResult%2A> zwraca gotowy <xref:System.Threading.Tasks.Task%601> obiekt, który przechowuje podaną wartość jako jego <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość. Ta metoda jest przydatna podczas wykonywania operacji <xref:System.Threading.Tasks.Task%601> asynchronicznej, która <xref:System.Threading.Tasks.Task%601> zwraca obiekt, a wynik tego obiektu jest już obliczany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera ciągi z sieci Web. Definiuje `DownloadStringAsync` metodę. Ta metoda pobiera ciągi z sieci web asynchronicznie. W tym przykładzie <xref:System.Collections.Concurrent.ConcurrentDictionary%602> użyto również obiektu do buforowania wyników poprzednich operacji. Jeśli adres wejściowy jest przechowywany `DownloadStringAsync` w <xref:System.Threading.Tasks.Task.FromResult%2A> tej pamięci <xref:System.Threading.Tasks.Task%601> podręcznej, używa metody do tworzenia obiektu, który przechowuje zawartość pod tym adresem. W `DownloadStringAsync` przeciwnym razie pobiera plik z sieci Web i dodaje wynik do pamięci podręcznej.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 W tym przykładzie oblicza czas, który jest wymagany do pobrania wielu ciągów dwa razy. Drugi zestaw operacji pobierania powinien zająć mniej czasu niż pierwszy zestaw, ponieważ wyniki są przechowywane w pamięci podręcznej. Metoda <xref:System.Threading.Tasks.Task.FromResult%2A> umożliwia `DownloadStringAsync` metody do <xref:System.Threading.Tasks.Task%601> tworzenia obiektów, które posiadają te wstępnie obliczone wyniki.  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
