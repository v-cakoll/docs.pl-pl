---
title: Zestaw
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 7d313dee1015362bd0215ed98ab7e898312cfbcd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373163"
---
# <a name="assembly-visual-basic"></a>Assembly (Visual Basic)
Określa, że atrybut na początku pliku źródłowego dotyczy całego zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Wiele atrybutów odnosi się do pojedynczego elementu programistycznego, takiego jak Klasa lub właściwość. Ten atrybut jest stosowany przez dołączenie bloku atrybutu w nawiasach kątowych ( `< >` ) bezpośrednio do instrukcji deklaracji.  
  
 Jeśli atrybut dotyczy nie tylko następującego elementu, ale do całego zestawu, umieścisz blok atrybutu na początku pliku źródłowego i zidentyfikujesz atrybut za pomocą `Assembly` słowa kluczowego. Jeśli dotyczy bieżącego modułu zestawu, należy użyć słowa kluczowego [modułu](module-keyword.md) .  
  
 Można również zastosować atrybut do zestawu w pliku AssemblyInfo. vb, w tym przypadku nie trzeba używać bloku atrybutu w głównym pliku kodu źródłowego.  
  
## <a name="see-also"></a>Zobacz też

- [Elementu\<keyword>](module-keyword.md)
- [Przegląd atrybutów](../../programming-guide/concepts/attributes/index.md)
