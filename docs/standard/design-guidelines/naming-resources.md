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
ms.openlocfilehash: 762ba99c4751ba40f5f33e99455cf950af35cdf6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290152"
---
# <a name="naming-resources"></a>Nazewnictwo zasobów
Ponieważ zasoby lokalizowalne mogą być przywoływane za pośrednictwem pewnych obiektów, tak jakby były właściwościami, wskazówki dotyczące nazewnictwa dla zasobów są podobne do wytycznych dotyczących właściwości.

 ✔️ używać PascalCasing w kluczach zasobów.

 ✔️ Podaj opis, a nie krótkie identyfikatory.

 ❌NIE używaj słów kluczowych właściwych dla języka dla głównych języków CLR.

 ✔️ używać tylko znaków alfanumerycznych i podkreśleń w przypadku nazw zasobów.

 ✔️ używać następującej konwencji nazewnictwa dla zasobów komunikatów o wyjątkach.

 Identyfikator zasobu powinien być nazwą typu wyjątku i krótkim identyfikatorem wyjątku:

 `ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`
 `ArgumentExceptionFileNameIsMalformed`

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania struktury](index.md)
- [Wskazówki dotyczące nazewnictwa](naming-guidelines.md)
