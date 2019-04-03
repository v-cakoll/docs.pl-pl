---
title: Zmienne struktur (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 9a6e542e297a17f44d929235530ae6058cf13a36
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816333"
---
# <a name="structure-variables-visual-basic"></a>Zmienne struktur (Visual Basic)
Po utworzeniu struktury można zadeklarować zmienne poziom procedury i poziom modułu jako tego typu. Na przykład można utworzyć struktury rejestrującą informacje o systemie komputerowym. Poniższy przykład przedstawia to.  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 Możesz teraz zadeklarować zmienne tego typu. Następująca deklaracja przedstawia to.  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  W klasach i moduły struktury zadeklarowane za pomocą [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) domyślnie dostępu publicznego. Jeśli planujesz struktury jako prywatny, upewnij się, można zadeklarować za pomocą [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe.  
  
## <a name="access-to-structure-values"></a>Dostęp do wartości struktury  
 Aby przypisać i pobieranie wartości z elementów tworzonej tablicy zmiennej struktury, należy użyć tej samej składni jak umożliwia ustawianie i pobieranie właściwości w obiekcie. Umieść operator dostępu do elementu członkowskiego (`.`) między nazwą zmiennej struktury i nazwy elementu. Poniższy przykład uzyskuje dostęp do elementów zmiennych wcześniej zadeklarowany jako typ `systemInfo`.  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a>Przypisywanie zmienne struktur  
 Można także przypisać jedną zmienną do innego, jeśli obie są tego samego typu struktury. Wszystkie elementy jedną strukturę to skopiowanie na odpowiednie elementy w innym. Następująca deklaracja przedstawia to.  
  
```  
yourSystem = mySystem  
```  
  
 Jeśli element struktury jest typu odwołania, takich jak `String`, `Object`, lub tablicy, wskaźnik do danych jest kopiowany. W poprzednim przykładzie Jeśli `systemInfo` zawiera zmienną obiektu, a następnie w poprzednim przykładzie będą kopiowane wskaźnika z `mySystem` do `yourSystem`, a zmiany do obiektu danych za pomocą jedną strukturę będzie obowiązywać podczas uzyskiwania dostępu do za pomocą innych struktury.  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Instrukcje: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Struktury oraz inne elementy programowania](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Struktury i klasy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
