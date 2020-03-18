---
title: Grupowanie wyników według ciągłych kluczy (LINQ w języku C#)
description: Jak grupować wyniki według ciągłych kluczy przy użyciu LINQ w języku C#.
ms.date: 08/14/2018
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: b5753c85bb07be4fc84b78a299eece961969ff9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659907"
---
# <a name="group-results-by-contiguous-keys"></a>Grupowanie wyników według ciągłych kluczy

W poniższym przykładzie pokazano, jak grupować elementy na fragmenty reprezentujące podsekwencje ciągłych kluczy. Załóżmy na przykład, że podano następującą sekwencję par klucz-wartość:

|Klucz|Wartość|
|---------|-----------|
|A|My|
|A|Myśleć|
|A|Że|
|B|Linq|
|C|is|
|A|Naprawdę|
|B|Cool|
|B|!|

W następującej kolejności zostaną utworzone następujące grupy:

1. My, myślimy, że

2. Linq

3. is

4. Naprawdę

5. Cool!

Rozwiązanie jest implementowane jako metoda rozszerzenia, która jest bezpieczna dla wątków i która zwraca jego wyniki w sposób przesyłania strumieniowego. Innymi słowy, tworzy swoje grupy, gdy porusza się po sekwencji źródłowej. W `group` przeciwieństwie `orderby` do lub operatorów można rozpocząć zwracanie grup do obiektu wywołującego przed wszystkie sekwencji został odczytany.

Bezpieczeństwo wątków jest realizowane przez wykonanie kopii każdej grupy lub fragmentu jako sekwencji źródłowej jest iterowana, jak wyjaśniono w komentarzach kodu źródłowego. Jeśli sekwencja źródłowa ma dużą sekwencję sąsiadujących elementów, czas <xref:System.OutOfMemoryException>wykonywania języka wspólnego może zgłosić plik .

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano zarówno metodę rozszerzenia, jak i kod klienta, który go używa:

[!code-csharp[cscsrefContiguousGroups#1](~/samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]

Aby użyć metody rozszerzenia w projekcie, skopiuj `MyExtensions` klasę statyczną do nowego lub `using` istniejącego pliku kodu źródłowego, a jeśli jest to wymagane, dodaj dyrektywę dla obszaru nazw, w którym się znajduje.

## <a name="see-also"></a>Zobacz też

- [Language Integrated Query (LINQ)](index.md)
