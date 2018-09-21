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
ms.openlocfilehash: 9f9aca20a3ff65d061c04a21e31db3fb5eab62ba
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46528999"
---
# <a name="-deterministic"></a>-deterministyczne

Powoduje, że kompilator generuje zestawu, którego dane wyjściowe dla bajt jest identyczna w kompilacjach identycznych danych wejściowych. 

## <a name="syntax"></a>Składnia

```
-deterministic
```

## <a name="remarks"></a>Uwagi

Domyślnie dane wyjściowe kompilatora z danego zestawu danych wejściowych jest unikatowa, ponieważ kompilator sam doda sygnaturę czasową i identyfikator GUID, który jest generowany na podstawie liczby losowe. Możesz użyć `-deterministic` opcję, aby wygenerować *deterministyczne zestawu*, jedną z którego zawartość binarna jest identyczne w kompilacji, tak długo, jak dane wejściowe pozostają bez zmian.

Kompilator traktuje następujące dane wejściowe na potrzeby determinizm:

- Sekwencja parametry wiersza polecenia.
- Zawartość pliku odpowiedzi rsp kompilatora.
- Dokładne wersję kompilatora, używane, a jego przywoływanych zestawów.
- Ścieżka bieżącego katalogu.
- Binarny zawartość wszystkich plików jawnie przekazywane do kompilator bezpośrednio lub pośrednio, w tym:
    - Pliki źródłowe
    - przywoływanych zestawach
    - Moduły odwołania
    - Resources
    - Plik klucza silnej nazwy
    - @ pliki odpowiedzi
    - Analizatory
    - Zestawy reguł
    - Dodatkowe pliki, które mogą być używane przez analizatorów
- Bieżącą kulturą (język, w których dane diagnostyczne i wyjątków są produkowane wiadomości).
- Domyślnym kodowaniem (lub bieżącej stronie kodowej) Jeśli nie określono kodowanie.
- Istnienie, nie istnieje i zawartość plików na ścieżki wyszukiwania kompilatora (określone, na przykład przez `/lib` lub `/recurse`).
- Platforma CLR, na którym jest uruchamiany kompilator.
- Wartość `%LIBPATH%`, co może wpłynąć na ładowanie zależności analizatora.

W przypadku publicznie dostępnego źródła kompilacji deterministycznej może służyć do ustalenia, czy plik binarny jest kompilowany z zaufanego źródła. Również może być przydatne w systemie kompilacji ciągłej do określenia, czy należy wykonać kroki kompilacji, które są zależne od zmian w pliku binarnym. 

## <a name="see-also"></a>Zobacz też  

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
