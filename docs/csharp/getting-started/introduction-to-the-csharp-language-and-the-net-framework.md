---
title: Wprowadzenie do języka C# i systemu .NET Framework
description: Poznaj podstawy języków C# i .NET. Zapoznaj się z omówieniem języka C# i ekosystemu platformy .NET.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: 55b90d10a1d8ac8534ba98e1cc5af906d69822a6
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100837"
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>Wprowadzenie do języka C# i .NET Framework

C# to elegancki i bezpieczny dla typu język oparty na obiektach, który umożliwia deweloperom tworzenie różnorodnych bezpiecznych i niezawodnych aplikacji, które działają w ekosystemie platformy .NET. Ekosystem .NET składa się ze wszystkich implementacji platformy .NET, w tym między innymi z [programu .NET Core](../../core/index.yml)i [.NET Framework](../../framework/index.yml). Ten artykuł koncentruje się na .NET Framework. Za pomocą języka C# można tworzyć aplikacje klienckie systemu Windows, usługi sieci Web XML, składniki rozproszone, aplikacje klient-serwer, aplikacje baz danych i wiele innych.

> [!NOTE]
> Dokumentacja języka Visual C# założono, że znasz podstawowe koncepcje programowania. Jeśli jesteś kompletnym początkującym, warto zapoznać się z tematem Visual C# Express, który jest dostępny w sieci Web. Możesz również wykorzystać książki i zasoby sieci Web dotyczące języka C#, aby poznać praktyczne umiejętności programistyczne.

## <a name="c-language"></a>C# — język

Składnia języka C# jest wysoce jasno, ale jest również prosta i łatwa do uczenia się. Składnia języka C# w nawiasach klamrowych będzie natychmiast rozpoznawalna dla każdego znanego w języku C, C++ lub Java. Deweloperzy, którzy znają którykolwiek z tych języków, zazwyczaj mogą zacząć wydajnie pracować w języku C# w krótkim czasie. Składnia języka C# upraszcza wiele złożoności języka C++ i zapewnia zaawansowane funkcje, takie jak typy dopuszczające wartości null, wyliczenia, Delegaty, wyrażenia lambda i bezpośredni dostęp do pamięci. Język C# obsługuje ogólne metody i typy, które zapewniają zwiększone bezpieczeństwo typu i wydajność oraz Iteratory, które umożliwiają implementacje klas kolekcji w celu zdefiniowania niestandardowych zachowań iteracji, które są proste do użycia przez kod klienta. Wyrażenia programu Query-Integrated Language (LINQ) czynią silnie wpisaną kwerendę do konstrukcji języka pierwszej klasy.

Jako język zorientowany obiektowo, C# obsługuje koncepcje hermetyzacji, dziedziczenia i polimorfizmu. Wszystkie zmienne i metody, w tym `Main` Metoda, punkt wejścia aplikacji, są hermetyzowane w definicjach klas. Klasa może dziedziczyć bezpośrednio z jednej klasy nadrzędnej, ale może implementować dowolną liczbę interfejsów. Metody, które zastępują metody wirtualne w klasie nadrzędnej, wymagają `override` słowa kluczowego jako sposobu, aby uniknąć przypadkowej ponownej definicji. W języku C# struktura jest taka sama jak Klasa uproszczona; jest typem przydzielonym przez stos, który może implementować interfejsy, ale nie obsługuje dziedziczenia.

Oprócz tych podstawowych zasad opartych na obiektach, język C# ułatwia tworzenie składników oprogramowania za pomocą kilku innowacyjnych konstrukcji językowych, w tym następujących:

- Wyhermetyzowane sygnatury metod o nazwie *pełnomocnicy*, które włączają powiadomienia o zdarzeniach bezpiecznych dla typów.
- Właściwości, które stanowią metody dostępu do zmiennych prywatnych elementów członkowskich.
- Atrybuty, które zapewniają deklaratywne metadane dotyczące typów w czasie wykonywania.
- Komentarze do wbudowanej dokumentacji XML.
- Language-Integrated Query (LINQ), który udostępnia wbudowane funkcje zapytań w różnych źródłach danych.

Jeśli konieczne jest współdziałanie z innym oprogramowaniem systemu Windows, takim jak obiekty COM lub natywne biblioteki DLL Win32, można to zrobić w języku C# za pomocą procesu o nazwie "Interop". Międzyoperacyjność umożliwia aplikacjom języka C# niemal wszystko, co można zrobić za pomocą natywnej aplikacji C++. Język C# obsługuje nawet wskaźniki i koncepcję niebezpiecznego kodu dla tych przypadków, w których bezpośredni dostęp do pamięci jest krytyczny.

