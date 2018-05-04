---
title: Zestaw znaków (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
ms.openlocfilehash: 5e7886215cac2d9363a9ed68cd03a0fce4374055
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="input-character-set-entity-sql"></a>Zestaw znaków (jednostka SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] akceptuje zakodowane w formacie UTF-16 znaków UNICODE.  
  
 Literały ciągu może zawierać dowolne znaki UTF-16, ujęta w apostrofy. Na przykład N "文字列リテラル". Porównaniu literałów ciągów są używane oryginalnych wartości UTF-16. Na przykład N'ABC "różni się w języku japońskim i Latin strony kodowe.  
  
 Komentarze mogą zawierać dowolne znaki UTF-16.  
  
 Identyfikatory o zmienionym znaczeniu może zawierać dowolne znaki UTF-16, w nawiasach kwadratowych. Na przykład [エスケープされた識別子]. Porównanie identyfikatory UTF-16, znaki ucieczki nie uwzględnia wielkości liter. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] traktuje wersji liter wyglądają tak samo, które pochodzą z różnych kodowe jako różne znaki. Na przykład [ABC] jest odpowiednikiem [abc], jeśli odpowiedni znak z tej samej strony kodowej. Jednak w przypadku tego samego dwóch identyfikatorów z innej strony kodowe, nie są równoważne.  
  
 Biały znak jest dowolny znak odstępu UTF-16.  
  
 Nowy wiersz jest znakiem nowego wiersza znormalizowane UTF-16. Na przykład "\n" i "\r\n" są traktowane jako znaki nowego wiersza, ale "\r" nie jest znakiem nowego wiersza.  
  
 Słowa kluczowe, wyrażenia i znaków interpunkcyjnych może być dowolny znak UTF-16, który normalizuje do Latin. Na przykład wybierz w japońskich strony kodowej jest nieprawidłowy — słowo kluczowe.  
  
 Słowa kluczowe, wyrażenia i znaków interpunkcyjnych może być tylko znaki alfabetu łacińskiego. `SELECT` w japońskich strona kodowa nie jest słowem kluczowym. +,-, *, /, =, (,), ", [,] i innych konstrukcji języka nie podane w tym polu może być tylko znaki alfabetu łacińskiego.  
  
 Proste identyfikatory mogą być tylko znaki alfabetu łacińskiego. Dzięki temu można uniknąć niejednoznaczności podczas porównywania, ponieważ oryginalne wartości są porównywane. Na przykład ABC może być różna w w języku japońskim i Latin strony kodowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
