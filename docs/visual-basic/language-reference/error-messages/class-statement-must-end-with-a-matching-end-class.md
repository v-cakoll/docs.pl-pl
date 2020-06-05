---
title: Instrukcja „Class” musi być zakończona odpowiadającą jej instrukcją „End Class”
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 01c231f577d21028e9ef92f37c7ac5f7f1fe2aa3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415391"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a>Instrukcja „Class” musi być zakończona odpowiadającą jej instrukcją „End Class”
`Class`służy do inicjowania `Class` bloku; w związku z tym może wystąpić tylko na początku bloku, z odpowiadającą instrukcją `End Class` kończącą blok. Istnieje instrukcja nadmiarowa `Class` lub nie zakończono `Class` blokady przy użyciu `End Class` .  
  
 **Identyfikator błędu:** BC30481  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Znajdź i Usuń niezbędną `Class` instrukcję.  
  
- Zakończ `Class` blok ze zgodnym elementem `End Class` .  
  
## <a name="see-also"></a>Zobacz też

- [End — \<keyword> instrukcja](../statements/end-keyword-statement.md)
- [Class, instrukcja](../statements/class-statement.md)
