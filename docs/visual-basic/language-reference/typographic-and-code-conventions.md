---
title: Konwencje związane z typografią i kodami
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
ms.openlocfilehash: 4906c5ebadb7ce77f2d0e53b2fc5dbab69c5b41f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352713"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>Konwencje związane z typografią i kodami (Visual Basic)

W dokumentacji Visual Basic są stosowane następujące konwencje typograficzne i kody.  
  
## <a name="typographic-conventions"></a>Konwencje typograficzne  
  
|Przykład|Opis|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True``Debug`|Słowa kluczowe specyficzne dla języka i składowe środowiska uruchomieniowego mają początkowe wielkie litery i są sformatowane jak pokazano w tym przykładzie.|  
|**SmallProject**, **buttoncollection**|Wyrazy i frazy, które należy wpisać, są formatowane, jak pokazano w tym przykładzie.|  
|[Module, instrukcja](../../visual-basic/language-reference/statements/module-statement.md)|Linki, które można kliknąć, aby przejść do innej strony pomocy, są sformatowane jak pokazano w tym przykładzie.|  
|*obiekt*, *zmiennaname*, `argumentList`|Symbole zastępcze dla dostarczonych informacji są formatowane, jak pokazano w tym przykładzie.|  
|[Shadows], [ *expressionlist* ]|W obszarze Składnia elementy opcjonalne są ujęte w nawiasy klamrowe.|  
|{`Public` &#124; `Friend` &#124; `Private`}|W składni, gdy musisz wybrać co najmniej dwa elementy, elementy są ujęte w nawiasy klamrowe i oddzielane pionowo.<br /><br /> Należy wybrać jeden i tylko jeden element.|  
|[`Protected` &#124; `Friend`]|W składni, gdy istnieje możliwość wybrania dwóch lub więcej elementów, elementy są ujęte w nawiasy kwadratowe i oddzielane przez pionowe paski.<br /><br /> Można wybrać dowolną kombinację elementów lub brak elementu.|  
|[{`ByVal` &#124; `ByRef`}]|W polu składnia, gdy można wybrać więcej niż jeden element, ale można również całkowicie pominąć elementy, elementy są ujęte w nawiasy kwadratowe otoczone nawiasami klamrowymi i rozdzielone pionowymi paskami.|  
|*członekname*1, *MemberName*2, *MemberName*3|Wiele wystąpień tego samego symbolu zastępczego różni się od indeksów dolnych, jak pokazano w przykładzie.|  
|*memberName1*<br /><br /> Przyciski ...<br /><br /> *memberNameN*|W składni, wielokropek (...) jest używany do wskazania nieograniczonej liczby elementów typu bezpośrednio przed wielokropkiem.<br /><br /> W kodzie, wielokropek oznacza kod pominięty w celu przejrzystości.|  
|ESC, ENTER|Nazwy kluczy i sekwencje klawiszy na klawiaturze są wyświetlane wielkimi literami.|  
|ALT+F1|Gdy znaki plus (+) pojawiają się między nazwami kluczy, należy trzymać jeden klawisz podczas naciskania drugiego. Na przykład ALT + F1 oznacza przytrzymanie klawisza ALT podczas naciskania klawisza F1.|  
  
## <a name="code-conventions"></a>Konwencje kodu  
  
|Przykład|Opis|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|Przykłady kodu są wyświetlane w czcionce o stałej szerokości i są sformatowane tak, jak pokazano w tym przykładzie.|  
|Poprzednia instrukcja ustawia wartość `sampleString` na "Hello, World!"|Elementy kodu w tekście wyjaśniającym pojawiają się w czcionce o stałej szerokości, jak pokazano w tym przykładzie.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Komentarze do kodu są wprowadzane przez apostrof (') lub słowo kluczowe REM.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|Spacja, po której następuje znak podkreślenia (_) na końcu wiersza wskazuje, że instrukcja jest kontynuowana w następującym wierszu.|  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka Visual Basic](../../visual-basic/language-reference/index.md)
- [Słowa kluczowe](../../visual-basic/language-reference/keywords/index.md)
- [Elementy członkowskie biblioteki środowiska uruchomieniowego Visual Basic](../../visual-basic/language-reference/runtime-library-members.md)
- [Konwencje nazewnictwa Visual Basic](../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Instrukcje: przerywanie i łączenie instrukcji w kodzie](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Komentarze w kodzie](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
