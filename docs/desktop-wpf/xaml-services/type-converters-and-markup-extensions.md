---
title: Typy konwerterów i rozszerzenia znaczników dla XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services
- XAML [XAML Services], value converters
- XAML [XAML Services], markup extension services
- value converters for XAML [XAML Services]
- XAML [XAML Services], service context
ms.assetid: db07a952-05ce-4aa4-b6f9-aac7397d0326
ms.openlocfilehash: bee94b03d4fd6e6f5ef8571e83f554b381dd6582
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071655"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>Typy konwerterów i rozszerzenia znaczników dla XAML

Konwertery typów i rozszerzenia znaczników to dwie techniki używane przez systemy typu XAML i moduły zapisu XAML do generowania składników wykresu obiektów. Chociaż mają one pewne cechy, konwertery typów i rozszerzenia znaczników są reprezentowane inaczej w strumieniu węzła XAML. W tym zestawie dokumentacji konwertery typów, rozszerzenia znaczników i podobne konstrukcje są czasami zbiorczo określane jako konwertery wartości.

## <a name="value-converters"></a>Konwertery wartości

W języku XAML konwertery wartości są używane w różnych scenariuszach. Na poniższej liście przedstawiono różne typy konwerterów wartości w języku XAML:

- Konwerter typów

- Rozszerzenie znaczników

- Serializator wartości

- Pokrewna klasa lub klasa pomocy technicznej, która udostępnia logikę składni tekstu XAML

## <a name="type-converters"></a>Konwertery typów

W definicji usług .NET XAML konwertery typów <xref:System.ComponentModel.TypeConverter> są klasy, które pochodzą z klasy CLR. <xref:System.ComponentModel.TypeConverter>jest klasą, która była w .NET przed XAML istniał. Jego pierwotnym celem było obsługa okien właściwości i podobnych metafor edycji tekstowych dla właściwości IDE. Wprowadzenie formatu XAML do <xref:System.ComponentModel.TypeConverter> platformy .NET służy do konwertowania składni tekstu (znalezionej w wartości atrybutu lub węzła wartości XAML) na obiekt. <xref:System.ComponentModel.TypeConverter>może być również używany do serializacji wartości obiektu do składni tekstu. <xref:System.ComponentModel.TypeConverter>był również używany w poprzednich implementacjach XAML specyficznych dla struktury w Windows Presentation Foundation (WPF) i Windows Communication Foundation (WCF). Aby uzyskać więcej <xref:System.ComponentModel.TypeConverter> informacji na temat w języku XAML, zobacz [Konwertery typów dla XAML Overview](type-converters-overview.md).

## <a name="markup-extensions"></a>Rozszerzenia struktury znaczników

