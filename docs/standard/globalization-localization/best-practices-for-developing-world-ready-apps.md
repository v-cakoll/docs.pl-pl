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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141304"
---
# <a name="best-practices-for-developing-world-ready-applications"></a>Najlepsze rozwiązania dotyczące tworzenia aplikacji gotowych do użytku na całym świecie

W tej sekcji opisano najlepsze rozwiązania, które należy wykonać podczas tworzenia aplikacji gotowych do działania.

## <a name="globalization-best-practices"></a>Najlepsze rozwiązania z zakresu globalizacji

1. Udostępnianie kodu Unicode aplikacji wewnętrznie.

2. Użyj klas opartych na kulturze dostarczonych przez przestrzeń nazw <xref:System.Globalization>, aby manipulować i formatować dane.

    - W celu sortowania Użyj klasy <xref:System.Globalization.SortKey> i klasy <xref:System.Globalization.CompareInfo>.

    - W przypadku porównywania ciągów użyj klasy <xref:System.Globalization.CompareInfo>.

    - W przypadku formatowania daty i godziny użyj klasy <xref:System.Globalization.DateTimeFormatInfo>.

    - W przypadku formatowania liczbowego należy użyć klasy <xref:System.Globalization.NumberFormatInfo>.

    - W przypadku kalendarzy gregoriańskich i innych niż gregoriański należy użyć klasy <xref:System.Globalization.Calendar> lub jednej z określonych implementacji kalendarza.

3. Użyj ustawień właściwości kultury dostarczonych przez klasę <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> w odpowiednich sytuacjach. Użyj właściwości <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> do formatowania zadań, takich jak Data i godzina lub formatowanie numeryczne. Użyj właściwości <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>, aby pobrać zasoby. Należy pamiętać, że właściwości `CurrentCulture` i `CurrentUICulture` można ustawić na wątek.

4. Zezwól aplikacji na odczytywanie i zapisywanie danych do i z różnych kodowań przy użyciu klas kodowania w przestrzeni nazw <xref:System.Text>. Nie zakładaj danych ASCII. Załóżmy, że znaki międzynarodowe zostaną dostarczone wszędzie tam, gdzie użytkownik może wprowadzić tekst. Na przykład aplikacja powinna akceptować znaki międzynarodowe w nazwach serwerów, katalogach, nazwach plików, nazwach użytkowników i adresach URL.

5. Korzystając z klasy <xref:System.Text.UTF8Encoding>, ze względów bezpieczeństwa Użyj funkcji wykrywania błędów oferowanej przez tę klasę. Aby włączyć funkcję wykrywania błędów, Utwórz wystąpienie klasy przy użyciu konstruktora, który przyjmuje parametr `throwOnInvalidBytes` i ustaw wartość tego parametru na `true`.

6. Jeśli to możliwe, należy obsługiwać ciągi jako całe ciągi, a nie jako serię pojedynczych znaków. Jest to szczególnie ważne podczas sortowania lub wyszukiwania podciągów. Uniemożliwi to problemy związane z analizowaniem połączonych znaków. Możesz również współpracować z jednostkami tekstu, a nie pojedynczymi znakami przy użyciu klasy <xref:System.Globalization.StringInfo?displayProperty=nameWithType>.

7. Wyświetlaj tekst przy użyciu klas dostarczonych przez przestrzeń nazw <xref:System.Drawing>.

8. W celu zachowania spójności w systemach operacyjnych nie Zezwalaj ustawieniom użytkownika na przesłonięcie <xref:System.Globalization.CultureInfo>. Użyj konstruktora `CultureInfo`, który akceptuje parametr `useUserOverride` i ustaw go na `false`.

9. Przetestuj funkcjonalność aplikacji w międzynarodowych wersjach systemu operacyjnego, korzystając z danych międzynarodowych.

10. Jeśli decyzja dotycząca zabezpieczeń opiera się na wyniku porównania ciągów lub operacji zmiany wielkości liter, należy użyć niewrażliwej na kulturę operacji na ciągach. Ta metoda zapewnia, że wartość `CultureInfo.CurrentCulture`nie wpłynie na wynik. Zobacz sekcję ["porównania ciągów, które wykorzystują bieżącą kulturę"](../../../docs/standard/base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) [najlepszych rozwiązań dotyczących używania ciągów](../../../docs/standard/base-types/best-practices-strings.md) , aby zapoznać się z przykładem, w jaki sposób porównania ciągów zależnych od kultury mogą generować niespójne wyniki.

## <a name="localization-best-practices"></a>Najlepsze rozwiązania dotyczące lokalizacji

