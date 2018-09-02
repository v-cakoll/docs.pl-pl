---
title: 'Porady: deklarowanie stałej (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
ms.openlocfilehash: ce45e4df7f74cd68bde0fb2adba10197a11edb1b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394317"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>Porady: deklarowanie stałej (Visual Basic)
Możesz użyć `Const` instrukcję, aby zadeklarować stałą i określanie jego wartości. Wartość, przez zadeklarowanie stałą, przypisać znaczącą nazwę. Po zadeklarowaniu stałej nie można modyfikować ani przypisywana nowa wartość.  
  
 Możesz deklarować stałą w procedurze lub w sekcji deklaracji modułu, klasy lub struktury. Klasa lub stałe na poziomie struktury są `Private` domyślnie, ale może być także zadeklarowana jako `Public`, `Friend`, `Protected`, lub `Protected Friend` na odpowiedni poziom dostępu kodu.  
  
 Stała musi mieć poprawną nazwę symboliczną (zasady są takie same jak w przypadku tworzenia nazwy zmiennych) i wyrażenie złożone, liczbą lub ciągiem stałe i operatory (ale nie wywołań funkcji).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>Aby zadeklarować — stała  
  
-   Deklaracja, która zawiera specyfikator dostępu do zapisu `Const` — słowo kluczowe i wyrażenie, tak jak w poniższych przykładach:  
  
     [!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     Gdy [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) jest `Off` i [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) jest `On`, należy jawnie zadeklarować stałą, określając typ danych (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, lub `String`).  
  
     Gdy `Option Infer` jest `On` lub `Option Strict` jest `Off`, stałej można zadeklarować bez określania typu danych za pomocą `As` klauzuli. Kompilator Określa typ stałej z typu wyrażenia. Aby uzyskać więcej informacji, zobacz [stała i typy danych literału](constant-and-literal-data-types.md).  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>Aby zadeklarować stałą, która ma typ danych podane jawnie  
  
-   Zapis deklaracji, która obejmuje `As` — słowo kluczowe i jawne danych typu, jak w następujących przykładach:  
  
     [!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     Można zadeklarować kilka stałych w jednym wierszu, mimo że kod jest bardziej czytelny, jeśli zadeklarujesz pojedynczej stałej dla każdego wiersza. Jeśli możesz zadeklarować kilka stałych w jednym wierszu, muszą mieć ten sam poziom dostępu (`Public`, `Private`, `Friend`, `Protected`, lub `Protected Friend`).  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>Aby zadeklarować kilka stałych w pojedynczym wierszu  
  
-   Deklaracje oddzielać przecinkiem i spacją, jak w poniższym przykładzie:  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Const, instrukcja](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [Typy danych Stała i Literał](constant-and-literal-data-types.md)  
 [Stałe — Przegląd](constants-overview.md) [porady: deklarowanie stałej](how-to-declare-a-constant.md) [stałe zdefiniowane przez użytkownika](user-defined-constants.md) [typy danych stała i literał](constant-and-literal-data-types.md) [jak: Grupa Powiązanych wartości stałych](how-to-group-related-constant-values-together.md) [Enumerations — Przegląd](enumerations-overview.md) [porady: deklarowanie wyliczeń](how-to-declare-enumerations.md) [jak: odnoszą się do elementu członkowskiego wyliczenia](how-to-refer-to-an-enumeration-member.md) [Wyliczenie i kwantyfikacja nazwy](enumerations-and-name-qualification.md) [porady: iterowanie za pomocą wyliczania](how-to-iterate-through-an-enumeration.md) [porady: Określanie ciągu skojarzonego z wartością wyliczenia](how-to-determine-the-string-associated-with-an-enumeration-value.md) [Kiedy stosować wyliczanie](when-to-use-an-enumeration.md)

 [Wyliczenia — przegląd](enumerations-overview.md)  
 [Stałe — przegląd](constants-overview.md)  
 [Porady: deklarowanie wyliczeń](how-to-declare-enumerations.md)  
 [Wyliczenia i kwalifikacja nazw](enumerations-and-name-qualification.md)  
 [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
