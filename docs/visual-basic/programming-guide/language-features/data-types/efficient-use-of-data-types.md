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
ms.openlocfilehash: 6e71c4e2225bbcde3bb2bd20ae098f5600990051
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647764"
---
# <a name="efficient-use-of-data-types-visual-basic"></a>Skuteczne stosowanie typów danych (Visual Basic)
Niezadeklarowany zmiennych i zmiennych zadeklarowanych bez typu danych są przypisane `Object` — typ danych. To ułatwia szybkie pisania programów, ale może to spowodować ich do wykonania wolniej.  
  
## <a name="strong-typing"></a>Silne wpisywanie  
 Określenie typów danych dla wszystkich zmiennych nosi nazwę *silne wpisywanie*. Przy użyciu silne wpisywanie ma kilka zalet:  
  
-   Umożliwia obsługę funkcji IntelliSense dla zmiennych. Dzięki temu można zobaczyć ich właściwości oraz o innych elementach członkowskich jako typu w kodzie.  
  
-   Trwa zaletą Sprawdzanie typu kompilatora. To połowy instrukcji, które może zakończyć się niepowodzeniem w czasie wykonywania z powodu błędów, takich jak przepełnienia. Przechwytuje również wywołania metod, w obiektach, które nie są obsługiwane.  
  
-   Wynikiem szybsze wykonywanie kodu.  
  
## <a name="most-efficient-data-types"></a>Najbardziej efektywne typy danych  
 Zmienne, które nigdy nie zawierają ułamków typy całkowite danych są bardziej wydajne niż nonintegral typów. W języku Visual Basic `Integer` i `UInteger` są najbardziej efektywny typy liczbowe.  
  
 Liczb ułamkowych `Double` jest najbardziej wydajnym typu danych, ponieważ procesorów na platformach bieżącego wykonywania operacji zmiennoprzecinkowych w podwójnej precyzji. Jednak operacje przy użyciu `Double` nie są tak szybko, jak w przypadku typów całkowitych, takich jak `Integer`.  
  
## <a name="specifying-data-type"></a>Określanie typu danych  
 Użyj [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) Aby zadeklarować zmienną określonego typu. Można jednocześnie określić jego poziom dostępu za pomocą [publicznego](../../../../visual-basic/language-reference/modifiers/public.md), [chronione](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), lub [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe, jak w Poniższy przykład.  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a>Konwersja znaków  
 `AscW` i `ChrW` funkcje działają w standardzie Unicode. Powinny być używane w preference do `Asc` i `Chr`, które muszą tłumaczyć do i z Unicode.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Typy danych liczbowych](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Korzystanie z funkcji IntelliSense](/visualstudio/ide/using-intellisense)
