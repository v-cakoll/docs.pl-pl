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
ms.openlocfilehash: a2cd1039f95a763002922fc2fa24eff77838de80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141304"
---
# <a name="best-practices-for-developing-world-ready-applications"></a>Najlepsze praktyki dotyczące tworzenia aplikacji gotowych do pracy na całym świecie

W tej sekcji opisano najlepsze rozwiązania, które należy przestrzegać podczas opracowywania aplikacji gotowych do użycia na całym świecie.

## <a name="globalization-best-practices"></a>Najlepsze praktyki w zakresie globalizacji

1. Zrób aplikację Unicode wewnętrznie.

2. Użyj klas z uwzględnieniem <xref:System.Globalization> kultury dostarczonych przez obszar nazw do manipulowania i formatowania danych.

    - Do sortowania należy <xref:System.Globalization.SortKey> użyć <xref:System.Globalization.CompareInfo> klasy i klasy.

    - W przypadku porównań <xref:System.Globalization.CompareInfo> ciągów należy użyć klasy.

    - W przypadku formatowania daty i <xref:System.Globalization.DateTimeFormatInfo> godziny należy użyć tej klasy.

    - W przypadku formatowania liczbowego <xref:System.Globalization.NumberFormatInfo> należy użyć tej klasy.

    - W przypadku kalendarzy gregoriańskiego i niegregoriańskiego należy użyć <xref:System.Globalization.Calendar> klasy lub jednej z określonych implementacji kalendarza.

3. Użyj ustawienia właściwości kultury <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> dostarczonych przez klasę w odpowiednich sytuacjach. <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> Właściwość służy do formatowania zadań, takich jak data i godzina lub formatowanie liczbowe. Użyj <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> właściwości, aby pobrać zasoby. Należy zauważyć, że `CurrentCulture` i `CurrentUICulture` właściwości można ustawić na wątek.

4. Umożliwia aplikacji odczytywanie i zapisywanie danych do i z różnych kodowania przy <xref:System.Text> użyciu klas kodowania w przestrzeni nazw. Nie zakładaj danych ASCII. Załóżmy, że znaki międzynarodowe będą dostarczane wszędzie tam, gdzie użytkownik może wprowadzać tekst. Na przykład aplikacja powinna akceptować znaki międzynarodowe w nazwach serwerów, katalogach, nazwach plików, nazwach użytkowników i adresach URL.

5. Korzystając z <xref:System.Text.UTF8Encoding> klasy, ze względów bezpieczeństwa, należy użyć funkcji wykrywania błędów oferowanych przez tę klasę. Aby włączyć funkcję wykrywania błędów, należy utworzyć wystąpienie klasy przy `throwOnInvalidBytes` użyciu konstruktora, `true`który przyjmuje parametr i ustawić wartość tego parametru .

6. Jeśli to możliwe, doobsługi ciągów jako ciągi całe zamiast jako szereg pojedynczych znaków. Jest to szczególnie ważne podczas sortowania lub wyszukiwania podciągów. Zapobiegnie to problemom związanym z analizowaniem połączonych znaków. Można również pracować z jednostkami tekstu, a <xref:System.Globalization.StringInfo?displayProperty=nameWithType> nie pojedynczymi znakami, używając klasy.

7. Wyświetlanie tekstu przy użyciu <xref:System.Drawing> klas podanych przez obszar nazw.

8. Aby zapewnić spójność między systemami operacyjnymi, <xref:System.Globalization.CultureInfo>nie zezwalaj na zastępowanie ustawień użytkownika . Użyj `CultureInfo` konstruktora, `useUserOverride` który akceptuje parametr `false`i ustaw go na .

9. Przetestuj funkcjonalność aplikacji w międzynarodowych wersjach systemu operacyjnego, korzystając z danych międzynarodowych.

10. Jeśli decyzja o zabezpieczeniach jest oparta na wyniku porównania ciągów lub operacji zmiany wielkości sprawy, należy użyć operacji ciągu niewrażliwego na kulturę. Praktyka ta gwarantuje, że wartość wyniku nie `CultureInfo.CurrentCulture`ma wpływu na wynik . Zobacz ["Porównania ciągów, które używają bieżącej kultury"](../../../docs/standard/base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) sekcji [Najlepsze rozwiązania dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md) na przykład, który pokazuje, jak porównania ciągów zależnych od kultury może powodować niespójne wyniki.

## <a name="localization-best-practices"></a>Najważniejsze praktyki lokalizacyjne

