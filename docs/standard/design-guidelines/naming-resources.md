---
title: Nazewnictwo zasobów
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: 95aff35569e58eacfd064609140a29b53e0036da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743818"
---
# <a name="naming-resources"></a>Nazewnictwo zasobów
Ponieważ zasoby lokalizowalne mogą być przywoływane za pośrednictwem pewnych obiektów, tak jakby były właściwościami, wskazówki dotyczące nazewnictwa dla zasobów są podobne do wytycznych dotyczących właściwości.

 ✔️ używać PascalCasing w kluczach zasobów.

 ✔️ Podaj opis, a nie krótkie identyfikatory.

 ❌ nie używać słów kluczowych właściwych dla języka dla głównych języków CLR.

 ✔️ używać tylko znaków alfanumerycznych i podkreśleń w przypadku nazw zasobów.

 ✔️ używać następującej konwencji nazewnictwa dla zasobów komunikatów o wyjątkach.

 Identyfikator zasobu powinien być nazwą typu wyjątku i krótkim identyfikatorem wyjątku:

 `ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`
 `ArgumentExceptionFileNameIsMalformed`

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
