---
title: 'Porady: wywoływanie procedury zwracającej wartość'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 7f5d46babf31ea3c6babb29c0f1c08a23e51d598
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340740"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Porady: wywoływanie procedury zwracającej wartość (Visual Basic)
Procedura `Function` zwraca wartość do kodu wywołującego. Należy to wywołać, dołączając jego nazwę i argumenty po prawej stronie instrukcji przypisania lub w wyrażeniu.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>Aby wywołać procedurę funkcji w wyrażeniu  
  
1. Użyj nazwy procedury `Function` w taki sam sposób jak w przypadku użycia zmiennej. Można użyć wywołania procedury `Function` w dowolnym miejscu, w którym można użyć zmiennej lub stałej w wyrażeniu.  
  
2. Postępuj zgodnie z nazwą procedury z nawiasami, aby ująć listę argumentów. Jeśli nie ma żadnych argumentów, możesz opcjonalnie pominąć nawiasy. Jednak użycie nawiasów sprawia, że kod można ułatwić odczytywanie.  
  
3. Umieść argumenty na liście argumentów w nawiasach rozdzielonych przecinkami. Upewnij się, że podasz argumenty w tej samej kolejności, w której procedura `Function` definiuje odpowiednie parametry.  
  
     Alternatywnie można przekazać jeden lub więcej argumentów według nazwy. Aby uzyskać więcej informacji, zobacz [przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md).  
  
4. Wartość zwrócona przez procedurę uczestniczy w wyrażeniu tak samo jak wartość zmiennej lub stałej.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>Aby wywołać procedurę funkcji w instrukcji przypisania  
  
1. Użyj nazwy procedury `Function` po znaku równości (`=`) w instrukcji przypisania.  
  
2. Postępuj zgodnie z nazwą procedury z nawiasami, aby ująć listę argumentów. Jeśli nie ma żadnych argumentów, możesz opcjonalnie pominąć nawiasy. Jednak użycie nawiasów sprawia, że kod można ułatwić odczytywanie.  
  
3. Umieść argumenty na liście argumentów w nawiasach rozdzielonych przecinkami. Upewnij się, że podasz argumenty w tej samej kolejności, w jakiej procedura `Function` definiuje odpowiednie parametry, chyba że przekazujesz je według nazwy.  
  
4. Wartość zwracana z procedury jest przechowywana w zmiennej lub właściwości po lewej stronie instrukcji przypisania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wywołuje <xref:Microsoft.VisualBasic.Interaction.Environ%2A> Visual Basic, aby pobrać wartość zmiennej środowiskowej systemu operacyjnego. Pierwszy wiersz wywołuje `Environ` wewnątrz wyrażenia, a drugi wiersz wywołuje go w instrukcji przypisania. `Environ` przyjmuje nazwę zmiennej jako jedynego argumentu. Zwraca wartość zmiennej do kodu wywołującego.  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury funkcji](./function-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Function, instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrukcje: tworzenie procedury, która zwraca wartość](./how-to-create-a-procedure-that-returns-a-value.md)
- [Instrukcje: zwracanie wartości z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Instrukcje: wywoływanie procedury, która nie zwraca wartości](./how-to-call-a-procedure-that-does-not-return-a-value.md)
