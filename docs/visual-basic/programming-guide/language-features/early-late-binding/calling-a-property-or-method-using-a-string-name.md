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
ms.openlocfilehash: 865270cfc8089d0bf229d9de7a7775dd2a3361d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731529"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>Wywoływanie właściwości lub metody za pomocą nazwy ciągu (Visual Basic)
W większości przypadków dostęp do właściwości i metod obiektu w czasie projektowania i napisać kod, aby je obsłużyć. Jednak w niektórych przypadkach użytkownik może nie wiedzieć o właściwości i metod obiektu z wyprzedzeniem lub po prostu chcesz elastyczność umożliwienie użytkownikowi końcowemu określić właściwości lub wykonywanie metod w czasie wykonywania.  
  
## <a name="callbyname-function"></a>CallByName — funkcja  
 Należy wziąć pod uwagę, na przykład, aplikacja kliencka, która ocenia wyrażenia wprowadzonej przez użytkownika, przekazując operator składnika modelu COM. Załóżmy, że są stale Dodawanie nowych funkcji do składników, które wymagają nowych operatorów. Korzystając z metody dostępu do obiektu standard, należy ponownie skompilować i rozpowszechniania aplikacji klienckiej, zanim można go używać nowych operatorów. Aby tego uniknąć, można użyć `CallByName` funkcję, aby przekazać nowych operatorów jako ciągi, bez konieczności zmieniania aplikacji.  
  
 `CallByName` Funkcja pozwala użyć ciągu, aby określić właściwości lub metody w czasie wykonywania. Podpis dla `CallByName` funkcja wygląda następująco:  
  
 *Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())  
  
 Pierwszy argument *obiektu*, przyjmuje nazwę obiektu, które mają być wykonywane działania. *Nazwaprocedury* argument przyjmuje ciąg, który zawiera nazwę metody lub właściwości procedury wywoływanej. *CallType* argument przyjmuje stałą, który reprezentuje typ procedury, aby wywołać: metody (`Microsoft.VisualBasic.CallType.Method`), właściwość Odczyt (`Microsoft.VisualBasic.CallType.Get`), lub zestaw właściwości (`Microsoft.VisualBasic.CallType.Set`). *Argumenty* argumentu, który jest opcjonalny, pobiera tablicę typu `Object` zawierający żadnych argumentów do procedury.  
  
 Możesz użyć `CallByName` z klasami z bieżącego rozwiązania, ale w większości przypadków umożliwia dostęp do obiektów COM lub obiekty [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów.  
  
 Załóżmy, że możesz dodać odwołania do zestawu, który zawiera klasę o nazwie `MathClass`, która zawiera nową funkcję o nazwie `SquareRoot`, jak pokazano w poniższym kodzie:  
  
 [!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]  
  
 Aplikacja może używać formantów pól tekstowych do kontroli, która metoda zostanie wywołana i jego argumenty. Na przykład jeśli `TextBox1` zawiera wyrażenie, które ma zostać obliczone, i `TextBox2` jest używana, wprowadź nazwę funkcji, można użyć poniższego kodu do wywołania `SquareRoot` funkcji na wyrażeniu w `TextBox1`:  
  
 [!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]  
  
 W przypadku wprowadzenia "64" na `TextBox1`, "SquareRoot" w `TextBox2`, a następnie wywołać `CallMath` procedurę, pierwiastek kwadratowy liczby w parametrze `TextBox1` jest oceniany. Wywołuje kod w przykładzie `SquareRoot` funkcji (który przyjmuje ciąg, który zawiera wyrażenie, które ma zostać obliczone jako wymaganego argumentu) i zwraca "8" w `TextBox1` (pierwiastek kwadratowy liczby 64). Oczywiście, jeśli użytkownik wprowadzi nieprawidłowy ciąg w `TextBox2`, jeśli ciąg zawiera nazwę właściwości zamiast metody lub jeśli metoda dodatkowe wymaganego argumentu, występuje błąd w czasie wykonywania. Trzeba dodać niezawodny kod obsługi błędów, gdy używasz `CallByName` przewidywać to lub inne błędy.  
  
> [!NOTE]
>  Gdy `CallByName` funkcja może być przydatna w niektórych przypadkach, należy porównać jego użyteczność względem wpływ na wydajność — przy użyciu `CallByName` do wywołania procedury jest nieco wolniej niż wywołanie z późnym wiązaniem. Jeśli to wywołanie funkcji, która jest wywoływana wielokrotnie, takie jak wewnątrz pętli, `CallByName` mogą mieć poważny wpływ na wydajność.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>
- [Określanie typu obiektu](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
