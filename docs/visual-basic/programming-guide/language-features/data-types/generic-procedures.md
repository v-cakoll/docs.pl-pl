---
title: "Procedury ogólne w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e019ca32277f93f798e99e996a3670c8302ba9b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="generic-procedures-in-visual-basic"></a>Procedury ogólne w Visual Basic
A *ogólnego procedury*, nazywany również *Metoda ogólna*, jest to procedura zdefiniowane z co najmniej jeden typ parametru. Dzięki temu kod wywołujący dostosować typy danych do jej wymagania dotyczące zawsze wywołuje procedurę.  
  
 Procedura nie jest rodzajowa po prostu z definiowany wewnątrz klasy ogólnej lub to struktura generyczna. Aby wartość była ogólna, procedurę należy wykonać co najmniej jeden parametr typu, oprócz parametry normalnej, może to potrwać. Ogólny klasy lub struktury może zawierać procedury nierodzajowe i nierodzajowe klasy, struktury, lub moduł może zawierać procedury ogólne.  
  
 Procedury ogólne można użyć swoich parametrów typu liście jego normalnej parametru, jego typ zwracany, jeśli ma ona jedną i w jego procedury kodu.  
  
## <a name="type-inference"></a>Wnioskowanie o typie  
 Procedury ogólne można wywołać bez podawania żadnych argumentów typu na wszystkich. Jeśli należy wywołać go w ten sposób, kompilator spróbuje określić typy odpowiednie dane do przekazania do procedury argumentów typu. Ta metoda jest wywoływana *wnioskowanie typu*. Poniższy kod przedstawia wywołanie w którym kompilator ustala, że należy przekazać typ `String` do parametru typu `t`.  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 Jeśli kompilator nie można wywnioskować argumentów typu z kontekstu wywołania, zgłasza błąd. Jedną z możliwych przyczyn takiego błędu jest niezgodność rangi tablicy. Załóżmy na przykład zdefiniować normalne parametr jako tablica parametru typu. Wywołanie procedury ogólne na tablicę rangi różnych (liczba wymiarów), udostępnia niezgodność powoduje, że wnioskowanie o typie się niepowodzeniem. Poniższy kod przedstawia wywołanie, w którym jest tablicą dwuwymiarową jest przekazany do procedury, która oczekuje tablicą jednowymiarową.  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 Wnioskowanie o typie można wywołać tylko przez pominięcie wszystkich argumentów typu. Jeśli podasz jeden argument typu, należy podać je wszystkie.  
  
 Wnioskowanie o typie jest obsługiwana tylko dla ogólnych procedurach. Nie można wywołać wnioskowanie o typie na ogólne klasy, struktury, interfejsy lub delegatów.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie zdefiniowano ogólnego `Function` procedurę, aby znaleźć określony element w tablicy. Definiuje jeden parametr typu, a używa go do utworzenia dwóch parametrów na liście parametrów.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a>Komentarze  
 Powyższy przykład wymaga możliwości porównania `searchValue` względem każdego elementu `searchArray`. Aby zagwarantować tę możliwość, jego ogranicza parametr typu `T` do zaimplementowania <xref:System.IComparable%601> interfejsu. W kodzie użyto <xref:System.IComparable%601.CompareTo%2A> zamiast metody `=` operatora, ponieważ nie ma gwarancji, że podany argument typu dla `T` obsługuje `=` operatora.  
  
 Możesz przetestować `findElement` procedury z następującym kodem.  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 Poprzedni wywołań `MsgBox` wyświetlić odpowiednio "0", "1" i "-1".  
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Porady: Definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [Porady: używanie klasy ogólnej](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Procedury](../../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Parametry i argumenty procedur](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [Lista typów](../../../../visual-basic/language-reference/statements/type-list.md)  
 [Listy parametrów](../../../../visual-basic/language-reference/statements/parameter-list.md)
