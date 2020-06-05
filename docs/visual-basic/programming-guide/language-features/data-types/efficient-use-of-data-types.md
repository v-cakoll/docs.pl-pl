---
title: Skuteczne stosowanie typów danych
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: 0de02840cb18fde16134ef43df9d63abb503c979
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394174"
---
# <a name="efficient-use-of-data-types-visual-basic"></a>Skuteczne stosowanie typów danych (Visual Basic)
Niezadeklarowane zmienne i zmienne zadeklarowane bez typu danych są przypisywane do `Object` typu danych. Ułatwia to szybkie pisanie programów, ale może spowodować spowolnienie ich wykonywania.

## <a name="strong-typing"></a>Silne wpisywanie
 Określanie typów danych dla wszystkich zmiennych jest znane jako *silne wpisywanie*. Używanie silnego wpisywania ma kilka zalet:

- Umożliwia obsługę technologii IntelliSense dla zmiennych. Dzięki temu można zobaczyć swoje właściwości i innych członków podczas wpisywania kodu.

- Wykorzystuje ona sprawdzanie typów kompilatora. Ta instrukcja przechwytuje instrukcje, które mogą zakończyć się niepowodzeniem w czasie wykonywania z powodu błędów, takich jak przepełnienie. Przechwytuje również wywołania metod na obiektach, które ich nie obsługują.

- Skutkuje to przyspieszeniem wykonywania kodu.

## <a name="most-efficient-data-types"></a>Najbardziej wydajne typy danych
 W przypadku zmiennych, które nigdy nie zawierają ułamków, typy danych całkowitych są bardziej wydajne niż typy niecałkowite. W Visual Basic `Integer` i `UInteger` to najbardziej wydajne typy liczbowe.

 W przypadku liczb ułamkowych `Double` jest najbardziej wydajnym typem danych, ponieważ procesory na bieżących platformach wykonują operacje zmiennoprzecinkowe w podwójnej precyzji. Jednak operacje z `Double` nie są tak szybkie jak w przypadku typów całkowitych, takich jak `Integer` .

## <a name="specifying-data-type"></a>Określanie typu danych
 Użyj [instrukcji Dim](../../../language-reference/statements/dim-statement.md) , aby zadeklarować zmienną określonego typu. Możesz jednocześnie określić swój poziom dostępu przy użyciu słowa kluczowego [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md)lub [Private](../../../language-reference/modifiers/private.md) , jak w poniższym przykładzie.

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a>Konwersja znaków
 `AscW`Funkcje i `ChrW` działają w formacie Unicode. Należy używać ich z preferencjami do `Asc` i `Chr` , które muszą przełożyć na i z wartości Unicode.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Typy danych](index.md)
- [Typy danych liczbowych](numeric-data-types.md)
- [Deklaracja zmiennej](../variables/variable-declaration.md)
- [Korzystanie z IntelliSense](/visualstudio/ide/using-intellisense)
