---
title: Skuteczne stosowanie typów danych (Visual Basic)
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
ms.openlocfilehash: 0b517bca3a9e296eb891e30df91c1d32eb357432
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830126"
---
# <a name="efficient-use-of-data-types-visual-basic"></a>Skuteczne stosowanie typów danych (Visual Basic)
Niezadeklarowany zmienne i zmienne zadeklarowane bez typu danych są przypisywane `Object` typu danych. To ułatwia szybkie pisanie programów, ale może to spowodować ich pracę wolniej.  
  
## <a name="strong-typing"></a>Silne wpisywanie  
 Określenie typów danych dla wszystkich zmiennych jest znany jako *silne wpisywanie*. Za pomocą silne wpisywanie ma kilka zalet:  
  
-   Umożliwia obsługę funkcji IntelliSense dla zmiennych. Dzięki temu można zobaczyć ich właściwości i inne elementy członkowskie podczas wpisywania w kodzie.  
  
-   Wykorzystuje ona sprawdzania typu kompilatora. To połowy instrukcji, które może zakończyć się niepowodzeniem w czasie wykonywania z powodu błędów, takich jak przepełnienia. Przechwytuje także wywołania metod, na obiektach, które nie obsługują je.  
  
-   Powoduje ona szybsze wykonywanie Twojego kodu.  
  
## <a name="most-efficient-data-types"></a>Najbardziej wydajne typy danych  
 W przypadku zmiennych, które nigdy nie zawierają ułamki typy całkowite danych są bardziej wydajne niż nonintegral typów. W języku Visual Basic `Integer` i `UInteger` są najbardziej efektywny sposób typów liczbowych.  
  
 W przypadku liczb ułamkowych `Double` jest najbardziej efektywny sposób typ danych, ponieważ procesorów na platformach bieżącego wykonywania operacji zmiennoprzecinkowej w podwójnej precyzji. Jednak operacje `Double` nie są tak szybko, podobnie jak w przypadku typów całkowitych, takie jak `Integer`.  
  
## <a name="specifying-data-type"></a>Określanie typu danych  
 Użyj [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) Aby zadeklarować zmienną określonego typu. Można jednocześnie określić jego poziom dostępu za pomocą [publicznych](../../../../visual-basic/language-reference/modifiers/public.md), [chronione](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), lub [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe, jak Poniższy przykład.  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a>Konwersja znaków  
 `AscW` i `ChrW` funkcje działają w formacie Unicode. Powinny być używane w preference do `Asc` i `Chr`, który musi przetłumaczyć do i z Unicode.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Typy danych liczbowych](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Korzystanie z funkcji IntelliSense](/visualstudio/ide/using-intellisense)
