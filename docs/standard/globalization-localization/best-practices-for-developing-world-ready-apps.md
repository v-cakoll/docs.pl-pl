---
title: "Najlepsze praktyki dotyczące tworzenia aplikacji gotowych do wydania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- global applications, best practices
- world-ready applications, best practices
- globalization [.NET Framework], best practices
- international applications [.NET Framework], best practices
ms.assetid: f08169c7-aad8-4ec3-9a21-9ebd3b89986c
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8a50080fa4b84abe84fbb1a44f18e1fb680a07c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="best-practices-for-developing-world-ready-applications"></a>Najlepsze praktyki dotyczące tworzenia aplikacji gotowych do wydania
W tej sekcji opisano najlepszych rozwiązań, które należy wykonać podczas tworzenia aplikacji gotowych.  
  
## <a name="globalization-best-practices"></a>Najlepsze rozwiązania w zakresie globalizacji  
  
1.  Należy wewnętrznie aplikacja Unicode.  
  
2.  Używać klas obsługujących kultury podał <xref:System.Globalization> przestrzeni nazw do manipulowania i formatowanie danych.  
  
    -   Do sortowania, użyj <xref:System.Globalization.SortKey> klasy i <xref:System.Globalization.CompareInfo> klasy.  
  
    -   Porównywanie ciągów, można użyć <xref:System.Globalization.CompareInfo> klasy.  
  
    -   Formatowania daty i czasu, użyj <xref:System.Globalization.DateTimeFormatInfo> klasy.  
  
    -   Formatowanie, użyj <xref:System.Globalization.NumberFormatInfo> klasy.  
  
    -   Kalendarzy — gregoriańskiego i innych niż gregoriański, użyj <xref:System.Globalization.Calendar> klasy lub jednej z implementacji określonego kalendarza.  
  
3.  Użyj ustawienia właściwości kultury dostarczone przez <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> klasy w odpowiednich przypadkach. Użyj <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> właściwości formatowania zadań, takich jak daty i godziny lub formatowanie. Użyj <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> właściwości można pobrać zasobów. Należy pamiętać, że `CurrentCulture` i `CurrentUICulture` właściwości można ustawić na wątek.  
  
4.  Zezwalaj aplikacji na odczytywanie i zapisywanie danych do i z różnych kodowań przy użyciu kodowania klas w <xref:System.Text> przestrzeni nazw. Nie należy zakładać danych ASCII. Załóżmy dostarczenia znaki międzynarodowe dowolnym użytkownik może wprowadzić tekst. Na przykład aplikacja powinna obsługiwać znaków międzynarodowych nazw serwerów, katalogów, nazwy pliku, nazwy użytkowników i adresów URL.  
  
5.  Korzystając z <xref:System.Text.UTF8Encoding> klasy, ze względów bezpieczeństwa używać funkcji wykrywania błędów oferowane przez tę klasę. Aby włączyć funkcję wykrywania błędów, aplikacja tworzy wystąpienie klasy przy użyciu konstruktora, który przyjmuje `throwOnInvalidBytes` parametru i ustawia wartość tego parametru, aby `true`.  
  
6.  Jeśli to możliwe, dojście ciągi jako ciągi całego zamiast jako serię znaki. Jest to szczególnie ważne podczas sortowania i wyszukiwania podciągów. Pozwoli to uniknąć problemów związanych z przetwarzaniem łączenie znaków.  
  
7.  Wyświetlanie tekstu przy użyciu klas dostarczonych przez <xref:System.Drawing> przestrzeni nazw.  
  
8.  W celu zachowania spójności we wszystkich systemach operacyjnych, nie zezwalaj na zastąpienie ustawień użytkownika <xref:System.Globalization.CultureInfo>. Użyj `CultureInfo` konstruktora akceptującego `useUserOverride` parametru i wartości `false`.  
  
9. Testowanie funkcji z aplikacji na międzynarodowe wersje systemów operacyjnych, przy użyciu danych w różnych językach.  
  
10. Decyzja zabezpieczeń jest na podstawie wyniku porównania ciągów lub przypadku zmiana operacji, należy mieć aplikacji niezależnych od kultury operacji. Daje to gwarancję, że wynik nie ma wpływu na wartość `CultureInfo.CurrentCulture`. Zobacz sekcję "Ciąg porównania który Użyj bieżącej kultury" [najlepsze rozwiązania dotyczące ciągów za pomocą](../../../docs/standard/base-types/best-practices-strings.md) na przykład, który demonstruje sposób zależne od kultury ciąg porównania może spowodować niespójne wyniki.  
  
## <a name="localization-best-practices"></a>Najlepsze rozwiązania lokalizacji  
  
