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
ms.openlocfilehash: 130e9b4e7f8d7076d1dc3f21f51dc07a68799bbe
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709455"
---
# <a name="enum-design"></a>Projekt wyliczeń

Wyliczenia są specjalnym rodzajem typu wartości. Istnieją dwa rodzaje wyliczeń: proste wyliczenia i wyliczenia flag.

Proste wyliczenia reprezentują małe zamknięte zestawy wyborów. Typowym przykładem prostego wyliczenia jest zestaw kolorów.

Typy wyliczeniowe flag są przeznaczone do obsługi operacji bitowych na wartościach wyliczeniowych. Typowym przykładem wyliczenia flag jest lista opcji.

**✓ DO** silnie wpisz parametry, właściwości, za pomocą wyliczeniem i zwracać wartości, które reprezentują zestawy wartości.

**✓ DO** Preferuj przy użyciu wyliczenia zamiast stałych statycznych.

**X DO NOT** wyliczenia na użytek otwartych zestawów (takie jak wersja systemu operacyjnego, nazwy użytkownika znajomych, itp.).

**X DO NOT** Podaj zastrzeżone wyliczenia wartości, które są przeznaczone do użytku w przyszłości.

Zawsze możesz po prostu dodać wartości do istniejącego wyliczenia na późniejszym etapie. Aby uzyskać więcej informacji na temat dodawania wartości do typów wyliczeniowych, zobacz [Dodawanie wartości do wyliczeń](#add_value) . Wartości zarezerwowane powodują zanieczyszczenie zestawu rzeczywistych wartości i umożliwiają osiągnięcie błędów użytkownika.

**X AVOID** publicznie udostępnianie wyliczenia z tylko jedną wartość.

Typowym sposobem zapewnienia przyszłej rozszerzalności interfejsów API języka C jest dodanie zarezerwowanych parametrów do sygnatur metod. Takie zastrzeżone parametry można wyrazić jako wyliczenia z pojedynczą wartością domyślną. Nie należy tego robić w zarządzanych interfejsach API. Przeciążanie metod pozwala dodawać parametry w przyszłych wersjach.

**X DO NOT** zawierają wartości wskaźnikowych w wyliczeniach.

Chociaż są czasami pomocne dla deweloperów platformy, wartości wskaźnikowe są mylące dla użytkowników struktury. Są one używane do śledzenia stanu wyliczenia, a nie jako jedna z wartości z zestawu reprezentowanego przez wyliczenie.

**✓ DO** Podaj wartość zero w prosty wyliczenia.

Rozważ wywołanie wartości podobnej do "none". Jeśli taka wartość nie jest odpowiednia dla danego wyliczenia, najbardziej typowa wartość domyślna dla wyliczenia powinna mieć przypisaną podstawową wartość równą zero.

**✓ CONSIDER** przy użyciu <xref:System.Int32> (ustawienie domyślne w większości języków programowania) jako typu bazowego typu wyliczeniowego, chyba że jest spełniony jeden z następujących czynności:

- Wyliczenie jest wyliczeniem flag i ma więcej niż 32 flag lub oczekuje więcej w przyszłości.

- Typ podstawowy musi być inny niż <xref:System.Int32>, aby ułatwić współdziałanie z kodem niezarządzanym.

- Mniejszy typ podstawowy spowoduje znaczne oszczędności w miejscu. Jeśli spodziewasz się, że Wyliczenie ma być używane głównie jako argument dla przepływu sterowania, rozmiar powoduje niewielkie różnice. Oszczędność rozmiaru może być istotna, jeśli:

  - Oczekuje się, że Wyliczenie ma być używane jako pole w bardzo często skonkretyzowanyj strukturze lub klasie.

  - Oczekujesz, że użytkownicy będą tworzyć duże tablice lub kolekcje wystąpień wyliczeniowych.

  - Oczekuje się, że wiele wystąpień wyliczenia ma być serializowana.

W przypadku użycia w pamięci należy pamiętać, że obiekty zarządzane są zawsze `DWORD`wyrównane, dlatego w celu wprowadzenia różnic należy użyć wielu wyliczeń lub innych małych struktur w wystąpieniu do spakowania mniejszego wyliczenia z, ponieważ całkowity rozmiar wystąpienia zawsze będzie zaokrąglany do `DWORD`.

**✓ DO** nazwa wyliczenia flagi rzeczowniki w liczbie mnogiej lub fraz rzeczownik i proste wyliczenia za pomocą pojedynczej rzeczowniki ani fraz rzeczownik.

**X DO NOT** rozszerzyć <xref:System.Enum?displayProperty=nameWithType> bezpośrednio.

<xref:System.Enum?displayProperty=nameWithType> jest specjalnym typem używanym przez środowisko CLR do tworzenia wyliczeń zdefiniowanych przez użytkownika. Większość języków programowania udostępnia element programistyczny, który zapewnia dostęp do tej funkcji. Na przykład, w C# `enum` słowo kluczowe jest używane do definiowania wyliczenia.

<a name="design"></a>

### <a name="designing-flag-enums"></a>Projektowanie typów wyliczeniowych flag

**✓ DO** zastosować <xref:System.FlagsAttribute?displayProperty=nameWithType> do wyliczenia flagi. Nie stosuj tego atrybutu do prostych typów wyliczeniowych.

**✓ DO** używać potęgami liczby dwa dla wartości wyliczenia flag, dlatego można je dowolnie łączyć przy użyciu operacji bitowej OR.

**✓ CONSIDER** dostarczanie wartości wyliczenia specjalne powszechnie używane kombinacji flag.

Operacje bitowe są zaawansowaną koncepcją i nie powinny być wymagane w przypadku prostych zadań. Przykładem takiej wartości jest <xref:System.IO.FileAccess.ReadWrite>.

**X AVOID** tworzenia wyliczenia flag gdzie niektórych kombinacji wartości są nieprawidłowe.

**X AVOID** przy użyciu flagi wyliczenia wartości zero, chyba że wartość reprezentuje "wszystkie flagi są czyszczone" i nazwie odpowiednio, zgodnie z wytycznymi dalej.

**✓ DO** nazwę zerowej wartości wyliczenia flagi `None`. W przypadku wyliczenia flag wartość musi zawsze oznaczać, że wszystkie flagi są wyczyszczone.

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a>Dodawanie wartości do typów wyliczeniowych

Bardzo typowym sposobem jest odnajdowanie, że należy dodać wartości do wyliczenia po jego już wysłaniu. Występuje potencjalny problem ze zgodnością aplikacji w przypadku zwrócenia nowo dodanej wartości z istniejącego interfejsu API, ponieważ źle zapisywane aplikacje mogą nieprawidłowo obsłużyć nową wartość.

**✓ CONSIDER** dodawania wartości do wyliczenia, pomimo ryzyka małych zgodności.

Jeśli masz prawdziwe dane dotyczące niezgodności aplikacji spowodowanych przez dodatki do wyliczenia, rozważ dodanie nowego interfejsu API, który zwraca nowe i stare wartości, i Zastąp stary interfejs API, który powinien nadal zwracać tylko stare wartości. Dzięki temu istniejące aplikacje będą nadal zgodne.

*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
