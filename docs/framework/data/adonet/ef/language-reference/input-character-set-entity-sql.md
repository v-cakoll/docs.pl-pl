---
title: "Zestaw znaków (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8d75d8c96d1cc028bed8beea16e2728e5654a12c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="input-character-set-entity-sql"></a>Zestaw znaków (jednostka SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]akceptuje zakodowane w formacie UTF-16 znaków UNICODE.  
  
 Literały ciągu może zawierać dowolne znaki UTF-16, ujęta w apostrofy. Na przykład N "文字列リテラル". Porównaniu literałów ciągów są używane oryginalnych wartości UTF-16. Na przykład N'ABC "różni się w języku japońskim i Latin strony kodowe.  
  
 Komentarze mogą zawierać dowolne znaki UTF-16.  
  
 Identyfikatory o zmienionym znaczeniu może zawierać dowolne znaki UTF-16, w nawiasach kwadratowych. Na przykład [エスケープされた識別子]. Porównanie identyfikatory UTF-16, znaki ucieczki nie uwzględnia wielkości liter. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]traktuje wersji liter wyglądają tak samo, które pochodzą z różnych kodowe jako różne znaki. Na przykład [ABC] jest odpowiednikiem [abc], jeśli odpowiedni znak z tej samej strony kodowej. Jednak w przypadku tego samego dwóch identyfikatorów z innej strony kodowe, nie są równoważne.  
  
 Biały znak jest dowolny znak odstępu UTF-16.  
  
 Nowy wiersz jest znakiem nowego wiersza znormalizowane UTF-16. Na przykład "\n" i "\r\n" są traktowane jako znaki nowego wiersza, ale "\r" nie jest znakiem nowego wiersza.  
  
 Słowa kluczowe, wyrażenia i znaków interpunkcyjnych może być dowolny znak UTF-16, który normalizuje do Latin. Na przykład wybierz w japońskich strony kodowej jest nieprawidłowy — słowo kluczowe.  
  
 Słowa kluczowe, wyrażenia i znaków interpunkcyjnych może być tylko znaki alfabetu łacińskiego. `SELECT`w japońskich strona kodowa nie jest słowem kluczowym. +,-, *, /, =, (,), ", [,] i innych konstrukcji języka nie podane w tym polu może być tylko znaki alfabetu łacińskiego.  
  
 Proste identyfikatory mogą być tylko znaki alfabetu łacińskiego. Dzięki temu można uniknąć niejednoznaczności podczas porównywania, ponieważ oryginalne wartości są porównywane. Na przykład ABC może być różna w w języku japońskim i Latin strony kodowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
