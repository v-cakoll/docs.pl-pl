---
title: Konwencje nazewnictwa
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: 20531e379ddf9b93a278795e9b3c0eb91b47e077
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398347"
---
# <a name="visual-basic-naming-conventions"></a>Visual Basic — Konwencje nazewnictwa
Po wybraniu nazwy elementu w aplikacji Visual Basic pierwszy znak tej nazwy musi być znakiem alfabetycznym lub podkreśleniem. Należy jednak zauważyć, że nazwy zaczynające się od znaku podkreślenia nie są zgodne z [zależnościami od języka i składnikami niezależnymi od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Poniższe sugestie dotyczą nazewnictwa.  
  
- Zacznij od każdego oddzielnego wyrazu w nazwie wielką literą, jak w `FindLastRecord` i `RedrawMyForm` .  
  
- Rozpocznij funkcję i nazwy metod z czasownikiem, jak w `InitNameArray` lub `CloseDialog` .  
  
- Rozpocznij od klasy, struktury, modułu i nazw właściwości rzeczownik, jak w `EmployeeName` lub `CarAccessory` .  
  
- Rozpocznij nazwy interfejsów z prefiksem "I", po którym następuje rzeczownik lub fraza rzeczownikowa, taka jak `IComponent` lub za pomocą przymiotnika opisującego zachowanie interfejsu, na przykład `IPersistable` . Nie używaj znaku podkreślenia i rzadko używaj skrótów, ponieważ skróty mogą spowodować pomyłkę.  
  
- Rozpocznij nazwy programu obsługi zdarzeń z rzeczownikiem opisującym typ zdarzenia, po którym następuje `EventHandler` sufiks "", jak w " `MouseEventHandler` ".  
  
- W nazwach klas argumentów zdarzeń zawiera `EventArgs` sufiks "".  
  
- Jeśli zdarzenie ma koncepcję "Before" lub "After", użyj sufiksu w obecności lub w ciągu ostatnich, jak w " `ControlAdd` " lub " `ControlAdded` ".  
  
- Dla długich lub często używanych terminów użyj skrótów, aby zachować odpowiednie długości nazw, na przykład "HTML", a nie "HTML". Ogólnie rzecz biorąc, nazwy zmiennych o wartości większej niż 32 znaków są trudne do odczytania na monitorze o niskiej rozdzielczości. Upewnij się również, że skróty są spójne w całej aplikacji. Losowe przełączanie w projekcie między "HTML" i "HTML" może prowadzić do pomyłek.  
  
- Należy unikać używania nazw w zakresie wewnętrznym, które są takie same jak nazwy w zewnętrznym zakresie. Błędy mogą wynikać z niewłaściwej zmiennej. Jeśli występuje konflikt między zmienną i słowem kluczowym o tej samej nazwie, należy zidentyfikować słowo kluczowe, poprzedzając je odpowiednią biblioteką typów. Na przykład jeśli masz zmienną o nazwie, można `Date` użyć `Date` funkcji wewnętrznej tylko przez wywołanie <xref:System.DateTime.Date%2A?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Zobacz też

- [Słowa kluczowe jako nazwy elementów w kodzie](keywords-as-element-names-in-code.md)
- [Me, My, MyBase i MyClass](me-my-mybase-and-myclass.md)
- [Nazwy zadeklarowanych elementów](../language-features/declared-elements/declared-element-names.md)
- [Struktura programu i konwencje związane z kodem](program-structure-and-code-conventions.md)
- [Dokumentacja języka Visual Basic](../../language-reference/index.md)
