---
title: Nazwy zadeklarowanych elementów
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
ms.openlocfilehash: cdba2b5f3e17fc6666ca653abd7f4bd7dfb31c4a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392925"
---
# <a name="declared-element-names-visual-basic"></a>Zadeklarowane nazwy elementów (Visual Basic)
Każdy zadeklarowany element ma nazwę, nazywaną również *identyfikatorem*, który jest używany przez kod do odwoływania się do niego.  
  
## <a name="rules"></a>Reguły  
 Nazwa elementu w Visual Basic musi być zgodna z następującymi regułami:  
  
- Musi zaczynać się od litery lub znaku podkreślenia ( `_` ).  
  
- Musi zawierać tylko znaki alfanumeryczne, cyfry dziesiętne i podkreślenia.  
  
- Musi zawierać co najmniej jedną literę lub cyfrę dziesiętną, jeśli zaczyna się od znaku podkreślenia.  
  
- Nie może być dłuższa niż 1023 znaków.  
  
 Limit długości 1023 znaków ma zastosowanie również do całego ciągu w pełni kwalifikowanej nazwy, na przykład `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement` .  
  
 Poniższy przykład pokazuje nieprawidłowe nazwy elementów.  
  
 `aB123__45`  
  
 `_567`  
  
 W poniższym przykładzie przedstawiono niektóre nieprawidłowe nazwy elementów. Pierwszy zawiera tylko podkreślenie, drugi zaczyna się cyfrą dziesiętną, a trzecia zawiera nieprawidłowy znak ($).  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
> Nazwy elementów zaczynające się od znaku podkreślenia ( `_` ) nie są częścią [niezależną od języka i składników niezależnych od języka](../../../../standard/language-independence-and-language-independent-components.md) (CLS), więc kod zgodny ze specyfikacją CLS nie może używać składnika, który definiuje takie nazwy. Jednakże podkreślenie w każdym innym miejscu w nazwie elementu jest zgodne ze specyfikacją CLS.  
  
### <a name="name-length-guidelines"></a>Wskazówki dotyczące długości nazwy  
 Ze względu na to, że Twoja nazwa powinna być tak krótka, jak to możliwe, podczas gdy nadal jasno identyfikuje charakter elementu. Poprawia to czytelność kodu i zmniejsza długość wiersza i rozmiar pliku źródłowego.  
  
 Z drugiej strony, Twoja nazwa nie powinna być tak krótka, aby nie opisująca znaczenia elementu i sposobu jego użycia przez kod. Jest to ważne dla czytelności kodu. Jeśli ktoś inny próbuje zrozumieć ten element, lub jeśli ty przeglądasz ją przez długi czas po jego zapisaniu, odpowiednie nazwy elementów mogą zaoszczędzić znaczną ilość czasu.  
  
## <a name="escaped-names"></a>Nazwy o zmienionym znaczeniu  
 Ogólnie rzecz biorąc, nazwa elementu nie może być zgodna ze słowami kluczowymi zarezerwowanych przez Visual Basic, takich jak `Case` lub `Friend` . Można jednak zdefiniować *nazwę ucieczki*, która jest ujęta w nawiasy kwadratowe ( `[ ]` ). Nazwa o zmienionym znaczeniu może być zgodna ze słowem kluczowym Visual Basic, ponieważ nawiasy usuwają dowolną niejednoznaczność. Możesz również użyć nawiasów, gdy odwołujesz się do nazwy w dalszej części kodu.  
  
 Ogólnie rzecz biorąc należy używać nazw unikowych tylko wtedy, gdy:  
  
- Twój kod został zmigrowany z poprzedniej wersji Visual Basic, która nie zarezerwował słowa kluczowego używanego jako nazwa; oraz  
  
- Pracujesz z kodem zapisanym w innym języku, w którym określone słowo kluczowe nie jest zarezerwowane.  
  
 W przeciwnym razie należy rozważyć zmianę nazwy elementu, jeśli jego nazwa powoduje konflikt ze słowem kluczowym. Zintegrowane środowisko programistyczne (IDE) zapewnia łatwy sposób wykonania tej czynności. Aby uzyskać więcej informacji, zobacz [Refaktoryzacja](/visualstudio/ide/refactoring-in-visual-studio).  
  
## <a name="case-sensitivity-in-names"></a>Rozróżnianie wielkości liter w nazwach  
 W nazwach elementów w Visual Basic nie jest rozróżniana wielkość liter. Oznacza to, że gdy kompilator porównuje dwie nazwy, które różnią się tylko wielkością liter, interpretuje je jako tę samą nazwę. Na przykład uważa `ABC` i `abc` odwołuje się do tego samego zadeklarowanego elementu.  
  
 Jednak środowisko uruchomieniowe języka wspólnego (CLR) używa powiązania z rozróżnianiem wielkości liter. W związku z tym, podczas tworzenia zestawu lub biblioteki DLL i udostępnienia go innym zestawom nazwy nie są dłuższe. Na przykład, jeśli zdefiniujesz klasę z elementem o nazwie `ABC` , a inne zestawy używają klasy za pomocą środowiska uruchomieniowego języka wspólnego, muszą odwoływać się do elementu jako `ABC` . Jeśli następnie ponownie skompilujesz klasę i zmienisz nazwę elementu na `abc` , inne zestawy używające klasy nie będą miały już dostępu do tego elementu. W związku z tym po wydaniu zaktualizowanej wersji zestawu nie należy zmieniać wielkości liter każdego z elementów publicznych.  
  
## <a name="names-and-locales"></a>Nazwy i ustawienia regionalne  
 Porównanie nazw jest niezależne od ustawień regionalnych. Jeśli dwie nazwy są zgodne z jednym ustawieniem regionalnym, są one gwarantowane do dopasowania we wszystkich ustawieniach regionalnych.  
  
## <a name="see-also"></a>Zobacz też

- [Zadeklarowane elementy](index.md)
- [Charakterystyka zadeklarowanych elementów](declared-element-characteristics.md)
- [Odwołania do elementów zadeklarowanych](references-to-declared-elements.md)
- [Instrukcje](../../../language-reference/statements/index.md)
