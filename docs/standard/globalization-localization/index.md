---
title: Globalizacja i lokalizacja aplikacji .NET Framework
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- international applications [.NET Framework]
- globalization [.NET Framework], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET Framework], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
caps.latest.revision: 42
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 63f0e001280773c55f18f0604ca93986acbb9674
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="globalizing-and-localizing-net-framework-applications"></a>Globalizacja i lokalizacja aplikacji .NET Framework
Tworzenie [aplikacji gotowe](http://msdn.microsoft.com/goglobal/bb978433.aspx), w tym aplikacji, która może być lokalizowany do co najmniej jednego języka, obejmuje trzy kroki: sprawdzenie, lokalizacja i globalizacja.  
  
 [Globalizacja](../../../docs/standard/globalization-localization/globalization.md)  
 Ten krok obejmuje projektowanie i programowanie aplikacji neutralnej kulturowo i językowo, która obsługuje zlokalizowane interfejsy użytkownika i dane regionalne dla wszystkich użytkowników. Obejmuje to podejmowanie decyzji projektowych i programistycznych, które nie są oparte na założeniach specyficznych dla kultury. Aplikacja zglobalizowana nie jest zlokalizowana, ale została zaprojektowana i napisana tak, że jej lokalizacja w jednym lub kilku językach będzie stosunkowo łatwa.  
  
 [Sprawdzenie możliwości lokalizacji](../../../docs/standard/globalization-localization/localizability-review.md)  
 Ten krok obejmuje przegląd kodu i projektu aplikacji w celu upewnienia się, że można go łatwo zlokalizować i zidentyfikować potencjalne przeszkody dla lokalizacji, oraz potwierdzenia, że kod wykonywalny aplikacji jest oddzielony od jej zasobów. Jeśli etap globalizacji był skuteczny, przegląd możliwości zlokalizowania potwierdzi wybory dotyczące projektowania i kodowania dokonane podczas globalizacji. Na etapie przeglądu możliwości lokalizacji można również zidentyfikować pozostałe problemy, dzięki czemu nie trzeba będzie modyfikować kodu aplikacji na etapie lokalizacji.  
  
 [Lokalizacja](../../../docs/standard/globalization-localization/localization.md)  
 Ten krok obejmuje dostosowywanie aplikacji do określonych kultur lub regionów. Jeśli etapy globalizacji i przeglądu możliwości lokalizacji zostały wykonane poprawnie, lokalizacja składa się głównie z tłumaczenia interfejsu użytkownika.  
  
 Wykonanie tych trzech kroków ma dwie zalety:  
  
-   Go zwalnia z konieczności zakresie wyposażenia aplikacji, która jest przeznaczona do obsługi pojedynczego kultury, takie jak stany USA Angielski, do obsługi dodatkowych kultur.  
  
-   Skutkuje zlokalizowanymi aplikacjami, które są stabilniejsze i zawierają mniej błędów.  
  
 Program .NET Framework oferuje zaawansowaną obsługę dla rozwoju aplikacji gotowych do użycia na całym świecie i aplikacji zlokalizowanych. W szczególności wiele składowych typów w bibliotece klas programu .NET Framework wspiera globalizację, zwracając wartości, które odzwierciedlają konwencje kultury bieżącego użytkownika lub określonej kultury. Program .NET Framework obsługuje także zestawy satelickie, które ułatwiają proces lokalizowania aplikacji.  
  
 Aby uzyskać dodatkowe informacje, zobacz [dokumentacji globalizacji](/globalization/).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Globalizacja](../../../docs/standard/globalization-localization/globalization.md)  
 Omówienie pierwszego etapu tworzenia aplikacji gotowych do użycia na całym świecie, który obejmuje projektowanie i programowanie aplikacji neutralnej językowo i kulturowo.  
  
 [Sprawdzenie możliwości lokalizacji](../../../docs/standard/globalization-localization/localizability-review.md)  
 Omówienie drugiego etapu tworzenia zlokalizowanych aplikacji, który obejmuje określenie potencjalnych przeszkód w procesie lokalizacji.  
  
 [Lokalizacja](../../../docs/standard/globalization-localization/localization.md)  
 Omówienie końcowego etapu tworzenia zlokalizowanych aplikacji, który polega na dostosowywaniu interfejsu użytkownika aplikacji dla określonych regionów lub kultur.  
  
 [Niezależne od kultury operacje na ciągach](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 Opis sposobu użycia metod i klas programu .NET Framework, które domyślnie są zależne od kultury w celu uzyskania wyników niezależnych od kultury.  
  
 [Najlepsze rozwiązania dotyczące tworzenia aplikacji gotowych do wydania](../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md)  
 Opis najlepszych rozwiązań w zakresie globalizacji, lokalizacji i projektowania gotowych do użycia na całym świecie aplikacji ASP.NET.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Globalization?displayProperty=nameWithType>przestrzeń nazw  
 Zawiera klasy, które definiują informacje związane z kulturą, w tym język, kraj/region, używane kalendarze, wzorce formatu daty, waluty i liczb oraz kolejność sortowania dla ciągów.  
  
 <xref:System.Resources>przestrzeń nazw  
 Udostępnia klasy służące do tworzenia i używania zasobów oraz wykonywania na nich operacji.  
  
 <xref:System.Text>przestrzeń nazw  
 Zawiera klasy reprezentujące kodowania znaków ASCII, ANSI, Unicode i inne.  
  
 [Resgen.exe (generator pliku zasobów)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 Opis sposobu używania programu Resgen.exe w celu konwertowania plików z rozszerzeniem txt i zasobów opartych na formacie języka XML (resx) na pliki binarne resources środowiska uruchomieniowego języka wspólnego.  
  
 [Winres.exe (Edytor zasobów formularzy Windows Forms)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)  
 Opis sposobu używania programu Winres.exe w celu lokalizowania formularzy programu Windows Forms.
