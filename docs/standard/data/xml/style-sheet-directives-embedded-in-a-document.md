---
title: Dyrektywy dotyczące arkusza stylów osadzone w dokumencie
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
ms.openlocfilehash: 19e25ab7262bb006144eea71e74bd7454066b3f6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710157"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a>Dyrektywy dotyczące arkusza stylów osadzone w dokumencie

Czasami istniejący kod XML zawiera dyrektywę arkusz stylów `<?xml:stylesheet?>`. Program Microsoft Internet Explorer akceptuje to jako alternatywę dla `<?xml-stylesheet?>` składni. Gdy dane XML zawierają `<?xml:stylesheet?>` dyrektywę, jak pokazano w poniższych danych, próba załadowania tych danych do pliku XML Document Object Model (dom) zgłasza wyjątek.

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

Dzieje się tak, `<?xml:stylesheet?>` ponieważ jest uznawany za nieprawidłową **ProcessingInstruction** do modelu DOM. Każdy **ProcessingInstruction**, zgodnie z przestrzeniami nazw w specyfikacji XML, może mieć tylko nazwy bez dwukropka (NCNames), w przeciwieństwie do nazw kwalifikowanych (QName).

Z sekcji 6 przestrzeni nazw w specyfikacji XML, efekt zastosowania metod **Load** i **LoadXml** jest zgodny ze specyfikacją w dokumencie:

- Wszystkie typy elementów i nazwy atrybutów zawierają jeden dwukropek.

- Brak nazw jednostek, obiektów docelowych ProcessingInstruction ani nazw notacji zawierających dowolne dwukropki.

Z `<?xml:stylesheet?>` zawierającym dwukropek, nastąpi naruszenie reguły w drugim punkcie.

Zgodnie z zaleceniami organizacja World Wide Web Consortium (W3C) [kojarzenia arkuszy stylów z dokumentami XML w wersji 1,0 zalecenie](https://www.w3.org/TR/xml-stylesheet/), instrukcja przetwarzania, aby skojarzyć arkusz stylów XSLT z dokumentem XML `<?xml-stylesheet?>`, z kreską zastępującą dwukropek.

## <a name="see-also"></a>Zobacz też

- [XML Document Object Model (DOM)](xml-document-object-model-dom.md)
