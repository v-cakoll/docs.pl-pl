---
title: Omówienie środowiska uruchomieniowego języka dynamicznego | Dokumentacja firmy Microsoft
ms.date: 03/30/2017
helpviewer_keywords:
- dynamic language runtime
- IronPython
- DLR
- IronRuby
ms.assetid: f769a271-8aff-4bea-bfab-6160217ce23d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09cd345daffa2418b33f032e8bab47c81e2a8526
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dynamic-language-runtime-overview"></a>Przegląd środowiska uruchomieniowego języka dynamicznego
*Środowisko uruchomieniowe języka dynamicznego* (DLR) jest środowisko uruchomieniowe, który dodaje zestaw usług dla języków dynamicznych do środowisko uruchomieniowe języka wspólnego (CLR). DLR ułatwia tworzenie dynamicznych języki do uruchomienia w programie .NET Framework oraz dodawać funkcje dynamicznego do statycznie językach.  
  
 Dynamiczne języków można zidentyfikować typu obiektu w czasie wykonywania, natomiast w statycznie wpisana języków, takich jak C# i Visual Basic (Jeśli używasz `Option Explicit On`) należy określić typy obiektów w czasie projektowania. Przykładami dynamiczne są Lisp, Smalltalk, JavaScript, PHP, Ruby, Python, ColdFusion, Lua, Cobra i Groovy.  
  
 Najbardziej dynamiczną języków zapewniają następujące korzyści dla deweloperów:  
  
-   Możliwość używania pętlę szybkie opinii (REPL lub pętli odczytu oceny drukarek). Dzięki temu można wprowadzić kilka deklaracji i natychmiast wykonać je, aby wyświetlić wyniki.  
  
-   Obsługę góra dół programowanie i bardziej tradycyjnej programowanie z dołu do góry. Na przykład użycie metody góry do dołu, można wywoływać funkcje, które nie zostały jeszcze zaimplementowane, a następnie dodaj podstawowej implementacji, gdy będziesz potrzebować.  
  
