---
title: Erase — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 6d2052ceccbecd772c4e4bb18052aed74223a36e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343699"
---
# <a name="erase-statement-visual-basic"></a>Erase — Instrukcja (Visual Basic)
Służy do zwalniania zmiennych tablicy i cofania przydziału pamięci używanej dla ich elementów.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a>Części  
 `arraylist`  
 Wymagana. Lista zmiennych tablicy do usunięcia. Wiele zmiennych rozdziela się przecinkami.  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja `Erase` może występować tylko na poziomie procedury. Oznacza to, że można zwolnić tablice wewnątrz procedury, ale nie na poziomie klasy ani modułu.  
  
 Instrukcja `Erase` jest równoważna przypisaniu `Nothing` do każdej zmiennej tablicowej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji `Erase`, aby wyczyścić dwie tablice i zwolnić pamięć (odpowiednio 1000 i 100 elementów magazynu). Następnie instrukcja `ReDim` przypisuje nowe wystąpienie tablicy do trójwymiarowej tablicy.  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Zobacz także

- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [ReDim, instrukcja](../../../visual-basic/language-reference/statements/redim-statement.md)
