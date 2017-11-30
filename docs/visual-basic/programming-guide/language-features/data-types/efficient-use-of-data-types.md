---
title: "Skuteczne stosowanie typów danych (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e13a1d61aacb06eb336c39aab969847127dfc67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="efficient-use-of-data-types-visual-basic"></a>Skuteczne stosowanie typów danych (Visual Basic)
Niezadeklarowany zmiennych i zmiennych zadeklarowanych bez typu danych są przypisane `Object` — typ danych. To ułatwia szybkie pisania programów, ale może to spowodować ich do wykonania wolniej.  
  
## <a name="strong-typing"></a>Silne wpisywanie  
 Określenie typów danych dla wszystkich zmiennych nosi nazwę *silne wpisywanie*. Przy użyciu silne wpisywanie ma kilka zalet:  
  
-   Umożliwia obsługę funkcji IntelliSense dla zmiennych. Dzięki temu można zobaczyć ich właściwości oraz o innych elementach członkowskich jako typu w kodzie.  
  
-   Trwa zaletą Sprawdzanie typu kompilatora. To połowy instrukcji, które może zakończyć się niepowodzeniem w czasie wykonywania z powodu błędów, takich jak przepełnienia. Przechwytuje również wywołania metod, w obiektach, które nie są obsługiwane.  
  
-   Wynikiem szybsze wykonywanie kodu.  
  
## <a name="most-efficient-data-types"></a>Najbardziej efektywne typy danych  
 Zmienne, które nigdy nie zawierają ułamków typy całkowite danych są bardziej wydajne niż nonintegral typów. W [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], `Integer` i `UInteger` są najbardziej efektywny typy liczbowe.  
  
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
 [Numeryczne typy danych](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Korzystanie z IntelliSense](/visualstudio/ide/using-intellisense)
