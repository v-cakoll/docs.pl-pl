---
title: Przegląd środowiska uruchomieniowego języka dynamicznego | Dokumentacja firmy Microsoft
ms.date: 03/30/2017
helpviewer_keywords:
- dynamic language runtime
- IronPython
- DLR
- IronRuby
ms.assetid: f769a271-8aff-4bea-bfab-6160217ce23d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a4645efc9276429cbdb0812f1ca501c89ea5dbb
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44140102"
---
# <a name="dynamic-language-runtime-overview"></a>Przegląd środowiska uruchomieniowego języka dynamicznego
*Środowisko uruchomieniowe języka dynamicznego* (DLR) jest środowisko uruchomieniowe, który dodaje zestaw usług dla języków dynamicznych do środowisko uruchomieniowe języka wspólnego (CLR). DLR sprawia, że łatwiej tworzyć języki dynamiczne, do uruchamiania na .NET Framework i dodawania funkcji dynamicznego do języków statycznie wpisane.  
  
 Języki dynamiczne można zidentyfikować typ obiektu w czasie wykonywania, natomiast w statycznie wpisane języków, takich jak C# i Visual Basic (Jeśli używasz `Option Explicit On`) należy określić typy obiektów w czasie projektowania. Przykładami języki dynamiczne są Lisp, Smalltalk, JavaScript, PHP, Ruby, Python, ColdFusion, Lua, Cobra i Groovy.  
  
 Języki najbardziej dynamiczne zapewniają następujące korzyści dla deweloperów:  
  
-   Możliwość używania pętlę błyskawicznych opinii (REPL lub odczytu oceny — Drukuj pętli). Dzięki temu można wprowadzić kilka instrukcji i natychmiast wykonać je, aby wyświetlić wyniki.  
  
-   Obsługa dla rozwoju góra dół i bardziej tradycyjny rozwoju od dołu do góry. Na przykład korzystając z podejścia góra dół, można wywoływać funkcje, które nie są jeszcze zaimplementowane, a następnie dodać podstawowej implementacji, gdy ich potrzebujesz.  
  
