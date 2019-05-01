---
title: Instrukcje „Module” mogą wystąpić tylko na poziomie pliku lub przestrzeni nazw
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: bf0239422fb5a98e4670aea407f684753d3a7ea4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920864"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a>Instrukcje „Module” mogą wystąpić tylko na poziomie pliku lub przestrzeni nazw
`Module` instrukcje musi znajdować się w górnej części pliku źródłowego natychmiast po `Option` i `Imports` instrukcje, atrybutami globalnymi i deklaracje przestrzeni nazw, ale przed innych deklaracji.  
  
 **Identyfikator błędu:** BC30617  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Przenieś `Module` instrukcji na górze pliku deklaracji ani źródła przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcja Module](../../../visual-basic/language-reference/statements/module-statement.md)
