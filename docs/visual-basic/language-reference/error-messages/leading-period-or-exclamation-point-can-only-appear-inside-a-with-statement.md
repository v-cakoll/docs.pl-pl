---
title: Początkowe &#39;. &#39; lub &#39;! &#39; może wystąpić tylko wewnątrz &#39;z&#39; — instrukcja
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 7802b8e0aaf3dff83d5bfbe11f0b8bb1b5bb46cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589450"
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a>Początkowe &#39;. &#39; lub &#39;! &#39; może wystąpić tylko wewnątrz &#39;z&#39; — instrukcja
Kropki (.) lub wykrzyknika (!) nie jest który wewnątrz `With` bloku odbywa się bez wyrażenie po lewej stronie. Dostęp do elementu członkowskiego (`.`) i dostęp do elementu członkowskiego słownika (`!`) wymagają wyrażenie określające element, który zawiera element członkowski. Musi występować od razu po lewej stronie metody dostępu lub jako element docelowy `With` blok zawierający dostęp do elementu członkowskiego.  
  
 **Identyfikator błędu:** BC30157  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że `With` bloku jest poprawnie sformatowana.  
  
2.  W przypadku nie `With` bloków, Dodaj wyrażenie w lewo metody dostępu, która ocenia zdefiniowanego elementu zawierający element członkowski.  
  
## <a name="see-also"></a>Zobacz też  
 [Znaki specjalne w kodzie](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 [With...End With, instrukcja](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
