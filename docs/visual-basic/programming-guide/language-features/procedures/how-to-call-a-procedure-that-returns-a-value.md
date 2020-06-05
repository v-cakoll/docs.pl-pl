---
title: 'Porady: wywoływanie procedury zwracającej wartość'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: a110cf9f3b42c7244d8d5bf7b49d5e6dac8c2e21
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388767"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Porady: wywoływanie procedury zwracającej wartość (Visual Basic)
`Function`Procedura zwraca wartość do kodu wywołującego. Należy to wywołać, dołączając jego nazwę i argumenty po prawej stronie instrukcji przypisania lub w wyrażeniu.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>Aby wywołać procedurę funkcji w wyrażeniu  
  
1. Użyj `Function` nazwy procedury w taki sam sposób, jak w przypadku użycia zmiennej. Możesz użyć `Function` wywołania procedury wszędzie tam, gdzie można użyć zmiennej lub stałej w wyrażeniu.  
  
2. Postępuj zgodnie z nazwą procedury z nawiasami, aby ująć listę argumentów. Jeśli nie ma żadnych argumentów, możesz opcjonalnie pominąć nawiasy. Jednak użycie nawiasów sprawia, że kod można ułatwić odczytywanie.  
  
3. Umieść argumenty na liście argumentów w nawiasach rozdzielonych przecinkami. Upewnij się, że podasz argumenty w tej samej kolejności, w której `Function` procedura definiuje odpowiednie parametry.  
  
     Alternatywnie można przekazać jeden lub więcej argumentów według nazwy. Aby uzyskać więcej informacji, zobacz [przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md).  
  
4. Wartość zwrócona przez procedurę uczestniczy w wyrażeniu tak samo jak wartość zmiennej lub stałej.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>Aby wywołać procedurę funkcji w instrukcji przypisania  
  
1. Użyj `Function` nazwy procedury po znaku równości ( `=` ) w instrukcji przypisania.  
  
2. Postępuj zgodnie z nazwą procedury z nawiasami, aby ująć listę argumentów. Jeśli nie ma żadnych argumentów, możesz opcjonalnie pominąć nawiasy. Jednak użycie nawiasów sprawia, że kod można ułatwić odczytywanie.  
  
3. Umieść argumenty na liście argumentów w nawiasach rozdzielonych przecinkami. Upewnij się, że podasz argumenty w tej samej kolejności, w jakiej `Function` procedura definiuje odpowiednie parametry, chyba że przekazujesz je według nazwy.  
  
4. Wartość zwracana z procedury jest przechowywana w zmiennej lub właściwości po lewej stronie instrukcji przypisania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wywołuje Visual Basic, <xref:Microsoft.VisualBasic.Interaction.Environ%2A> Aby pobrać wartość zmiennej środowiskowej systemu operacyjnego. Pierwszy wiersz wywołuje `Environ` wewnątrz wyrażenia, a drugi wiersz wywołuje go w instrukcji przypisania. `Environ`przyjmuje nazwę zmiennej jako jedynego argumentu. Zwraca wartość zmiennej do kodu wywołującego.  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Zobacz też

- [Procedury funkcji](./function-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Function, instrukcja](../../../language-reference/statements/function-statement.md)
- [Instrukcje: tworzenie procedury, która zwraca wartość](./how-to-create-a-procedure-that-returns-a-value.md)
- [Porady: zwracanie wartości z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Porady: wywoływanie procedury, która nie zwraca wartości](./how-to-call-a-procedure-that-does-not-return-a-value.md)
