---
title: -deterministyczne (Opcje kompilatora C#)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
ms.openlocfilehash: ed5d1db4618649391f88affad67e62dd9fc95925
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73455187"
---
# <a name="-deterministic"></a>-deterministic

Powoduje, że kompilator do produkcji zestawu, którego dane wyjściowe bajt dla bajtów jest identyczny w kompilacjach dla identycznych danych wejściowych.

## <a name="syntax"></a>Składnia

```console
-deterministic
```

## <a name="remarks"></a>Uwagi

Domyślnie dane wyjściowe kompilatora z danego zestawu danych wejściowych jest unikatowa, ponieważ kompilator dodaje sygnaturę czasową i identyfikator GUID, który jest generowany na podstawie liczb losowych. Opcja ta `-deterministic` służy do tworzenia *zestawu deterministycznego,* którego zawartość binarna jest identyczna w kompilacjach, o ile dane wejściowe pozostają takie same.

Kompilator uwzględnia następujące dane wejściowe w celu determinizmu:

- Sekwencja parametrów wiersza polecenia.
- Zawartość pliku odpowiedzi .rsp kompilatora.
- Dokładna wersja kompilatora używane i jego zestawy odwołuje.
- Bieżąca ścieżka katalogu.
- Zawartość binarna wszystkich plików jawnie przekazywane do kompilatora bezpośrednio lub pośrednio, w tym:
  - Pliki źródłowe
  - Zestawy odniesienia
  - Moduły referencyjne
  - Zasoby
  - Plik klucza silnej nazwy
  - @ pliki odpowiedzi
  - Analizatory
  - Zasady
  - Dodatkowe pliki, które mogą być używane przez analizatory
- Bieżąca kultura (dla języka, w którym są tworzone komunikaty diagnostyczne i wyjątki).
- Domyślne kodowanie (lub bieżąca strona kodowa), jeśli kodowanie nie jest określone.
- Istnienie, nieistnienie i zawartość plików na ścieżkach wyszukiwania kompilatora (określone `-lib` na `-recurse`przykład przez lub ).
- Platforma CLR, na której jest uruchamiany kompilator.
- Wartość `%LIBPATH%`, które mogą mieć wpływ na ładowanie zależności analizatora.

Gdy źródła są publicznie dostępne, kompilacji deterministycznej może służyć do ustalenia, czy plik binarny jest kompilowany z zaufanego źródła. Może być również przydatne w systemie ciągłej kompilacji do określania, czy kroki kompilacji, które są zależne od zmian do binarnego muszą być wykonywane.

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
