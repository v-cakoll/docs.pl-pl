---
title: Projekt wyliczenia
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 544f617ca3a352814504125d7a61d70db5a81566
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579252"
---
# <a name="enum-design"></a>Projekt wyliczenia
Wyliczenia to specjalny rodzaj typu wartości. Istnieją dwa rodzaje wyliczenia: proste Typy wyliczeniowe i flagi wyliczenia.  
  
 Proste typy wyliczeniowe reprezentują małych zestawów zamkniętego opcji. Typowym przykładem prostego wyliczenia to zestaw kolorów.  
  
 Typy wyliczeniowe flag zostały zaprojektowane do obsługi Operacje bitowe wartości wyliczenia. Typowym przykładem wyliczenia flag znajduje się lista opcji.  
  
 **CZY ✓** silnie wpisz parametry, właściwości, za pomocą wyliczeniem i zwracać wartości, które reprezentują zestawy wartości.  
  
 **CZY ✓** Preferuj przy użyciu wyliczenia zamiast stałych statycznych.  
  
 **X nie** wyliczenia na użytek otwartych zestawów (takie jak wersja systemu operacyjnego, nazwy użytkownika znajomych, itp.).  
  
 **X nie** Podaj zastrzeżone wyliczenia wartości, które są przeznaczone do użytku w przyszłości.  
  
 Zawsze po prostu można dodać wartości do istniejących wyliczenia na późniejszym etapie. Zobacz [dodawania wartości do wyliczenia](#add_value) uzyskać więcej informacji dotyczących dodawania wartości do wyliczenia. Zastrzeżone wartości po prostu charakteryzują się zbiór wartości rzeczywistych i powodowało błędy użytkownika.  
  
 **X należy UNIKAĆ** publicznie udostępnianie wyliczenia z tylko jedną wartość.  
  
 Jest typowym rozwiązaniem dla zapewnienia przyszłych rozszerzalności interfejsów API C aby dodać parametry zarezerwowane do sygnatury metody. Parametry takie zastrzeżone może zostać wyrażona jako wyliczenia za pomocą pojedynczego domyślną wartość. Nie należy to zrobić w zarządzanych interfejsów API. Przeciążenie metody umożliwia dodawanie parametrów w przyszłych wersjach.  
  
 **X nie** zawierają wartości wskaźnikowych w wyliczeniach.  
  
 Chociaż są czasami pomaga deweloperom framework, wartości wartownika są trudne dla użytkowników platformy. Są one używane do śledzenia stanu wyliczenia, a nie jest jedną z wartości z zestawu reprezentowany przez wyliczenia.  
  
 **CZY ✓** Podaj wartość zero w prosty wyliczenia.  
  
 Należy wziąć pod uwagę podczas wywoływania wartości podobnie "None." Jeśli wartość ta nie jest odpowiedni dla tego konkretnego wyliczenia, najczęściej domyślna wartość wyliczenia należy przypisać odpowiednia wartość zero.  
  
 **✓ ROZWAŻ** przy użyciu <xref:System.Int32> (ustawienie domyślne w większości języków programowania) jako typu bazowego typu wyliczeniowego, chyba że jest spełniony jeden z następujących czynności:  
  
-   Wyliczenia jest wyliczenia flag, i mieć więcej niż 32 flagi lub oczekiwana jest więcej w przyszłości.  
  
-   Typ podstawowy musi być inna niż <xref:System.Int32> ułatwia współdziałanie z kodem niezarządzanym oczekiwano inny rozmiar wyliczenia.  
  
-   Mniejsze podstawowy typ spowoduje znaczne oszczędności miejsca. Jeśli planujesz wyliczenia mają być używane głównie jako argument dla przepływu sterowania, rozmiar sprawia, że mała różnica. Wielkość oszczędności mogą być istotne jeśli:  
  
    -   Spodziewasz się wyliczenia mają być używane jako pola na bardzo często skonkretyzowanym struktury lub klasy.  
  
    -   Spodziewasz się użytkownikom na tworzenie dużych tablice lub kolekcji wystąpień wyliczenia.  
  
    -   Spodziewasz się dużej liczby wystąpień wyliczenia do serializacji.  
  
 Do użytku w pamięci, należy pamiętać, zawsze są zarządzane obiekty `DWORD`-wyrównane, więc należy skutecznie wiele typów wyliczeniowych lub inne małych struktury w wystąpieniu można spakować mniejszych wyliczenie o Aby pracować wydajniej, ponieważ rozmiar całkowitą wystąpienia jest zawsze będzie zaokrągloną w górę do `DWORD`.  
  
 **CZY ✓** nazwa wyliczenia flagi rzeczowniki w liczbie mnogiej lub fraz rzeczownik i proste wyliczenia za pomocą pojedynczej rzeczowniki ani fraz rzeczownik.  
  
 **X nie** rozszerzyć <xref:System.Enum?displayProperty=nameWithType> bezpośrednio.  
  
 <xref:System.Enum?displayProperty=nameWithType> specjalny typ służy przez środowisko CLR do tworzenia wyliczenia zdefiniowanych przez użytkownika. Większość języków programowania udostępnia elementu programistycznego, która umożliwia dostęp do tej funkcji. Na przykład w języku C# `enum` — słowo kluczowe jest używane do definiowania wyliczenia.  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a>Projektowanie wyliczenia flagi  
 **CZY ✓** zastosować <xref:System.FlagsAttribute?displayProperty=nameWithType> do wyliczenia flagi. Nie dotyczą tego atrybutu prostego wyliczenia.  
  
 **CZY ✓** używać potęgami liczby dwa dla wartości wyliczenia flag, dlatego można je dowolnie łączyć przy użyciu operacji bitowej OR.  
  
 **ROZWAŻ ✓** dostarczanie wartości wyliczenia specjalne powszechnie używane kombinacji flag.  
  
 Operacje bitowe są zaawansowane koncepcji i nie może być wymagane dla prostych zadań. <xref:System.IO.FileAccess.ReadWrite> jest to przykład specjalna wartość.  
  
 **X należy UNIKAĆ** tworzenia wyliczenia flag gdzie niektórych kombinacji wartości są nieprawidłowe.  
  
 **X należy UNIKAĆ** przy użyciu flagi wyliczenia wartości zero, chyba że wartość reprezentuje "wszystkie flagi są czyszczone" i nazwie odpowiednio, zgodnie z wytycznymi dalej.  
  
 **CZY ✓** nazwę zerowej wartości wyliczenia flagi `None`. Dla wyliczenia flag wartość musi zawsze oznacza "wszystkie flagi są czyszczone."  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a>Dodając wartość wyliczenia  
 Często zdarza się, aby dowiedzieć się, że trzeba dodać do wyliczenia wartości, po już zostały dostarczone. Brak potencjalny problem ze zgodnością aplikacji, gdy zostanie zwrócona wartość nowo dodanego przez istniejący interfejs API, ponieważ niepoprawnie napisane aplikacji nie może obsługiwać nową wartość poprawnie.  
  
 **ROZWAŻ ✓** dodawania wartości do wyliczenia, pomimo ryzyka małych zgodności.  
  
 Jeśli masz prawdziwe dane dotyczące problemów ze zgodnością aplikacji spowodowane przez dodatki do wyliczenia, należy dodać nowy interfejs API, który zwraca wartości nowym i starym i zastąpić starego interfejsu API, który powinno być kontynuowane zwracanie starych wartości. Daje to pewność, że istniejące aplikacje są zgodne.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
