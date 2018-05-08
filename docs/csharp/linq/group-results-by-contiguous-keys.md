---
title: Grupy wyników według ciągłych kluczy
description: Jak grupowanie wyników według ciągłych kluczy.
ms.date: 12/1/2016
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: a8d6ac133932a12154d5b23454065144c7652067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
 
