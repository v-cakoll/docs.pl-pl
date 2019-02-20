---
title: Najlepsze praktyki dotyczące tworzenia aplikacji gotowych do wydania
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- global applications, best practices
- world-ready applications, best practices
- globalization [.NET Framework], best practices
- international applications [.NET Framework], best practices
ms.assetid: f08169c7-aad8-4ec3-9a21-9ebd3b89986c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a42a568e7c3f3a1a5c84d2ceae49c262f77d275d
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442493"
---
# <a name="best-practices-for-developing-world-ready-applications"></a>Najlepsze rozwiązania dotyczące tworzenia aplikacji gotowych

W tej sekcji opisano najważniejsze praktyki do naśladowania podczas tworzenia aplikacji gotowych.

## <a name="globalization-best-practices"></a>Najlepsze praktyki w zakresie globalizacji

1. Przyznawanie aplikacji Unicode wewnętrznie.

2. Użyj klas świadomych kultury dostarczonych przez <xref:System.Globalization> przestrzeń nazw do manipulowania i formatowania danych.

    - Do sortowania użyj <xref:System.Globalization.SortKey> klasy i <xref:System.Globalization.CompareInfo> klasy.

    - W przypadku porównywania ciągów znaków użyj <xref:System.Globalization.CompareInfo> klasy.

    - W przypadku formatowania daty i godziny, użyj <xref:System.Globalization.DateTimeFormatInfo> klasy.

    - Do formatowania liczbowego użyj <xref:System.Globalization.NumberFormatInfo> klasy.

    - W przypadku kalendarzy — gregoriańskiego i innych niż gregoriański, użyj <xref:System.Globalization.Calendar> klasy lub jednej z określonych implementacji kalendarza.

3. Użyj ustawień właściwości kultury dostarczonych przez <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> klasy w odpowiednich sytuacjach. Użyj <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwości formatowania zadań, takich jak Data i godzina lub formatowanie numeryczne. Użyj <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> właściwość służąca do pobierania zasobów. Należy pamiętać, że `CurrentCulture` i `CurrentUICulture` właściwości mogą być ustawiane dla wątku.

4. Umożliw aplikacji odczytywanie i zapisywanie danych do i z różnych kodowań przy użyciu klas kodowania w <xref:System.Text> przestrzeni nazw. Nie zakładaj danych ASCII. Przyjęto założenie, że znaki międzynarodowe zostaną umieszczone gdziekolwiek można wprowadzać tekst. Na przykład aplikacja powinna obsługiwać znaki międzynarodowe w nazwy serwerów, katalogów, nazw plików, nazwy użytkowników i adresów URL.

5. Korzystając z <xref:System.Text.UTF8Encoding> klasy, ze względów bezpieczeństwa używać funkcji wykrywania błędów oferowanych przez tę klasę. Aby włączyć funkcję wykrywania błędów, należy utworzyć wystąpienie klasy za pomocą konstruktora, który przyjmuje `throwOnInvalidBytes` parametru i ustaw wartość tego parametru na `true`.

6. Jeśli to możliwe, należy obsługiwać ciągi jako ciągi całego, a nie jako serię pojedynczych znaków. Jest to szczególnie ważne podczas sortowania i wyszukiwania podciągów. Pozwoli to uniknąć problemów związanych z przetwarzaniem znaków łączonych. Można również pracować jednostkach tekstowe, a nie pojedyncze znaki przy użyciu <xref:System.Globalization.StringInfo?displayProperty=nameWithType> klasy.

7. Wyświetl tekst przy użyciu klas dostarczonych przez <xref:System.Drawing> przestrzeni nazw.

8. W celu zapewnienia spójności we wszystkich systemach operacyjnych nie zezwalaj na ustawienia użytkownika zastępowały <xref:System.Globalization.CultureInfo>. Użyj `CultureInfo` Konstruktor, który akceptuje `useUserOverride` parametru i ustaw ją na `false`.

9. Przetestuj funkcjonalność swojej aplikacji w międzynarodowych wersjach systemu operacyjnego, przy użyciu danych w różnych językach.

10. Jeśli decyzja dot. zabezpieczeń opiera się na wyniku porównania ciągów lub operacji zmiany wielkości, należy użyć operacji niewrażliwość na ustawienia kulturowe ciąg. Daje to gwarancję, że wynik nie wpływa wartość `CultureInfo.CurrentCulture`. Zobacz ["Ciągów porównań, użyj bieżącej kultury"](../../../docs/standard/base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) części [najlepsze rozwiązania dotyczące Using Strings](../../../docs/standard/base-types/best-practices-strings.md) dla przykładu, który demonstruje sposób ciągach wrażliwych na kulturę może wygenerować porównania niespójne wyniki.