Proces kompilacji w języku C# jest prosty w porównaniu z C i C++ i bardziej elastyczny niż w języku Java. Nie ma oddzielnych plików nagłówkowych i nie ma potrzeby deklarowania metod i typów w określonej kolejności. Plik źródłowy języka C# może definiować dowolną liczbę klas, struktur, interfejsów i zdarzeń.

Poniżej przedstawiono dodatkowe zasoby w języku C#:

- Aby uzyskać dobre Ogólne wprowadzenie do języka, zobacz rozdział 1 [specyfikacji języka C#](/dotnet/csharp/language-reference/language-specification/introduction).
- Aby uzyskać szczegółowe informacje na temat określonych aspektów języka C#, zobacz [Dokumentacja języka c#](../language-reference/index.md).
- Aby uzyskać więcej informacji na temat LINQ, zobacz [LINQ (zapytanie zintegrowane z językiem)](../programming-guide/concepts/linq/index.md).

## <a name="net-framework-platform-architecture"></a>Architektura platformy .NET Framework

Programy w języku C# są uruchamiane na .NET Framework, integralnym składniku systemu Windows, który zawiera wirtualny system wykonywania o nazwie środowisko uruchomieniowe języka wspólnego (CLR) i ujednolicony zestaw bibliotek klas. Środowisko CLR to komercyjna implementacja infrastruktury Common Language Infrastructure (CLI), która jest podstawą do tworzenia środowisk wykonawczych i programistycznych, w których Języki i biblioteki współpracują ze sobą.

Kod źródłowy zapisany w języku C# jest kompilowany do [języka pośredniego (IL)](../../standard/managed-code.md) , który jest zgodny ze specyfikacją interfejsu wiersza polecenia. Kod IL i zasoby, takie jak mapy bitowe i ciągi, są przechowywane na dysku w pliku wykonywalnym nazywanym zestawem, zazwyczaj z rozszerzeniem exe lub dll. Zestaw zawiera manifest, który zawiera informacje o typach, wersji, kulturze i wymaganiach dotyczących zestawu.

Gdy program C# jest wykonywany, zestaw jest ładowany do środowiska CLR, co może potrwać różne akcje na podstawie informacji zawartych w manifeście. Następnie, jeśli spełnione są wymagania dotyczące zabezpieczeń, środowisko CLR wykonuje kompilację just-in-Time (JIT), aby przekonwertować kod IL na instrukcje maszyny natywnej. Środowisko CLR udostępnia również inne usługi związane z automatycznym odzyskiwaniem pamięci, obsługą wyjątków i zarządzaniem zasobami. Kod wykonywany przez środowisko CLR jest czasami określany jako "kod zarządzany", w przeciwieństwie do "kodu niezarządzanego", który jest kompilowany do macierzystego języka maszynowego, który jest przeznaczony dla określonego systemu. Na poniższym diagramie przedstawiono relacje czasu kompilacji i czasu wykonywania dla plików kodu źródłowego C#, .NET Framework biblioteki klas, zestawy i środowisko CLR.

![Z kodu źródłowego C# do wykonywania maszynowego](./media/introduction-to-the-csharp-language-and-the-net-framework/net-architecture-relationships.png)

Współdziałanie języków jest kluczową funkcją .NET Framework. Ponieważ kod IL tworzony przez kompilator języka C# jest zgodny ze specyfikacją Common Type Specification (CTS), kod IL wygenerowany na podstawie języka C# może współistnieć z kodem, który został wygenerowany na podstawie wersji .NET Visual Basic, Visual C++ lub dowolnego z ponad 20 innych języków zgodnych ze standardem CTS. Pojedynczy zestaw może zawierać wiele modułów pisanych w różnych językach .NET, a typy mogą się odwoływać nawzajem, tak jakby były zapisywane w tym samym języku.

Oprócz usług czasu wykonywania, .NET Framework również zawiera rozbudowana Biblioteka ponad 4000 klas zorganizowanych w przestrzenie nazw, które zapewniają szeroką gamę użytecznych funkcji dla wszystkich elementów od danych wejściowych i wyjściowych na potrzeby manipulowania ciągami do analizy XML, do Windows Forms formantów. Typowa aplikacja C# używa biblioteki klas .NET Framework w szerokim stopniu do obsługi typowych zadań "wodociągów".

Aby uzyskać więcej informacji na temat .NET Framework, zobacz [Omówienie struktury Microsoft .NET](../../framework/get-started/overview.md).

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie z Visual C #](/visualstudio/ide/quickstart-csharp-console)
