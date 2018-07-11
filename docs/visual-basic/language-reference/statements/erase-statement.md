---
title: Erase — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 317e2a7dc5facb08388f3a3e635734e4daed5eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601796"
---
# <a name="erase-statement-visual-basic"></a>Erase — Instrukcja (Visual Basic)
Służy do zwalniania zmiennych tablicy i cofania przydziału pamięci używanej dla ich elementów.  
  
## <a name="syntax"></a>Składnia  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a>Części  
 `arraylist`  
 Wymagana. Lista zmiennych tablicowych usunięcie. Wiele zmiennych są oddzielone przecinkami.  
  
## <a name="remarks"></a>Uwagi  
 `Erase` Instrukcja może wystąpić tylko na poziomie procedury. Oznacza to, że można zwolnić tablice wewnątrz procedury, ale nie na poziomie klasę lub moduł.  
  
 Instrukcja `Erase` jest równoważna z przypisywaniem wartości `Nothing` do każdej zmiennej tablicy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Erase` instrukcji, aby wyczyścić dwiema tablicami i zwolnić pamięć, ich (1000 i 100 elementów magazynu odpowiednio). `ReDim` Instrukcji następnie przypisuje nowego wystąpienia tablicy tablicą trójwymiarową.  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Nothing](../../../visual-basic/language-reference/nothing.md)  
 [ReDim, instrukcja](../../../visual-basic/language-reference/statements/redim-statement.md)
