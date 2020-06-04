---
title: Erase, instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 31aeaf822bc9c1de59a5c5f68406c6521216ae0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404722"
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
 `Erase`Instrukcja może wystąpić tylko na poziomie procedury. Oznacza to, że można zwolnić tablice wewnątrz procedury, ale nie na poziomie klasy lub modułu.  
  
 `Erase`Instrukcja jest równoznaczna z przypisaniem `Nothing` do każdej zmiennej tablicowej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji, `Erase` Aby wyczyścić dwie tablice i zwolnić pamięć (odpowiednio 1000 i 100 elementów magazynu). `ReDim`Następnie instrukcja przypisuje nowe wystąpienie tablicy do trójwymiarowej tablicy.  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Zobacz też

- [Nothing](../nothing.md)
- [ReDim, instrukcja](redim-statement.md)
