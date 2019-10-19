---
title: Erase — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 7dec2a859f664ee8dcbb305082ec33aeacbaccb4
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583388"
---
# <a name="erase-statement-visual-basic"></a>Erase — Instrukcja (Visual Basic)
Używane do zwalniania zmiennych tablicowych i cofania alokacji pamięci używanej dla ich elementów.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a>Części  
 `arraylist`  
 Wymagany. Lista zmiennych tablicowych, które mają zostać wymazane. Wiele zmiennych jest oddzielonych przecinkami.  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja `Erase` może występować tylko na poziomie procedury. Oznacza to, że można zwolnić tablice wewnątrz procedury, ale nie na poziomie klasy lub modułu.  
  
 Instrukcja `Erase` jest równoważna przypisaniu `Nothing` do każdej zmiennej tablicowej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji `Erase`, aby wyczyścić dwie tablice i zwolnić pamięć (odpowiednio 1000 i 100 elementów magazynu). Następnie instrukcja `ReDim` przypisuje nowe wystąpienie tablicy do trójwymiarowej tablicy.  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Zobacz także

- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [ReDim, instrukcja](../../../visual-basic/language-reference/statements/redim-statement.md)
