---
title: "Grupy wyników według ciągłych kluczy"
description: "Jak grupowanie wyników według ciągłych kluczy."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: cdd06a6fad037291bbc5aa011b47bb668fa2f062
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="group-results-by-contiguous-keys"></a>Grupy wyników według ciągłych kluczy

Poniższy przykład przedstawia sposób grupowania elementów na fragmenty, które reprezentują podciągów ciągłych kluczy. Załóżmy na przykład, zostanie wyświetlony następujący ciąg par klucz wartość:  
  
|Key|Wartość|  
|---------|-----------|  
|ELEMENT|Firma Microsoft|  
|ELEMENT|Pomyśl|  
|ELEMENT|który|  
|B|LINQ|  
|C|is|  
|ELEMENT|naprawdę|  
|B|Cool|  
|B|!|  
  
 Następujące grupy zostanie utworzony w następującej kolejności:  
  
1.  Firma Microsoft, wziąć pod uwagę, że  
  
2.  LINQ  
  
3.  is  
  
4.  naprawdę  
  
5.  Cool!  
  
 Rozwiązanie jest implementowany jako metodę rozszerzenia, który jest wątkowo i które zwraca wyniki w sposób przesyłania strumieniowego. Innymi słowy tworzy jej grup przesyłane za pośrednictwem sekwencji źródłowej. W odróżnieniu od `group` lub `orderby` operatorów, jego można rozpocząć zwracanie grupy do obiektu wywołującego przed wszystkie sekwencji została przeczytana.  
  
 Bezpieczeństwo wątków jest realizowane przez utworzenie kopii każdej grupy lub fragmentu, jak sekwencji źródłowej jest iterowane, zgodnie z objaśnieniem w komentarze w kodzie źródłowym. Jeśli sekwencji źródłowej ma duże sekwencję elementów ciągły, środowisko uruchomieniowe języka wspólnego może zgłaszać <xref:System.OutOfMemoryException>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano zarówno metodę rozszerzenia, jak i kodu klienta, który korzysta z niego.  
  
 [!code-csharp[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 Aby używać metody rozszerzenia w projekcie, skopiuj `MyExtensions` klasy statycznej do nowego lub istniejącego źródła code pliku i w razie potrzeby, Dodaj `using` dyrektywy dla przestrzeni nazw, w którym znajduje się.  
  
## <a name="see-also"></a>Zobacz także  
 [Wyrażenia zapytań LINQ](index.md)  
 
