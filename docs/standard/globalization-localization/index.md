---
title: Globalizacja i lokalizowanie aplikacji .NET
ms.date: 06/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- international applications [.NET]
- globalization [.NET], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
ms.openlocfilehash: eae1c38c2383d13bfb4dab83f2fe9551970b39f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120886"
---
# <a name="globalizing-and-localizing-net-applications"></a>Globalizacja i lokalizowanie aplikacji .NET

Opracowanie aplikacji gotowej na świat, w tym aplikacji, która może być zlokalizowana w jednym lub kilku językach, obejmuje trzy kroki: globalizację, przegląd możliwości lokalizowania i lokalizację.

[Globalizacja](globalization.md)

Ten krok obejmuje projektowanie i programowanie aplikacji neutralnej kulturowo i językowo, która obsługuje zlokalizowane interfejsy użytkownika i dane regionalne dla wszystkich użytkowników. Obejmuje to podejmowanie decyzji projektowych i programistycznych, które nie są oparte na założeniach specyficznych dla kultury. Aplikacja zglobalizowana nie jest zlokalizowana, ale została zaprojektowana i napisana tak, że jej lokalizacja w jednym lub kilku językach będzie stosunkowo łatwa.

[Sprawdzenie możliwości lokalizacji](localizability-review.md)

Ten krok obejmuje przegląd kodu i projektu aplikacji w celu upewnienia się, że można go łatwo zlokalizować i zidentyfikować potencjalne przeszkody dla lokalizacji, oraz potwierdzenia, że kod wykonywalny aplikacji jest oddzielony od jej zasobów. Jeśli etap globalizacji był skuteczny, przegląd możliwości zlokalizowania potwierdzi wybory dotyczące projektowania i kodowania dokonane podczas globalizacji. Na etapie przeglądu możliwości lokalizacji można również zidentyfikować pozostałe problemy, dzięki czemu nie trzeba będzie modyfikować kodu aplikacji na etapie lokalizacji.

[Lokalizacja](localization.md)

Ten krok obejmuje dostosowywanie aplikacji do określonych kultur lub regionów. Jeśli etapy globalizacji i przeglądu możliwości lokalizacji zostały wykonane poprawnie, lokalizacja składa się głównie z tłumaczenia interfejsu użytkownika.

Wykonanie tych trzech kroków ma dwie zalety:

- Uwalnia użytkownika od konieczności przeprojektowywania aplikacji, której konstrukcja przewiduje obsługę jednej kultury, takiej jak Angielski-Stany Zjednoczone, w celu obsługi dodatkowych kultur.

- Skutkuje zlokalizowanymi aplikacjami, które są stabilniejsze i zawierają mniej błędów.

.NET zapewnia szerokie wsparcie dla rozwoju aplikacji gotowych na świat i zlokalizowanych. W szczególności wiele elementów członkowskich typu w bibliotece klasy .NET pomocy globalizacji przez zwracanie wartości, które odzwierciedlają konwencje kultury bieżącego użytkownika lub określonej kultury. Ponadto .NET obsługuje zestawy satelickie, które ułatwiają proces lokalizowania aplikacji.

Aby uzyskać dodatkowe informacje, zobacz [dokumentację globalizacji](/globalization/).

## <a name="in-this-section"></a>W tej sekcji

[Globalizacja](globalization.md)

Omówienie pierwszego etapu tworzenia aplikacji gotowych do użycia na całym świecie, który obejmuje projektowanie i programowanie aplikacji neutralnej językowo i kulturowo.

[Sprawdzenie możliwości lokalizacji](localizability-review.md)

Omówienie drugiego etapu tworzenia zlokalizowanych aplikacji, który obejmuje określenie potencjalnych przeszkód w procesie lokalizacji.

[Lokalizacja](localization.md)

Omówienie końcowego etapu tworzenia zlokalizowanych aplikacji, który polega na dostosowywaniu interfejsu użytkownika aplikacji dla określonych regionów lub kultur.

[Niezależne od kultury operacje na ciągach](culture-insensitive-string-operations.md)

W tym artykule opisano, jak używać metod i klas .NET, które są domyślnie zależne od kultury, aby uzyskać wyniki niewrażliwe na kulturę.

[Najlepsze praktyki dotyczące tworzenia aplikacji gotowych do pracy na całym świecie](best-practices-for-developing-world-ready-apps.md)

Opis najlepszych rozwiązań w zakresie globalizacji, lokalizacji i projektowania gotowych do użycia na całym świecie aplikacji ASP.NET.

## <a name="reference"></a>Dokumentacja

- <xref:System.Globalization?displayProperty=nameWithType>Namespace

   Zawiera klasy, które definiują informacje związane z kulturą, w tym język, kraj/region, używane kalendarze, wzorce formatu daty, waluty i liczb oraz kolejność sortowania dla ciągów.

- <xref:System.Resources>Namespace

   Udostępnia klasy służące do tworzenia i używania zasobów oraz wykonywania na nich operacji.

- <xref:System.Text>Namespace

   Zawiera klasy reprezentujące kodowania znaków ASCII, ANSI, Unicode i inne.

- [Resgen.exe (generator pliku zasobów)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)

   Opis sposobu używania programu Resgen.exe w celu konwertowania plików z rozszerzeniem txt i zasobów opartych na formacie języka XML (resx) na pliki binarne resources środowiska uruchomieniowego języka wspólnego.

- [Winres.exe (Edytor zasobów formularzy systemu Windows)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)

   Opis sposobu używania programu Winres.exe w celu lokalizowania formularzy programu Windows Forms.
