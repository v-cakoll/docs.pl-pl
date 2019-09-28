---
title: Parametrów typu nie można używać jako kwalifikatorów
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 88b5f365c47b98964d9f5a0d22a941d85dcfb95f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592136"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>Parametrów typu nie można używać jako kwalifikatorów
Element programistyczny jest kwalifikowana za pomocą ciągu kwalifikacji, który zawiera parametr typu.  
  
 Parametr typu reprezentuje wymaganie dla typu, który ma zostać dostarczony podczas konstruowania typu ogólnego. Nie reprezentuje określonego zdefiniowanego typu. Ciąg kwalifikacji musi zawierać tylko elementy, które są zdefiniowane w czasie kompilacji.  
  
 Poniższe instrukcje mogą generować ten błąd.  
  
```vb  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **Identyfikator błędu:** BC32098  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Usuń parametr typu z ciągu kwalifikacji lub zastąp go zdefiniowanym typem.  
  
2. Jeśli musisz użyć skonstruowanego typu do zlokalizowania kwalifikowanego elementu programistycznego, musisz użyć dodatkowej logiki programu.  
  
## <a name="see-also"></a>Zobacz także

- [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Lista typów](../../../visual-basic/language-reference/statements/type-list.md)
