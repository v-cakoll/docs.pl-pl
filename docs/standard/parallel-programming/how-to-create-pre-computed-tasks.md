---
title: 'Instrukcje: Tworzenie wstępnie obliczonych zadań'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e68465b6fae39089600457414e7f2a2328f725b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593123"
---
# <a name="how-to-create-pre-computed-tasks"></a>Instrukcje: Tworzenie wstępnie obliczonych zadań
W tym dokumencie opisano, jak używać <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody do pobierania wyników asynchronicznych operacji pobrania, które są przechowywane w pamięci podręcznej. <xref:System.Threading.Tasks.Task.FromResult%2A> Metoda zwraca Zakończono <xref:System.Threading.Tasks.Task%601> obiekt, który przechowuje, podana jest wartość jako jego <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości. Ta metoda jest przydatna, gdy wykonujesz operację asynchroniczną, która zwraca <xref:System.Threading.Tasks.Task%601> obiektu, a wynik tego obiektu <xref:System.Threading.Tasks.Task%601> obiektu jest już obliczony.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera ciągi z sieci web. Definiuje `DownloadStringAsync` metody. Ta metoda asynchronicznie pobiera ciągi z sieci web. W tym przykładzie również użyto <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obiektu w pamięci podręcznej wyników poprzedniej operacji. Jeśli adres wejściowe są przechowywane w tej pamięci podręcznej `DownloadStringAsync` używa <xref:System.Threading.Tasks.Task.FromResult%2A> metody do tworzenia <xref:System.Threading.Tasks.Task%601> obiekt, który przechowuje zawartość pod tym adresem. W przeciwnym razie `DownloadStringAsync` pobiera plik z sieci web i dodaje wynik do pamięci podręcznej.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 W tym przykładzie oblicza czas, który jest wymagany do pobierania wielu ciągów dwa razy. Drugi zestaw operacji pobierania powinna trwać krócej niż pierwszy zestaw, ponieważ wyniki są przechowywane w pamięci podręcznej. <xref:System.Threading.Tasks.Task.FromResult%2A> Metoda umożliwia `DownloadStringAsync` metodę w celu utworzenia <xref:System.Threading.Tasks.Task%601> obiektów, które zawierają te wstępnie obliczone wyniki.  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
