---
title: Ograniczenia
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: f7e19977a011565bb4b1536af5cab195f8a01017
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347369"
---
# <a name="visual-basic-limitations"></a>Ograniczenia Visual Basic
Wcześniejsze wersje Visual Basic wymuszają granice w kodzie, takie jak długość nazw zmiennych, liczba zmiennych dozwolona w modułach i rozmiar modułu. W Visual Basic .NET te ograniczenia były swobodne, co zapewnia większą swobodę pisania i rozmieszczania kodu.  
  
 Limity fizyczne są zależne od większej ilości pamięci w czasie wykonywania niż kwestie dotyczące czasu kompilacji. W przypadku korzystania z rozsądnych praktyk programistycznych i dzielenia dużych aplikacji na wiele klas i modułów, istnieje bardzo mało znaczące prawdopodobieństwo napotkania wewnętrznego ograniczenia Visual Basic.  
  
 Poniżej przedstawiono niektóre ograniczenia, które mogą wystąpić w skrajnych przypadkach:  
  
- **Długość nazwy.** Nazwa każdego zadeklarowanego elementu programowania zawiera maksymalną liczbę znaków. Ta wartość maksymalna ma zastosowanie do całego ciągu kwalifikacji, jeśli nazwa elementu jest kwalifikowana. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
- **Długość wiersza.** W fizycznym wierszu kodu źródłowego istnieje maksymalnie 65535 znaków. Logiczny wiersz kodu źródłowego może być dłuższy w przypadku używania znaków kontynuacji wiersza. Zobacz [jak: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
- **Wymiary tablicy.** Istnieje maksymalna liczba wymiarów, które można zadeklarować dla tablicy. Ogranicza to liczbę indeksów, których można użyć do określenia elementu tablicy. Zobacz [Wymiary tablicy w Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
- **Długość ciągu.** Istnieje maksymalna liczba znaków Unicode, które można przechowywać w jednym ciągu. Zobacz [Typ danych ciągu](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
- **Długość ciągu środowiska.** Dla każdego ciągu środowiska, który jest używany jako argument wiersza polecenia, istnieje maksymalnie 32768 znaków. Jest to ograniczenie na wszystkich platformach.  
  
## <a name="see-also"></a>Zobacz także

- [Struktura programu i konwencje związane z kodami](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Konwencje nazewnictwa Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
