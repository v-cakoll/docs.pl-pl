---
title: Typy metod manipulowania ciągami
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: aba9af9c699cf8d07862c5d2967902bec1623500
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363762"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Typy metod manipulowania ciągami w Visual Basic
Istnieje kilka różnych sposobów analizowania ciągów i manipulowania nimi. Niektóre metody są częścią języka Visual Basic, a inne są związane z `String` klasą.  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic język i .NET Framework  
 Metody Visual Basic są używane jako funkcje związane z językiem. Mogą być używane bez kwalifikacji w kodzie. W poniższym przykładzie przedstawiono typowe użycie Visual Basic polecenie manipulowania ciągiem:  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 W tym przykładzie `Mid` Funkcja wykonuje operację bezpośrednią na `aString` i przypisuje wartość do `bString` .  
  
 Aby zapoznać się z listą metod manipulowania ciągami Visual Basic, zobacz [Podsumowanie manipulowania ciągami](../../../language-reference/keywords/string-manipulation-summary.md).  
  
### <a name="shared-methods-and-instance-methods"></a>Metody udostępnione i metody wystąpień  
 Można również manipulować ciągami przy użyciu metod `String` klasy. Istnieją dwa typy metod w `String` : metody *Shared* i metody *wystąpień* .  
  
#### <a name="shared-methods"></a>Metody udostępnione  
 Metoda wspólna to metoda, która jest uruchamiana z `String` samej klasy i nie wymaga wystąpienia tej klasy do działania. Metody te mogą być kwalifikowana nazwą klasy ( `String` ), a nie z wystąpieniem `String` klasy. Przykład:  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 W poprzednim przykładzie <xref:System.String.Copy%2A?displayProperty=nameWithType> Metoda jest metodą statyczną, która operuje na wyrażeniu, które jest określone, i przypisuje wartość wyniki do `bString` .  
  
#### <a name="instance-methods"></a>Metody wystąpień  
 Metody wystąpień, które różnią się od określonego wystąpienia `String` i muszą być kwalifikowane przy użyciu nazwy wystąpienia. Przykład:  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 W tym przykładzie <xref:System.String.Substring%2A?displayProperty=nameWithType> Metoda jest metodą wystąpienia `String` (to jest, `aString` ). Wykonuje operację na `aString` i przypisuje tę wartość do `bString` .  
  
 Aby uzyskać więcej informacji, zobacz dokumentację <xref:System.String> klasy.  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do ciągów w Visual Basic](introduction-to-strings.md)
