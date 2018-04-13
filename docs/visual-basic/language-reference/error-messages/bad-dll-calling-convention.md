---
title: Nieprawidłowa konwencja wywoływania biblioteki DLL
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa84e82d2fbe1041af56fdd5cc3855efd814ddf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="bad-dll-calling-convention"></a>Nieprawidłowa konwencja wywoływania biblioteki DLL
Argumenty przekazane do biblioteki dołączanej (dynamicznie DLL) musi dokładnie odpowiadać wartości oczekiwanych przez procedurę. Konwencje wywoływania uwzględniać liczbę, typ i kolejność argumentów. Program może wywołania procedury w bibliotece DLL, który jest przekazywany nieprawidłowego typu lub liczba argumentów.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że wszystkie typy argumentów są zgodne z danymi określony w deklaracji procedury, która jest wywoływana.  
  
2.  Upewnij się, że przekazywane taką samą liczbę argumentów wskazanych w deklaracji procedury, które są nawiązywane.  
  
3.  Jeśli procedura DLL oczekuje argumentów według wartości, upewnij się, `ByVal` dla tych argumentów w deklaracji dla procedury określono.  
  
## <a name="see-also"></a>Zobacz też  
 [Error — typy](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Call — instrukcja](../../../visual-basic/language-reference/statements/call-statement.md)  
 [DECLARE — instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
