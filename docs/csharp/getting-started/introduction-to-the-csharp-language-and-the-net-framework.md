---
title: Wprowadzenie do języka C# i systemu .NET Framework
description: Poznaj podstawy C# i .NET. Zapoznaj się z omówieniem C# języka i ekosystemu platformy .NET.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: 57fd4ab59a1162145087b375cbbb71816a10e78c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420340"
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>Wprowadzenie do języka C# i systemu .NET Framework

C#to elegancki i bezpieczny dla typu język oparty na obiektach, który umożliwia deweloperom tworzenie różnorodnych bezpiecznych i niezawodnych aplikacji uruchamianych na .NET Framework. Za pomocą C# programu można tworzyć aplikacje klienckie systemu Windows, usługi sieci Web XML, składniki rozproszone, aplikacje klient-serwer, aplikacje baz danych i wiele innych. Wizualizacja C# zapewnia zaawansowany edytor kodu, wygodne projektanta interfejsu użytkownika, Zintegrowany debuger i wiele innych narzędzi ułatwiających tworzenie aplikacji na podstawie C# języka i .NET Framework.  
  
> [!NOTE]
> Dokumentacja wizualna C# założono, że znasz podstawowe pojęcia programistyczne. Jeśli jesteś kompletnym początkującym, warto zapoznać się z tematem C# Visual Express, który jest dostępny w sieci Web. Możesz również wykorzystać książki i zasoby sieci Web, C# aby poznać praktyczne umiejętności programistyczne.  
  
## <a name="c-language"></a>Język C#

 C#Składnia jest wysoce wyraźna, ale jest również prosta i łatwa do uczenia się. Składnia C# nawiasów klamrowych jest natychmiast rozpoznawalna dla każdego znanego w języku C C++ lub Java. Deweloperzy, którzy znają którykolwiek z tych języków, zazwyczaj mogą zacząć pracować wydajnie w C# bardzo krótkim czasie. C#Składnia upraszcza wiele złożoności C++ i zapewnia zaawansowane funkcje, takie jak typy wartości null, wyliczenia, Delegaty, wyrażenia lambda i bezpośredni dostęp do pamięci, które nie znajdują się w języku Java. C#obsługuje metody generyczne i typy, które zapewniają zwiększone bezpieczeństwo typu i wydajność oraz Iteratory, które umożliwiają implementacje klas kolekcji w celu zdefiniowania niestandardowych zachowań iteracji, które są proste do użycia przez kod klienta. wyrażenia [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] tworzą silnie wpisaną kwerendę w konstrukcji języka pierwszej klasy.  
  
 Jako język zorientowany obiektowo program C# obsługuje koncepcje hermetyzacji, dziedziczenia i polimorfizmu. Wszystkie zmienne i metody, w tym Metoda `Main`, punktu wejścia aplikacji, są hermetyzowane w ramach definicji klas. Klasa może dziedziczyć bezpośrednio z jednej klasy nadrzędnej, ale może implementować dowolną liczbę interfejsów. Metody, które zastępują metody wirtualne w klasie nadrzędnej, wymagają słowa kluczowego `override` jako sposobu, aby uniknąć przypadkowej ponownej definicji. W C#programie struktura jest taka sama jak Klasa uproszczona; jest typem przydzielonym przez stos, który może implementować interfejsy, ale nie obsługuje dziedziczenia.  
  
 Oprócz tych podstawowych zasad zorientowanych obiektowo program C# ułatwia tworzenie składników oprogramowania za pomocą kilku innowacyjnych konstrukcji językowych, w tym następujących:  
  
- Wyhermetyzowane sygnatury metod o nazwie *pełnomocnicy*, które włączają powiadomienia o zdarzeniach bezpiecznych dla typów.  
  
- Właściwości, które stanowią metody dostępu do zmiennych prywatnych elementów członkowskich.  
  
- Atrybuty, które zapewniają deklaratywne metadane dotyczące typów w czasie wykonywania.  
  
- Komentarze do wbudowanej dokumentacji XML.  
  
- [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], które udostępnia wbudowane funkcje zapytań w różnych źródłach danych.  
  
 Jeśli konieczne jest współdziałanie z innym oprogramowaniem systemu Windows, takim jak obiekty COM lub natywne biblioteki DLL Win32, C# można to zrobić za pomocą procesu o nazwie "międzyoperacyjna". Międzyoperacyjność umożliwia C# programom niemal wszystko, co C++ można zrobić w aplikacji natywnej. C#Program obsługuje również wskaźniki i koncepcję niebezpiecznego kodu dla tych przypadków, w których bezpośredni dostęp do pamięci jest absolutnie krytyczny.  
  
 Proces C# kompilacji jest prosty w porównaniu z C i C++ i bardziej elastyczny niż w języku Java. Nie ma oddzielnych plików nagłówkowych i nie ma potrzeby deklarowania metod i typów w określonej kolejności. Plik C# źródłowy może definiować dowolną liczbę klas, struktur, interfejsów i zdarzeń.  
  
 Poniżej znajdują się C# dodatkowe zasoby:  
  
