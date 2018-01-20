---
title: "Wprowadzenie do języka C# i systemu .NET Framework"
description: "Poznaj podstawy języka C# i platformy .NET. Omówienie języka C# i ekosystemu platformy .NET."
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: get-started-article
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b2ffb641f436a41c97a94a6ec117f6087851d482
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/20/2018
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>Wprowadzenie do języka C# i systemu .NET Framework
C# jest elegancki i bezpieczne zorientowany obiektowo język, który umożliwia deweloperom tworzenie szerokiej gamy bezpieczeństwa i niezawodności aplikacji uruchamianych na [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Służy C# do tworzenia klienta systemu Windows aplikacji, usług XML sieci Web, rozproszonej składniki, klient serwer aplikacji, aplikacje baz danych i znacznie, znacznie więcej. Visual C# zawiera edytora kodu zaawansowane, projektantów interfejsu użytkownika wygodny zintegrowane debugera i inne narzędzia ułatwiające tworzenie aplikacji na podstawie języka C# i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
> [!NOTE]
> [!INCLUDE[csprcs](~/includes/csprcs-md.md)] Dokumentacji przyjęto założenie, że zrozumienia podstawowe pojęcia dotyczące programowania. W przypadku pełnej dla początkujących użytkowników można eksplorować [!INCLUDE[csprcsxpr](~/includes/csprcsxpr-md.md)], który jest dostępny w sieci Web. Można również korzystać z książki i zasoby sieci Web o C#, aby dowiedzieć się praktycznych umiejętności programowania.  
  
## <a name="c-language"></a>Język C#  
 Składnia języka C# jest wysoce obszerne, ale również jest proste i łatwe dowiedzieć się więcej. Składnia nawias klamrowy języka C# będzie natychmiast rozpoznawalnych osobom zapoznać się z C, C++ lub Java. Deweloperów, którzy wiedzą żadnego z tych języków są zwykle możesz rozpocząć pracę efektywnie w języku C# w bardzo krótkim czasie. Składnia języka C# upraszcza wiele złożonością, C++ i udostępnia zaawansowane funkcje, takie jak typy dopuszczające wartości zerowe wartości wyliczenia, delegatów, wyrażenia lambda i bezpośredni dostęp do pamięci, które nie znajdują się w języku Java. C# obsługuje metody ogólne i typy, które zapewniają większą zabezpieczeń i wydajności i Iteratory, które umożliwiają implementacji klasy kolekcji do definiowania zachowania iteracji niestandardowych, które są proste w użyciu przez kod klienta. [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]wyrażenia należy jednoznacznie zapytania konstrukcji języka najwyższej jakości.  
  
 Jako zorientowany obiektowo język C# obsługuje pojęcia hermetyzacji, dziedziczenia i polimorfizm. Wszystkie zmienne i metod, w tym `Main` metody punktu wejścia aplikacji, są hermetyzowane w definicji klasy. Klasy mogą dziedziczyć bezpośrednio jednej klasie nadrzędnej, ale może wdrożyć dowolną liczbę interfejsów. Metody, które zastępują wirtualnej metody w klasie nadrzędnej wymagają `override` — słowo kluczowe w sposób, aby uniknąć przypadkowego zmiana definicji. W języku C# struktury przypomina klasy lightweight; jest to typ przydzielony stos, można zaimplementować interfejsów, ale nie obsługuje dziedziczenia.  
  
 Oprócz tych podstawowych zasad zorientowane obiektowo C# ułatwia tworzenie składników oprogramowania przez kilka konstrukcji języka innowacyjnych, takie jak następujące:  
  
-   Hermetyzowany sygnatury metody o nazwie *delegatów*, umożliwiające powiadomienia o zdarzeniach bezpieczne.  
  
-   Właściwości, które służą jako metody dostępu do zmiennych prywatnego elementu członkowskiego.  
  
-   Atrybuty, które zawierają deklaratywne metadanych o typach w czasie wykonywania.  
  
-   Komentarze dokumentacji XML w tekście.  
  