-   Łatwiejsze refaktoryzacji i kodu modyfikacji, ponieważ nie trzeba zmienić deklaracje typu statycznego w całym kodzie.  
  
 Języki dynamiczne należy doskonałą językach skryptów. Klienci mogą łatwo rozbudowywać aplikacje utworzone przy użyciu języków dynamicznych nowe polecenia i funkcje. Języki dynamiczne są również często używane do tworzenia witryn sieci Web i test, wiązka, utrzymywanie farm serwerów, różne narzędzia do tworzenia i wykonywanie przekształceń danych.  
  
 Celem DLR jest aby włączyć system języków dynamicznych do uruchamiania na .NET Framework i nadaj im współdziałaniu .NET. DLR wprowadza obiektów dynamicznych do języka C# i Visual Basic w programie Visual Studio 2010 do obsługi dynamicznego działania w tych językach i włączanie ich współdziałanie języków dynamicznych.  
  
 DLR ułatwia również tworzenie bibliotek, które obsługują operacji dynamicznych. Na przykład jeśli masz bibliotekę, która używa obiektów XML lub JavaScript Object Notation (JSON), może występować obiektów obiektów dynamicznych dla języków, które używają DLR. Pozwala to użytkownikom bibliotekę w kodzie składniowo prostszy i bardziej naturalne na potrzeby świadczenia z obiektami i uzyskiwania dostępu do członków obiektu.  
  
 Poniższy kod może na przykład użyć, aby zwiększyć licznik w formacie XML w języku C#.  
  
 `Scriptobj.SetProperty("Count", ((int)GetProperty("Count")) + 1);`  
  
 Za pomocą DLR, możesz użyć następującego kodu zamiast tej samej operacji.  
  
 `scriptobj.Count += 1;`  
  
 Podobnie jak CLR DLR jest częścią programu .NET Framework i jest dostarczana z pakiety instalacyjne systemu .NET Framework i programu Visual Studio. Jest również dostępna do pobrania w wersji typu open-source DLR [IronLanguages/dlr](https://github.com/IronLanguages/dlr) repozytorium w witrynie GitHub.  
  
> [!NOTE]
>  Wersja typu open-source DLR ma wszystkie funkcje DLR, który znajduje się w programie Visual Studio i .NET Framework. Zapewnia także dodatkową obsługę języka implementacje. Aby uzyskać więcej informacji, zobacz dokumentację na [IronLanguages/dlr](https://github.com/IronLanguages/dlr) repozytorium w witrynie GitHub. 
  
 Przykłady opracowano na podstawie DLR języków są następujące:  
  
-   IronPython. Dostępne jako oprogramowanie open source z [GitHub](https://github.com/IronLanguages/ironpython2) witryny sieci Web.  
  
-   IronRuby. Dostępne jako oprogramowanie open source z [RubyForge](https://go.microsoft.com/fwlink/?LinkId=141044) witryny sieci Web.  
  
## <a name="primary-dlr-advantages"></a>Podstawowe zalety DLR  
 DLR zapewnia następujące korzyści.  
  
### <a name="simplifies-porting-dynamic-languages-to-the-net-framework"></a>Upraszcza przenoszenie języki dynamiczne w .NET Framework  
 DLR umożliwia implementacji języka uniknąć tworzenia analizatory leksykalne, analizatory składni, analizatory semantyczne, generatorów kodu i inne narzędzia, które tradycyjnie było, aby utworzyć samodzielnie. Aby użyć DLR, język wymaga utworzenia *drzew wyrażeń*, reprezentujący kodu poziomu języka w strukturze drzewa w kształcie procedury pomocnika czasu wykonywania, i opcjonalnie dynamiczne obiekty, które implementuje <xref:System.Dynamic.IDynamicMetaObjectProvider> interfejsu. DLR i .NET Framework zautomatyzować wiele analizy kodu i zadania generowania kodu. Dzięki temu implementacji języka skoncentrować się na funkcje językowe unikatowy.  
  
### <a name="enables-dynamic-features-in-statically-typed-languages"></a>Umożliwia korzystanie z funkcji dynamicznego w językach statycznie wpisane  
 Istniejące języków .NET Framework, takich jak C# i Visual Basic można tworzyć obiektów dynamicznych i ich używać z typami statycznymi obiektami. Na przykład C# i Visual Basic można użyć obiektów dynamicznych w celu odbicia HTML Document Object Model (DOM) i .NET.  
  
### <a name="provides-future-benefits-of-the-dlr-and-net-framework"></a>Zalety przyszłych DLR i .NET Framework  
 Języki implementowane przy użyciu DLR mogą korzystać z przyszłe ulepszenia DLR i .NET Framework. Na przykład .NET Framework wydaje nową wersję, która ma ulepszoną moduł odśmiecania pamięci lub zestawu szybciej czas ładowania, języki implementowane przy użyciu DLR natychmiast uzyskać takie same korzyści. Jeśli DLR dodaje optymalizacje, takie jak lepsza kompilacji, wydajność zwiększa również dla wszystkich języków implementowane przy użyciu DLR.  
  
### <a name="enables-sharing-of-libraries-and-objects"></a>Umożliwia udostępnianie biblioteki i obiektów  
 Obiekty i biblioteki zaimplementowane w jednym języku może służyć przez innych języków. DLR umożliwia także współdziałanie między językami statycznie wpisane i dynamicznych. Na przykład C# można zadeklarować obiekt dynamiczny, który używa biblioteki, która jest napisana w języku dynamicznych. W tym samym czasie języki dynamiczne mogą korzystać z bibliotek z programu .NET Framework.  
  
### <a name="provides-fast-dynamic-dispatch-and-invocation"></a>Zapewnia szybkie dynamicznej alokacji i wywołanie  
 DLR zapewnia szybkie wykonywanie operacji dynamicznych dzięki obsłudze zaawansowane polimorficznych buforowania. DLR tworzy reguły dla powiązania operacji korzystających z obiektów do implementacji konieczne środowiska uruchomieniowego, a następnie buforuje te zasady, aby uniknąć wyczerpaniem zasobów powiązania obliczeń podczas kolejnymi wykonaniami ten sam kod na tych samych typach obiektów.  
  
## <a name="dlr-architecture"></a>Architektura DLR  
 Na poniższej ilustracji przedstawiono architekturę środowisko uruchomieniowe języka dynamicznego.  
  
 ![Omówienie architektury środowiska uruchomieniowego języka dynamicznego](../../../docs/framework/reflection-and-codedom/media/dlr-archoverview.png "DLR_ArchOverview")  
Architektura DLR  
  
 DLR dodaje zestaw usług do środowiska CLR dla lepiej obsługuje języki dynamiczne. Te usługi są następujące:  
  
-   Drzewa wyrażeń. DLR używa drzew wyrażeń, który reprezentuje semantykę języka. W tym celu DLR ma rozszerzone drzew wyrażeń LINQ do uwzględnienia przepływ sterowania, przypisywania i inne węzły modelowanie języka. Aby uzyskać więcej informacji, zobacz [drzew wyrażeń](https://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).  
  
-   Wywołaj buforowanie lokacji. A *witryny wywołania dynamicznego* to miejsce w kodzie, gdzie można wykonać operacji, takiej jak `a + b` lub `a.b()` obiektów dynamicznych. DLR buforuje charakterystyki `a` i `b` (zazwyczaj typy tych obiektów) i informacje na temat operacji. Jeśli taka operacja została wykonana wcześniej, DLR pobiera wszystkie niezbędne informacje z pamięci podręcznej na potrzeby szybkiego wysyłania.  
  
-   Współdziałanie obiekt dynamiczny. DLR zawiera zestaw klas i interfejsów, które reprezentują obiektów dynamicznych i operacje i mogą być używane przez implementacji języka i autorzy bibliotekami dynamicznymi. Te klasy i interfejsy obejmują <xref:System.Dynamic.IDynamicMetaObjectProvider>, <xref:System.Dynamic.DynamicMetaObject>, <xref:System.Dynamic.DynamicObject>, i <xref:System.Dynamic.ExpandoObject>.  
  
 DLR używa integratorów wywołania do komunikowania się nie tylko przy użyciu programu .NET Framework, ale z innymi infrastruktur i usług, w tym programu Silverlight i modelu COM. Integratorów hermetyzacji semantykę języka i określ, jak wykonywać operacje w witrynie wywołania przy użyciu drzew wyrażeń. To umożliwia dynamiczne i statycznie wpisane języki, które umożliwiają DLR Udostępnianie biblioteki i uzyskać dostęp do wszystkich technologii, które obsługuje DLR.  
  
## <a name="dlr-documentation"></a>Dokumentacja DLR  
 Aby uzyskać więcej informacji o sposobie używania wersji "open source" DLR dodanie zachowania dynamiczny język lub o tym, jak umożliwia korzystanie z języka dynamicznego przy użyciu programu .NET Framework, zobacz dokumentację na [IronLanguages/dlr](https://github.com/IronLanguages/dlr/tree/master/Docs) repozytorium w witrynie GitHub.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Dynamic.ExpandoObject>  
 <xref:System.Dynamic.DynamicObject>  
 [Środowisko uruchomieniowe języka wspólnego](../../../docs/standard/clr.md)  
 [Drzewa wyrażeń](https://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [Wskazówki: Tworzenie obiektów dynamicznych i posługiwanie](~/docs/csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
