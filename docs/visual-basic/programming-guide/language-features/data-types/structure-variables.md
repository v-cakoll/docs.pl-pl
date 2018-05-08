---
title: Zmienne struktur (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 0dad7bdcac5428753e252f3b26ca0a127c293a7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="structure-variables-visual-basic"></a>Zmienne struktur (Visual Basic)
Po utworzeniu struktury procedury poziomie modułu i zmienne można zadeklarować jako tego typu. Na przykład można utworzyć struktury rejestrującą informacje o systemie komputera. W poniższym przykładzie pokazano to.  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 Teraz można zadeklarować zmienne tego typu. Następujące oświadczenie przedstawiono to.  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  Klasy i modułów, struktur zadeklarowane za pomocą [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) domyślną dostępu publicznego. Jeśli planujesz struktury ma charakter prywatny, upewnij się, Zadeklaruj ją przy użyciu [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe.  
  
## <a name="access-to-structure-values"></a>Dostęp do wartości — struktura  
 Aby przypisać i pobrać wartości z elementów zmiennej struktury, należy użyć takiej samej składni używanej do ustawiania i pobierania właściwości w obiekcie. Umieść operatora dostępu do elementu członkowskiego (`.`) między nazwą zmiennej struktury i nazwy elementu. Poniższy przykład uzyskuje dostęp do elementów zmiennych wcześniej zadeklarowany jako typ `systemInfo`.  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a>Przypisywanie zmienne struktur  
 Można także przypisać jedną zmienną do innego, jeśli oba warunki są tego samego typu struktury. Wszystkie elementy struktury jeden zostanie skopiowana do odpowiednich elementów w innym. Następujące oświadczenie przedstawiono to.  
  
```  
yourSystem = mySystem  
```  
  
 Jeśli element struktury jest typem referencyjnym, takich jak `String`, `Object`, lub jest kopiowany tablicy wskaźników do danych. W poprzednim przykładzie Jeśli `systemInfo` zawiera zmienną obiektu, a następnie w poprzednim przykładzie będzie kopiowany wskaźnika z `mySystem` do `yourSystem`, a zmiany obiektu danych za pośrednictwem struktury co będzie obowiązywać podczas uzyskiwania dostępu do za pomocą innych struktury.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Instrukcje: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Struktury oraz inne elementy programowania](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [Struktury i klasy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Structure, instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
