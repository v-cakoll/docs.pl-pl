---
title: -deterministyczne (opcje kompilatora C#)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2cb45ea6ed5c5795c910b2f6c3575b12f8189cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33213915"
---
# <a name="-deterministic"></a>-deterministyczna

Powoduje, że kompilator, aby utworzyć zestaw, której wyjście bajtów dla bajtów jest identyczne w kompilacji dla identycznych danych wejściowych. 

## <a name="syntax"></a>Składnia

```
-deterministic
```

## <a name="remarks"></a>Uwagi

Domyślnie dane wyjściowe kompilatora z danego zestawu danych wejściowych jest unikatowa, ponieważ kompilator dodaje znacznikiem czasu i identyfikatorem GUID, który jest generowany na podstawie liczby losowe. Możesz użyć `-deterministic` opcję, aby utworzyć *deterministyczne zestawu*, jedną z którego zawartość binarna jest identyczne w kompilacji, tak długo, jak dane wejściowe jest taka sama.

Kompilator uwzględnia następujące dane wejściowe na potrzeby determinizm:

- Sekwencja parametry wiersza polecenia.
- Zawartość pliku odpowiedzi .rsp — kompilatora.
- Dokładne wersja kompilatora używane i jego zestawów występujących w odwołaniach.
- Ścieżka bieżącego katalogu.
- Wszystkie pliki binarne treści jawnie przekazany do kompilatora bezpośrednio lub pośrednio, w tym:
    - Pliki źródłowe
    - przywoływanych zestawach
    - Przywoływany modułów
    - Zasoby
    - Plik klucza silnej nazwy
    - @ pliki odpowiedzi
    - Analizatory
    - Zestawy reguł
    - Dodatkowe pliki, które mogą być używane przez analizatory
- Bieżąca kultura (język, w którym diagnostyki i wyjątków są produkowane wiadomości).
- Domyślnym kodowaniem (lub bieżącej stronie kodowej) Jeśli nie określono kodowanie.
- Istnienie, brak i zawartość plików w ścieżkach wyszukiwania przez kompilator (określonej, na przykład przez `/lib` lub `/recurse`).
- Platforma CLR, na którym jest wykonywane przez kompilator.
- Wartość `%LIBPATH%`, co może wpłynąć na ładowanie zależności analizatora.

Gdy publicznie dostępnych źródeł, kompilacji deterministycznej może służyć do ustalenia, czy dane binarne ma być kompilowana z zaufanego źródła. Może być również przydatne w systemie kompilacji ciągłej do określenia, czy konieczne można wykonać kroki procesu kompilacji, które są zależne od zmian w pliku binarnym. 

## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
