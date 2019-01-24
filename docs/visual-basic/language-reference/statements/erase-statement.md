---
title: Erase — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: cab3da4465b4671d203036c2d9bcd40662dc234a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522443"
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
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [ReDim, instrukcja](../../../visual-basic/language-reference/statements/redim-statement.md)
