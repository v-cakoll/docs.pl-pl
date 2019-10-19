---
title: 'Porady: kontrolowanie dostępności zmiennej (Visual Basic)'
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
ms.openlocfilehash: 84aaeecdbd3cc8ab12589c0342b982bf3f1c8529
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582618"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>Porady: kontrolowanie dostępności zmiennej (Visual Basic)
Możesz kontrolować dostępność zmiennej, określając jej *poziom dostępu*. Poziom dostępu określa kod, który ma uprawnienia do odczytu lub zapisu do zmiennej.  
  
- *Zmienne składowe* (zdefiniowane na poziomie modułu i poza każdą procedurę) domyślnie mają dostęp publiczny, co oznacza, że każdy kod, który może je zobaczyć, może uzyskać do nich dostęp. Można to zmienić, określając modyfikator dostępu.  
  
- *Zmienne lokalne* (zdefiniowane wewnątrz procedury) mają nominalny dostęp publiczny, chociaż tylko kod w ramach procedury ma dostęp do nich. Nie można zmienić poziomu dostępu zmiennej lokalnej, ale można zmienić poziom dostępu do procedury, która go zawiera.  
  
 Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="private-and-public-access"></a>Dostęp prywatny i publiczny  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>Aby udostępnić zmienną tylko z poziomu jej modułu, klasy lub struktury  
  
1. Umieść [instrukcję Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza jakąkolwiek procedurą.  
  
2. Dołącz [prywatne](../../../../visual-basic/language-reference/modifiers/private.md) słowo kluczowe do instrukcji `Dim`.  
  
     Możesz odczytać lub zapisać w zmiennej z dowolnego miejsca w module, klasie lub strukturze, ale nie spoza niej.  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>Aby udostępnić zmienną z dowolnego kodu, który może go zobaczyć  
  
1. Dla zmiennej składowej należy umieścić instrukcję `Dim` dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza dowolną procedurą.  
  
2. Dołącz słowo kluczowe [Public](../../../../visual-basic/language-reference/modifiers/public.md) do instrukcji `Dim`.  
  
     Można odczytać lub zapisać w zmiennej z dowolnego kodu, który współdziała z zestawem.  
  
 —lub—  
  
1. Dla zmiennej lokalnej Umieść instrukcję `Dim` dla zmiennej wewnątrz procedury.  
  
2. Nie dodawaj słowa kluczowego `Public` w instrukcji `Dim`.  
  
     Możesz odczytać lub zapisać w zmiennej z dowolnego miejsca w ramach procedury, ale nie spoza niej.  
  
## <a name="protected-and-friend-access"></a>Dostęp chroniony i przyjazny  
 Można ograniczyć poziom dostępu zmiennej do jej klasy i wszelkich klas pochodnych lub do zestawu. Można również określić Unię tych ograniczeń, co umożliwia dostęp z kodu w dowolnej klasie pochodnej lub w innym miejscu w tym samym zestawie. Należy określić tę Unię, łącząc `Protected` i `Friend` słowa kluczowe w tej samej deklaracji.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>Aby udostępnić zmienną tylko z poziomu jej klasy i wszystkich klas pochodnych  
  
1. Umieść instrukcję `Dim` dla zmiennej wewnątrz klasy, ale poza jakąkolwiek procedurą.  
  
2. Uwzględnij [chronione](../../../../visual-basic/language-reference/modifiers/protected.md) słowo kluczowe w instrukcji `Dim`.  
  
     Można odczytać lub zapisać w zmiennej z dowolnego miejsca w klasie, a także z poziomu dowolnej klasy pochodnej, ale nie spoza żadnej klasy w łańcuchu pochodnym.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>Aby udostępnić zmienną tylko z poziomu tego samego zestawu  
  
1. Umieść instrukcję `Dim` dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza jakąkolwiek procedurą.  
  
2. Dołącz słowo kluczowe [zaprzyjaźnione](../../../../visual-basic/language-reference/modifiers/friend.md) w instrukcji `Dim`.  
  
     Możesz odczytać lub zapisać w zmiennej z dowolnego miejsca w module, klasie lub strukturze, a także z dowolnego kodu w tym samym zestawie, ale nie spoza zestawu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono deklaracje zmiennych z `Public`, `Protected`, `Friend`, `Protected Friend` i `Private` poziomów dostępu. Należy pamiętać, że gdy instrukcja `Dim` określa poziom dostępu, nie trzeba uwzględniać słowa kluczowego `Dim`.  
  
```vb  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Im bardziej restrykcyjny poziom dostępu zmiennej, tym mniejsze prawdopodobieństwo, że złośliwy kod może być niewłaściwym użyciem.  
  
## <a name="see-also"></a>Zobacz także

- [Poziomy dostępu w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Dim, instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Public](../../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../../visual-basic/language-reference/modifiers/private.md)
