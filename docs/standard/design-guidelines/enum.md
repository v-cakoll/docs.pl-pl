---
title: Projekt wyliczeń
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
author: KrzysztofCwalina
ms.openlocfilehash: 429f2e3821ff12ff4fc51b73c102ee3799d0228d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148135"
---
# <a name="enum-design"></a>Projekt wyliczeń
Typy wyliczeniowe są specjalnym rodzajem typu wartości. Istnieją dwa rodzaje wyliczeń: prostych typów wyliczeniowych i flagi wyliczeń.  
  
 Proste typy wyliczeniowe reprezentują małych zamknięte zestawów opcji. Typowym przykładem proste wyliczenia to zestaw kolorów.  
  
 Typy wyliczeniowe flag są przeznaczone do wsparcia Operacje bitowe wartości wyliczenia. Typowym przykładem wyliczenia flag jest lista opcji.  
  
 **✓ DO** silnie wpisz parametry, właściwości, za pomocą wyliczeniem i zwracać wartości, które reprezentują zestawy wartości.  
  
 **✓ DO** Preferuj przy użyciu wyliczenia zamiast stałych statycznych.  
  
 **X DO NOT** wyliczenia na użytek otwartych zestawów (takie jak wersja systemu operacyjnego, nazwy użytkownika znajomych, itp.).  
  
 **X DO NOT** Podaj zastrzeżone wyliczenia wartości, które są przeznaczone do użytku w przyszłości.  
  
 Na późniejszym etapie można zawsze po prostu dodać wartości do istniejącego typu wyliczeniowego. Zobacz [dodanie wartości do wyliczenia](#add_value) Aby uzyskać więcej informacji na temat dodawania wartości do wyliczenia. Zastrzeżone wartości po prostu charakteryzują się zestaw wartości rzeczywistych i powodowało błędy użytkowników.  
  
 **X AVOID** publicznie udostępnianie wyliczenia z tylko jedną wartość.  
  
 Powszechną praktyką zapewniających przyszłej rozszerzalności interfejsów API języka C jest dodać zastrzeżone parametry do podpisów metod. Takie zastrzeżone parametry mogą być wyrażone jako Typy wyliczeniowe atrybutem wartość domyślną pojedynczej. To nie należy wykonywać w zarządzanych interfejsów API. Przeciążenie metody umożliwia dodawanie parametrów w przyszłych wersjach.  
  
 **X DO NOT** zawierają wartości wskaźnikowych w wyliczeniach.  
  
 Chociaż czasami są przydatne dla deweloperów w ramach, wartownik wartości są mylące dla użytkowników Framework. Są one używane do śledzenia stanu typu wyliczeniowego, a nie jest jedną z wartości z zestawu, reprezentowany przez wyliczenie.  
  
 **✓ DO** Podaj wartość zero w prosty wyliczenia.  
  
 Należy wziąć pod uwagę podczas wywoływania wartość podobną "None". Jeśli wartość ta nie jest właściwa dla tego konkretnego wyliczenia, najbardziej typowe domyślna wartość wyliczenia powinny przypisany podstawową wartość zero.  
  
 **✓ CONSIDER** przy użyciu <xref:System.Int32> (ustawienie domyślne w większości języków programowania) jako typu bazowego typu wyliczeniowego, chyba że jest spełniony jeden z następujących czynności:  
  
-   Wyliczenia jest wyliczenie flag i masz więcej niż 32 flag lub chcą mieć w przyszłości.  
  
-   Typ podstawowy musi być inna niż <xref:System.Int32> dla ułatwia współdziałanie z kodem niezarządzanym Oczekiwano innego rozmiaru wyliczenia.  
  
-   Mniejsze bazowego typu spowoduje znaczne oszczędności miejsca. Jeśli oczekujesz, wyliczenia, które ma być używany przede wszystkim jako argument dla przepływu sterowania, rozmiar sprawia, że niewielkie różnice. Oszczędności rozmiaru wynikające mogą być znaczące, jeśli:  
  
    -   Oczekujesz, że wyliczenie, które ma być używany jako pole w bardzo często skonkretyzowany struktury lub klasy.  
  
    -   Oczekujesz, że użytkownicy, aby utworzyć duże tablice i kolekcje wystąpieniami enum.  
  
    -   Spodziewasz się dużej liczby wystąpień typu wyliczeniowego do zserializowania.  
  
 Do użycia w pamięci należy pamiętać, że zarządzane obiekty są zawsze `DWORD`-wyrównane, więc należy skutecznie wiele typów wyliczeniowych lub innych struktur małe w wystąpieniu umieszczenie mniejszych wyliczenia z celu reagować, ponieważ rozmiar wystąpienia całkowita jest zawsze Zamierzasz zaokrąglone do `DWORD`.  
  
 **✓ DO** nazwa wyliczenia flagi rzeczowniki w liczbie mnogiej lub fraz rzeczownik i proste wyliczenia za pomocą pojedynczej rzeczowniki ani fraz rzeczownik.  
  
 **X DO NOT** rozszerzyć <xref:System.Enum?displayProperty=nameWithType> bezpośrednio.  
  
 <xref:System.Enum?displayProperty=nameWithType> jest specjalnym typem jest używana przez środowisko CLR do tworzenia wyliczenia zdefiniowanych przez użytkownika. Większość języków programowania, podaj element programowania, który umożliwia dostęp do tej funkcji. Na przykład w języku C# `enum` — słowo kluczowe jest używane do definiowania wyliczenia.  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a>Projektowanie flagi wyliczeń  
 **✓ DO** zastosować <xref:System.FlagsAttribute?displayProperty=nameWithType> do wyliczenia flagi. Nie dotyczą tego atrybutu prostych typów wyliczeniowych.  
  
 **✓ DO** używać potęgami liczby dwa dla wartości wyliczenia flag, dlatego można je dowolnie łączyć przy użyciu operacji bitowej OR.  
  
 **✓ CONSIDER** dostarczanie wartości wyliczenia specjalne powszechnie używane kombinacji flag.  
  
 Operacje bitowe są zaawansowane pojęcia i nie powinno być wymagane dla prostych zadań. <xref:System.IO.FileAccess.ReadWrite> znajduje się przykład specjalna wartość.  
  
 **X AVOID** tworzenia wyliczenia flag gdzie niektórych kombinacji wartości są nieprawidłowe.  
  
 **X AVOID** przy użyciu flagi wyliczenia wartości zero, chyba że wartość reprezentuje "wszystkie flagi są czyszczone" i nazwie odpowiednio, zgodnie z wytycznymi dalej.  
  
 **✓ DO** nazwę zerowej wartości wyliczenia flagi `None`. Dla wyliczenia flag wartość musi zawsze oznacza "wszystkie flagi są czyszczone."  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a>Dodanie wartości do wyliczenia  
 Jest bardzo popularne jest potrzebna dodać wartości do wyliczenia, po już został wysłany. Istnieje potencjalny problem ze zgodnością aplikacji gdy nowo dodanych wartość jest zwracana z istniejących interfejsów API, ponieważ źle napisane aplikacje nie może obsługiwać nową wartość poprawnie.  
  
 **✓ CONSIDER** dodawania wartości do wyliczenia, pomimo ryzyka małych zgodności.  
  
 Jeśli masz rzeczywiste dane dotyczące problemów ze zgodnością aplikacji spowodowanych dodatki do wyliczenia, Rozważ dodanie nowego interfejsu API, które zwraca wartości nowym i starym i wycofana starego interfejsu API, który powinno być kontynuowane, zwracając starej wartości. Pozwoli to zagwarantować, że istniejące aplikacje są zgodne.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)  
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