-   Łatwiejsze refaktoryzacji i kodu zmian, ponieważ nie trzeba zmienić typ statyczny deklaracje w całym kodzie.  
  
 Dynamiczne języków należy znakomity języków skryptowych. Klientów można z łatwością rozszerzyć aplikacje utworzone przy użyciu języków dynamiczne nowych poleceń i funkcjonalność. Języki dynamiczne są również często używane do tworzenia witryn sieci Web i testów przewodów, obsługa farmy serwerów, tworzenie różnych narzędzi i przekształcenia danych.  
  
 Celem Runtime jest umożliwienie system dynamiczne języki do uruchamiania w programie .NET Framework i nadaj im współdziałaniu .NET. Runtime wprowadza obiekty dynamiczne C# i Visual Basic w programie Visual Studio 2010 do obsługi dynamicznego zachowania w tych językach i włączanie ich współdziałanie języków dynamicznych.  
  
 Runtime umożliwia również tworzenie bibliotek, które obsługują operacji dynamicznych. Na przykład jeśli masz biblioteki, która używa obiektów XML lub JavaScript Object Notation (JSON), może wystąpić obiektów obiekty dynamiczne na języki, które używają Runtime. Umożliwia to użytkownikom biblioteki napisać kod składniowo prostszy i bardziej naturalne do pracy z obiektami i uzyskiwania dostępu do elementów członkowskich obiektu.  
  
 Może na przykład użyć poniższego kodu, aby zwiększyć licznik w pliku XML w języku C#.  
  
 `Scriptobj.SetProperty("Count", ((int)GetProperty("Count")) + 1);`  
  
 Za pomocą Runtime, możesz użyć poniższego kodu zamiast tego tej samej operacji.  
  
 `scriptobj.Count += 1;`  
  
 Podobnie jak CLR Runtime jest częścią programu .NET Framework i jest dostarczana z pakietów instalacyjnych .NET Framework i Visual Studio. Jest również dostępny do pobrania w wersji open source Runtime [IronLanguages/Runtime](https://github.com/IronLanguages/dlr) repozytorium w witrynie GitHub.  
  
> [!NOTE]
>  Wersja open source Runtime ma wszystkie funkcje DLR, który znajduje się w programie Visual Studio i .NET Framework. Umożliwia także dodatkowe wsparcie dla obiektów implementujących języka. Aby uzyskać więcej informacji, zobacz dokumentację na [IronLanguages/Runtime](https://github.com/IronLanguages/dlr) repozytorium w witrynie GitHub. 
  
 Przykłady opracowano na podstawie Runtime języki są następujące:  
  
-   IronPython. Dostępny jako oprogramowanie open source z [GitHub](https://github.com/IronLanguages/ironpython2) witryny sieci Web.  
  
-   IronRuby. Dostępny jako oprogramowanie open source z [RubyForge](http://go.microsoft.com/fwlink/?LinkId=141044) witryny sieci Web.  
  
## <a name="primary-dlr-advantages"></a>Podstawowe zalety Runtime  
 DLR zapewnia następujące korzyści.  
  
### <a name="simplifies-porting-dynamic-languages-to-the-net-framework"></a>Upraszcza przenoszenie dynamiczne języków .NET Framework  
 Runtime umożliwia implementacje języka uniknąć tworzenia leksykalne analizatorów, analizatory składni semantycznego analizatorów, generatory kodu i innych narzędzi, które miały tradycyjnie można utworzyć samodzielnie. Aby użyć Runtime, język musi utworzyć *drzew wyrażeń*, które reprezentują kodu języka na poziomie w strukturze drzewa w kształcie, procedury pomocnika środowiska uruchomieniowego, i opcjonalne dynamiczne obiekty, które implementuje <xref:System.Dynamic.IDynamicMetaObjectProvider> interfejsu. Runtime oraz programu .NET Framework zautomatyzować wiele analizy kodu i zadania generowania kodu. Dzięki temu implementacje języka skoncentrować się na funkcjach języka unikatowy.  
  
### <a name="enables-dynamic-features-in-statically-typed-languages"></a>Umożliwia korzystanie z funkcji dynamicznego w językach statycznie  
 Istniejące języków .NET Framework, takich jak C# i Visual Basic można tworzyć dynamiczne obiekty i ich używać z typami statycznymi obiektami. Na przykład C# i Visual Basic można użyć obiektami dynamicznymi w celu odbicia HTML, modelu DOM (Document Object) i .NET.  
  
### <a name="provides-future-benefits-of-the-dlr-and-net-framework"></a>Zalety przyszłych Runtime i .NET Framework  
 Języki implementowane przy użyciu DLR mogą korzystać z przyszłe ulepszenia Runtime i .NET Framework. Na przykład programu .NET Framework udostępnia nową wersję ulepszone modułu zbierającego elementy bezużyteczne lub szybsze zestawu czasu ładowania, języków implementowane przy użyciu Runtime natychmiast uzyskać takie same korzyści. Jeśli DLR dodaje optymalizacji, np. lepszą kompilacji, wydajność także usprawnia dla wszystkich języków implementowane przy użyciu Runtime.  
  
### <a name="enables-sharing-of-libraries-and-objects"></a>Umożliwia udostępnianie biblioteki i obiektów  
 Obiekty i biblioteki zaimplementowana w jednym języku mogą posłużyć innych języków. Runtime umożliwia współdziałanie między językami statycznie maszynowy i dynamicznych. Na przykład C# można zadeklarować obiekt dynamiczny, który korzysta z biblioteki, która jest napisany w języku dynamicznej. W tym samym czasie dynamiczne języków można użyć bibliotek z programu .NET Framework.  
  
### <a name="provides-fast-dynamic-dispatch-and-invocation"></a>Zapewnia szybkie dynamicznej alokacji i wywołanie  
 DLR zapewnia szybkie wykonywanie operacji dynamicznych dzięki obsłudze zaawansowane polimorficznych buforowania. DLR tworzy powiązanie operacji korzystających z obiektów do implementacji środowiska uruchomieniowego konieczne zasady, a następnie buforuje te reguły, aby uniknąć obliczenia powiązanie wyczerpaniem zasobów podczas kolejnych wykonań tego samego kodu na takich samych typach obiektów.  
  
## <a name="dlr-architecture"></a>Architektura Runtime  
 Na poniższej ilustracji przedstawiono architekturę środowiska uruchomieniowego języka dynamicznego.  
  
 ![Przegląd architektury środowiska uruchomieniowego języka dynamicznego](../../../docs/framework/reflection-and-codedom/media/dlr-archoverview.png "DLR_ArchOverview")  
Architektura Runtime  
  
 Runtime dodaje zestaw usług do środowiska CLR dla lepszej obsługi języków dynamicznych. Te usługi są następujące:  
  
-   Drzewa wyrażeń. Runtime używa drzew wyrażeń do reprezentowania semantykę języka. W tym celu Runtime ma rozszerzone LINQ drzew wyrażeń do uwzględnienia przepływu sterowania, przypisywania i inne węzły język modelowania. Aby uzyskać więcej informacji, zobacz [drzew wyrażeń](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).  
  
-   Wywołanie buforowanie lokacji. A *lokacji wywołania dynamicznego* to miejsce w kodzie, gdzie można wykonać operacji, takich jak `a + b` lub `a.b()` na obiekty dynamiczne. Właściwości buforuje DLR `a` i `b` (zazwyczaj typy te obiekty) i informacje na temat operacji. Jeśli takie działanie ma zostać wykonane wcześniej, Runtime pobiera niezbędne informacje z pamięci podręcznej na potrzeby szybkiego wysyłania.  
  
-   Współdziałanie obiekt dynamiczny. DLR zapewnia zbiór klasy i interfejsy, które reprezentują dynamiczne obiekty i operacje i mogą być używane przez implementacje języka i autorów dynamicznej biblioteki. Te klasy i interfejsy obejmują <xref:System.Dynamic.IDynamicMetaObjectProvider>, <xref:System.Dynamic.DynamicMetaObject>, <xref:System.Dynamic.DynamicObject>, i <xref:System.Dynamic.ExpandoObject>.  
  
 Runtime używa integratorów w miejsc wywołania do komunikowania się nie tylko w środowisku .NET Framework, ale z innymi infrastruktury i usług, w tym Silverlight i modelu COM. Integratorów Hermetyzowanie semantykę języka i określ sposób przeprowadzenia operacji w witrynie wywołanie za pomocą drzewa wyrażeń. To umożliwia dynamiczne i statycznie wpisane języków, które używają DLR do udziału biblioteki, a dostęp do wszystkich technologie, które obsługuje Runtime.  
  
## <a name="dlr-documentation"></a>Dokumentacja Runtime  
 Aby uzyskać więcej informacji o sposobie używania wersji typu open source DLR dodać dynamicznego zachowania do języka lub temat Korzystanie z języka dynamicznego z programu .NET Framework, zobacz dokumentację na [IronLanguages/Runtime](https://github.com/IronLanguages/dlr/tree/master/Docs) repozytorium w witrynie GitHub.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Dynamic.ExpandoObject>  
 <xref:System.Dynamic.DynamicObject>  
 [Środowisko uruchomieniowe języka wspólnego](../../../docs/standard/clr.md)  
 [Drzewa wyrażeń](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [Wskazówki: Tworzenie obiektów dynamicznych i posługiwanie](~/docs/csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
