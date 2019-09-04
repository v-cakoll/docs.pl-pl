---
title: Wejściowy zestaw znaków (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
ms.openlocfilehash: b1c6475704ec384800af0b678edd943246bf8044
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250637"
---
# <a name="input-character-set-entity-sql"></a>Wejściowy zestaw znaków (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]akceptuje znaki UNICODE zakodowane w UTF-16.  
  
 Literały ciągu mogą zawierać dowolny znak UTF-16 ujęty w apostrofy. Na przykład N "文字列リテラル". Gdy literały ciągu są porównywane, używane są oryginalne wartości UTF-16. Na przykład N'ABC "różni się w języku japońskim i łacińskim stronie kodowej.  
  
 Komentarze mogą zawierać dowolny znak UTF-16.  
  
 Identyfikatory o zmienionym znaczeniu mogą zawierać dowolny znak UTF-16 ujęty w nawiasy kwadratowe. Na przykład [エスケープされた識別子]. W porównaniu z identyfikatorami ucieczki UTF-16 wielkość liter nie jest rozróżniana. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]traktuje wersje liter, które wyglądają tak samo, ale pochodzą z różnych stron kodowych jako różne znaki. Na przykład [ABC] jest odpowiednikiem [abc], jeśli odpowiednie znaki pochodzą z tej samej strony kodowej. Jeśli jednak te same dwa identyfikatory pochodzą z różnych stron kodowych, nie są równoważne.  
  
 Biały znak jest dowolnego znaku w formacie UTF-16.  
  
 Nowy wiersz jest dowolnym znormalizowanym znakiem nowego wiersza UTF-16. Na przykład "\n" i "\r\n" są uznawane za znaki nowego wiersza, ale "\r" nie jest znakiem nowego wiersza.  
  
 Słowa kluczowe, wyrażenia i interpunkcja mogą być dowolnego znaku UTF-16, który normalizuje do alfabetu łacińskiego. Na przykład wybierz w japońskiej stronie kodowej jest prawidłowym słowem kluczowym.  
  
 Słowa kluczowe, wyrażenia i interpunkcja mogą zawierać tylko znaki łacińskie. `SELECT`w japońskiej stronie kodowej nie jest słowem kluczowym. znaki +,- \*,,/, =, (,), ', [,] i wszelkie inne konstrukcje języka, które nie są ujęte w tym miejscu, mogą być tylko znakami łacińskimi.  
  
 Proste identyfikatory mogą zawierać tylko znaki łacińskie. Pozwala to uniknąć niejednoznaczności podczas porównania, ponieważ oryginalne wartości są porównywane. Na przykład ABC będzie różnić się w japońskiej i Łacińskiej stronie kodowej.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