W implementacji usług .NET XAML rozszerzenia znaczników są <xref:System.Windows.Markup.MarkupExtension> klasy, które pochodzą z klasy. Rozszerzenia znaczników to koncepcja, która w tym formularzu jest pochodząca z języka XAML. Rozszerzenie znaczników można myśleć jako coś jak rozszerzalna sekwencja ucieczki, która wywołuje do klasy usługi, aby zapewnić jego logikę. Pod względem znaczników procesory XAML powszechnie rozpoznają rozszerzenie znaczników za pomocą sekwencji tekstowej, która rozpoczyna się od nawiasu klamrowego otwierającego ({) w ciągu tekstowym.

Rozszerzenia znaczników różnią się od konwerterów typów. Konwertery typów są zazwyczaj skojarzone z typami lub członkami. Są one wywoływane, gdy tworzenie wykresu obiektu lub serializacji napotka składnię tekstu, która jest skojarzona z tymi jednostkami.

Rozszerzenia znaczników są skojarzone z pojedynczą klasą usługi pomocniczej, ale można zastosować do dowolnej wartości elementu członkowskiego. (Można jednak zaimplementować rozszerzenie znaczników, aby celowo ograniczyć jego użycie do niektórych elementów członkowskich lub typów docelowych przy użyciu kontekstu usługi). Rozszerzenia znaczników mogą zastąpić skojarzenie konwertera typów. Można ich użyć do określenia wartości atrybutu dla elementów członkowskich, które w przeciwnym razie nie będą obsługiwać składni tekstu.

Aby uzyskać więcej informacji na temat wzorca implementacji rozszerzenia znaczników dla XAML, zobacz [Rozszerzenia znaczników dla XAML Overview](markup-extensions-overview.md).

## <a name="value-serializers"></a>Serializatory wartości

A <xref:System.Windows.Markup.ValueSerializer> jest konwerterem typu wyspecjalizowanego, który jest zoptymalizowany do konwersji obiektu na ciąg. A <xref:System.Windows.Markup.ValueSerializer> dla XAML może `ConvertFrom` nie implementować metody w ogóle. Implementacja <xref:System.Windows.Markup.ValueSerializer> uzyskuje usługi w sposób, <xref:System.ComponentModel.TypeConverter> który jest podobny do implementacji. Metody wirtualne zapewniają `context` parametr wejściowy. Parametr `context` jest typu <xref:System.Windows.Markup.IValueSerializerContext>, który dziedziczy z <xref:System.IServiceProvider> <xref:System.IServiceProvider.GetService%2A> interfejsu i ma metodę.

W systemie typu XAML i dla implementacji modułu zapisującego XAML, które używają przetwarzania pętli węzłów XAML do <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> serializacji, konwerter wartości skojarzony z typem lub elementem członkowskim jest zgłaszany przez własną właściwość. Znaczenie dla modułów zapisu XAML, <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> które <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> wykonują serializacji jest, że jeśli i istnieje, konwerter typu powinny być używane dla ścieżki ładowania i serializatora wartości powinny być używane dla ścieżki zapisywania. Jeśli <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> istnieje, <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> `null`ale jest , konwerter typów jest również używany dla ścieżki zapisywania.

## <a name="other-value-converters"></a>Inne konwertery wartości

Konwerter wartości jest rozszerzalny poza określone wzorce konwertera typu lub rozszerzenia znaczników. Jednak to dostosowanie wymagałoby również ponownego zdefiniowania systemu typu XAML, zgodnie z usługami .NET XAML Services. Istniejący system typów XAML ma reprezentacje i systemy raportowania dla konwerterów typów, rozszerzeń znaczników i serializatorów wartości, ale nie dla niestandardowych form konwersji wartości. Jeśli chcesz utworzyć konwertery wartości <xref:System.Xaml.Schema.XamlValueConverter%601> niestandardowych, użyj tego typu.

## <a name="type-converters-and-markup-extensions-in-combination"></a>Typ konwertery i rozszerzenia znaczników w kombinacji

Rozszerzenia znaczników i konwertery typów są używane w różnych sytuacjach w języku XAML. Chociaż kontekst jest dostępny dla użycia rozszerzenia znaczników, zachowanie konwersji typu właściwości, w których rozszerzenie znaczników zapewnia wartość, zazwyczaj nie jest sprawdzane w implementacjach rozszerzenia znaczników. Innymi słowy, nawet jeśli rozszerzenie znaczników zwraca `ProvideValue` ciąg tekstowy jako jego dane wyjściowe, zachowanie konwersji typu na tym ciągu, stosowane do określonej właściwości lub typ wartości właściwości nie jest wywoływana. Ogólnie rzecz biorąc celem rozszerzenia znaczników jest przetwarzanie ciągu i zwracanie obiektu bez dowolnego typu konwertera zaangażowanych.

## <a name="service-context-for-a-value-converter"></a>Kontekst usługi dla konwertera wartości

Podczas implementowania konwertera wartości często potrzebny jest dostęp do kontekstu, w którym stosuje się konwerter wartości. Ten kontekst jest znany jako kontekst usługi. Kontekst usługi może zawierać informacje, takie jak aktywny kontekst schematu XAML, dostęp do systemu mapowania typów, który zapewnia kontekst schematu XAML i moduł zapisujący obiekty XAML i tak dalej. Aby uzyskać więcej informacji na temat kontekstów usługi dostępnych dla konwertera wartości i sposobu uzyskiwania dostępu do usług, które może zapewnić kontekst usługi, zobacz [Konteksty usług dostępne dla konwerterów typów i rozszerzenia znaczników](service-contexts-with-type-converters-and-markup-extensions.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Rozszerzenia znaczników dla przeglądu XAML](markup-extensions-overview.md)
- [Typy konwerterów dla XAML — Omówienie](type-converters-overview.md)
- [Konteksty usług dostępne dla typów konwerterów i rozszerzeń znaczników](service-contexts-with-type-converters-and-markup-extensions.md)