-   [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]zapewniające możliwości wbudowaną kwerendę w różnych źródeł danych.  
  
 Jeśli masz wchodzić w interakcje z innego oprogramowania systemu Windows, takich jak obiekty COM lub natywnych bibliotek DLL systemu Win32, można to zrobić w języku C# w procesie nazywanym "Interop." Współdziałanie umożliwia C# programów prawie wszystko, co można zrobić natywnych aplikacji C++. C# nawet obsługuje wskaźników i pojęcie "unsafe" kod dla tych przypadków, w których bezpośredni dostęp do pamięci jest absolutnie krytyczne.  
  
 Proces kompilacji C# jest prosta w porównaniu do C i C++ i bardziej elastyczne niż w języku Java. Istnieją żadne pliki oddzielny nagłówek i nie można zadeklarować metody i typów w określonej kolejności jest wymagany. Plik źródłowy języka C# mogą określić dowolną liczbę klasy, struktury, interfejsami i zdarzeniami.  
  
 Poniżej przedstawiono dodatkowe zasoby C#:  
  
-   Dobrym ogólne wprowadzenie do języka, zobacz rozdział 1 [specyfikacji języka C#](../../csharp/language-reference/language-specification/index.md).  
  
-   Aby uzyskać szczegółowe informacje o aspektach określonego języka C#, zobacz [odwołanie w C#](../../csharp/language-reference/index.md).  
  
-   Aby uzyskać więcej informacji na temat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], zobacz [LINQ (zapytania język Language-Integrated)](../programming-guide/concepts/linq/index.md).  

## <a name="net-framework-platform-architecture"></a>Architektura platformy .NET Framework  
 C# programy uruchamiane [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], integralnym składnikiem systemu Windows, która zawiera system wykonywania wirtualnych nazywanych środowisko uruchomieniowe języka wspólnego (CLR) i zestaw połączonych bibliotek klas. CLR jest komercyjnych wykonania typowych language infrastructure (CLI), międzynarodowy standard, która stanowi podstawę tworzenia wykonywania i środowisk deweloperskich, w których języków i bibliotek współpracować ze sobą przez firmę Microsoft.  
  
 Kod źródłowy napisane w języku C# jest kompilowany do języka pośredniego (IL), który jest zgodny ze specyfikacją interfejsu wiersza polecenia. Kod IL i zasoby, takie jak mapy bitowe i ciągi, są przechowywane na dysku w pliku wykonywalnego o nazwie zestawu, zwykle z rozszerzeniem .exe lub .dll. Zestaw zawiera manifestu, który zawiera informacje o zestawu typów, wersji, kultury i wymagania dotyczące zabezpieczeń.  
  
 Podczas wykonywania programu C# zestaw jest ładowany do środowiska CLR, co może zająć różne akcje na podstawie informacji w manifeście. Następnie jeśli spełnione są wymagania dotyczące zabezpieczeń, środowisko CLR wykonuje tylko w kompilacji time (JIT) można przekonwertować kodu IL do instrukcji natywny maszyny. Środowisko CLR także innych usług związanych z automatycznego wyrzucanie elementów bezużytecznych, obsługa wyjątków i zarządzanie zasobami. Kod, który jest wykonywany przez środowisko CLR jest czasami nazywany "kodu zarządzanego", w przeciwieństwie do "niezarządzany kod", który ma zostać skompilowany w języku macierzystym maszyny, przeznaczonego dla określonego systemu. Na poniższym diagramie przedstawiono relacje kompilacji i środowiska wykonawczego języka C# — pliki kodu źródłowego, biblioteki klas .NET Framework, zestawy i środowiska CLR.  
  
 ![Z & C# 35; kod do wykonania maszyny źródłowy](../../csharp/getting-started/media/netarchitecture.png "NETarchitecture")  
  
 Współdziałanie języków jest kluczowym elementem [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Ponieważ kod IL generowane przez kompilator języka C# zgodne do wspólnej specyfikacji typu (CTS), kod IL wygenerowany w języku C# zakłócają kod, który został wygenerowany z wersji platformy .NET, Visual Basic, Visual C++ lub ponad 20 języków CTS zgodne. Pojedynczy zestaw może zawierać wiele modułów napisane w różnych językach .NET i typy mogą odwoływać się siebie tak jak gdyby zostały napisane w języku.  
  
 Oprócz usługi w czasie wykonywania [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] obejmuje również szeroką gamę biblioteki klas ponad 4000 zorganizowane w przestrzeni nazw, które zapewniają szeroką gamę przydatne funkcje dla wszystkich z pliku danych wejściowych i wyjściowych do manipulowanie ciągami do pliku XML analizowanie formanty formularzy systemu Windows. Typowa aplikacja C# używa [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteki klas, często w celu obsługi typowych zadań "instalację".  
  
 Aby uzyskać więcej informacji na temat programu .NET Framework, zobacz [Omówienie programu Microsoft .NET Framework](../../framework/get-started/overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [C#](../../csharp/index.md) [wprowadzenie do języka Visual C# i Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
