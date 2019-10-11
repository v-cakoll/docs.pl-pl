---
title: Parametrów typu nie można używać jako kwalifikatorów
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 3ff4b189539bf119351a94dabadd596c336ac723
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250329"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>Parametrów typu nie można używać jako kwalifikatorów

Element programistyczny jest kwalifikowana za pomocą ciągu kwalifikacji, który zawiera parametr typu.

Parametr typu reprezentuje wymaganie dla typu, który ma zostać dostarczony podczas konstruowania typu ogólnego. Nie reprezentuje określonego zdefiniowanego typu. Ciąg kwalifikacji musi zawierać tylko elementy, które są zdefiniowane w czasie kompilacji.

Następujący kod może generować ten błąd:

```vb  
Public Function CheckText(Of c As System.Windows.Forms.Control)(
    badText As String) As Boolean
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.
End Function  
```  
  
 **Identyfikator błędu:** BC32098  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Usuń parametr typu z ciągu kwalifikacji lub zastąp go zdefiniowanym typem.  
  
2. Jeśli musisz użyć skonstruowanego typu do zlokalizowania kwalifikowanego elementu programistycznego, musisz użyć dodatkowej logiki programu.  
  
## <a name="see-also"></a>Zobacz także

- [Odwołania do zadeklarowanych elementów](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Typy ogólne w Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Lista typów](../statements/type-list.md)
