---
title: '&#39; &lt;typename&gt;&#39; jest to typ delegowany'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords: BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9428f0ac321b90e36d4d987381ed69b6c968894c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a>&#39; &lt;typename&gt;&#39; jest to typ delegowany
"\<typename >" jest typem delegowanym. Delegat konstrukcji zezwala na tylko jedno wyrażenie AddressOf jako listy argumentów. Wyrażenia AddressOf można często zamiast konstrukcji obiektu delegowanego.  
  
 A `New` klauzuli tworzenia wystąpienia klasy delegata dostarcza listy nieprawidłowy argument do konstruktora delegata.  
  
 Można podać tylko jeden `AddressOf` wyrażenie podczas tworzenia nowego wystąpienia obiektu delegowanego.  
  
 Ten błąd może spowodować żadnych argumentów nie jest przekazywany do konstruktora delegata, jeśli przekazać więcej niż jeden argument lub w przypadku przekazania pojedynczy argument który nie jest prawidłową `AddressOf` wyrażenia.  
  
 **Identyfikator błędu:** BC32008  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Użyj pojedynczego `AddressOf` wyrażenia argumentu na liście w klasie obiektów delegowanych `New` klauzuli.  
  
## <a name="see-also"></a>Zobacz też  
 [New — Operator](../../../visual-basic/language-reference/operators/new-operator.md)  
 [AddressOf — Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Obiekty delegowane](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Porady: wywoływanie metody delegata](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
