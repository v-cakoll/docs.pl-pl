---
title: Stałe — Przegląd (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 2ec43254013df5444048b5197489c55217d5328a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648388"
---
# <a name="constants-overview-visual-basic"></a>Stałe — Przegląd (Visual Basic)
Stała jest znaczącą nazwę, która ma miejsce, liczby lub ciąg, który nie ulega zmianie. Stałe przechowywać wartości, które jak wskazuje nazwę, pozostają takie same w całej wykonywania aplikacji. Można znacznie poprawić czytelność kodu i ułatwić Obsługa za pomocą stałych. Korzystanie z nich kod, który zawiera wartości, które się ponownie lub to zależy od niektórych liczb, które są trudne do zapamiętania lub mieć znaczenia oczywiste.  
  
## <a name="how-to-create-and-use-constants"></a>Tworzenie i używanie stałych  
 Visual Basic zawiera szereg wstępnie zdefiniowanych stałe głównie przy użyciu drukowania i wyświetlania. Można również tworzyć własne stałe z `Const` instrukcji, korzystając z tego samego wskazówek, jak do tworzenia nazwy zmiennej. Jeśli `Option Strict` jest `On`, musisz jawnie zadeklarować typu stałej.  
  
 Stała zakresu, który jest zestaw wszystkich kod, który może odwoływać się do niego bez kwalifikujących się jego nazwa, jest taka sama jak zmiennej zadeklarowanej w tej samej lokalizacji. Aby utworzyć stałą, który istnieje w zakresie określona procedura, należy zadeklarować wewnątrz tej procedury. Aby utworzyć stałą, które są dostępne w całej aplikacji, Zadeklaruj ją przy użyciu `Public` — słowo kluczowe w sekcji deklaracji klasy.  
  
> [!NOTE]
>  Chociaż stałe wyglądać nieco zmiennych, nie można ich modyfikować ani przypisać nowe wartości dla nich jak do zmiennych.  
  
 Stałe w kodzie użyto mogą zostać zdefiniowane przez model obiektów dla formantów lub elementów pracy z lub mogą być zdefiniowane przez użytkownika (czyli tych samodzielnie utworzony).  
  
## <a name="compile-time-and-run-time-constants"></a>Stałe kompilacji i środowiska wykonawczego  
 Stała kompilacji jest obliczana w czasie kompilowania kodu, gdy tylko można obliczyć stałą czasu wykonywania, gdy aplikacja jest uruchomiona. Stała kompilacji będzie mieć taką samą wartość każdym uruchomieniu aplikacji, gdy stałą czasu wykonywania mogą ulec zmianie w każdym. Stałe kompilacji są wymagane w przypadkach, takich jak granice tablicy, wyrażenia case lub inicjatory modułu wyliczającego.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Definicja|Termin|  
|---|---|  
|[Instrukcje: deklarowanie stałej](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|Wyjaśniono, jak używać `Const` instrukcji deklarowanie stałej i ustaw jej wartość; przez deklarowanie stałej, Przypisz nazwę opisową wartości.|  
|[Stałe zdefiniowane przez użytkownika](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Opisuje, jak utworzyć własne stałe, w tym informacji na temat określania zakresu oraz uniknąć odwołań cyklicznych.|  
|[Typy danych Stała i Literał](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Zawiera informacje na temat sposobu kompilator Visual Basic inicjuje stałe podczas `Option Explicit` jest wyłączona.|  
|[Instrukcje: grupowanie powiązanych wartości stałych](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|Pokazuje sposób grupowania stałe wartości, które są powiązane.|  
  
## <a name="reference"></a>Tematy pomocy  
  
|Definicja|Termin|  
|---|---|  
|[Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Wyświetla listę stałych wstępnie zdefiniowane przez program Visual Basic.|  
|[Const, instrukcja](../../../../visual-basic/language-reference/statements/const-statement.md)|W tym artykule opisano `Const` instrukcji i jego użycia.|  
|[Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|W tym artykule opisano `Option Strict` instrukcji i jego użycia.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Porady: inicjowanie zmiennej tablicy w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
