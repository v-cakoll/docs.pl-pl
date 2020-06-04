---
title: 'Instrukcje: deklarowanie i wywoływanie w właściwości domyślnej'
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: 4de5d94a94e764d1fc543ffae41b00a9bb729c94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388157"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic
*Właściwość domyślna* jest klasą lub właściwością struktury, do której Twój kod może uzyskać dostęp bez określania go. Podczas wywoływania nazw kodu klasy lub struktury, ale nie do właściwości, a kontekst umożliwia dostęp do właściwości, Visual Basic rozpoznaje dostęp do tej klasy lub domyślnej właściwości tej struktury, jeśli taki istnieje.  
  
 Klasa lub struktura może mieć co najwyżej jedną właściwość domyślną. Można jednak przeciążyć właściwość domyślną i mieć więcej niż jedną wersję.  
  
 Aby uzyskać więcej informacji, zobacz [domyślne](../../../language-reference/modifiers/default.md).  
  
### <a name="to-declare-a-default-property"></a>Aby zadeklarować właściwość domyślną  
  
1. Zadeklaruj właściwość w normalny sposób. Nie określaj `Shared` `Private` słowa kluczowego or.  
  
2. Uwzględnij `Default` słowo kluczowe w deklaracji właściwości.  
  
3. Określ co najmniej jeden parametr właściwości. Nie można zdefiniować właściwości domyślnej, która nie przyjmuje co najmniej jednego argumentu.  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a>Aby wywołać właściwość domyślną  
  
1. Zadeklaruj zmienną zawierającą typ klasy lub struktury.  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. Użyj samej nazwy zmiennej w wyrażeniu, gdzie zwykle zawiera nazwę właściwości.  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. Postępuj według nazwy zmiennej z listą argumentów w nawiasach. Właściwość domyślna musi mieć co najmniej jeden argument.  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. Aby pobrać wartość domyślną właściwości, użyj nazwy zmiennej z listą argumentów w wyrażeniu lub po znaku równości ( `=` ) w instrukcji przypisania.  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. Aby ustawić domyślną wartość właściwości, użyj nazwy zmiennej z listą argumentów po lewej stronie instrukcji przypisania.  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. Można zawsze określić domyślną nazwę właściwości wraz z nazwą zmiennej, tak jak w przypadku uzyskania dostępu do innej właściwości.  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje właściwość domyślną klasy.  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób wywoływania właściwości domyślnej `myProperty` klasy `class1` . Trzy instrukcje przypisania przechowują wartości w `myProperty` , a <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> wywołanie odczytuje wartości.  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 Najbardziej typowym zastosowaniem właściwości domyślnej jest <xref:Microsoft.VisualBasic.Collection.Item%2A> Właściwość różnych klas kolekcji.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Właściwości domyślne mogą spowodować niewielkie zmniejszenie kodu źródłowego, ale może to utrudnić odczytywanie kodu. Jeśli kod wywołujący nie jest zaznajomiony z klasą lub strukturą, gdy tworzy odwołanie do nazwy klasy lub struktury, nie można określić, czy odwołanie uzyskuje dostęp do samej klasy lub struktury, czy też do właściwości domyślnej. Może to prowadzić do błędów kompilatora lub niewielkich błędów logiki czasu wykonywania.  
  
 Możesz nieco skrócić ryzyko błędów właściwości domyślnych, zawsze używając [instrukcji Option Strict](../../../language-reference/statements/option-strict-statement.md) , aby ustawić sprawdzanie typu kompilatora `On` .  
  
 Jeśli planujesz użycie wstępnie zdefiniowanej klasy lub struktury w kodzie, musisz określić, czy ma ona właściwość domyślną, a jeśli tak, to jaki jest jej nazwa.  
  
 Ze względu na te wady należy rozważyć niedefiniowanie właściwości domyślnych. Aby uzyskać czytelność kodu, należy również rozważyć zawsze odwołanie do wszystkich właściwości jawnie, nawet właściwości domyślnych.  
  
## <a name="see-also"></a>Zobacz też

- [Procedury własności](./property-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Property — Instrukcja](../../../language-reference/statements/property-statement.md)
- [Domyślne](../../../language-reference/modifiers/default.md)
- [Różnice pomiędzy właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)
- [Instrukcje: tworzenie właściwości](./how-to-create-a-property.md)
- [Porady: deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Porady: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)
- [Instrukcje: umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)
- [Instrukcje: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)
