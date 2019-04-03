---
title: Erase — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: bf3eb6476dc1485faeddab475f29e508175d3378
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840409"
---
# <a name="erase-statement-visual-basic"></a>Erase — Instrukcja (Visual Basic)
Służy do zwalniania zmiennych tablicy i cofania przydziału pamięci używanej dla ich elementów.  
  
## <a name="syntax"></a>Składnia  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a>Części  
 `arraylist`  
 Wymagane. Lista zmiennych tablicy do usunięcia. W przypadku wielu zmiennych są one oddzielane przecinkami.  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja `Erase` może wystąpić tylko na poziomie procedury. Oznacza to, że można zwolnić tablice wewnątrz procedury, ale nie na poziomie klasy ani modułu.  
  
 Instrukcja `Erase` jest równoważna z przypisywaniem wartości `Nothing` do każdej zmiennej tablicy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto instrukcji `Erase`, aby wyczyścić dwie tablice i zwolnić ich pamięć (odpowiednio 1000 i 100 elementów pamięci). Następnie instrukcja `ReDim` przypisuje nową instancję tablicy do tablicy trójwymiarowej.  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Zobacz także

- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [ReDim, instrukcja](../../../visual-basic/language-reference/statements/redim-statement.md)
