---
title: Nazewnictwo parametrów
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: ebe2e2db4b109057bf576d4e18cfe511c657707e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743829"
---
# <a name="naming-parameters"></a>Nazewnictwo parametrów
Poza oczywistym powodem czytelności należy postępować zgodnie z wytycznymi dotyczącymi nazw parametrów, ponieważ parametry są wyświetlane w dokumentacji i w projektancie, gdy narzędzia projektowania wizualnego zapewniają funkcje IntelliSense i przeglądanie klas.

 ✔️ używać camelCasing w nazwach parametrów.

 ✔️ należy używać opisowych nazw parametrów.

 ✔️ ROZWAŻYĆ użycie nazw na podstawie znaczenia parametru, a nie typu parametru.

### <a name="naming-operator-overload-parameters"></a>Parametry przeciążenia operatora nazewnictwa
 ✔️ używać `left` i `right` dla nazw parametrów przeciążenia operatora binarnego, jeśli nie ma znaczenia dla parametrów.

 ✔️ używać `value` dla nazw parametrów przeciążenia operatora jednoargumentowego, jeśli nie ma znaczenia dla parametrów.

 ✔️ NALEŻY rozważyć znaczące nazwy dla parametrów przeciążenia operatora, jeśli spowoduje to dodanie znaczącej wartości.

 ❌ nie używaj skrótów ani indeksów liczbowych dla nazw parametrów przeciążenia operatora.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
