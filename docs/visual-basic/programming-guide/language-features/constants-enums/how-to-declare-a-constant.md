---
title: "Porady: deklarowanie stałej (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.constant
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 554f659e060087228fb43efd8b9d06103e21e980
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-a-constant-visual-basic"></a>Porady: deklarowanie stałej (Visual Basic)
Możesz użyć `Const` instrukcji deklarowanie stałej i ustaw jej wartość. Przez deklarowanie stałej, nazwę opisową przypisać wartość. Po zadeklarowaniu stałą, nie można zmodyfikować ani przypisywana nowa wartość.  
  
 Należy zadeklarować stała w procedurze lub w sekcji deklaracji modułu, klasy lub struktury. Klasa lub stałe na poziomie struktury są `Private` domyślnie, ale może również być zadeklarowany jako `Public`, `Friend`, `Protected`, lub `Protected Friend` na odpowiedni poziom dostępu kodu.  
  
 Stała musi mieć poprawną nazwę symboliczną (reguły są takie same jak do tworzenia nazwy zmiennych) i wyrażeń składają numeryczny lub ciąg stałe i operatory (ale nie wywołania funkcji).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>Deklarowanie stałej  
  
-   Zapis deklaracji, która obejmuje specyfikator dostępu `Const` — słowo kluczowe i wyrażenia, na przykład:  
  
     [!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     Gdy [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) jest `Off` i [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) jest `On`, musisz jawnie zadeklarować stałą przez określenie typu danych (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, lub `String`).  
  
     Gdy `Option Infer` jest `On` lub `Option Strict` jest `Off`, mogą zadeklarować stałą bez określania typu danych z `As` klauzuli. Kompilator Określa typ stałej z typem wyrażenia. Aby uzyskać więcej informacji, zobacz [stała i typy danych literału](constant-and-literal-data-types.md).  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>Aby zadeklarować o typie danych jawnie określonej stałej  
  
-   Zapis deklaracji, która obejmuje `As` — słowo kluczowe i jawnych danych, wpisz na przykład:  
  
     [!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     Można zadeklarować wiele stałych w jednym wierszu, mimo że kod jest bardziej przejrzysta zadeklarować pojedynczej stałej w jednym wierszu. W przypadku wielu stałe w jednym wierszu, ich muszą mieć ten sam poziom dostępu (`Public`, `Private`, `Friend`, `Protected`, lub `Protected Friend`).  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>Aby zadeklarować wiele stałych w jednym wierszu  
  
-   Deklaracje oddzielać przecinkiem i spacją, jak w poniższym przykładzie:  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Const — instrukcja](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [Stała i typy literałów](constant-and-literal-data-types.md)  
 [Stałe — Przegląd](constants-overview.md) [porady: deklarowanie stałej](how-to-declare-a-constant.md) [stałe zdefiniowane przez użytkownika](user-defined-constants.md) [stała i typy literałów](constant-and-literal-data-types.md) [porady: Grupa Związanych wartości stałych](how-to-group-related-constant-values-together.md) [Enumerations — Przegląd](enumerations-overview.md) [porady: deklarowanie wyliczeń](how-to-declare-enumerations.md) [porady: odwołuje się do elementu członkowskiego wyliczenia](how-to-refer-to-an-enumeration-member.md) [Wyliczenie i kwantyfikacja nazwy](enumerations-and-name-qualification.md) [porady: iterowanie za pomocą wyliczenie](how-to-iterate-through-an-enumeration.md) [porady: Określanie ciągu skojarzonego z wartością wyliczenia](how-to-determine-the-string-associated-with-an-enumeration-value.md) [Kiedy stosować wyliczanie](when-to-use-an-enumeration.md)

 [Enumerations — Przegląd](enumerations-overview.md)  
 [Stałe — Przegląd](constants-overview.md)  
 [Porady: deklarowanie wyliczeń](how-to-declare-enumerations.md)  
 [Wyliczenie i kwantyfikacja nazwy](enumerations-and-name-qualification.md)  
 [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
