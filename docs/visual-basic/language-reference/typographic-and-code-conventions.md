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
ms.openlocfilehash: 3255dff8268cd5500a1244716f37bf30f5b43cfb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698606"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>Konwencje związane z typografią i kodami (Visual Basic)
Dokumentacja języka Visual Basic używa następujących związane z typografią i konwencje związane.  
  
## <a name="typographic-conventions"></a>Konwencje związane z typografią  
  
|Przykład|Opis|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|Słowa kluczowe specyficzne dla języka i środowiska uruchomieniowego członkowie mają początkowych wielkich liter i są sformatowane, jak pokazano w poniższym przykładzie.|  
|**SmallProject**, **ButtonCollection**|Wyrazy i frazy, które należy wpisać są formatowane, jak pokazano w poniższym przykładzie.|  
|[Instrukcja Module](../../visual-basic/language-reference/statements/module-statement.md)|Łącza, które można kliknąć, aby przejść do innej strony pomocy są formatowane, jak pokazano w poniższym przykładzie.|  
|*obiekt*, *nazwa_zmiennej*, `argumentList`|Symbole zastępcze użytkownik poda informacje o są formatowane, jak pokazano w poniższym przykładzie.|  
|[Cieni], [ *expressionList* ]|W składni elementy opcjonalne są ujęte w nawiasy kwadratowe.|  
|{ `Public` &#124; `Friend` &#124; `Private` }|W składni gdy należy dokonać wyboru między dwoma lub więcej elementów, elementy są ujęte w nawiasy klamrowe i rozdzielone pionowych słupków.<br /><br /> Należy wybrać jeden i tylko jeden z elementów.|  
|[ `Protected` &#124; `Friend` ]|Przy użyciu składni gdy masz możliwość wyboru między dwoma lub więcej elementów, elementy są ujęte w nawiasy kwadratowe i rozdzielone pionowych słupków.<br /><br /> Można wybrać dowolną kombinację elementów lub Brak elementów.|  
|[{ `ByVal` &#124; `ByRef` }]|W składni po wybraniu nie więcej niż jeden element, ale można również całkowicie pominąć elementy elementy są ujęte w nawiasy kwadratowe, ujęte w nawiasach klamrowych i rozdzielone pionowych słupków.|  
|*memberName*1, *memberName*2, *memberName*3|Wiele wystąpień tego samego symbolu zastępczego są zróżnicowane według indeksów dolnych, jak pokazano w przykładzie.|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|W składni wielokropka (...) jest używany do wskazania nieokreśloną liczbę elementów rodzaju natychmiast przed wielokropka.<br /><br /> W kodzie elipsy oznaczają kod pominięty dla jasności.|  
|ESC, ENTER|Nazwy kluczy i kluczami sekwencji na klawiaturze pojawiają się wielkimi literami.|  
|ALT+F1|Gdy znak plus (+) pojawią się między nazwami kluczy, musi przytrzymaj jednego klucza podczas drugiego. ALT + F1 oznacza na przykład, naciskając klawisz F1, przytrzymując naciśnięty klawisz ALT.|  
  
## <a name="code-conventions"></a>Konwencje kodu  
  
|Przykład|Opis|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|Przykłady kodu są wyświetlane w czcionce stałych i są sformatowane, jak pokazano w poniższym przykładzie.|  
|Poprzednia instrukcja ustawia wartość `sampleString` do "Hello, world!"|Elementy kodu w tekście objaśnienia są wyświetlane w czcionkę stałych, jak pokazano w poniższym przykładzie.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Komentarze w kodzie są wprowadzone przez apostrof (') lub REM — słowo kluczowe.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|Odstęp następuje znaku podkreślenia (_) na końcu wiersza wskazuje, że instrukcja jest kontynuowane od następujący wiersz.|  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka Visual Basic](../../visual-basic/language-reference/index.md)
- [Słowa kluczowe](../../visual-basic/language-reference/keywords/index.md)
- [Elementy członkowskie biblioteki środowiska uruchomieniowego Visual Basic](../../visual-basic/language-reference/runtime-library-members.md)
- [Visual Basic — konwencje nazewnictwa](../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Komentarze w kodzie](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
