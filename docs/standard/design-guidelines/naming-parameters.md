---
title: Nazewnictwo parametrów
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 0bb67056bb39b6a5f372191a1d0b0bb0dc1fe4d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709182"
---
# <a name="naming-parameters"></a>Nazewnictwo parametrów
Poza oczywistym powodem czytelności należy postępować zgodnie z wytycznymi dotyczącymi nazw parametrów, ponieważ parametry są wyświetlane w dokumentacji i w projektancie, gdy narzędzia projektowania wizualnego zapewniają funkcje IntelliSense i przeglądanie klas.  
  
 **✓ DO** Użyj camelCasing w nazwach parametrów.  
  
 **✓ DO** Użyj nazwy opisowej parametrów.  
  
 **✓ CONSIDER** przy użyciu nazwy parametru znaczenie niż typ parametru.  
  
### <a name="naming-operator-overload-parameters"></a>Parametry przeciążenia operatora nazewnictwa  
 **✓ DO** użyj `left` i `right` dla nazw parametrów przeciążenia operatora binarnego Jeśli znaczenia parametrów nie istnieje.  
  
 **✓ DO** użyj `value` dla Jednoargumentowy operator przeciążenia nazwy parametrów, jeśli żadnego znaczenia parametrów nie istnieje.  
  
 **✓ CONSIDER** łatwy do rozpoznania nazwy dla operatora przeciążenia parametrów, jeśli wykonanie tej tak dodaje wartość.  
  
 **X DO NOT** Użyj skrótów lub wskaźniki liczbowe dla operatora przeciążenia nazwy parametrów.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
