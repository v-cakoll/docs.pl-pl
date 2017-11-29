---
title: "Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8baa03e37325a6ad7065ec1a60052b3ea6a46c6f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic
A *domyślna właściwość* jest właściwością klasy lub struktury kodu można uzyskać dostęp bez określania go. Podczas wywoływania kodu nazwy klasy lub struktury, ale nie właściwości i kontekst zezwala na dostęp do właściwości, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] rozpoznaje dostęp do tej klasy lub struktury domyślnej właściwości, jeśli taka istnieje.  
  
 Klasy lub struktury może mieć co najwyżej jeden domyślny właściwości. Jednak można przeciążać właściwości domyślnej i więcej niż jedna wersja go.  
  
 Aby uzyskać więcej informacji, zobacz [domyślne](../../../../visual-basic/language-reference/modifiers/default.md).  
  
### <a name="to-declare-a-default-property"></a>Deklarowanie właściwości domyślne  
  
1.  Deklarowanie właściwości w zwykły sposób. Nie określaj `Shared` lub `Private` — słowo kluczowe.  
  
2.  Obejmują `Default` — słowo kluczowe w deklaracji właściwości.  
  
3.  Określ co najmniej jeden parametr dla właściwości. Nie można zdefiniować domyślnej właściwości, które nie wymaga co najmniej jednego argumentu.  
  
     [!code-vb[VbVbcnProcedures#17](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### <a name="to-call-a-default-property"></a>Wywoływanie właściwości domyślne  
  
1.  Deklarowanie zmiennej typu zawierającego klasy lub struktury.  
  
     [!code-vb[VbVbcnProcedures#16](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  Użyj nazwy zmiennej w wyrażeniu, w którym zwykle obejmuje nazwę właściwości.  
  
     [!code-vb[VbVbcnProcedures#21](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  Wykonaj nazwy zmiennej z listy argumentów w nawiasach. Domyślna właściwość musi mieć co najmniej jednego argumentu.  
  
     [!code-vb[VbVbcnProcedures#20](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  Można pobrać wartości właściwości domyślnej, użyj nazwy zmiennej, z listy argumentów w wyrażeniu lub po równości (`=`) Zaloguj się w instrukcji przypisania.  
  
     [!code-vb[VbVbcnProcedures#15](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  Aby ustawić wartość właściwości domyślnej, użyj nazwy zmiennej, z listy argumentów po lewej stronie instrukcji przypisania.  
  
     [!code-vb[VbVbcnProcedures#14](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  Zawsze można określić domyślną nazwę właściwości wraz z nazwą zmiennej, tak jak będzie można uzyskać dostępu do innych właściwości.  
  
     [!code-vb[VbVbcnProcedures#19](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje właściwości domyślnej klasy.  
  
 [!code-vb[VbVbcnProcedures#12](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób wywoływania domyślnej właściwości `myProperty` w klasie `class1`. Instrukcje przypisania trzy przechowywanie wartości w `myProperty`i <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> wywołania odczytuje wartości.  
  
 [!code-vb[VbVbcnProcedures#13](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 Najczęściej właściwości domyślnej jest <xref:Microsoft.VisualBasic.Collection.Item%2A> właściwości na różne klasy kolekcji.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Właściwości domyślnych może spowodować zmniejszenie małych znaków kodu źródłowego, ale może wprowadzić czytelność kodu. Jeśli kod wywołujący nie są zaznajomieni z klasy lub struktury, podczas wykonywania odwołanie do nazwy klasy lub struktury nie może być niektórych czy uzyskuje dostęp tego odwołania do klasy lub struktury, sam lub domyślnej właściwości. Może to prowadzić do błędów kompilatora lub błędy niewielkie logiki czasu wykonywania.  
  
 Nieco zmniejsza ryzyko błędów właściwości domyślne przy użyciu zawsze [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md) można ustawić typ kompilatora sprawdzania `On`.  
  
 Jeśli planujesz użyć wstępnie zdefiniowanych klasy lub struktury w kodzie, należy określić, czy ma ona domyślnej właściwości, a jeśli tak, jakie jego nazwa jest.  
  
 Z powodu niedogodności należy rozważyć nie definiuje właściwości domyślnych. Aby zwiększyć czytelność kodu należy również wziąć pod uwagę zawsze odwołujących się do wszystkich właściwości jawnie, nawet domyślnej właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury własności](./property-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Domyślne](../../../../visual-basic/language-reference/modifiers/default.md)  
 [Różnice pomiędzy właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)  
 [Porady: Tworzenie właściwości](./how-to-create-a-property.md)  
 [Porady: deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Porady: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)  
 [Porady: umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)  
 [Porady: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)