1. Przenieś wszystkie zasoby lokalizowe, aby oddzielić biblioteki DLL tylko do zasobów. Zlokalizowane zasoby obejmują elementy interfejsu użytkownika, takie jak ciągi, komunikaty o błędach, okna dialogowe, menu i zasoby obiektów osadzonych.

2. Nie należy kodować ciągów ani zasobów interfejsu użytkownika.

3. Nie należy umieszczać zasobów nielokalizowanych w bibliotekach DLL tylko do zasobów. Powoduje to zamieszanie dla tłumaczy.

4. Nie należy używać ciągów złożonych, które są tworzone w czasie wykonywania z połączonych fraz. Ciągi złożone są trudne do zlokalizowania, ponieważ często przyjmują angielski porządek gramatyczny, który nie ma zastosowania do wszystkich języków.

5. Należy unikać niejednoznacznych konstrukcji, takich jak "Pusty folder", gdzie ciągi mogą być tłumaczone inaczej w zależności od ról gramatycznych składników ciągu. Na przykład "pusty" może być czasownikiem lub przymiotnikiem, co może prowadzić do różnych tłumaczeń w językach takich jak włoski lub francuski.

6. Unikaj używania obrazów i ikon zawierających tekst w aplikacji. Są one drogie do zlokalizowania.

7. Pozostawić dużo miejsca na długość ciągów, aby rozwinąć w interfejsie użytkownika. W niektórych językach frazy mogą wymagać 50-75 procent więcej miejsca niż potrzebują w innych językach.

8. Użyj <xref:System.Resources.ResourceManager?displayProperty=nameWithType> klasy do pobierania zasobów na podstawie kultury.

9. Program [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) służy do tworzenia okien dialogowych formularzy systemu Windows, dzięki czemu można je zlokalizować za pomocą [Edytora zasobów formularzy systemu Windows (Winres.exe).](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md) Nie należy ręcznie kodować okien dialogowych formularzy systemu Windows.

10. Zorganizuj profesjonalną lokalizację (tłumaczenie).

11. Aby uzyskać pełny opis tworzenia i lokalizowania zasobów, zobacz [Zasoby w aplikacjach](../../../docs/framework/resources/index.md).

## <a name="globalization-best-practices-for-aspnet-applications"></a>Najważniejsze rozwiązania dotyczące globalizacji dla aplikacji ASP.NET

1. Jawnie ustaw <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> <xref:System.Globalization.CultureInfo.CurrentCulture%2A> i właściwości w aplikacji. Nie należy polegać na wartości ach domyślnych.

2. Należy zauważyć, że ASP.NET aplikacje są aplikacje zarządzane i dlatego można użyć tych samych klas, jak inne aplikacje zarządzane do pobierania, wyświetlania i manipulowania informacjami na podstawie kultury.

3. Należy pamiętać, że w ASP.NET można określić następujące trzy typy kodowania:

    - requestEncoding określa kodowanie otrzymane z przeglądarki klienta.

    - responseEncoding określa kodowanie do wysłania do przeglądarki klienta. W większości przypadków to kodowanie powinno być takie samo jak określone dla requestEncoding.

    - fileEncoding określa domyślne kodowanie dla analizy plików .aspx, .asmx i .asax.

4. Określ wartości atrybutów requestEncoding, responseEncoding, fileEncoding, culture i uiCulture w następujących trzech miejscach w aplikacji ASP.NET:

    - W sekcji globalizacji pliku Web.config. Ten plik jest zewnętrzny dla aplikacji ASP.NET. Aby uzyskać więcej informacji, zobacz [ \<globalizacja> element](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hy4kkhe0(v=vs.100)).

    - W dyrektywie strony. Należy zauważyć, że gdy aplikacja znajduje się na stronie, plik został już przeczytany. W związku z tym jest za późno, aby określić fileEncoding i requestEncoding. Tylko uiCulture, kultury i odpowiedziKodowanie encoding można określić w dyrektywie strony.

    - Programowo w kodzie aplikacji. To ustawienie może się różnić w zależności od żądania. Podobnie jak w przypadku dyrektywy strony, do czasu osiągnięcia kodu aplikacji jest za późno, aby określić fileEncoding i requestEncoding. Tylko uiCulture, Kultury i odpowiedziKodowanie encoding można określić w kodzie aplikacji.

5. Należy zauważyć, że wartość uiCulture można ustawić na język akceptacji przeglądarki.

## <a name="see-also"></a>Zobacz też

- [Globalizacja i lokalizacja](../../../docs/standard/globalization-localization/index.md)
- [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)
