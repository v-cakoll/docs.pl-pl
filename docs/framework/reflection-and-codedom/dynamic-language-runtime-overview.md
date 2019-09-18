---
title: Omówienie środowiska uruchomieniowego języka dynamicznego | Microsoft Docs
ms.date: 03/30/2017
helpviewer_keywords:
- dynamic language runtime
- IronPython
- DLR
- IronRuby
ms.assetid: f769a271-8aff-4bea-bfab-6160217ce23d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6b6de8f0a178914c46ba5a65dfb56795cf23c71
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046124"
---
# <a name="dynamic-language-runtime-overview"></a>Przegląd środowiska uruchomieniowego języka dynamicznego

*Moduł uruchomieniowy języka dynamicznego* (DLR) to środowisko uruchomieniowe, które dodaje zestaw usług dla języków dynamicznych do środowiska uruchomieniowego języka wspólnego (CLR). DLR ułatwia opracowywanie dynamicznych języków do uruchamiania na .NET Framework i Dodawanie funkcji dynamicznych do statycznie wpisanych języków.

Języki dynamiczne mogą identyfikować typ obiektu w czasie wykonywania, natomiast w językach z statycznym typem, takimi C# jak i Visual Basic (w przypadku `Option Explicit On`używania) należy określić typy obiektów w czasie projektowania. Przykłady języków dynamicznych to Lisp, Smalltalk, JavaScript, PHP, Ruby, Python, ColdFusion, Lua, Cobra i Groovy.

Większość języków dynamicznych zapewnia deweloperom następujące korzyści:

- Możliwość korzystania z szybkiej pętli do przesyłania opinii (REPL lub pętli odczytu i oceny). Pozwala to wprowadzić kilka instrukcji i od razu wykonać je, aby zobaczyć wyniki.

- Obsługa zarówno rozwoju z góry, jak i bardziej tradycyjnego rozwoju w dół. Na przykład w przypadku użycia podejścia w dół można wywołać funkcje, które nie zostały jeszcze zaimplementowane, a następnie dodać podstawowe implementacje, gdy będą potrzebne.

- Łatwiejsze Refaktoryzacja i modyfikacje kodu, ponieważ nie trzeba zmieniać deklaracji typu statycznego w całym kodzie.

Języki dynamiczne sprawiają, że są to doskonałe Języki tworzenia skryptów. Klienci mogą łatwo rozbudować aplikacje utworzone przy użyciu języków dynamicznych z nowymi poleceniami i funkcjami. Języki dynamiczne są również często używane do tworzenia witryn sieci Web i testów, obsługi farm serwerów, tworzenia różnych narzędzi i wykonywania transformacji danych.

Celem DLR jest umożliwienie działania systemu w językach dynamicznych na .NET Framework i umożliwienie im współdziałania z platformą .NET. DLR dodaje dynamiczne obiekty do C# i Visual Basic do obsługi zachowania dynamicznego w tych językach i umożliwia ich współdziałanie z językami dynamicznymi.

DLR ułatwia również tworzenie bibliotek, które obsługują operacje dynamiczne. Na przykład jeśli masz bibliotekę, która korzysta z obiektów XML lub JavaScript Object Notation (JSON), obiekty mogą być wyświetlane jako obiekty dynamiczne w językach, które używają DLR. Dzięki temu użytkownicy biblioteki zapisują składniowo prostsze i bardziej naturalny kod służący do pracy z obiektami i uzyskiwania dostępu do elementów członkowskich obiektu.

Na przykład można użyć poniższego kodu, aby zwiększyć licznik w XML w C#.

`Scriptobj.SetProperty("Count", ((int)GetProperty("Count")) + 1);`

Za pomocą DLR, zamiast tego można użyć poniższego kodu dla tej samej operacji.

`scriptobj.Count += 1;`