1.  Przenieś wszystkie zasoby Lokalizowalny do oddzielania pliki DLL tylko z zasobów. Lokalizowalny zasoby obejmują elementy interfejsu użytkownika, takie jak ciągi, komunikaty o błędach, okna dialogowe, menu i zasoby osadzone.  
  
2.  Czy nie umieszczaj ciągów lub zasoby interfejsu użytkownika.  
  
3.  Nie należy umieszczać nonlocalizable zasobów do biblioteki DLL tylko z zasobami. To powodować problemy interpretacyjne dla tłumaczy.  
  
4.  Nie nie te złożone ciągów użycia, które są tworzone w czasie wykonywania z połączonych fraz. Ciągi złożone są trudne do zlokalizowania, ponieważ często zakładają angielskiej wersji językowej gramatyczne kolejności nie ma zastosowania do wszystkich języków.  
  
5.  Unikaj niejednoznaczne konstrukcje, takich jak "Pusty Folder" gdzie ciągi można przetłumaczyć inaczej w zależności od gramatyczne ról składników ciąg. Na przykład "pusta" może być zlecenie lub przymiotnik, co może prowadzić do tłumaczenia różnych języków, takich jak włoski lub francuski.  
  
6.  Unikaj używania obrazów i ikon, zawierających tekst w aplikacji. Są one kosztowne do zlokalizowania.  
  
7.  Zezwalaj na dużej ilości miejsca dla długość ciągów, aby rozwinąć w interfejsie użytkownika. W przypadku niektórych języków wyrażenia może wymagać 50-75 procent wymagają więcej miejsca niż ich w innych językach.  
  
8.  Użyj <xref:System.Resources.ResourceManager?displayProperty=nameWithType> można pobrać zasobów na podstawie kultury.  
  
9. Użyć programu Visual Studio do tworzenia okien dialogowych formularzy systemu Windows, dzięki czemu może być lokalizowany, za pomocą [Edytor zasobów formularzy systemu Windows (Winres.exe)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md). Nie ręcznie kodu dialogowe w formularzach systemu Windows.  
  
10. Rozmieść lokalizacji professional (tłumaczenia).  
  
11. Aby uzyskać pełny opis tworzenia i lokalizowanie zasobów, zobacz [zasobów w aplikacjach](../../../docs/framework/resources/index.md).  
  
## <a name="globalization-best-practices-for-aspnet-applications"></a>Globalizacja najlepsze rozwiązania dla aplikacji ASP.NET  
  
1.  Jawnie ustawiona <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> i <xref:System.Globalization.CultureInfo.CurrentCulture%2A> właściwości w aplikacji. Nie należy polegać na wartości domyślne.  
  
2.  Należy pamiętać, że aplikacje ASP.NET są aplikacje zarządzane i w związku z tym można użyć tej samej klasy co inne zarządzane aplikacje do pobierania, wyświetlanie i operowanie nimi informacji na podstawie kultury.  
  
3.  Należy pamiętać, że w programie ASP.NET można określić następujące trzy rodzaje kodowania:  
  
    -   requestEncoding Określa kodowanie otrzymanych od przeglądarki klienta.  
  
    -   responseEncoding Określa kodowanie do wysłania do przeglądarki klienta. W większości przypadków kodowanie powinna być taka sama jak określona dla requestEncoding.  
  
    -   kodowanie plików określa domyślne kodowanie plików .aspx, .asmx i .asax plików.  
  
4.  Określ wartości dla atrybutów requestEncoding, responseEncoding kodowanie plików, kultury i uiCulture w następujących trzech miejscach w aplikacji ASP.NET:  
  
    -   W sekcji globalizacji w pliku Web.config. Ten plik jest zewnętrzne do aplikacji ASP.NET. Aby uzyskać więcej informacji, zobacz [ \<globalizacji > elementu](http://msdn.microsoft.com/en-us/e2dffc8e-ebd2-439b-a2fd-e3ac5e620da7).  
  
    -   W dyrektywie page. Należy pamiętać, że gdy aplikacja znajduje się na stronie, plik jest już przeczytana. W związku z tym jest za późno na Określ kodowanie plików i requestEncoding. Można określić tylko uiCulture, kultury i responseEncoding w dyrektywie page.  
  
    -   W kodzie aplikacji. To ustawienie może się różnić na żądanie. Zgodnie z dyrektywą strony w czasie kodu aplikacji w osiągnięciu on jest za późno na Określ kodowanie plików i requestEncoding. Można określić tylko uiCulture, kultury i responseEncoding w kodzie aplikacji.  
  
5.  Należy pamiętać, że wartość uiCulture można ustawić w przeglądarce zaakceptować języka.  
  
## <a name="see-also"></a>Zobacz też  
 [Lokalizacja i globalizacja](../../../docs/standard/globalization-localization/index.md)  
 [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)
