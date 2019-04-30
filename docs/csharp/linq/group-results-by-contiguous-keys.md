---
title: Grupowanie wyników według ciągłych kluczy (LINQ w C#)
description: Jak grupowanie wyników według ciągłych kluczy za pomocą LINQ w C#.
ms.date: 08/14/2018
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: b5753c85bb07be4fc84b78a299eece961969ff9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659907"
---
# <a name="group-results-by-contiguous-keys"></a>Grupowanie wyników według ciągłych kluczy

Poniższy przykład pokazuje, jak należy zgrupować elementy na fragmenty, które reprezentują podciągów ciągłych kluczy. Na przykład załóżmy, że podano następującej pary klucz wartość:

|Key|Wartość|
|---------|-----------|
|ELEMENT|Firma Microsoft|
|ELEMENT|namysłu|
|ELEMENT|który|
|B|Linq|
|C|is|
|ELEMENT|tak naprawdę|
|B|chłodna|
|B|!|

Następujące grupy zostaną utworzone w następującej kolejności:

1. Uważamy, że

2. Linq

3. is

4. tak naprawdę

5. chłodna!

Rozwiązanie jest implementowane jako metodę rozszerzenia, która jest bezpieczna dla wątków i który zwraca wyniki w sposób przesyłania strumieniowego. Innymi słowy tworzy jej grup kiedy przesuwa się on przez sekwencję źródłową. W odróżnieniu od `group` lub `orderby` operatorów, jego może rozpocząć zwracanie grup do obiektu wywołującego przed wszystkie sekwencji został odczytany.

Bezpieczeństwo wątków odbywa się przez utworzenie kopii każdej grupy lub fragmentów, jak sekwencja źródłowa jest postanowiliśmy, zgodnie z objaśnieniem w komentarzach do kodu źródłowego. Jeśli sekwencja źródłowa jest duże sekwencję elementów sąsiadujących, środowisko uruchomieniowe języka wspólnego może zgłaszać <xref:System.OutOfMemoryException>.

## <a name="example"></a>Przykład

Poniższy kod przedstawia metody rozszerzenia i kod klienta, który korzysta z niego:

[!code-csharp[cscsrefContiguousGroups#1](~/samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]

Aby użyć metody rozszerzenia w projekcie, skopiuj `MyExtensions` klasy statycznej do nowego lub istniejącego źródła plik kodu i jeśli jest to konieczne, należy dodać `using` dyrektywy dla przestrzeni nazw, w którym znajduje się.

## <a name="see-also"></a>Zobacz także

- [Language Integrated Query (LINQ)](index.md)
