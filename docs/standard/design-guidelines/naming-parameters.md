---
title: Nazewnictwo parametrów
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 0d5c5cd144fbae88439ee981fbdb6e30ff487005
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290165"
---
# <a name="naming-parameters"></a>Nazewnictwo parametrów
Poza oczywistym powodem czytelności należy postępować zgodnie z wytycznymi dotyczącymi nazw parametrów, ponieważ parametry są wyświetlane w dokumentacji i w projektancie, gdy narzędzia projektowania wizualnego zapewniają funkcje IntelliSense i przeglądanie klas.

 ✔️ używać camelCasing w nazwach parametrów.

 ✔️ należy używać opisowych nazw parametrów.

 ✔️ ROZWAŻYĆ użycie nazw na podstawie znaczenia parametru, a nie typu parametru.

### <a name="naming-operator-overload-parameters"></a>Parametry przeciążenia operatora nazewnictwa
 ✔️ Użyj `left` i `right` dla nazw parametrów przeciążenia operatora binarnego, jeśli nie ma znaczenia dla parametrów.

 ✔️ używać `value` dla jednoargumentowych nazw parametrów przeciążenia, jeśli nie ma znaczenia dla parametrów.

 ✔️ NALEŻY rozważyć znaczące nazwy dla parametrów przeciążenia operatora, jeśli spowoduje to dodanie znaczącej wartości.

 ❌NIE używaj skrótów ani indeksów liczbowych dla nazw parametrów przeciążenia operatora.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania struktury](index.md)
- [Wskazówki dotyczące nazewnictwa](naming-guidelines.md)
