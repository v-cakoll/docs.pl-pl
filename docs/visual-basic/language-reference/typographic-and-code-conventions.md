---
title: Konwencje związane z typografią i kodami (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- typographic conventions [Visual Basic]
- document conventions [Visual Basic]
- conventions [Visual Basic], documentation
- Visual Basic code, conventions
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
ms.openlocfilehash: eb7a33ef21bf6beda730dffa8eb7ff9cabe599fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604500"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>Konwencje związane z typografią i kodami (Visual Basic)
Dokumentacja języka Visual Basic korzysta z następujących czynności związane z typografią i konwencje związane z kodami.  
  
## <a name="typographic-conventions"></a>Konwencje związane z typografią  
  
|Przykład|Opis|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|Słowa kluczowe specyficzne dla języka i środowiska uruchomieniowego elementów członkowskich mają początkowej wielkich liter i są sformatowane, jak pokazano w poniższym przykładzie.|  
|**SmallProject**, **ButtonCollection**|Słów i wyrażeń, które należy wpisać są sformatowane, jak pokazano w poniższym przykładzie.|  
|[Module, instrukcja](../../visual-basic/language-reference/statements/module-statement.md)|W poniższym przykładzie są formacie łącza, które można kliknąć, aby przejść do innej strony pomocy.|  
|*obiekt*, *nazwa_zmiennej*, `argumentList`|Symbole zastępcze podawane informacje są sformatowane, jak pokazano w poniższym przykładzie.|  
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
 [Elementy członkowskie biblioteki środowiska uruchomieniowego Visual Basic](../../visual-basic/language-reference/runtime-library-members.md)  
 [Visual Basic — konwencje nazewnictwa](../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [Komentarze w kodzie](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
