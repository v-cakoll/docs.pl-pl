---
title: Zadeklarowane nazwy elementów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: 5b1f8ccc402f7f5928a33f434664b0f28d108e6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61828623"
---
# <a name="declared-element-names-visual-basic"></a>Zadeklarowane nazwy elementów (Visual Basic)
Każdy element zadeklarowany ma nazwę, nazywany również *identyfikator*, czyli kod używa się do niego.  
  
## <a name="rules"></a>reguły  
 Nazwa elementu w języku Visual Basic musi być zgodna z następującymi zasadami:  
  
- Musi zaczynać się od litery lub znaku podkreślenia (`_`).  
  
- Musi ona zawierać tylko znaki alfabetu, cyfry i znaki podkreślenia.  
  
- Jeśli zaczyna się od znaku podkreślenia musi zawierać co najmniej jeden znak alfabetu lub cyfrę dziesiętną.  
  
- Nie może być dłuższa niż 1023 znaków.  
  
 Limit długości 1023 znaków ma również zastosowanie do całego ciągu w pełni kwalifikowana nazwa, takich jak `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.  
  
 Poniższy przykład przedstawia niektóre nazwy prawidłowego elementu.  
  
 `aB123__45`  
  
 `_567`  
  
 Poniższy przykład przedstawia niektóre nazwy nieprawidłowy element. Pierwszy zawiera tylko znak podkreślenia, drugi zaczyna się od cyfry dziesiętne, a trzeci zawiera nieprawidłowy znak ($).  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  Nazwy elementów rozpoczynające się od podkreślenia (`_`) nie są częścią [niezależność od języka i składniki niezależne od języka](../../../../standard/language-independence-and-language-independent-components.md) (CLS), dzięki czemu kod zgodny ze specyfikacją CLS nie można użyć składnika, który definiuje takich nazw. Podkreślenia w innym miejscu, w nazwie elementu jest jednak zgodny ze specyfikacją CLS.  
  
### <a name="name-length-guidelines"></a>Wytyczne dotyczące długość nazwy  
 Jako to w praktyce Twoja nazwa powinna być możliwie krótkie podczas identyfikacji nadal wyraźnie rodzaj elementu. To zwiększa czytelność kodu i zmniejsza rozmiar wiersza długości i pliku źródłowego.  
  
 Z drugiej strony Twoja nazwa nie powinna być zbyt krótki, że nie odpowiednio opisano element reprezentuje i jak Twój kod używający tych informacji. Jest to ważne dla czytelności kodu. Jeśli ktoś inny spróbuje go zrozumieć lub samodzielnie przeglądasz go przez długi czas, po jego autorem, odpowiedni element nazw można zapisać znaczną ilość czasu.  
  
## <a name="escaped-names"></a>Nazwy wyjścia  
 Ogólnie rzecz biorąc, nazwa elementu nie może odpowiadać dowolnych słów kluczowych, zastrzeżone w języku Visual Basic, takie jak `Case` lub `Friend`. Jednakże można zdefiniować *poprzedzone znakiem zmiany znaczenia nazwa*, która jest ujęta w nawiasy kwadratowe (`[ ]`). Nazwa o zmienionym znaczeniu może odnosić się słowa kluczowego języka Visual Basic, ponieważ nawiasy, usuń wszelkie niejednoznaczności. Możesz także użyć nawiasów, gdy odwołujesz się do nazwy w dalszej części kodu.  
  
 Ogólnie rzecz biorąc, należy używać nazwy wyjścia tylko wtedy, gdy:  
  
- Kod został zmigrowany z poprzedniej wersji programu Visual Basic, który nie zarezerwować słowa kluczowego jako nazwy; lub  
  
- Pracujesz z kodu napisanego w innym języku, w którym dane słowo kluczowe nie jest zarezerwowana.  
  
 W przeciwnym razie należy rozważyć, jeśli jego nazwa jest w konflikcie ze słowem kluczowym, zmiana nazwy elementu. Zintegrowane środowisko programistyczne (IDE) zapewnia prosty sposób, aby to zrobić. Aby uzyskać więcej informacji, zobacz [Refactoring](/visualstudio/vb-ide/refactoring-vb).  
  
## <a name="case-sensitivity-in-names"></a>Rozróżnianie wielkości liter w nazwach  
 Nazwy elementów w języku Visual Basic jest rozróżniana wielkość liter. Oznacza to, że gdy kompilator porównuje dwie nazwy, które różnią się alfabetyczne tylko wielkością liter, interpretuje je jako tej samej nazwie. Na przykład, które uzna za `ABC` i `abc` do odwoływania się do tego samego elementu zadeklarowane.  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) używa jednak powiązania z uwzględnieniem wielkości liter. W związku z tym podczas tworzenia zestawu lub biblioteki DLL i był dostępny dla innych zestawów, nazwy nie są już bez uwzględniania wielkości liter. Na przykład, jeśli zdefiniujesz klasę z elementu o nazwie `ABC`, i innych zestawów, należy użyć klasy za pomocą środowiska uruchomieniowego języka wspólnego, ich musi odwoływać się do elementu jako `ABC`. Jeśli są później ponownie skompilować klasy i Zmień nazwę elementu do `abc`, zestawy, przy użyciu klasy nie będzie można uzyskać dostępu do tego elementu. W związku z tym po zwolnieniu zaktualizowanej wersji zestawu, nie należy zmieniać wielkość liter alfabetu wszelkie publiczne elementy.  
  
## <a name="names-and-locales"></a>Nazwy i ustawienia regionalne  
 Porównanie nazw jest niezależne od ustawień regionalnych. Jeśli dwie nazwy są zgodne w jednym ustawień regionalnych, mają gwarancję, że odpowiada we wszystkich ustawieniach regionalnych.  
  
## <a name="see-also"></a>Zobacz także

- [Zadeklarowane elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [Charakterystyka zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Instrukcje](../../../../visual-basic/language-reference/statements/index.md)
