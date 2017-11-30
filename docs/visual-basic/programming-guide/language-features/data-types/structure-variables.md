---
title: Zmienne struktur (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef42c44de84caffde909eb2b3e9361016a6abb97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Podstawowe typy danych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Typy wartości i typy referencyjne](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Rozwiązywanie problemów z typów danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Porady: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Struktury oraz inne elementy programowania](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [Struktury i klasy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Structure — instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)
