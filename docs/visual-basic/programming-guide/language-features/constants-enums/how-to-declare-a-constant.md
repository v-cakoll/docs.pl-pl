---
title: 'Porady: deklarowanie stałej'
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
ms.openlocfilehash: ffaa98f6af3d4b276f5c0b1153841acdea0809d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414482"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>Porady: deklarowanie stałej (Visual Basic)
Użyj instrukcji, `Const` Aby zadeklarować stałą i ustawić jej wartość. Deklarując stałą, należy przypisać do wartości nazwę zrozumiałą. Po zadeklarowaniu stałej nie można jej modyfikować ani przypisywać nowej wartości.  
  
 Należy zadeklarować stałą w ramach procedury lub w sekcji deklaracji modułu, klasy lub struktury. Stałe klasy lub struktury są `Private` Domyślnie, ale mogą być również deklarowane jako,, `Public` `Friend` `Protected` lub `Protected Friend` dla odpowiedniego poziomu dostępu kodu.  
  
 Stała musi mieć prawidłową nazwę symboliczną (reguły są takie same jak w przypadku tworzenia nazw zmiennych) i wyrażenie składające się ze stałych liczbowych lub ciągów oraz operatorów (ale bez wywołań funkcji).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>Aby zadeklarować stałą  
  
- Napisz deklarację, która zawiera specyfikator dostępu, `Const` słowo kluczowe i wyrażenie, jak w następujących przykładach:  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     Gdy [opcja wnioskowanie](../../../language-reference/statements/option-infer-statement.md) jest `Off` i [opcją Strict](../../../language-reference/statements/option-strict-statement.md) jest `On` , należy zadeklarować stałą jawnie przez określenie typu danych (,,,,,,,,, `Boolean` `Byte` `Char` `DateTime` `Decimal` `Double` `Integer` `Long` `Short` `Single` lub `String` ).  
  
     Gdy `Option Infer` jest `On` lub `Option Strict` jest `Off` , można zadeklarować stałą bez określania typu danych z `As` klauzulą. Kompilator określa typ stałej z typu wyrażenia. Aby uzyskać więcej informacji, zobacz [typy danych stałej i literału](constant-and-literal-data-types.md).  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>Aby zadeklarować stałą, która ma jawnie zadeklarowany typ danych  
  
- Napisz deklarację zawierającą `As` słowo kluczowe i jawny typ danych, jak w następujących przykładach:  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     Można zadeklarować wiele stałych w pojedynczym wierszu, chociaż kod jest bardziej czytelny, Jeśli zadeklarujesz tylko jedną stałą na wiersz. Jeśli zadeklarujesz wiele stałych w pojedynczym wierszu, muszą one mieć taki sam poziom dostępu ( `Public` , `Private` , `Friend` , `Protected` lub `Protected Friend` ).  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>Aby zadeklarować wiele stałych w pojedynczym wierszu  
  
- Oddziel deklaracje przecinkami i spacjami, tak jak w poniższym przykładzie:  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Const, instrukcja](../../../language-reference/statements/const-statement.md)
- [Stała i typy literałów](constant-and-literal-data-types.md)
- [Stałe — Przegląd](constants-overview.md)
- [Instrukcje: deklarowanie stałej](how-to-declare-a-constant.md)
- [Stałe zdefiniowane przez użytkownika](user-defined-constants.md)
- [Stała i typy literałów](constant-and-literal-data-types.md)
- [Porady: grupowanie związanych wartości stałych](how-to-group-related-constant-values-together.md)
- [Enumerations — Przegląd](enumerations-overview.md)
- [Instrukcje: deklarowanie wyliczeń](how-to-declare-enumerations.md)
- [Porady: odwoływanie się do elementu członkowskiego wyliczenia](how-to-refer-to-an-enumeration-member.md)
- [Wyliczenie i kwantyfikacja nazwy](enumerations-and-name-qualification.md)
- [Instrukcje: iterowanie za pomocą wyliczania](how-to-iterate-through-an-enumeration.md)
- [Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Kiedy stosować wyliczanie](when-to-use-an-enumeration.md)

- [Enumerations — Przegląd](enumerations-overview.md)
- [Stałe — Przegląd](constants-overview.md)
- [Instrukcje: deklarowanie wyliczenia](how-to-declare-enumerations.md)
- [Wyliczenie i kwantyfikacja nazwy](enumerations-and-name-qualification.md)
- [Option Strict — Instrukcja](../../../language-reference/statements/option-strict-statement.md)
- [Stałe i wyliczenia](../../../language-reference/constants-and-enumerations.md)
