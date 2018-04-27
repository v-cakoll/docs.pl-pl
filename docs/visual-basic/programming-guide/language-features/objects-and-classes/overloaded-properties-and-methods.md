---
title: Przeciążone właściwości i metody (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96d5ef2462f5312baa5269865977596035a254d5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Przeciążone właściwości i metody (Visual Basic)

Przeciążanie jest tworzenie więcej niż jednej procedury, wystąpienie konstruktora lub właściwości w klasie z tej samej nazwie, ale argument różnych typów.  
  
## <a name="overloading-usage"></a>Przeciążanie użycia

 Przeciążanie jest szczególnie przydatna w przypadku, gdy model obiektu mówią, że zostanie zastosowana identycznych nazw dla procedur, które działają na różnych typach danych. Na przykład klasa służąca do wyświetlania kilku różnych typów danych może mieć `Display` procedur, które wyglądają następująco:  
  
 [!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]
  
 Bez przeładowania, będzie potrzebny do tworzenia unikatowych nazw dla każdej procedury, mimo że robią to samo, jak pokazano w następnym:  
  
 [!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]
  
 Przeciążanie ułatwia używać właściwości lub metody, ponieważ umożliwia wybór typów danych, które mogą być używane. Na przykład przeciążone `Display` omówionych wcześniej można wywołać metody za pomocą dowolnego z następujących wierszy kodu:  
  
 [!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]
  
 W czasie wykonywania Visual Basic wywołuje procedurę poprawne na podstawie typów danych parametrów, które określisz.  
  
## <a name="overloading-rules"></a>Przeciążanie reguły

 Przeciążonego elementu członkowskiego klasy można utworzyć przez dodanie dwóch lub więcej właściwości lub metody o tej samej nazwie. Z wyjątkiem przeciążone elementy członkowskie pochodnej każdy przeciążonego elementu członkowskiego musi mieć listy różnych parametrów, a następujące elementy nie może pełnić funkcji różnego przeciążania właściwość lub procedura:  
  
-   Modyfikatory, takich jak `ByVal` lub `ByRef`, które są stosowane do elementu członkowskiego lub parametrów elementu członkowskiego.  
  
-   Nazwy parametrów  
  
-   Zwracane typy procedur  
  
 `Overloads` — Słowo kluczowe jest opcjonalny w przypadku przeciążania, ale jeśli występują przeciążony używa elementu członkowskiego `Overloads` — słowo kluczowe, a następnie wszystkie inne przeciążone elementy członkowskie o tej samej nazwie należy także określić słowa kluczowego.  
  
 Klasy pochodne mogą przeciążania dziedziczonych członków z elementów członkowskich, które mają identyczne parametry i typy parametrów procesu nazywanego *przesłanianie według nazwy i podpisu*. Jeśli `Overloads` — słowo kluczowe jest używana, gdy przesłanianie według nazwy i podpisu, implementacja klasy pochodnej elementu członkowskiego zamiast będzie używany do implementacji w klasie podstawowej, i inne przeciążenia dla tego elementu członkowskiego będą dostępne do wystąpień klasy pochodnej.  
  
 Jeśli `Overloads` — słowo kluczowe zostanie pominięty przeciążania dziedziczonego elementu członkowskiego z elementem członkowskim, który ma identyczne parametry i typy parametrów, a następnie przeładowanie jest nazywany *przesłanianie według nazwy*. Przesłanianie według nazwy zastępuje implementacji dziedziczonego elementu członkowskiego, a także udostępnia inne przeciążenia jest niedostępny dla wystąpień klasy pochodnej i jego decedents.  
  
 `Overloads` i `Shadows` Modyfikatory nie można używać z tej samej właściwości lub metody.  
  
### <a name="example"></a>Przykład

 Poniższy przykład tworzy przeciążonych metod, które akceptują albo `String` lub `Decimal` reprezentację kwota dolara ($) i zwracany ciąg zawierający podatku.  
  
#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Aby użyć w tym przykładzie do utworzenia przeciążonej metody
  
1.  Otwórz nowy projekt i Dodaj klasę o nazwie `TaxClass`.  
  
2.  Dodaj następujący kod do `TaxClass` klasy.  
  
     [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]
  
3.  Poniższej procedury można dodać do formularza.  
  
     [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]
  
4.  Dodawanie przycisku do formularza i wywołanie `ShowTax` procedury z `Button1_Click` zdarzeń przycisku.  
  
5.  Uruchom projekt i kliknij przycisk w formularzu do testowania przeciążone `ShowTax` procedury.  
  
 W czasie wykonywania kompilator wybiera odpowiednią przeciążonej funkcji zgodny z parametrami używane. Po kliknięciu przycisku przeciążona metoda jest wywoływana najpierw z `Price` parametr, który jest ciągiem i komunikat "cena jest ciągiem. Podatek jest $5,12" jest wyświetlany. `TaxAmount` jest wywoływana z `Decimal` wartość po raz drugi i komunikat, "cena jest wartości dziesiętnej. Podatek jest $5,12" jest wyświetlany.  
  
## <a name="see-also"></a>Zobacz także

 [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Przesłanianie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Sub, instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Podstawowe informacje o dziedziczeniu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)  
 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)  
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
