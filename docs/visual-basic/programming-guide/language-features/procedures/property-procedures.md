---
title: Procedury własności (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: 47e93ee17f160ce5cd701fd0a12ec16b3997ce9b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828352"
---
# <a name="property-procedures-visual-basic"></a>Procedury własności (Visual Basic)
Procedury właściwości jest szereg instrukcji, które manipulowania właściwości niestandardowych dla modułu, klasy lub struktury. Procedury własności są również nazywane *Akcesory właściwości*.  
  
 Visual Basic zawiera następujące procedury właściwości:  
  
-   A `Get` procedura zwraca wartość właściwości. Jest ona wywoływana, gdy uzyskujesz dostęp do właściwości w wyrażeniu.  
  
-   A `Set` procedury ustawia właściwość na wartość, w tym odwołanie do obiektu. Jest ona wywoływana podczas przypisywania wartości do właściwości.  
  
 Zazwyczaj definiowanie procedury właściwości w parach, za pomocą `Get` i `Set` instrukcji, ale można zdefiniować tych procedurach, tylko, jeśli właściwość jest tylko do odczytu ([instrukcja Get](../../../../visual-basic/language-reference/statements/get-statement.md)) lub tylko do zapisu ([zestawu Instrukcja](../../../../visual-basic/language-reference/statements/set-statement.md)).  
  
 Możesz pominąć `Get` i `Set` procedury w przypadku przy użyciu automatycznie implementowanych właściwości. Aby uzyskać więcej informacji, zobacz [implemented Properties](./auto-implemented-properties.md).  
  
 Można zdefiniować właściwości klas, struktur i modułów. Właściwości są `Public` domyślnie, co oznacza, że można go wywołać z dowolnego miejsca w aplikacji, które mogą uzyskiwać dostęp do właściwości kontenera.  
  
 Dla porównania z właściwościami i zmiennymi, zobacz [różnice między właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md).  
  
## <a name="declaration-syntax"></a>Składnia deklaracji  
 Sama właściwość jest definiowany przez blok kodu ujęte w [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md) i `End Property` instrukcji. Wewnątrz tego bloku każdej procedury właściwość pojawia się jako wewnętrzny blok ujęte w instrukcji deklaracji (`Get` lub `Set`) i dopasowywania `End` deklaracji.  
  
 Składnia deklaracji właściwości i jej procedury jest następująca:  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 `Modifiers` Można określić poziom dostępu i informacji dotyczących przeciążenia, zastępowanie, udostępnianie i przesłanianie, a także tego, czy właściwość jest tylko do odczytu lub tylko do zapisu. `AccessLevel` Na `Get` lub `Set` procedura może być dowolny poziom, który jest bardziej restrykcyjny niż poziom dostępu, określony dla samej właściwości. Aby uzyskać więcej informacji, zobacz [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md).  
  
### <a name="data-type"></a>Typ danych  
 Typ danych właściwości i poziom dostępu jednostki są definiowane w `Property` instrukcji, a nie w procedurach właściwości. Właściwość może mieć tylko jednego typu danych. Na przykład nie można zdefiniować właściwości w celu przechowywania `Decimal` wartość, ale pobieranie `Double` wartość.  
  
### <a name="access-level"></a>Poziom dostępu  
 Można jednak określić poziom dostępu jednostki dla właściwości i bardziej ograniczyć poziomu dostępu na jeden z jego procedury właściwości. Na przykład można zdefiniować `Public` właściwości, a następnie zdefiniować `Private Set` procedury. `Get` Pozostaje procedury `Public`. Można zmienić poziomu dostępu tylko w jednym procedury właściwości i można tworzyć tylko je bardziej restrykcyjny niż poziom dostępu podmiotu zabezpieczeń. Aby uzyskać więcej informacji, zobacz [jak: Deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md).  
  
## <a name="parameter-declaration"></a>Deklaracja parametru  
 Zadeklaruj taki sam sposób jak w przypadku każdego parametru [procedury Sub](./sub-procedures.md), z tą różnicą, że mechanizm przekazywania musi być `ByVal`.  
  
 Składnia dla każdego parametru na liście parametrów jest w następujący sposób:  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 Jeśli parametr jest opcjonalny, należy również podać wartości domyślnej w ramach swojej deklaracji. Składnia określająca wartość domyślna jest następująca:  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a>Wartość właściwości  
 W `Get` procedury, wartość zwracana jest dostarczany do wywoływania wyrażenia jako wartości właściwości.  
  
 W `Set` procedury, nowa wartość właściwości jest przekazywana do parametru `Set` instrukcji. Jeśli parametr jest jawnie deklarować, należy zadeklarować ją za pomocą tego samego typu danych, ponieważ właściwość. Jeśli nie deklaruj parametru, kompilator używa niejawny parametr `Value` do reprezentowania nową wartość do przypisania do właściwości.  
  
## <a name="calling-syntax"></a>Składnia wywoływania  
 Wywoływanie procedury właściwości są niejawnie, wprowadzając odwołanie do właściwości. Możesz użyć nazwy właściwości taki sam sposób użyje nazwę zmiennej, z tą różnicą, że należy podać wartości w argumentach, które nie są opcjonalne i listy argumentów należy ująć w nawiasy. Jeśli zostały dostarczone żadne argumenty, opcjonalnie można pominąć nawiasów.  
  
 Składnia wywołanie niejawne `Set` procedura jest następująca:  
  
 `propertyname[(argumentlist)] = expression`  
  
 Składnia wywołanie niejawne `Get` procedura jest następująca:  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustracja deklaracji i wywołanie  
 Następująca właściwość przechowuje pełną nazwę w postaci dwie nazwy składowych, imię i nazwisko. Podczas wywoływania kodu odczytuje `fullName`, `Get` procedury łączy dwie nazwy składowych i zwraca pełną nazwę. Gdy kod wywołujący przypisuje nową pełną nazwę, `Set` procedury próbuje podzielenie go na dwie nazwy składowych. Jeśli nie znajdzie spację, przechowuje on wszystkie jako imię.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 W poniższym przykładzie przedstawiono typowe wywołania procedur właściwość `fullName`.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Procedury funkcji](./function-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Różnice między właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)
- [Instrukcje: Tworzenie właściwości](./how-to-create-a-property.md)
- [Instrukcje: Wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)
- [Instrukcje: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: Umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)
- [Instrukcje: Pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)
