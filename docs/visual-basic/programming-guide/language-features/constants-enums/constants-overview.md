---
title: Stałe — Przegląd
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: f45cb12c6ef0f90b9c90190f30ce8600fec80947
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414521"
---
# <a name="constants-overview-visual-basic"></a>Stałe — Przegląd (Visual Basic)
Stała jest zrozumiałą nazwą, która przyjmuje miejsce liczby lub ciągu, który nie jest zmieniany. Stałe wartości magazynu, takie jak nazwa oznacza, pozostają takie same w czasie wykonywania aplikacji. Można znacznie poprawić czytelność kodu i ułatwić obsługę przy użyciu stałych. Należy używać ich w kodzie, który zawiera wartości, które są ponownie wyświetlane lub które są zależne od pewnych liczb, które trudno pamiętać lub nie mają oczywistych znaczenia.  
  
## <a name="how-to-create-and-use-constants"></a>Jak tworzyć i używać stałych  
 Visual Basic zawiera wiele wstępnie zdefiniowanych stałych, głównie do drukowania i wyświetlania. Możesz również utworzyć własne stałe przy `Const` użyciu instrukcji, korzystając z tych samych wytycznych, które należy wykonać w celu utworzenia nazwy zmiennej. Jeśli `Option Strict` jest `On` , należy jawnie zadeklarować typ stałej.  
  
 Zakres stałej, który jest zestawem wszystkich kodów, które mogą odwoływać się do niego bez kwalifikowania się jego nazwy, jest taka sama jak zmienna zadeklarowana w tej samej lokalizacji. Aby utworzyć stałą, która istnieje w zakresie określonej procedury, zadeklaruj ją wewnątrz tej procedury. Aby utworzyć stałą dostępną w całej aplikacji, należy ją zadeklarować przy użyciu `Public` słowa kluczowego w sekcji deklaracji klasy.  
  
> [!NOTE]
> Chociaż stałe są bardzo podobne do zmiennych, nie można ich modyfikować ani przypisywać do nich nowych wartości, jak w przypadku zmiennych.  
  
 Stałe, które są używane w kodzie, mogą być definiowane przez model obiektów dla formantów lub składników, z którymi pracujesz, lub mogą być zdefiniowane przez użytkownika (to oznacza, że zostały utworzone samodzielnie).  
  
## <a name="compile-time-and-run-time-constants"></a>Stałe czasu kompilacji i czasu wykonywania  
 Stała czasu kompilacji jest obliczana w momencie kompilowania kodu, podczas gdy stała czasu wykonywania może być obliczana tylko wtedy, gdy aplikacja jest uruchomiona. Stała czasu kompilacji będzie miała taką samą wartość za każdym razem, gdy aplikacja zostanie uruchomiona, a stała czasu wykonywania może się zmieniać za każdym razem. Stałe czasu kompilacji są wymagane dla przypadków takich jak granice tablicy, wyrażenia wielkości liter lub inicjatory modułu wyliczającego.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Definicja|Okres|  
|---|---|  
|[Instrukcje: deklarowanie stałej](how-to-declare-a-constant.md)|Wyjaśnia, w jaki sposób używać `Const` instrukcji w celu deklarowania stałej i ustawiania jej wartości; deklarując stałą, należy przypisać do wartości nazwę zrozumiałą.|  
|[Stałe zdefiniowane przez użytkownika](user-defined-constants.md)|Opisuje sposób tworzenia własnych stałych, w tym informacje na temat określania zakresu i sposób unikania odwołań cyklicznych.|  
|[Stała i typy literałów](constant-and-literal-data-types.md)|Zawiera informacje dotyczące sposobu, w jaki kompilator Visual Basic inicjuje stałe, gdy `Option Explicit` jest wyłączone.|  
|[Porady: grupowanie związanych wartości stałych](how-to-group-related-constant-values-together.md)|Pokazuje, jak grupować stałe wartości, które są powiązane.|  
  
## <a name="reference"></a>Dokumentacja  
  
|Definicja|Okres|  
|---|---|  
|[Stałe i wyliczenia](../../../language-reference/constants-and-enumerations.md)|Wyświetla listę stałych wstępnie zdefiniowanych przez Visual Basic.|  
|[Const, instrukcja](../../../language-reference/statements/const-statement.md)|Zawiera opis `Const` instrukcji i jej użycia.|  
|[Option Strict — Instrukcja](../../../language-reference/statements/option-strict-statement.md)|Zawiera opis `Option Strict` instrukcji i jej użycia.|  
  
## <a name="see-also"></a>Zobacz też

- [Enumerations — Przegląd](enumerations-overview.md)
- [Porady: inicjowanie zmiennej tablicy w języku Visual Basic](../arrays/how-to-initialize-an-array-variable.md)
