---
title: 'Instrukcje: deklarowanie wyliczeń'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: c8f228c205c93adf7f2f555dc840a7daac61950b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414456"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Porady: deklarowanie wyliczeń (Visual Basic)
Wyliczenie można utworzyć przy użyciu `Enum` instrukcji w sekcji deklaracji klasy lub modułu. Nie można zadeklarować wyliczenia w ramach metody. Aby określić odpowiedni poziom dostępu, użyj,, `Private` `Protected` `Friend` , lub `Public` .  
  
 `Enum`Typ ma nazwę, typ podstawowy i zestaw pól, z których każdy reprezentuje stałą. Nazwa musi być prawidłowym kwalifikatorem Visual Basic platformy .NET. Typ podstawowy musi być jednym z typów całkowitych — `Byte` , `Short` , `Long` lub `Integer` . Wartość domyślna to `Integer`. Wyliczenia są zawsze silnie wpisane i nie mogą być zamienne z typami liczb całkowitych.  
  
 Wyliczenia nie mogą mieć wartości zmiennoprzecinkowych. Jeśli Wyliczenie ma przypisaną wartość zmiennoprzecinkową z `Option Strict On` , wynik błędu kompilatora. Jeśli `Option Strict` jest `Off` , wartość jest automatycznie konwertowana na `Enum` Typ.  
  
 Aby uzyskać informacje o nazwach i sposobie używania `Imports` instrukcji w celu niepotrzebnej kwalifikacji nazwy, zobacz [wyliczenia i kwalifikowanie nazw](enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Aby zadeklarować Wyliczenie  
  
1. Napisz deklarację zawierającą poziom dostępu do kodu, `Enum` słowo kluczowe i prawidłową nazwę, jak w poniższych przykładach, z których każdy deklaruje inną `Enum` .  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. Zdefiniuj stałe w wyliczeniu. Domyślnie pierwsza stała w wyliczeniu jest inicjowana do `0` , a kolejne stałe są inicjowane do wartości jednej z więcej niż poprzednia stała. Na przykład następujące Wyliczenie, `Days` ,, zawiera stałą o nazwie `Sunday` z wartością `0` , stała o nazwie `Monday` z wartością `1` , stała o nazwie `Tuesday` z wartością `2` i tak dalej.  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. Można jawnie przypisać wartości do stałych w wyliczeniu przy użyciu instrukcji przypisania. Można przypisać dowolną liczbę całkowitą, łącznie z liczbami ujemnymi. Na przykład, możesz chcieć mieć stałe z wartościami mniejszymi od zera, aby reprezentować warunki błędu. W poniższym wyliczeniu, stała `Invalid` ma jawnie przypisaną wartość `–1` , a stała `Sunday` ma przypisaną wartość `0` . Ponieważ jest to pierwsza stała w wyliczeniu, `Saturday` również jest inicjowana do wartości `0` . Wartość `Monday` jest `1` (jedna większa niż wartość `Sunday` ); wartość `Tuesday` jest `2` i tak dalej.  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Aby zadeklarować Wyliczenie jako typ jawny  
  
- Określ typ wyliczenia przy użyciu `As` klauzuli, jak pokazano w poniższym przykładzie.  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenie i kwantyfikacja nazwy](enumerations-and-name-qualification.md)
- [Porady: odwoływanie się do elementu członkowskiego wyliczenia](how-to-refer-to-an-enumeration-member.md)
- [Porady: iterowanie za pomocą wyliczania w Visual Basic](how-to-iterate-through-an-enumeration.md)
- [Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Kiedy stosować wyliczanie](when-to-use-an-enumeration.md)
- [Stałe — Przegląd](constants-overview.md)
- [Stała i typy literałów](constant-and-literal-data-types.md)
- [Stałe i wyliczenia](../../../language-reference/constants-and-enumerations.md)
