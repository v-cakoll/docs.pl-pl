---
title: 'Instrukcje: Kontrolowanie dostępności zmiennej (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
ms.openlocfilehash: fb400b113e3f3305f5b724734b2bf9aa9425d03f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311529"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>Instrukcje: Kontrolowanie dostępności zmiennej (Visual Basic)
Kontrolowanie dostępności zmiennej, określając jego *poziom dostępu*. Poziom dostępu decyduje o tym, jaki kod ma uprawnienie do odczytu lub zapisu do zmiennej.  
  
-   *Zmienne Członkowskie* (zdefiniowany na poziomie modułu i na zewnątrz dowolnej procedury) domyślnie publicznym dostępem, który oznacza, że wszelki kod, który je wyświetlić mają do nich dostęp. Można to zmienić, określając modyfikatora dostępu.  
  
-   *Zmienne lokalne* (zdefiniowane wewnątrz procedury) nominalnie ma dostęp publiczny, mimo że tylko kod w ramach ich procedury mają do nich dostęp. Nie można zmienić poziomu dostępu do zmiennej lokalnej, ale można zmienić poziomu dostępu procedury, która go zawiera.  
  
 Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="private-and-public-access"></a>Dostęp do prywatnych i publicznych  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>Aby zmienna był dostępny tylko w obrębie jego modułu, klasy lub struktury  
  
1. Miejsce [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) zmiennej wewnątrz modułu, klasy lub struktury, ale poza programem dowolnej procedury.  
  
2. Obejmują [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe w `Dim` instrukcji.  
  
     Może odczytać lub zapisać zmiennej z dowolnego miejsca w ramach modułu, klasy lub struktury, ale nie z poza nim.  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>Aby udostępnić zmienną z dowolnego kodu, który można zobaczyć, jak to  
  
1. Dla zmiennej składowej, umieść `Dim` instrukcji dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza programem dowolnej procedury.  
  
2. Obejmują [publicznych](../../../../visual-basic/language-reference/modifiers/public.md) — słowo kluczowe w `Dim` instrukcji.  
  
     Można odczytu lub zapisu do zmiennej wszelki kod, który współdziała z zestawu.  
  
 —lub—  
  
1. Dla zmiennej lokalnej, należy umieścić `Dim` instrukcji dla zmiennej wewnątrz procedury.  
  
2. Nie dołączaj `Public` — słowo kluczowe w `Dim` instrukcji.  
  
     Może odczytać lub zapisać zmiennej z dowolnego miejsca, w ramach procedury, ale nie z poza nim.  
  
## <a name="protected-and-friend-access"></a>Chronione i dostępu przyjaznego  
 Można ograniczyć poziomu dostępu zmiennej, do swojej klasy i wszystkie klasy pochodne lub własnego zestawu. Można również określić sumę tych ograniczeń, która zezwala na dostęp z kodu w dowolnej klasy pochodnej lub w innym miejscu, w tym samym zestawie. Należy określić ten Unii, łącząc `Protected` i `Friend` słów kluczowych w tej samej deklaracji.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>Aby zmienna był dostępny tylko w obrębie swojej klasy i wszystkie klasy pochodne  
  
1. Miejsce `Dim` instrukcji dla zmiennej wewnątrz klasy, ale poza programem dowolnej procedury.  
  
2. Obejmują [chronione](../../../../visual-basic/language-reference/modifiers/protected.md) — słowo kluczowe w `Dim` instrukcji.  
  
     Może odczytać lub zapisać zmiennej z dowolnego miejsca, w ramach klasy, a także z poziomu dowolnej klasy pochodnej z niego, ale nie z poza dowolnej klasy w łańcuchu pochodnym.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>Aby zmienna był dostępny tylko w obrębie tego samego zestawu  
  
1. Miejsce `Dim` instrukcji dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza programem dowolnej procedury.  
  
2. Obejmują [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) — słowo kluczowe w `Dim` instrukcji.  
  
     Może odczytać lub zapisać zmiennej z dowolnego miejsca w ramach modułu, klasy lub struktury, a także z dowolnego kodu, w tym samym zestawie, ale nie z spoza zestawu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano deklaracje zmiennych z `Public`, `Protected`, `Friend`, `Protected Friend`, i `Private` poziomy dostępu. Należy pamiętać, że w przypadku `Dim` Instrukcja określa poziom dostępu, nie musisz uwzględnić `Dim` — słowo kluczowe.  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Bardziej restrykcyjny poziom dostępu do zmiennej, z niego korzystać mniejszy szanse, że złośliwy kod może być niepoprawne.  
  
## <a name="see-also"></a>Zobacz także

- [Poziomy dostępu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Dim, instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Public](../../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../../visual-basic/language-reference/modifiers/private.md)
