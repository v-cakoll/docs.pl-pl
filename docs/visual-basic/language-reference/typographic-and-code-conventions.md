---
title: "Konwencje związane z typografią i kodami (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- typographic conventions [Visual Basic]
- document conventions [Visual Basic]
- conventions [Visual Basic], documentation
- Visual Basic code, conventions
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7b6db5c223b0548e308b49a686cff72eaaf8da36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="typographic-and-code-conventions-visual-basic"></a>Konwencje związane z typografią i kodami (Visual Basic)
Dokumentacja języka Visual Basic korzysta z następujących czynności związane z typografią i konwencje związane z kodami.  
  
## <a name="typographic-conventions"></a>Konwencje związane z typografią  
  
|Przykład|Opis|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|Słowa kluczowe specyficzne dla języka i środowiska uruchomieniowego elementów członkowskich mają początkowej wielkich liter i są sformatowane, jak pokazano w poniższym przykładzie.|  
|**SmallProject**, **ButtonCollection**|Słów i wyrażeń, które należy wpisać są sformatowane, jak pokazano w poniższym przykładzie.|  
|[Module — instrukcja](../../visual-basic/language-reference/statements/module-statement.md)|W poniższym przykładzie są formacie łącza, które można kliknąć, aby przejść do innej strony pomocy.|  
|*obiekt*, *nazwa_zmiennej*,`argumentList`|Symbole zastępcze podawane informacje są sformatowane, jak pokazano w poniższym przykładzie.|  
|[Shadows], [ *expressionList* ]|W składni elementy opcjonalne są ujęte w nawiasy kwadratowe.|  
|{ `Public` &#124; `Friend` &#124; `Private` }|W składni podczas wybór między dwa lub więcej elementów, należy się upewnić elementy są ujęte w nawiasy klamrowe i oddzielone pionowych słupków.<br /><br /> Musisz wybrać jeden i tylko jeden z elementów.|  
|[ `Protected` &#124; `Friend` ]|W składni przypadku możliwość wyboru między dwa lub więcej elementów, elementy są ujęte w nawiasy kwadratowe i oddzielone pionowych słupków.<br /><br /> Można wybrać dowolną kombinację elementy lub żadnego elementu.|  
|[{ `ByVal` &#124; `ByRef` }]|W składni po nie więcej niż jeden element można wybrać, ale można również całkowicie pominąć elementy elementy są ujęte w nawiasy kwadratowe ujęte w nawiasy klamrowe i oddzielone pionowych słupków.|  
|*memberName*1, *memberName*2, *memberName*3|Wiele wystąpień tego samego symbolu zastępczego są zróżnicowane przez indeksy dolne, jak pokazano w przykładzie.|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|W składni wielokropek (...) służy do wskazywania nieokreśloną liczbę elementów rodzaju bezpośrednio przed wielokropka.<br /><br /> W kodzie wielokropek oznaczającego pominięcia dla jasności kodu.|  
|ESC, WPROWADŹ|Nazwy kluczy i kluczy sekwencji na klawiaturze pojawiają się wielkimi literami.|  
|ALT + F1|Gdy znak plus (+) pojawią się między nazwami klucza, musi przytrzymaj jednego klucza podczas drugiego. Na przykład ALT + F1 oznacza, że naciśnięcie klawisza F1, przytrzymując naciśnięty klawisz ALT.|  
  
## <a name="code-conventions"></a>Konwencje związane z kodami  
  
|Przykład|Opis|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|Przykłady kodu są wyświetlane przy użyciu czcionki o stałej wysokości i są sformatowane, jak pokazano w poniższym przykładzie.|  
|Poprzednia instrukcja ustawia wartość `sampleString` na "tekst Hello, world!"|Elementy kodu w tekst objaśnienia są wyświetlane w stałych czcionki, jak pokazano w poniższym przykładzie.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Komentarze w kodzie zostały wprowadzone przez apostrof (') lub REM — słowo kluczowe.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|Miejsca, a następnie znaku podkreślenia (_) na końcu wiersza wskazuje, że instrukcja jest kontynuowane od następującego wiersza.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka Visual Basic](../../visual-basic/language-reference/index.md)  
 [Słowa kluczowe](../../visual-basic/language-reference/keywords/index.md)  
 [Elementy członkowskie biblioteki wykonawczej języka Visual Basic](../../visual-basic/language-reference/runtime-library-members.md)  
 [Visual Basic — konwencje nazewnictwa](../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Porady: przerywanie i łączenie instrukcji w Code](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [Komentarze w kodzie](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
