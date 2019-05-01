---
title: Stałe — Przegląd (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 2939110de77718baf32e2a0d8f1aa52dba997cf3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907091"
---
# <a name="constants-overview-visual-basic"></a>Stałe — Przegląd (Visual Basic)
Stałe są znaczącą nazwę, która zajmuje miejsce liczbą lub ciągiem, który nie jest zmieniany. Stałe przechowywać wartości, które jak wskazuje nazwa, pozostają takie same w całej wykonywania aplikacji. Można znacznie zwiększyć czytelność kodu i ułatwić obsługę przy użyciu stałych. Ich używać w kodzie, który zawiera wartości, które się ponownie lub zależy niektórych liczb, które są trudne do zapamiętania lub nie mają oczywiste znaczenia.  
  
## <a name="how-to-create-and-use-constants"></a>Jak utworzyć i używać stałych  
 Visual Basic zawiera szereg wstępnie zdefiniowanych stałych, głównie za pomocą drukowania i wyświetlania. Można również utworzyć własne stałych z `Const` instrukcję, używając te same wytyczne, jak w przypadku tworzenia nazwy zmiennej. Jeśli `Option Strict` jest `On`, należy jawnie deklarować typ stałej.  
  
 Stała zakresu, który jest zestawem cały kod, który może odwoływać się do niego bez kwalifikowania nazwy, jest taka sama, jak Zmienna zadeklarowana w tej samej lokalizacji. Aby utworzyć stałą, znajdującą się w zakresie określonej procedury, należy zadeklarować ją w ramach tej procedury. Aby utworzyć stałą, która jest dostępna w całej aplikacji, Zadeklaruj go przy użyciu `Public` — słowo kluczowe w sekcji deklaracji klasy.  
  
> [!NOTE]
>  Mimo, że stałe nieco przypominają zmienne, nie można ich modyfikować ani przypisać do nich nowych wartości, jak to możliwe do zmiennych.  
  
 Stałe, należy użyć w kodzie można zdefiniować przez model obiektów dla formantów lub składniki pracujesz z lub mogą być zdefiniowane przez użytkownika (czyli tych utworzonych samodzielnie).  
  
## <a name="compile-time-and-run-time-constants"></a>Stałe w czasie kompilacji i czasu wykonywania  
 Stałą czasu kompilacji jest obliczana w czasie, którego kod jest kompilowany, gdy tylko można obliczyć stałą czasu wykonywania, gdy aplikacja jest uruchomiona. Stałą czasu kompilacji będzie mieć taką samą wartość w każdym razem, gdy aplikacja jest uruchamiana, gdy stałą środowiska wykonawczego mogą ulec zmianie każdorazowo. Stałe kompilacji są wymagane w przypadkach, takich jak granice tablicy, wyrażeniami case lub inicjatory modułu wyliczającego.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Definicja|Termin|  
|---|---|  
|[Instrukcje: Deklarowanie stałej](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|Opis sposobu użycia `Const` instrukcję, aby zadeklarować stałą i określanie jego wartości; przez zadeklarowanie stałą, nazwę opisową przypisywania do wartości.|  
|[Stałe zdefiniowane przez użytkownika](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Opisuje sposób tworzenia własnych stałych, włącznie z informacjami o zakresu oraz uniknąć odwołania cykliczne.|  
|[Typy danych Stała i Literał](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Zawiera informacje na temat jak kompilator języka Visual Basic inicjuje stałe podczas `Option Explicit` jest wyłączona.|  
|[Instrukcje: Grupowanie powiązanych ze sobą wartości stałych](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|Pokazuje, jak należy zgrupować wartości stałych, które są ze sobą powiązane.|  
  
## <a name="reference"></a>Tematy pomocy  
  
|Definicja|Termin|  
|---|---|  
|[Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Wyświetla listę stałych wstępnie zdefiniowane przez program Visual Basic.|  
|[Const, instrukcja](../../../../visual-basic/language-reference/statements/const-statement.md)|W tym artykule opisano `Const` instrukcji i jego użycia.|  
|[Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|W tym artykule opisano `Option Strict` instrukcji i jego użycia.|  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Instrukcje: Inicjowanie zmiennej tablicy w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
