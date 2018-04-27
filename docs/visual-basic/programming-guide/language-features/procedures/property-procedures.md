---
title: Procedury własności (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0d9df6f381c89263aa16315fb06a2b3b0d645bbf
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="property-procedures-visual-basic"></a>Procedury własności (Visual Basic)
Procedury właściwości jest szereg instrukcji, które modyfikowania właściwości niestandardowych dla modułu, klasy lub struktury. Procedury własności są również znane jako *metod dostępu do właściwości*.  
  
 Visual Basic zawiera następujące procedury właściwości:  
  
-   A `Get` procedury zwraca wartość właściwości. Jest ona wywoływana, gdy uzyskujesz dostęp do właściwości w wyrażeniu.  
  
-   A `Set` procedury ustawia właściwość na wartość, tym odwołanie do obiektu. Jest to przypisanie wartości do właściwości.  
  
 Procedury własności zazwyczaj Definiowanie parami przy użyciu `Get` i `Set` instrukcji, ale można zdefiniować tych procedurach, tylko jeśli właściwość jest tylko do odczytu ([instrukcja Get](../../../../visual-basic/language-reference/statements/get-statement.md)) lub w trybie tylko do zapisu ([ustawić Instrukcja](../../../../visual-basic/language-reference/statements/set-statement.md)).  
  
 Można pominąć `Get` i `Set` procedury w przypadku przy użyciu automatycznie implementowanych właściwości. Aby uzyskać więcej informacji, zobacz [Auto-Implemented właściwości](./auto-implemented-properties.md).  
  
 Można zdefiniować właściwości klas, struktur i modułów. Właściwości są `Public` domyślnie oznacza można Zadzwoń z dowolnego miejsca w aplikacji, które mogą uzyskiwać dostęp do właściwości kontenera.  
  
 Porównanie właściwości i zmiennych, zobacz [różnice pomiędzy właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md).  
  
## <a name="declaration-syntax"></a>Składnia deklaracji  
 Właściwość jest zdefiniowana za pomocą bloku kodu ujętą w nawiasy klamrowe [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md) i `End Property` instrukcji. W tym bloku każdej procedury właściwości pojawia się jako wewnętrzny bloku ujętą w nawiasy klamrowe instrukcji deklaracji (`Get` lub `Set`) i dopasowywania `End` deklaracji.  
  
 Składnia deklaracji właściwości i jej procedury wygląda następująco:  
  
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
  
 `Modifiers` Można określić poziom dostępu i informacji dotyczących przeładowanie, zastępowanie udostępniania i przesłanianie, a także określa, czy właściwość jest tylko do odczytu lub w trybie tylko do zapisu. `AccessLevel` Na `Get` lub `Set` procedura może być żadnych poziom, który jest bardziej restrykcyjny niż poziom dostępu do określonej dla samej właściwości. Aby uzyskać więcej informacji, zobacz [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md).  
  
### <a name="data-type"></a>Typ danych  
 Typ danych właściwości i poziom główny dostępu są definiowane w `Property` instrukcji nie w procedurach właściwości. Właściwości może mieć tylko jednego typu danych. Na przykład nie można zdefiniować właściwości do przechowywania `Decimal` wartość, ale pobrać `Double` wartość.  
  
### <a name="access-level"></a>Poziom dostępu  
 Jednak można zdefiniować na poziom główny dostępu dla właściwości i bardziej ograniczyć poziom dostępu w jednej z jego właściwości procedur. Na przykład można zdefiniować `Public` właściwości, a następnie definiuje `Private Set` procedury. `Get` Pozostaje procedury `Public`. Można zmienić poziom dostępu w tylko jednej z właściwości procedur i można tworzyć tylko on bardziej restrykcyjny niż poziom dostępu do podmiotu zabezpieczeń. Aby uzyskać więcej informacji, zobacz [porady: deklarowanie właściwości z mieszanych poziomów dostępu](./how-to-declare-a-property-with-mixed-access-levels.md).  
  
## <a name="parameter-declaration"></a>Deklaracja parametru  
 Deklarowanie tak samo jak w przypadku każdego parametru [procedury Sub](./sub-procedures.md), z wyjątkiem tego, że mechanizm przekazywania musi być `ByVal`.  
  
 Dla każdego parametru na liście parametrów ma następującą składnię:  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 Jeśli parametr jest opcjonalny, należy również podać wartości domyślnej jako części swojej deklaracji. Składnia służąca do określania wartości domyślnej jest następujący:  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a>Wartość właściwości  
 W `Get` procedury, zwracana wartość jest dostarczany do wywoływania wyrażenia jako wartość właściwości.  
  
 W `Set` procedury, nowa wartość właściwości jest przekazywany parametr `Set` instrukcji. Jawnie deklarować parametr, należy ją zadeklarować tego samego typu danych jako wartość właściwości. Jeśli parametr nie jest zadeklarować, kompilator używa parametru niejawne `Value` do reprezentowania nową wartość do przypisania do właściwości.  
  
## <a name="calling-syntax"></a>Składnia wywoływania  
 Wywołanie procedury właściwości jest niejawnie przez utworzenie odwołania do właściwości. Możesz użyć nazwy właściwości taki sam sposób, należy użyć nazwy zmiennej, z wyjątkiem tego, że należy podać wartości dla wszystkich argumentów, które nie są opcjonalne i listy argumentów należy ująć w nawias. Jeśli nie jest dostarczony bez argumentów, opcjonalnie można pominąć nawiasów.  
  
 Składnia niejawne wywołanie `Set` procedura wygląda następująco:  
  
 `propertyname[(argumentlist)] = expression`  
  
 Składnia niejawne wywołanie `Get` procedura wygląda następująco:  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustracja deklaracji i wywołanie  
 Następująca właściwość przechowuje pełną nazwę jako dwóch nazw składników, imię i nazwisko. Gdy odczytuje kod wywołujący `fullName`, `Get` procedura łączy dwie nazwy składników i zwraca pełną nazwę. Gdy kod wywołujący przypisuje nową pełną nazwę, `Set` procedury próbuje podzielić dwie nazwy składowych. Jeśli nie znajdzie spację, przechowuje on wszystkie jako pierwszej nazwy.  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 W poniższym przykładzie przedstawiono typowe wywołania procedury właściwości `fullName`.  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Procedury funkcji](./function-procedures.md)  
 [Procedury operatorów](./operator-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Różnice pomiędzy właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md)  
 [Instrukcje: tworzenie właściwości](./how-to-create-a-property.md)  
 [Instrukcje: wywoływanie procedury właściwości](./how-to-call-a-property-procedure.md)  
 [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Instrukcje: umieszczanie wartości we właściwości](./how-to-put-a-value-in-a-property.md)  
 [Instrukcje: pobieranie wartości z właściwości](./how-to-get-a-value-from-a-property.md)
