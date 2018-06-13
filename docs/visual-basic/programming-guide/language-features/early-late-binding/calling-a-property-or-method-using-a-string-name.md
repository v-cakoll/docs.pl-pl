---
title: Wywoływanie właściwości lub metody za pomocą nazwy ciągu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- passing operators [Visual Basic]
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls [Visual Basic], strings
- methods [Visual Basic], calling with string names
- calling methods [Visual Basic], string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
ms.openlocfilehash: 76be426049489bb58e50878822c03fa5cd5cca8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649230"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>Wywoływanie właściwości lub metody za pomocą nazwy ciągu (Visual Basic)
W większości przypadków może odnajdywać właściwości i metody obiektu w czasie projektowania, a do ich obsługi w kodzie. Jednak w niektórych przypadkach użytkownik może nie wiedzieć o właściwości i metod obiektu z wyprzedzeniem, lub po prostu chcesz elastyczność włączania użytkownika końcowego określić właściwości lub wykonywanie metod w czasie wykonywania.  
  
## <a name="callbyname-function"></a>CallByName — funkcja  
 Należy wziąć pod uwagę, na przykład aplikacji klienckiej, która ocenia wyrażenia wprowadzony przez użytkownika, przekazując operator składnika modelu COM. Załóżmy, że stale dodajesz nowe funkcje do składnika, który wymaga nowych operatorów. Korzystając z techniki dostępu standardowego obiektu, należy ponownie skompilować i wykonać ponowną dystrybucję aplikacji klienckiej, zanim można używać nowych operatorów. Aby tego uniknąć, można użyć `CallByName` funkcji przekazanie nowych operatorów jako ciągi, bez konieczności zmieniania aplikacji.  
  
 `CallByName` Funkcji umożliwia określenie właściwości lub metody w czasie wykonywania za pomocą ciągu. Podpis dla `CallByName` funkcja wygląda następująco:  
  
 *Wynik* = `CallByName`(*obiektu*, *Nazwaprocedury*, *Typ_wywołania*, *argumenty*())  
  
 Pierwszy argument *obiektu*, przyjmuje nazwę obiektu, który ma być wykonywane działania. *Nazwaprocedury* ciąg znaków zawierający nazwę metody lub właściwości procedury wywoływanej przyjmuje argumentu. *Typ_wywołania* argument ma stałą, który reprezentuje typ procedury, aby wywołać: metody (`Microsoft.VisualBasic.CallType.Method`), właściwości do odczytu (`Microsoft.VisualBasic.CallType.Get`), lub ustaw właściwość (`Microsoft.VisualBasic.CallType.Set`). *Argumenty* argument, który jest opcjonalny, pobiera tablicę typu `Object` zawierający żadnych argumentów do procedury.  
  
 Można użyć `CallByName` z klasami bieżącego rozwiązania, ale jest najczęściej używana dostęp do obiektów COM lub obiektów z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów.  
  
 Załóżmy, że możesz dodać odwołania do zestawu zawierającego klasę o nazwie `MathClass`, która zawiera nową funkcję o nazwie `SquareRoot`, jak pokazano w poniższym kodzie:  
  
 [!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]  
  
 Aplikacja może używać formantów pól tekstowych do argumentów i kontroli, która metoda zostanie wywołana. Na przykład jeśli `TextBox1` zawiera wyrażenie, które ma zostać obliczone i `TextBox2` jest używana, wprowadź nazwę funkcji, można użyć poniższego kodu do wywołania `SquareRoot` funkcji na wyrażeniu w `TextBox1`:  
  
 [!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]  
  
 Po wprowadzeniu "64" w `TextBox1`, "SquareRoot" w `TextBox2`, a następnie wywołać `CallMath` procedury, pierwiastek kwadratowy liczby w `TextBox1` jest obliczane. Kod w przykładzie wywołuje `SquareRoot` funkcji (który przyjmuje ciąg, który zawiera wyrażenie, które ma być traktowane jako wymagany argument) i zwraca "8" w `TextBox1` (pierwiastek kwadratowy liczby 64). Oczywiście, jeśli użytkownik wprowadzi nieprawidłowy ciąg w `TextBox2`, jeśli ciąg zawiera nazwę właściwości zamiast metody lub metody, gdyby dodatkowe wymaganego argumentu, występuje błąd w czasie wykonywania. Należy dodać niezawodne kodu obsługi błędu, gdy używasz `CallByName` przewidywania te lub inne błędy.  
  
> [!NOTE]
>  Gdy `CallByName` funkcja może być przydatna w niektórych przypadkach, należy porównać przydatności przed jego wpływu na wydajność — przy użyciu `CallByName` do wywołania procedury jest nieco wolniej niż wywołania z późnym wiązaniem. Jeśli są wywoływania funkcji wywoływanej cyklicznie, takie jak wewnątrz pętli, `CallByName` mogą mieć poważny wpływ na wydajność.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>  
 [Określanie typu obiektu](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