## <a name="localization-best-practices"></a>Najlepsze rozwiązania w lokalizacji

1. Przenieś wszystkie lokalizowalne zasoby do oddzielnych bibliotek DLL z samymi zasobami. Lokalizowalne zasoby obejmują elementy interfejsu użytkownika, takich jak ciągi, komunikaty o błędach, okna dialogowe, menu i zasoby obiektów osadzonych.

2. Czy nie wstawiaj na stałe ciągów ani zasobów interfejsu użytkownika.

3. Nie umieszczaj nielokalizowanych zasobów tylko do zasobu biblioteki dll. Powoduje to pracę tłumaczom.

4. Nie używaj złożonych ciągów, które są kompilowane w czasie wykonywania z wyrażeń połączonych. Ciągi złożone są trudne do zlokalizowania, ponieważ często zakładają porządek gramatyczny angielskiego, który nie ma zastosowania do wszystkich języków.

5. Unikaj niejednoznacznych konstrukcji, takich jak "Empty Folder", gdzie ciągi mogą być tłumaczone różnie w zależności od ról gramatycznych składników ciągów. Na przykład "empty" może być czasownikiem lub przymiotnikiem, co może prowadzić do różnych tłumaczeń w językach takich jak francuski czy włoski.

6. Należy unikać używania obrazów i ikon, które zawierają tekst w aplikacji. Są one kosztowne do zlokalizowania.

7. Zapewnij odpowiednią ilość miejsca dla długości ciągów, które mogą się rozszerzyć w interfejsie użytkownika. W przypadku niektórych języków frazy mogą wymagać 50-75 procent więcej miejsca niż potrzebne w innych językach.

8. Użyj <xref:System.Resources.ResourceManager?displayProperty=nameWithType> klasy do pobrania zasobów na podstawie kultury.

9. Użyj [programu Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) do tworzenia formularzy Windows oknach dialogowych, aby mogły być lokalizowane za pomocą [Edytor zasobów formularzy systemu Windows (Winres.exe)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md). Nie Koduj okien dialogowych kontrolek Windows ręcznie.

10. Przygotuj do profesjonalnej lokalizacji (tłumaczenia).

11. Aby uzyskać pełny opis tworzenia i lokalizowania zasobów, zobacz [zasoby w aplikacjach](../../../docs/framework/resources/index.md).

## <a name="globalization-best-practices-for-aspnet-applications"></a>Globalizacja najlepsze rozwiązania dotyczące aplikacji platformy ASP.NET

1. Jawnie ustawić <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> i <xref:System.Globalization.CultureInfo.CurrentCulture%2A> właściwości w aplikacji. Nie należy polegać na wartości domyślne.

2. Należy pamiętać, że aplikacje ASP.NET to aplikacje zarządzane i w związku z tym można użyć tych samych klas jako innych aplikacji zarządzanych do pobierania, wyświetlania, informacji i operowania nimi na podstawie kultury.

3. Należy pamiętać, że w programie ASP.NET: można określić trzy następujące typy kodowania:

    - Funkcja requestEncoding Określa kodowanie otrzymane od przeglądarki klienta.

    - Funkcja responseEncoding Określa kodowanie wysyłane do przeglądarki klienta. W większości sytuacji to kodowanie powinno być taka sama jak określone dla requestEncoding.

    - Funkcja fileEncoding Określa domyślne kodowanie .aspx, .asmx i .asax plików.

4. Określ wartości dla atrybutów requestEncoding, responseEncoding, fileEncoding, culture i uiCulture w następujących trzech miejscach w aplikacji ASP.NET:

    - W sekcji globalizacji w pliku Web.config. Ten plik jest zewnętrzny dla aplikacji ASP.NET. Aby uzyskać więcej informacji, zobacz [ \<globalizacji > Element](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hy4kkhe0(v=vs.100)).

    - W dyrektywie page. Należy pamiętać, że gdy aplikacja znajduje się na stronie, plik jest już przeczytana. Dlatego jest za późno, aby określić fileEncoding i requestEncoding. Tylko uiCulture, Culture i responseEncoding można określić w dyrektywie page.

    - Programowo w kodzie aplikacji. To ustawienie może się wraz z żądaniem. Jak z dyrektywą page przez czas kodu aplikacji w osiągnięciu jej jest za późno, aby określić fileEncoding i requestEncoding. Tylko uiCulture, Culture i responseEncoding można określić w kodzie aplikacji.

5. Język, jaki akceptuje należy pamiętać, że wartość uiCulture można ustawić w przeglądarce.

## <a name="see-also"></a>Zobacz także

- [Globalizacja i lokalizacja](../../../docs/standard/globalization-localization/index.md)
- [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)
