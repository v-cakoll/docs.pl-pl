---
title: Przewodnik po środowisku .NET
description: Przewodnik po kilku widocznych funkcjach platformy .NET.
author: cartermp
ms.author: wiwagn
ms.date: 05/22/2017
ms.technology: dotnet-standard
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
ms.openlocfilehash: 61d4792b1f1b92dd59442ee38810da96c6cf63bd
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78241146"
---
# <a name="tour-of-net"></a>Przewodnik po środowisku .NET

.NET to platforma programistyczna ogólnego przeznaczenia. Ma kilka najważniejszych funkcji, takich jak obsługa wielu języków programowania, asynchronicznych i współbieżnych modeli programowania oraz natywnego współdziałania, które umożliwiają szeroki zakres scenariuszy na wielu platformach.

Ten artykuł zawiera Przewodnik po kilku najważniejszych funkcjach platformy .NET. Zapoznaj się z tematem [składniki architektury .NET](components.md) , aby poznać elementy architektury .NET i ich użycia.

## <a name="how-to-run-the-code-samples"></a>Jak uruchomić przykłady kodu

Aby dowiedzieć się, jak skonfigurować środowisko programistyczne do uruchamiania przykładów kodu, zapoznaj się z tematem [wprowadzenie](get-started.md) . Skopiuj i wklej przykłady kodu z tej strony do środowiska, aby je uruchomić.

## <a name="programming-languages"></a>Języki programowania

Platforma .NET obsługuje wiele języków programowania. Implementacje platformy .NET implementują [Common Language Infrastructure (CLI)](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/), które między innymi określają środowisko uruchomieniowe niezależne od języka i współdziałanie języków. Oznacza to, że wybierasz dowolny język .NET do kompilowania aplikacji i usług na platformie .NET.

Firma Microsoft aktywnie opracowuje i obsługuje trzy języki .NET C#: F#, i Visual Basic.

* C# to prosta, wydajna, bezpieczne i zorientowane obiektowo, przy zachowaniu wyrazistości i elegancji stylów języka c. Każda osoba znająca język C i podobne Języki odnajduje kilka problemów w C#dostosowywaniu do programu. Zapoznaj się z [ C# przewodnikiem](../csharp/index.yml) , aby C#dowiedzieć się więcej.

* F#to międzyplatformowy, funkcjonalny język programowania, który obsługuje także tradycyjne programowanie zorientowane obiektowo i bezwzględne. Zapoznaj się z [ F# przewodnikiem](../fsharp/index.yml) , aby F#dowiedzieć się więcej.

* Visual Basic to prosty język, dzięki któremu można dowiedzieć się, jak tworzyć różne aplikacje działające na platformie .NET. W językach .NET składnia Visual Basic jest najbardziej zbliżona do zwykłego języka ludzkiego, często ułatwiająca tworzenie nowych oprogramowania przez inne osoby.

## <a name="automatic-memory-management"></a>Automatyczne zarządzanie pamięcią

Platforma .NET używa [wyrzucania elementów bezużytecznych (GC)](garbage-collection/index.md) w celu zapewnienia automatycznego zarządzania pamięcią dla programów. GC wykorzystuje podejście z opóźnieniem do zarządzania pamięcią, a tym samym przepływność aplikacji do natychmiastowego zbierania pamięci. Aby dowiedzieć się więcej na temat platformy .NET GC, zapoznaj się z tematem podstawowe informacje na temat [odzyskiwania pamięci (GC)](garbage-collection/fundamentals.md).

Oba te dwa wiersze przydzielą pamięć:

