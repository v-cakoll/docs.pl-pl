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
ms.openlocfilehash: 3b24bfefd3edb0585e9c6369e9b8151b17151661
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741713"
---
# <a name="enum-design"></a>Projekt wyliczeń

Wyliczenia są specjalnym rodzajem typu wartości. Istnieją dwa rodzaje wyliczeń: proste wyliczenia i wyliczenia flag.

Proste wyliczenia reprezentują małe zamknięte zestawy wyborów. Typowym przykładem prostego wyliczenia jest zestaw kolorów.

Typy wyliczeniowe flag są przeznaczone do obsługi operacji bitowych na wartościach wyliczeniowych. Typowym przykładem wyliczenia flag jest lista opcji.

✔️ Użyj wyliczenia, aby silnie typu parametry, właściwości i zwracane wartości reprezentujące zestawy wartości.

✔️ za pomocą wyliczenia zamiast stałych statycznych.

❌ nie należy używać wyliczenia dla zestawów otwartych (takich jak wersja systemu operacyjnego, nazwiska znajomych itp.).

❌ nie zapewniają zarezerwowanych wartości wyliczenia, które są przeznaczone do użytku w przyszłości.

Zawsze możesz po prostu dodać wartości do istniejącego wyliczenia na późniejszym etapie. Aby uzyskać więcej informacji na temat dodawania wartości do typów wyliczeniowych, zobacz [Dodawanie wartości do wyliczeń](#add_value) . Wartości zarezerwowane powodują zanieczyszczenie zestawu rzeczywistych wartości i umożliwiają osiągnięcie błędów użytkownika.

❌ uniknąć publicznego ujawniania wyliczeń tylko z jedną wartością.

Typowym sposobem zapewnienia przyszłej rozszerzalności interfejsów API języka C jest dodanie zarezerwowanych parametrów do sygnatur metod. Takie zastrzeżone parametry można wyrazić jako wyliczenia z pojedynczą wartością domyślną. Nie należy tego robić w zarządzanych interfejsach API. Przeciążanie metod pozwala dodawać parametry w przyszłych wersjach.

❌ nie obejmują wartości wskaźnikowych w wyliczeniach.

Chociaż są czasami pomocne dla deweloperów platformy, wartości wskaźnikowe są mylące dla użytkowników struktury. Są one używane do śledzenia stanu wyliczenia, a nie jako jedna z wartości z zestawu reprezentowanego przez wyliczenie.

✔️ zapewnić wartość zero dla prostych typów wyliczeniowych.

Rozważ wywołanie wartości podobnej do "none". Jeśli taka wartość nie jest odpowiednia dla danego wyliczenia, najbardziej typowa wartość domyślna dla wyliczenia powinna mieć przypisaną podstawową wartość równą zero.

✔️ ROZWAŻYĆ użycie <xref:System.Int32> (domyślnie w większości języków programowania) jako typ podstawowy wyliczenia, chyba że spełniony jest którykolwiek z następujących warunków:

- Wyliczenie jest wyliczeniem flag i ma więcej niż 32 flag lub oczekuje więcej w przyszłości.

- Typ podstawowy musi być inny niż <xref:System.Int32>, aby ułatwić współdziałanie z kodem niezarządzanym.

- Mniejszy typ podstawowy spowoduje znaczne oszczędności w miejscu. Jeśli spodziewasz się, że Wyliczenie ma być używane głównie jako argument dla przepływu sterowania, rozmiar powoduje niewielkie różnice. Oszczędność rozmiaru może być istotna, jeśli:

  - Oczekuje się, że Wyliczenie ma być używane jako pole w bardzo często skonkretyzowanyj strukturze lub klasie.

  - Oczekujesz, że użytkownicy będą tworzyć duże tablice lub kolekcje wystąpień wyliczeniowych.

  - Oczekuje się, że wiele wystąpień wyliczenia ma być serializowana.

W przypadku użycia w pamięci należy pamiętać, że obiekty zarządzane są zawsze `DWORD`wyrównane, dlatego w celu wprowadzenia różnic należy użyć wielu wyliczeń lub innych małych struktur w wystąpieniu do spakowania mniejszego wyliczenia z, ponieważ całkowity rozmiar wystąpienia zawsze będzie zaokrąglany do `DWORD`.

✔️ DO flagi nazwy wyliczenia z rzeczownikami w liczbie mnogiej lub rzeczownikami i prostymi wyliczeniami z pojedynczą rzeczownikami lub oznaczeniami rzeczowników.

❌ nie należy poszerzać <xref:System.Enum?displayProperty=nameWithType> bezpośrednio.

<xref:System.Enum?displayProperty=nameWithType> jest specjalnym typem używanym przez środowisko CLR do tworzenia wyliczeń zdefiniowanych przez użytkownika. Większość języków programowania udostępnia element programistyczny, który zapewnia dostęp do tej funkcji. Na przykład, w C# `enum` słowo kluczowe jest używane do definiowania wyliczenia.

<a name="design"></a>

### <a name="designing-flag-enums"></a>Projektowanie typów wyliczeniowych flag

✔️ zastosować <xref:System.FlagsAttribute?displayProperty=nameWithType> do flagi wyliczeń. Nie stosuj tego atrybutu do prostych typów wyliczeniowych.

✔️ Użyj uprawnień dwóch dla wartości wyliczenia flag, aby można je było swobodnie łączyć przy użyciu operacji bitowej lub.

✔️ ROZWAŻYĆ dostarczenie specjalnych wartości wyliczenia dla często używanych kombinacji flag.

Operacje bitowe są zaawansowaną koncepcją i nie powinny być wymagane w przypadku prostych zadań. Przykładem takiej wartości jest <xref:System.IO.FileAccess.ReadWrite>.

❌ unikać tworzenia wyliczeń flag, w których niektóre kombinacje wartości są nieprawidłowe.

❌ unikać używania wartości wyliczeniowych flag zero, chyba że wartość reprezentuje "wszystkie flagi są wyczyszczone" i jest odpowiednio określona, zgodnie z opisem w następnej wytycznej.

✔️ NALEŻY nazwać wartość zero dla wyliczeń flag `None`. W przypadku wyliczenia flag wartość musi zawsze oznaczać, że wszystkie flagi są wyczyszczone.

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a>Dodawanie wartości do typów wyliczeniowych

Bardzo typowym sposobem jest odnajdowanie, że należy dodać wartości do wyliczenia po jego już wysłaniu. Występuje potencjalny problem ze zgodnością aplikacji w przypadku zwrócenia nowo dodanej wartości z istniejącego interfejsu API, ponieważ źle zapisywane aplikacje mogą nieprawidłowo obsłużyć nową wartość.

✔️ ROZWAŻYĆ dodanie wartości do typów wyliczeniowych, pomimo małych zagrożeń zgodności.

Jeśli masz prawdziwe dane dotyczące niezgodności aplikacji spowodowanych przez dodatki do wyliczenia, rozważ dodanie nowego interfejsu API, który zwraca nowe i stare wartości, i Zastąp stary interfejs API, który powinien nadal zwracać tylko stare wartości. Dzięki temu istniejące aplikacje będą nadal zgodne.

*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
