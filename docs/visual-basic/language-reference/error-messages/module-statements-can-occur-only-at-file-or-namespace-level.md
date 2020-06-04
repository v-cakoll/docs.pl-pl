---
title: Instrukcje „Module” mogą wystąpić tylko na poziomie pliku lub przestrzeni nazw
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: d01c30571fc34e142300ac8706c56d5e99175fcf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397210"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a>Instrukcje „Module” mogą wystąpić tylko na poziomie pliku lub przestrzeni nazw
`Module`instrukcje muszą pojawić się w górnej części pliku źródłowego bezpośrednio po `Option` i `Imports` instrukcjach, atrybutach globalnych i deklaracjach przestrzeni nazw, ale przed wszystkimi innymi deklaracjami.  
  
 **Identyfikator błędu:** BC30617  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Przenieś `Module` instrukcję do początku deklaracji przestrzeni nazw lub pliku źródłowego.  
  
## <a name="see-also"></a>Zobacz też

- [Module — Instrukcja](../statements/module-statement.md)
