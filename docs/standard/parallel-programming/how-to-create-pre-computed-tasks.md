---
title: "Porady: Tworzenie wstępnie obliczonych zadań"
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
helpviewer_keywords: tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4596b28afe48aad4a84a7dd72b4a1d44a9ada8a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-pre-computed-tasks"></a>Porady: Tworzenie wstępnie obliczonych zadań
W tym dokumencie opisano sposób użycia <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metoda pobierania wyników operacji pobierania asynchroniczne, które są przechowywane w pamięci podręcznej. <xref:System.Threading.Tasks.Task.FromResult%2A> Metoda zwraca Zakończono <xref:System.Threading.Tasks.Task%601> obiekt przechowujący podanej wartości jako jego <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości. Ta metoda jest przydatna, gdy wykonujesz operację asynchroniczną, która zwraca <xref:System.Threading.Tasks.Task%601> obiektu i wynik tego <xref:System.Threading.Tasks.Task%601> obiekt już jest obliczana.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobieranie ciągów z sieci web. Definiuje `DownloadStringAsync` metody. Ta metoda pobiera asynchronicznie ciągów z sieci web. W tym przykładzie również używane <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obiektu w pamięci podręcznej wyniki poprzedniej operacji. Jeśli adres wejściowych odbywa się w tej pamięci podręcznej, `DownloadStringAsync` używa <xref:System.Threading.Tasks.Task.FromResult%2A> metodę, aby utworzyć <xref:System.Threading.Tasks.Task%601> obiektu z zawartością pod tym adresem. W przeciwnym razie `DownloadStringAsync` pobiera plik z sieci web i dodaje wynik do pamięci podręcznej.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 W tym przykładzie oblicza czas, który jest wymagany do pobrania wielu ciągów dwa razy. Drugi zestaw operacji pobierania powinno zająć mniej czasu niż pierwszy zestaw, ponieważ wyniki są przechowywane w pamięci podręcznej. <xref:System.Threading.Tasks.Task.FromResult%2A> Metody umożliwia `DownloadStringAsync` metodę w celu utworzenia <xref:System.Threading.Tasks.Task%601> obiektów, które zawierają te wstępnie obliczonych wyników.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `CachedDownloads.cs` (`CachedDownloads.vb` dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **CSC.exe CachedDownloads.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe CachedDownloads.vb**  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie asynchroniczne opartego na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