Podobnie jak w przypadku środowiska CLR, DLR jest częścią .NET Framework i są dostarczane z pakietami instalacyjnymi .NET Framework i Visual Studio. Wersja DLR typu open source jest również dostępna do pobrania w repozytorium [IronLanguages/DLR](https://github.com/IronLanguages/dlr) w witrynie GitHub.

> [!NOTE]
> Wersja DLR typu open source zawiera wszystkie funkcje DLR, które są zawarte w programie Visual Studio i .NET Framework. Zapewnia również dodatkowe wsparcie dla implementacji języka. Aby uzyskać więcej informacji, zobacz dokumentację repozytorium [IronLanguages/DLR](https://github.com/IronLanguages/dlr) w witrynie GitHub.

Przykłady języków opracowanych przy użyciu DLR obejmują następujące elementy:

- IronPython. Dostępne jako oprogramowanie Open Source w witrynie [GitHub](https://github.com/IronLanguages/ironpython2) w sieci Web.

- IronRuby. Dostępne jako oprogramowanie Open Source w witrynie sieci Web [Rubyforge](https://go.microsoft.com/fwlink/?LinkId=141044) .

## <a name="primary-dlr-advantages"></a>Podstawowe zalety DLR
 DLR zapewnia następujące korzyści.

### <a name="simplifies-porting-dynamic-languages-to-the-net-framework"></a>Upraszcza przenoszenie języków dynamicznych do .NET Framework
 DLR umożliwia implementacje języka, aby uniknąć tworzenia analizatorów leksykalnych, parserów, analiz semantycznych, generatorów kodu i innych narzędzi, które tradycyjnie musiały utworzyć siebie. Aby użyć DLR, język musi generować *drzewa wyrażeń*, które reprezentują kod poziomu języka w strukturze w kształcie drzewa, procedury pomocnika środowiska uruchomieniowego i opcjonalne dynamiczne obiekty, które implementują <xref:System.Dynamic.IDynamicMetaObjectProvider> interfejs. DLR i .NET Framework automatyzują wiele zadań związanych z analizą kodu i generowaniem kodu. Dzięki temu implementacje języka mogą koncentrować się na unikatowych funkcjach językowych.

### <a name="enables-dynamic-features-in-statically-typed-languages"></a>Włącza funkcje dynamiczne w językach, które są wpisane statycznie
 Istniejące .NET Framework języki takie jak C# i Visual Basic mogą tworzyć obiekty dynamiczne i używać ich razem z obiektami o statycznym typie. Na przykład, C# a Visual Basic mogą używać obiektów dynamicznych do odbicia w języku HTML, Document Object Model (dom) i .NET.

### <a name="provides-future-benefits-of-the-dlr-and-net-framework"></a>Oferuje przyszłe korzyści z DLR i .NET Framework
 Języki zaimplementowane przy użyciu DLR mogą korzystać z przyszłych DLR i .NET Framework ulepszeń. Na przykład jeśli .NET Framework wersja nowej wersji, która ma ulepszony Moduł wyrzucania elementów bezużytecznych lub szybszy czas ładowania zestawu, Języki wdrożone za pomocą DLR natychmiast uzyskają te same korzyści. Jeśli DLR dodaje optymalizacje, takie jak Lepsza kompilacja, wydajność jest również lepsza dla wszystkich języków wdrożonych przy użyciu DLR.

### <a name="enables-sharing-of-libraries-and-objects"></a>Umożliwia udostępnianie bibliotek i obiektów
 Obiekty i biblioteki zaimplementowane w jednym języku mogą być używane przez inne języki. DLR umożliwia również współdziałanie między językami statycznymi i dynamicznymi. Na przykład C# można zadeklarować obiekt dynamiczny, który używa biblioteki, która jest zapisywana w języku dynamicznym. W tym samym czasie Języki dynamiczne mogą korzystać z bibliotek z .NET Framework.

### <a name="provides-fast-dynamic-dispatch-and-invocation"></a>Zapewnia szybkie dynamiczne wysyłanie i wywoływanie
 DLR zapewnia szybkie wykonywanie operacji dynamicznych dzięki obsłudze zaawansowanej pamięci podręcznej polimorficznej. DLR tworzy reguły dla operacji wiązania, które używają obiektów do niezbędnych implementacji środowiska uruchomieniowego, a następnie buforuje te reguły, aby uniknąć tworzenia powiązań między zasobami podczas kolejnych wykonywania tego samego kodu w tych samych typach obiektów.

## <a name="dlr-architecture"></a>Architektura DLR
 Na poniższej ilustracji przedstawiono architekturę środowiska uruchomieniowego języka dynamicznego.

 ![Omówienie architektury środowiska uruchomieniowego języka dynamicznego](./media/dlr-archoverview.png "DLR_ArchOverview") Architektura DLR

 DLR dodaje zestaw usług do środowiska CLR w celu lepszego obsługi języków dynamicznych. Są to następujące usługi:

- Drzewa wyrażeń. DLR używa drzew wyrażeń do reprezentowania semantyki języka. W tym celu DLR ma rozszerzone drzewa wyrażeń LINQ, aby obejmowały przepływ sterowania, przypisanie i inne węzły modelowania języka. Aby uzyskać więcej informacji, zobacz [drzewa wyrażeńC#()](../../csharp/programming-guide/concepts/expression-trees/index.md) lub [drzewa wyrażeń (Visual Basic)](../../visual-basic/programming-guide/concepts/expression-trees/index.md).

- Wywołaj buforowanie lokacji. *Lokacja wywołania dynamicznego* to miejsce w kodzie, w którym można wykonać operację podobną `a + b` do `a.b()` lub dla obiektów dynamicznych. DLR przechowuje w pamięci podręcznej `a` cechy `b` i (zazwyczaj typy tych obiektów) oraz informacje o operacji. Jeśli taka operacja została wykonana wcześniej, DLR pobiera wszystkie niezbędne informacje z pamięci podręcznej do szybkiej wysyłki.

- Współdziałanie obiektów dynamicznych. DLR zawiera zestaw klas i interfejsów, które reprezentują dynamiczne obiekty i operacje, które mogą być używane przez implementacje języka i autorów bibliotek dynamicznych. Te klasy i interfejsy obejmują <xref:System.Dynamic.IDynamicMetaObjectProvider> <xref:System.Dynamic.DynamicObject>, <xref:System.Dynamic.DynamicMetaObject>,, i <xref:System.Dynamic.ExpandoObject>.

DLR używa programu Binders w witrynach wywołań do komunikowania się nie tylko z .NET Framework, ale z innymi infrastrukturami i usługami, w tym Silverlight i COM. Obiekty wiążące hermetyzują semantykę języka i określają sposób wykonywania operacji w witrynie wywołania przy użyciu drzew wyrażeń. Umożliwia to dynamiczne i statycznie wpisane Języki, które używają DLR do udostępniania bibliotek i uzyskiwania dostępu do wszystkich technologii obsługiwanych przez DLR.

## <a name="dlr-documentation"></a>Dokumentacja DLR
 Aby uzyskać więcej informacji na temat korzystania z wersji typu open source DLR w celu dodania dynamicznego zachowania do języka lub dowiedzieć się, jak włączyć używanie języka dynamicznego z .NET Framework, zapoznaj się z dokumentacją repozytorium [IronLanguages/DLR](https://github.com/IronLanguages/dlr/tree/master/Docs) w witrynie GitHub.

## <a name="see-also"></a>Zobacz także

- <xref:System.Dynamic.ExpandoObject>
- <xref:System.Dynamic.DynamicObject>
- [Środowisko uruchomieniowe języka wspólnego](../../standard/clr.md)
- [Drzewa wyrażeń (C#)](../../csharp/programming-guide/concepts/expression-trees/index.md)
- [Drzewa wyrażeń (Visual Basic)](../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Przewodnik: Tworzenie i używanie obiektów dynamicznych](../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
