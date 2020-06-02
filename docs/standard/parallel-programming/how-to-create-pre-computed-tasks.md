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
ms.openlocfilehash: 88f0782380d21858bc5dd0fc0fbf63bbf85403b8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289996"
---
# <a name="how-to-create-pre-computed-tasks"></a>Instrukcje: Tworzenie wstępnie obliczonych zadań
W tym dokumencie opisano sposób użycia <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody do pobierania wyników asynchronicznych operacji pobierania przechowywanych w pamięci podręcznej. <xref:System.Threading.Tasks.Task.FromResult%2A>Metoda zwraca gotowy <xref:System.Threading.Tasks.Task%601> obiekt, który posiada podaną wartość jako <xref:System.Threading.Tasks.Task%601.Result%2A> Właściwość. Ta metoda jest przydatna w przypadku wykonywania operacji asynchronicznej, która zwraca <xref:System.Threading.Tasks.Task%601> obiekt, a wynik tego <xref:System.Threading.Tasks.Task%601> obiektu jest już obliczany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera ciągi z sieci Web. Definiuje `DownloadStringAsync` metodę. Ta metoda umożliwia pobieranie ciągów z sieci Web asynchronicznie. Ten przykład używa również <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obiektu do buforowania wyników poprzednich operacji. Jeśli adres wejściowy jest przechowywany w tej pamięci podręcznej, `DownloadStringAsync` używa <xref:System.Threading.Tasks.Task.FromResult%2A> metody, aby utworzyć <xref:System.Threading.Tasks.Task%601> obiekt, który przechowuje zawartość pod tym adresem. W przeciwnym razie program `DownloadStringAsync` pobierze plik z sieci Web i doda wynik do pamięci podręcznej.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Ten przykład oblicza czas wymagany do pobrania wielu ciągów dwa razy. Drugi zestaw operacji pobierania powinien trwać krócej niż pierwszy zestaw, ponieważ wyniki są przechowywane w pamięci podręcznej. <xref:System.Threading.Tasks.Task.FromResult%2A>Metoda umożliwia `DownloadStringAsync` metodzie tworzenie <xref:System.Threading.Tasks.Task%601> obiektów, które zawierają te wstępnie obliczone wyniki.  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne oparte na zadaniach](task-based-asynchronous-programming.md)
