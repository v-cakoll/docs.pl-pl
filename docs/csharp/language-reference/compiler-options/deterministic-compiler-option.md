---
title: -deterministycznyC# (opcje kompilatora)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
ms.openlocfilehash: ed5d1db4618649391f88affad67e62dd9fc95925
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455187"
---
# <a name="-deterministic"></a>-deterministic

Powoduje, że kompilator tworzy zestaw, którego bajty w bajtach są identyczne w kompilacjach dla identycznych danych wejściowych.

## <a name="syntax"></a>Składnia

```console
-deterministic
```

## <a name="remarks"></a>Uwagi

Domyślnie dane wyjściowe kompilatora z danego zestawu danych wejściowych są unikatowe, ponieważ kompilator dodaje sygnaturę czasową i identyfikator GUID, który jest generowany na podstawie liczb losowych. Opcja `-deterministic` służy do tworzenia *deterministycznego zestawu*, który jest identyczny z zawartością binarną w kompilacjach, o ile dane wejściowe pozostają takie same.

Kompilator traktuje następujące dane wejściowe na potrzeby ustalenia:

- Sekwencja parametrów wiersza polecenia.
- Zawartość pliku odpowiedzi kompilatora. rsp.
- Dokładna wersja używanego kompilatora oraz zestawy, do których się odwołuje.
- Bieżąca ścieżka katalogu.
- Zawartość binarna wszystkich plików jawnie przekazana do kompilatora bezpośrednio lub pośrednio, w tym:
  - Pliki źródłowe
  - Przywoływane zestawy
  - Moduły, do których istnieją odwołania
  - Resources
  - Plik klucza o silnej nazwie
  - pliki odpowiedzi @
  - Analizatory
  - Zestaw reguł
  - Dodatkowe pliki, które mogą być używane przez analizatory
- Bieżąca kultura (dla języka, w którym są generowane diagnostyczne i komunikaty o wyjątkach).
- Domyślne kodowanie (lub bieżącą stronę kodową), Jeśli kodowanie nie jest określone.
- Istnienie, nieistnienie i zawartość plików na ścieżkach wyszukiwania kompilatora (na przykład przez `-lib` lub `-recurse`).
- Platforma CLR, na której jest uruchomiony kompilator.
- Wartość `%LIBPATH%`, która może wpływać na ładowanie zależności analizatora.

Gdy źródła są dostępne publicznie, można użyć deterministycznej kompilacji do ustalenia, czy plik binarny jest kompilowany z zaufanego źródła. Może być również przydatna w systemie ciągłej kompilacji, aby określić, czy należy wykonać kroki kompilacji, które są zależne od zmian w pliku binarnym.

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