- Aby uzyskać dobre Ogólne wprowadzenie do języka, zobacz rozdział 1 [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).  
  
- Aby uzyskać szczegółowe informacje na temat określonych aspektów C# języka, zobacz [ C# odwołanie](../language-reference/index.md).  
  
- Aby uzyskać więcej informacji na temat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], zobacz [LINQ (zapytanie zintegrowane z językiem)](../programming-guide/concepts/linq/index.md).  

## <a name="net-framework-platform-architecture"></a>Architektura platformy .NET Framework

 C#programy są uruchamiane na .NET Framework, integralnym składniku systemu Windows, który zawiera wirtualny system wykonywania o nazwie środowisko uruchomieniowe języka wspólnego (CLR) i ujednolicony zestaw bibliotek klas. Środowisko CLR to komercyjna implementacja infrastruktury Common Language Infrastructure (CLI), która jest podstawą do tworzenia środowisk wykonawczych i programistycznych, w których Języki i biblioteki współpracują ze sobą.  
  
 Kod źródłowy zapisany w C# programie jest kompilowany do [języka pośredniego (IL)](../../standard/managed-code.md) , który jest zgodny ze specyfikacją interfejsu wiersza polecenia. Kod IL i zasoby, takie jak mapy bitowe i ciągi, są przechowywane na dysku w pliku wykonywalnym nazywanym zestawem, zazwyczaj z rozszerzeniem exe lub dll. Zestaw zawiera manifest, który zawiera informacje o typach, wersji, kulturze i wymaganiach dotyczących zestawu.  
  
 Gdy C# program jest wykonywany, zestaw jest ładowany do środowiska CLR, co może potrwać różne akcje na podstawie informacji zawartych w manifeście. Następnie, jeśli spełnione są wymagania dotyczące zabezpieczeń, środowisko CLR wykonuje kompilację just in Time (JIT), aby przekonwertować kod IL na instrukcje maszyny natywnej. Środowisko CLR udostępnia również inne usługi związane z automatycznym odzyskiwaniem pamięci, obsługą wyjątków i zarządzaniem zasobami. Kod, który jest wykonywany przez środowisko CLR, jest czasami określany jako "kod zarządzany", w przeciwieństwie do "kodu niezarządzanego", który jest kompilowany do macierzystego języka maszynowego, który jest przeznaczony dla określonego systemu. Na poniższym diagramie przedstawiono relacje czasu kompilacji i czasu wykonywania dla C# plików kodu źródłowego, .NET Framework biblioteki klas, zestawy i środowisko CLR.  
  
 ![Z kodu&#35; źródłowego języka C do wykonywania maszynowego](./media/introduction-to-the-csharp-language-and-the-net-framework/net-architecture-relationships.png)  
  
 Współdziałanie języków jest kluczową funkcją .NET Framework. Ponieważ kod IL tworzony przez C# kompilator jest zgodny ze specyfikacją Common Type Specification (CTS), kod IL wygenerowany z C# może współistnieć z kodem, który został wygenerowany na podstawie wersji .NET Visual Basic, Visual C++lub dowolnej z więcej niż 20 innych Języki zgodne z CTS. Pojedynczy zestaw może zawierać wiele modułów pisanych w różnych językach .NET, a typy mogą się odwoływać nawzajem, tak jakby były zapisywane w tym samym języku.  
  
 Oprócz usług czasu wykonywania, .NET Framework również zawiera rozbudowana Biblioteka ponad 4000 klas zorganizowanych w przestrzenie nazw, które zapewniają szeroką gamę przydatnych funkcji dla wszystkich elementów od danych wejściowych i wyjściowych do manipulowania ciągami XML analizowanie do Windows Forms kontrolek. Typowa C# aplikacja używa biblioteki klas .NET Framework w szerokim stopniu do obsługi typowych zadań "wodociągów".  
  
 Aby uzyskać więcej informacji na temat .NET Framework, zobacz [Omówienie struktury Microsoft .NET](../../framework/get-started/overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [C#](../index.md)
- [Wprowadzenie z wizualizacjąC#](/visualstudio/ide/quickstart-csharp-console)