[!code-csharp[MemoryManagement](../../samples/snippets/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

Nie istnieje podobne słowo kluczowe do cofnięcia przydzielenia pamięci, ponieważ cofnięcie przydziału odbywa się automatycznie, gdy moduł zbierający elementy bezużyteczne ponownie przejmuje pamięć za pomocą zaplanowanego uruchomienia.

Moduł wyrzucania elementów bezużytecznych jest jedną z usług, które zapewniają *bezpieczeństwo pamięci*. Program jest bezpieczny dla pamięci, jeśli uzyskuje dostęp tylko do przydzieloną pamięci. Na przykład środowisko uruchomieniowe zapewnia, że aplikacja nie uzyskuje dostępu do nieprzypisanej pamięci poza granicami tablicy.

W poniższym przykładzie środowisko uruchomieniowe zgłasza wyjątek <xref:System.IndexOutOfRangeException>, aby wymusić bezpieczeństwo pamięci:

[!code-csharp[MemoryManagement](../../samples/snippets/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="working-with-unmanaged-resources"></a>Praca z niezarządzanymi zasobami

Niektóre obiekty odwołują się do *niezarządzanych zasobów*. Zasoby niezarządzane to zasoby, które nie są automatycznie obsługiwane przez środowisko uruchomieniowe platformy .NET. Na przykład dojście do pliku jest zasobem niezarządzanym. Obiekt <xref:System.IO.FileStream> jest obiektem zarządzanym, ale odwołuje się do dojścia do pliku, który jest niezarządzany. Gdy skończysz korzystać z <xref:System.IO.FileStream>, musisz zwolnić dojście do pliku.

W programie .NET obiekty odwołujące się do niezarządzanych zasobów implementują interfejs <xref:System.IDisposable>. Gdy skończysz korzystać z obiektu, wywołasz metodę <xref:System.IDisposable.Dispose> obiektu, która jest odpowiedzialna za zwolnienie niezarządzanych zasobów. Języki .NET udostępniają wygodną [instrukcję`using`](../csharp/language-reference/keywords/using.md) dla takich obiektów, jak pokazano w poniższym przykładzie:

[!code-csharp[UnmanagedResources](../../samples/snippets/csharp/snippets/tour/UnmanagedResources.csx#L1-L6)]

Po zakończeniu `using` bloku środowisko uruchomieniowe platformy .NET automatycznie wywoła metodę <xref:System.IDisposable.Dispose> obiektu `stream`, która zwalnia dojście do pliku. Środowisko uruchomieniowe robi to również wtedy, gdy wyjątek powoduje opuszczenie bloku.

Aby uzyskać więcej informacji, zobacz następujące tematy:

* Dla C#programu można znaleźć w temacie [usingC# (odwołanie)](../csharp/language-reference/keywords/using-statement.md) .
* W F#przypadku programu zobacz [Zarządzanie zasobami: słowo kluczowe use](../fsharp/language-reference/resource-management-the-use-keyword.md).
* Aby uzyskać Visual Basic, zobacz temat [using (Visual Basic)](../visual-basic/language-reference/statements/using-statement.md) .

## <a name="type-safety"></a>Bezpieczeństwo typów

Obiekt jest wystąpieniem określonego typu. Jedyną operacją dozwoloną dla danego obiektu są te typu. Typ `Dog` może mieć metody `Jump` i `WagTail`, ale nie metodę `SumTotal`. Program wywołuje tylko metody należące do danego typu. Wszystkie inne wywołania powodują błąd czasu kompilacji lub wyjątek czasu wykonywania (w przypadku korzystania z funkcji dynamicznych lub `object`).

Języki .NET są zorientowane obiektowo z hierarchiami klas podstawowych i pochodnych. Środowisko uruchomieniowe platformy .NET zezwala tylko na rzutowanie obiektów i wywołania, które są wyrównane z hierarchią obiektów. Należy pamiętać, że każdy typ zdefiniowany w dowolnym języku .NET pochodzi od podstawowego typu <xref:System.Object>.

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L19-L23)]

Zabezpieczenia typu są również używane do wymuszania hermetyzacji przez zagwarantowanie dokładności słów kluczowych metody dostępu. Słowa kluczowe metody dostępu to artefakty kontrolujące dostęp do elementów członkowskich danego typu przez inny kod. Są one zwykle używane w przypadku różnych rodzajów danych w ramach typu, który jest używany do zarządzania zachowaniem.

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#, Visual Basic i F# obsługują *wnioskowanie o typie*lokalnym. Wnioskowanie o typie oznacza, że kompilator określa typ wyrażenia po lewej stronie wyrażenia po prawej stronie. Nie oznacza to, że bezpieczeństwo typu jest zerwane lub nieuniknione. Typ wynikowy ma silny typ z wszystko, co oznacza. W poprzednim przykładzie `dog` jest zapisywana w celu wprowadzenia wnioskowania o typie, a pozostała część tego przykładu nie jest zmieniona:

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F#ma jeszcze więcej możliwości wnioskowania o typie niż w metodzie C# i Visual Basic. Aby dowiedzieć się więcej, zobacz [wnioskowanie o typie](../fsharp/language-reference/type-inference.md).

## <a name="delegates-and-lambdas"></a>Delegaci i wyrażenia lambda

Delegat jest reprezentowany przez sygnaturę metody. Dowolna metoda z tym podpisem może być przypisana do delegata i jest wykonywana, gdy obiekt delegowany jest wywoływany.

Delegaty są C++ podobne do wskaźników funkcji, z tą różnicą, że są typu bezpieczne. Są one rodzajową metodą rozłączoną w systemie typów CLR. Regularne metody są dołączane do klasy i można je bezpośrednio wywołać za pomocą konwencji wywoływania statycznego lub wystąpienia.

W programie .NET Delegaty są często używane w obsłudze zdarzeń, w definiowaniu operacji asynchronicznych i w wyrażeniach lambda, które są kamieńmi wieloskładnikowymi LINQ. Dowiedz się więcej w temacie [Delegaty i wyrażenia lambda](delegates-lambdas.md) .

## <a name="generics"></a>Typy ogólne

Typy ogólne umożliwiają programistom wprowadzanie *parametrów typu* podczas projektowania klas, które umożliwiają kod klienta (Użytkownicy typu), aby określić dokładny typ do użycia zamiast parametru typu.

Typy ogólne zostały dodane w celu ułatwienia deweloperom implementowania ogólnych struktur danych. Przed przybyciem, aby typ, taki jak typ `List`, był ogólny, musiał działać z elementami typu `object`. Miało to różne problemy z wydajnością i semantyką oraz potencjalne drobne błędy w czasie wykonywania. Typowy błąd czasu wykonywania polega na tym, że struktura danych zawiera na przykład zarówno liczby całkowite, jak i ciągi, a podczas przetwarzania członków listy jest zgłaszany <xref:System.InvalidCastException>.

Poniższy przykład pokazuje program podstawowy uruchomiony przy użyciu wystąpienia <xref:System.Collections.Generic.List%601> typów:

[!code-csharp[GenericsShort](../../samples/snippets/csharp/snippets/tour/GenericsShort.csx)]

Aby uzyskać więcej informacji, zobacz temat [Omówienie typów ogólnych (Generics)](generics.md) .

## <a name="async-programming"></a>Programowanie asynchroniczne

Programowanie asynchroniczne to koncepcja pierwszej klasy w ramach platformy .NET z obsługą asynchroniczną w środowisku uruchomieniowym, bibliotekach struktur i konstrukcjach języka .NET. Wewnętrznie są one oparte na obiektach (takich jak `Task`), które wykorzystują system operacyjny do wykonywania zadań związanych z we/wy odpowiednio efektywnie.

Aby dowiedzieć się więcej o programowaniu asynchronicznym w programie .NET, Rozpocznij pracę z tematem [Przegląd asynchroniczny](async.md) .

## <a name="language-integrated-query-linq"></a>Language Integrated Query (LINQ)

LINQ to zaawansowany zestaw funkcji dla C# i Visual Basic, które umożliwiają pisanie prostego, deklaratywnego kodu do obsługi danych. Dane mogą znajdować się w wielu formularzach (takich jak obiekty znajdujące się w pamięci, bazy danych SQL lub dokumenty XML), ale kod LINQ, który jest zwykle nie różni się od źródła danych.

Aby dowiedzieć się więcej i zapoznać się z przykładami, zobacz temat [LINQ (Language Integrated Query)](using-linq.md) .

## <a name="native-interoperability"></a>Współdziałanie natywne

Każdy system operacyjny zawiera interfejs programowania aplikacji (API), który zapewnia usługi systemowe. Platforma .NET oferuje kilka sposobów wywoływania tych interfejsów API.

Głównym sposobem zapewnienia natywnego współdziałania jest za pośrednictwem "wywołania platformy" lub P/Invoke dla krótkich, które są obsługiwane na platformach Linux i Windows. Sposób natywnego współdziałania jest określany tylko przez system Windows, który jest używany do pracy ze [składnikami modelu COM](/cpp/atl/introduction-to-com) w kodzie zarządzanym. Jest on oparty na infrastrukturze P/Invoke, ale działa na bardzo różne sposoby.

Większość funkcji obsługi współdziałania programu mono (i w ten sposób Xamarin) dla języka Java i celu w języku C jest zbudowana podobnie, czyli korzystają z tych samych zasad.

Aby uzyskać więcej informacji na temat współdziałania natywnego, zobacz artykuł dotyczący współdziałania [macierzystego](native-interop/index.md) .

## <a name="unsafe-code"></a>Niebezpieczny kod

W zależności od obsługi języków środowisko CLR umożliwia dostęp do pamięci natywnej i przeprowadzenie obliczeń wskaźnika za pośrednictwem kodu `unsafe`. Te operacje są niezbędne w przypadku niektórych algorytmów i współdziałania systemu. Chociaż nie jest zalecane korzystanie z niebezpiecznego kodu, chyba że jest to konieczne do współdziałania z interfejsami API systemu lub implementuje najbardziej wydajny algorytm. Kod niebezpieczny może nie działać w ten sam sposób w różnych środowiskach, a także traci korzyści ze stosowania modułu wyrzucania elementów bezużytecznych i bezpieczeństwa typów. Zaleca się ograniczenie i scentralizowanie niebezpiecznego kodu, jak to możliwe, i gruntowne sprawdzenie tego kodu.

Poniższy przykład jest zmodyfikowaną wersją metody `ToString()` z klasy `StringBuilder`. Ilustruje on sposób używania kodu `unsafe` może efektywnie zaimplementować algorytm przez bezpośrednie przechodzenie między fragmentami pamięci:

[!code-csharp[Unsafe](../../samples/snippets/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>Następne kroki

Jeśli interesuje Cię Przewodnik po C# funkcjach, zapoznaj się [z C#przewodnikiem ](../csharp/tour-of-csharp/index.md).

Jeśli interesuje Cię Przewodnik po F# funkcjach, zobacz [samouczek F# ](../fsharp/tour.md).

Jeśli chcesz zacząć pisać własny kod, odwiedź [wprowadzenie](get-started.md).

Aby dowiedzieć się więcej o ważnych składnikach platformy .NET, zapoznaj się ze [składnikami architektury .NET](components.md).
