---
title: '&#39;Moduł&#39; instrukcje mogą wystąpić tylko na poziomie pliku lub przestrzeni nazw'
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: bdbf8df5942e9df4b9696aeea4e3492121efe21a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54746315"
---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a>&#39;Moduł&#39; instrukcje mogą wystąpić tylko na poziomie pliku lub przestrzeni nazw
`Module` instrukcje musi znajdować się w górnej części pliku źródłowego natychmiast po `Option` i `Imports` instrukcje, atrybutami globalnymi i deklaracje przestrzeni nazw, ale przed innych deklaracji.  
  
 **Identyfikator błędu:** BC30617  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Przenieś `Module` instrukcji na górze pliku deklaracji ani źródła przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcja Module](../../../visual-basic/language-reference/statements/module-statement.md)