1. Przenieś wszystkie lokalizowalne zasoby do oddzielnych bibliotek DLL, które są oparte na zasobach. Zasoby lokalizowalne obejmują elementy interfejsu użytkownika, takie jak ciągi, komunikaty o błędach, okna dialogowe, menu i zasoby osadzonych obiektów.

2. Nie umieszczaj ciągów ani zasobów interfejsu użytkownika.

3. Nie należy umieszczać zasobów niezlokalizowanych w bibliotekach DLL z samymi zasobami. Powoduje to pomyłkę w przypadku tłumaczeń.

4. Nie używaj złożonych ciągów, które są kompilowane w czasie wykonywania z połączonych fraz. Ciągi złożone są trudne do zlokalizowania, ponieważ często zakładają angielską kolejność gramatyczną, która nie ma zastosowania do wszystkich języków.

5. Unikaj niejednoznacznych konstrukcji, takich jak "pusty folder", gdzie ciągi mogą być tłumaczone inaczej w zależności od ról gramatycznych składników ciągu. Na przykład "Empty" może być czasownikiem lub przymiotnikiem, który może prowadzić do różnych tłumaczeń w językach, takich jak włoski lub francuski.

6. Unikaj używania obrazów i ikon, które zawierają tekst w aplikacji. Ich lokalizowanie jest kosztowne.

7. Zezwól na dużą ilość miejsca na długość ciągów do rozwinięcia w interfejsie użytkownika. W przypadku niektórych języków frazy mogą wymagać od 50-75% więcej miejsca niż w innych językach.

8. Użyj klasy <xref:System.Resources.ResourceManager?displayProperty=nameWithType>, aby pobrać zasoby na podstawie kultury.

9. Użyj [programu Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) , aby utworzyć Windows Forms oknach dialogowych, aby można było je lokalizować przy użyciu [edytora zasobów Windows Forms (Winres. exe)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md). Nie należy ręcznie Windows Forms okien dialogowych.

10. Rozmieść na potrzeby profesjonalnej lokalizacji (tłumaczenia).

11. Pełny opis tworzenia i lokalizowania zasobów znajduje się [w temacie Zasoby w aplikacjach](../../../docs/framework/resources/index.md).

## <a name="globalization-best-practices-for-aspnet-applications"></a>Najlepsze rozwiązania z zakresu globalizacji dla aplikacji ASP.NET

1. Jawnie ustaw <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> i <xref:System.Globalization.CultureInfo.CurrentCulture%2A> właściwości w aplikacji. Nie należy polegać na wartościach domyślnych.

2. Należy pamiętać, że aplikacje ASP.NET są aplikacjami zarządzanymi i w związku z tym mogą używać tych samych klas, co inne zarządzane aplikacje do pobierania, wyświetlania i manipulowania informacjami w oparciu o kulturę.

3. Należy pamiętać, że można określić następujące trzy typy kodowania w ASP.NET:

    - requestEncoding określa kodowanie otrzymane z przeglądarki klienta.

    - responseEncoding określa kodowanie do wysłania do przeglądarki klienta. W większości sytuacji to kodowanie powinno być takie samo, jak określone dla requestEncoding.

    - fileEncoding określa domyślne kodowanie dla analizy plików aspx, asmx i. asax.

4. Określ wartości atrybutów requestEncoding, responseEncoding, fileEncoding, Culture i uiCulture w następujących trzech miejscach w aplikacji ASP.NET:

    - W sekcji globalizacji w pliku Web. config. Ten plik jest zewnętrzny względem aplikacji ASP.NET. Aby uzyskać więcej informacji, zobacz [\<globalizacja > elementu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hy4kkhe0(v=vs.100)).

    - W dyrektywie page. Pamiętaj, że gdy aplikacja znajduje się na stronie, plik został już odczytany. W związku z tym jest zbyt późno, aby określić fileEncoding i requestEncoding. Tylko uiCulture, Culture i responseEncoding można określić w dyrektywie page.

    - Programowo w kodzie aplikacji. To ustawienie może się różnić w zależności od żądania. Podobnie jak w przypadku dyrektywy Page, przez czas osiągnięcia kodu aplikacji, jest zbyt późno na określenie fileEncoding i requestEncoding. Tylko uiCulture, Culture i responseEncoding można określić w kodzie aplikacji.

5. Należy pamiętać, że wartość uiCulture można ustawić na język akceptowania przeglądarki.

## <a name="see-also"></a>Zobacz także

- [Globalizacja i lokalizacja](../../../docs/standard/globalization-localization/index.md)
- [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)
